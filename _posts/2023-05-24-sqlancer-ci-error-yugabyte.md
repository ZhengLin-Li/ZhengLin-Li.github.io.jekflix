https://github.com/sqlancer/sqlancer/issues/789

1. Function to create database: sqlancer.yugabyte.ysql.getCreateDatabaseCommand

1. Function to create table: sqlancer.yugabyte.ysql.createTables

1. Function to create table: sqlancer.yugabyte.ysql.gen.generate

1. Function to create tablegroup option: sqlancer.yugabyte.ysql.gen.create

Question is how to let the 4th function know that the 1st function has set a flag on the database?

Resolved:

We can determine that sqlancer/yugabyte/ysql/YSQLSchema.java is per database level. 

So we can run a `SELECT yb_is_database_colocated();` query on it to tell if it is a collocated database. The query will result in a 'f' for a non-colocated database.

Final PR: https://github.com/sqlancer/sqlancer/pull/795
