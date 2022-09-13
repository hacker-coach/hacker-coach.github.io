
# mysqldump

## GET BIG TABELS

SELECT table_name AS "Table", ROUND(((data_length + index_length) / 1024 / 1024), 2) AS "Size (MB)" FROM information_schema.TABLES WHERE table_schema =
'magento_db' AND ROUND(((data_length + index_length) / 1024 / 1024), 2)>=100 ORDER BY (data_length + index_length) DESC

## SCHEMA

mysqldump -u magento_db -h localhost -p'xxxxx' --databases  magento_db --no-data  --result-file=mmagento_db_schema.sql

## IGNORE

mysqldump -u magento_2_1 -h localhost -p'xxxxx' --databases  magento_db
--no-create-info
--ignore-table=magento_db.user
--ignore-table=magento_db.adress
--result-file=ignore_big_all_magento_2_1_data.sql

## NO CREATE

mysqldump -u magento_2_1 -h localhost -p'xxxxx' --databases  magento_db 
--no-create-info magento_db.user --result-file=magento_db_user.sql

## ELSE

### import (with pv)

pv db_dump.sql | mysql -u <user> -p'<password>' <database> > error.log

### import (without pv)

mysql -u <user> -p'<password>' <database> < db_dump.sql > error.log

### export

mysqldump -u <user> -h <host> -p'<password>' <database> | pv > db_dump.sql

mysqldump -u <user> -h <host> -p<password> <database> | pv --size 100m > db_dump.sql

<https://dba.stackexchange.com/questions/83125/mysql-any-way-to-import-a-huge-32-gb-sql-dump-faster>

<https://newbedev.com/mysql-dump-exclude-some-table-data>