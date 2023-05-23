I looked up the databend ci error: https://pipelines.actions.githubusercontent.com/serviceHosts/b763c072-24a0-4f4f-8d39-a81ced1119da/_apis/pipelines/1/runs/12/signedlogcontent/10?urlExpires=2023-05-23T12%3A27%3A59.5785928Z&urlSigningMethod=HMACV1&urlSignature=Qbwv7qaydkNIXnXueuWXeSnXQ6tzFBgBAj2WN5FR%2BWU%3D

first error:

```
2023-05-23T06:05:34.4059419Z [2023/05/23 06:05:34] Executed 26 queries (5 queries/s; 0.80/s dbs, successful statements: 93%). Threads shut down: 0.
2023-05-23T06:05:35.1206915Z java.lang.AssertionError: SELECT SUM(count) FROM (SELECT (((0.9505856037139893 NOT BETWEEN 0.7793450355529785 AND 9.69433728E8) IS NOT NULL AND (0.9505856037139893 NOT BETWEEN 0.7793450355529785 AND 9.69433728E8)) ::BIGINT)as count FROM t1) as res;
2023-05-23T06:05:35.1207950Z 	at sqlancer.common.query.SQLQueryAdapter.checkException(SQLQueryAdapter.java:111)
2023-05-23T06:05:35.1208693Z 	at sqlancer.common.query.SQLQueryAdapter.executeAndGet(SQLQueryAdapter.java:141)
2023-05-23T06:05:35.1209338Z 	at sqlancer.common.query.Query.executeAndGetLogged(Query.java:51)
2023-05-23T06:05:35.1210582Z 	at sqlancer.databend.test.DatabendNoRECOracle.getUnoptimizedQueryCount(DatabendNoRECOracle.java:90)
2023-05-23T06:05:35.1211757Z 	at sqlancer.databend.test.DatabendNoRECOracle.check(DatabendNoRECOracle.java:60)
2023-05-23T06:05:35.1212491Z 	at sqlancer.ProviderAdapter.generateAndTestDatabase(ProviderAdapter.java:61)
2023-05-23T06:05:35.1213055Z 	at sqlancer.Main$DBMSExecutor.run(Main.java:364)
2023-05-23T06:05:35.1213486Z 	at sqlancer.Main$2.run(Main.java:559)
2023-05-23T06:05:35.1213904Z 	at sqlancer.Main$2.runThread(Main.java:541)
2023-05-23T06:05:35.1214299Z 	at sqlancer.Main$2.run(Main.java:532)
2023-05-23T06:05:35.1214872Z 	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
2023-05-23T06:05:35.1215591Z 	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
2023-05-23T06:05:35.1216159Z 	at java.base/java.lang.Thread.run(Thread.java:829)
2023-05-23T06:05:35.1216647Z Caused by: java.sql.SQLException: Code: 1001, Text = error: 
2023-05-23T06:05:35.1217292Z   --> SQL:1:174
2023-05-23T06:05:35.1217611Z   |
2023-05-23T06:05:35.1218133Z 1 | SELECT SUM(count) FROM (SELECT (((0.9505856037139893 NOT BETWEEN 0.7793450355529785 AND 9.69433728E8) IS NOT NULL AND (0.9505856037139893 NOT BETWEEN 0.7793450355529785 AND 9.69433728E8)) ::BIGINT)as count FROM t1) as res;
2023-05-23T06:05:35.1218856Z   |                                                                                                                                                                              ^^^^^^^^^^^^ Decimal overflow at line : 906 while evaluating function `to_decimal(25, 16)(969433728)`
2023-05-23T06:05:35.1252144Z 
2023-05-23T06:05:35.1252784Z .
2023-05-23T06:05:35.1253451Z 	at com.mysql.cj.jdbc.exceptions.SQLError.createSQLException(SQLError.java:129)
2023-05-23T06:05:35.1254279Z 	at com.mysql.cj.jdbc.exceptions.SQLExceptionsMapping.translateException(SQLExceptionsMapping.java:122)
2023-05-23T06:05:35.1255173Z 	at com.mysql.cj.jdbc.StatementImpl.executeQuery(StatementImpl.java:1200)
2023-05-23T06:05:35.1255840Z 	at sqlancer.common.query.SQLQueryAdapter.executeAndGet(SQLQueryAdapter.java:131)
2023-05-23T06:05:35.1256371Z 	... 11 more
2023-05-23T06:05:35.1258025Z --java.lang.AssertionError: SELECT SUM(count) FROM (SELECT (((0.9505856037139893 NOT BETWEEN 0.7793450355529785 AND 9.69433728E8) IS NOT NULL AND (0.9505856037139893 NOT BETWEEN 0.7793450355529785 AND 9.69433728E8)) ::BIGINT)as count FROM t1) as res;
2023-05-23T06:05:35.1258981Z --	at sqlancer.common.query.SQLQueryAdapter.checkException(SQLQueryAdapter.java:111)
2023-05-23T06:05:35.1259820Z --	at sqlancer.common.query.SQLQueryAdapter.executeAndGet(SQLQueryAdapter.java:141)
2023-05-23T06:05:35.1260581Z --	at sqlancer.common.query.Query.executeAndGetLogged(Query.java:51)
2023-05-23T06:05:35.1261455Z --	at sqlancer.databend.test.DatabendNoRECOracle.getUnoptimizedQueryCount(DatabendNoRECOracle.java:90)
2023-05-23T06:05:35.1262650Z --	at sqlancer.databend.test.DatabendNoRECOracle.check(DatabendNoRECOracle.java:60)
2023-05-23T06:05:35.1263466Z --	at sqlancer.ProviderAdapter.generateAndTestDatabase(ProviderAdapter.java:61)
2023-05-23T06:05:35.1264135Z --	at sqlancer.Main$DBMSExecutor.run(Main.java:364)
2023-05-23T06:05:35.1264634Z --	at sqlancer.Main$2.run(Main.java:559)
2023-05-23T06:05:35.1265131Z --	at sqlancer.Main$2.runThread(Main.java:541)
2023-05-23T06:05:35.1265612Z --	at sqlancer.Main$2.run(Main.java:532)
2023-05-23T06:05:35.1266313Z --	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
2023-05-23T06:05:35.1267131Z --	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
2023-05-23T06:05:35.1267784Z --	at java.base/java.lang.Thread.run(Thread.java:829)
2023-05-23T06:05:35.1268344Z --Caused by: java.sql.SQLException: Code: 1001, Text = error: 
2023-05-23T06:05:35.1268791Z --  --> SQL:1:174
2023-05-23T06:05:35.1269135Z --  |
2023-05-23T06:05:35.1270191Z --1 | SELECT SUM(count) FROM (SELECT (((0.9505856037139893 NOT BETWEEN 0.7793450355529785 AND 9.69433728E8) IS NOT NULL AND (0.9505856037139893 NOT BETWEEN 0.7793450355529785 AND 9.69433728E8)) ::BIGINT)as count FROM t1) as res;
2023-05-23T06:05:35.1271383Z --  |                                                                                                                                                                              ^^^^^^^^^^^^ Decimal overflow at line : 906 while evaluating function `to_decimal(25, 16)(969433728)`
2023-05-23T06:05:35.1271856Z --
2023-05-23T06:05:35.1272177Z --.
2023-05-23T06:05:35.1272783Z --	at com.mysql.cj.jdbc.exceptions.SQLError.createSQLException(SQLError.java:129)
2023-05-23T06:05:35.1273711Z --	at com.mysql.cj.jdbc.exceptions.SQLExceptionsMapping.translateException(SQLExceptionsMapping.java:122)
2023-05-23T06:05:35.1274573Z --	at com.mysql.cj.jdbc.StatementImpl.executeQuery(StatementImpl.java:1200)
2023-05-23T06:05:35.1275336Z --	at sqlancer.common.query.SQLQueryAdapter.executeAndGet(SQLQueryAdapter.java:131)
2023-05-23T06:05:35.1275889Z --	... 11 more
2023-05-23T06:05:35.1276220Z --
2023-05-23T06:05:35.1276573Z -- Time: 2023/05/23 06:05:35
2023-05-23T06:05:35.1276971Z -- Database: databend3
2023-05-23T06:05:35.1277716Z -- Database version: 8.0.26-v1.1.44-nightly-d3a40d91b8a8ebaf878344e024164f36b6db5615(rust-1.70.0-nightly-2023-05-22T16:06:17.993138014Z)
2023-05-23T06:05:35.1278360Z -- seed value: 3
2023-05-23T06:05:35.1278701Z DROP DATABASE IF EXISTS databend3;
2023-05-23T06:05:35.1279054Z CREATE DATABASE databend3;
2023-05-23T06:05:35.1279370Z USE databend3;
2023-05-23T06:05:35.1279704Z CREATE TABLE t0(c0FLOAT DOUBLE NULL);
2023-05-23T06:05:35.1280075Z CREATE TABLE t1(c0FLOAT DOUBLE NOT NULL);
2023-05-23T06:05:35.1280446Z CREATE TABLE t2(c0BOOLEAN BOOLEAN NULL DEFAULT(true));
2023-05-23T06:05:35.1280846Z INSERT INTO t1(c0float) VALUES (0.4581953287124634);
2023-05-23T06:05:35.1281433Z INSERT INTO t1(c0float) VALUES (0.4581953287124634);
2023-05-23T06:05:35.1281868Z INSERT INTO t0(c0float) VALUES (0.17081978917121887), (0.17081978917121887);
2023-05-23T06:05:35.1282297Z INSERT INTO t1(c0float) VALUES (0.13291344046592712);
2023-05-23T06:05:35.1282707Z INSERT INTO t0(c0float) VALUES (0.8306243419647217);
2023-05-23T06:05:35.1283122Z INSERT INTO t0(c0float) VALUES (0.6578136682510376);
2023-05-23T06:05:35.1283500Z INSERT INTO t2(c0boolean) VALUES (false);
2023-05-23T06:05:35.1283884Z INSERT INTO t2(c0boolean) VALUES (true);
2023-05-23T06:05:35.1284288Z INSERT INTO t1(c0float) VALUES (0.17081978917121887);
2023-05-23T06:05:35.1284684Z INSERT INTO t2(c0boolean) VALUES (true);
2023-05-23T06:05:35.1285086Z INSERT INTO t0(c0float) VALUES (0.9505856037139893);
2023-05-23T06:05:35.1285526Z INSERT INTO t0(c0float) VALUES (0.7793450355529785), (0.6578136682510376), (0.25081709027290344);
2023-05-23T06:05:35.1285919Z DELETE FROM t1;
2023-05-23T06:05:35.1286278Z INSERT INTO t2(c0boolean) VALUES (true), (true);
2023-05-23T06:05:35.1286685Z INSERT INTO t2(c0boolean) VALUES (false);
2023-05-23T06:05:35.1287375Z CREATE VIEW v0 AS SELECT t1.c0float FROM t2, t0, t1 HAVING (('h')LIKE('v'));
2023-05-23T06:05:35.1287879Z INSERT INTO t0(c0float) VALUES (0.7793450355529785), (0.6772184371948242), (0.7793450355529785);
2023-05-23T06:05:35.1288351Z INSERT INTO t1(c0float) VALUES (0.3583638370037079), (0.4581953287124634), (0.31328457593917847);
2023-05-23T06:05:35.1288776Z INSERT INTO t2(c0boolean) VALUES (false);
2023-05-23T06:05:35.1289177Z INSERT INTO t2(c0boolean) VALUES (true);
2023-05-23T06:05:35.1289851Z INSERT INTO t1(c0float) VALUES (0.6578136682510376);
2023-05-23T06:05:35.1290405Z INSERT INTO t2(c0boolean) VALUES (false), (false), (true);
2023-05-23T06:05:35.1303837Z INSERT INTO t2(c0boolean) VALUES (false);
2023-05-23T06:05:35.1304697Z INSERT INTO t0(c0float) VALUES (0.3583638370037079);
2023-05-23T06:05:35.1305137Z EXPLAIN SELECT DISTINCT t0.c0float FROM t0 HAVING (((0.6772184371948242 NOT IN (0.46048539876937866))) IS NOT NULL);
2023-05-23T06:05:35.1305524Z INSERT INTO t0(c0float) VALUES (0.7772102952003479);
2023-05-23T06:05:35.1305872Z INSERT INTO t2(c0boolean) VALUES (true);
2023-05-23T06:05:35.1306201Z INSERT INTO t0(c0float) VALUES (0.6578136682510376);
```

It semas that there is a overflow

look at the `java.lang.AssertionError: SELECT SUM(count) FROM (SELECT (((0.9505856037139893 NOT BETWEEN 0.7793450355529785 AND 9.69433728E8) IS NOT NULL AND (0.9505856037139893 NOT BETWEEN 0.7793450355529785 AND 9.69433728E8)) ::BIGINT)as count FROM t1) as res;`

It is the cause of `Decimal overflow at line : 906 while evaluating function `to_decimal(25, 16)(969433728)``

refer: https://databend.rs/doc/sql-reference/data-types/data-type-decimal-types

