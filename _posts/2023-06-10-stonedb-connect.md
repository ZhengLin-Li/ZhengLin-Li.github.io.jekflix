

https://stonedb.io/docs/getting-started/quick-deploy-in-docker

```bash
docker pull stoneatom/stonedb
docker run -p 3306:3306 -itd  -e MYSQL_ROOT_PASSWORD='123456'  stoneatom/stonedb
docker ps
docker exec -it <Container ID> bash
/opt/stonedb57/install/bin/mysql -uroot -p123456
```


https://stonedb.io/docs/getting-started/quick-start


```sql
create database test DEFAULT CHARACTER SET utf8mb4;
use test
CREATE TABLE t_user(
  id INT NOT NULL AUTO_INCREMENT,
  first_name VARCHAR(20) NOT NULL,
  last_name VARCHAR(20) NOT NULL,
  sex VARCHAR(5) NOT NULL,
  score INT NOT NULL,
  copy_id INT NOT NULL,
  PRIMARY KEY (`id`)
) engine=tianmu;

CREATE TABLE t_user_innodb(
  id INT NOT NULL AUTO_INCREMENT,
  first_name VARCHAR(20) NOT NULL,
  last_name VARCHAR(20) NOT NULL,
  sex VARCHAR(5) NOT NULL,
  score INT NOT NULL,
  copy_id INT NOT NULL,
  PRIMARY KEY (`id`)
) engine=innodb;

SHOW TABLE STATUS WHERE Name = 't_user';
SHOW TABLE STATUS WHERE Name = 't_user_innodb';
```


useful statements:

```sql
select TABLE_NAME, ENGINE from information_schema.TABLES where table_schema = 'test';

select * from information_schema.columns where table_schema = 'test' AND TABLE_NAME='t_user';

SHOW TABLE STATUS WHERE Name = 't_user';

DESCRIBE table2;

CREATE TEMPORARY TABLE IF NOT EXISTS table2 AS (select * from information_schema.columns where table_schema = 'test' AND TABLE_NAME='t_user');
```
