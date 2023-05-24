https://github.com/sqlancer/sqlancer/issues/789

1. Function to create database: sqlancer.yugabyte.ysql.getCreateDatabaseCommand

1. Function to create table: sqlancer.yugabyte.ysql.createTables

1. Function to create table: sqlancer.yugabyte.ysql.gen.generate

1. Function to create tablegroup option: sqlancer.yugabyte.ysql.gen.create

Question is how to let the 4th function know that the 1st function has set a flag on the database?
