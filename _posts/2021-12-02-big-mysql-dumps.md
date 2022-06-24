---
title: IMPORT big-mysql-dumps > 30 GB
published: true
---

# import (with pv)
pv db_dump.sql | mysql -u <user> -p'<password>' <database> > error.log

# import (without pv)
mysql -u <user> -p'<password>' <database> < db_dump.sql > error.log

# export
mysqldump -u <user> -h <host> -p'<password>' <database> | pv > db_dump.sql

mysqldump -u <user> -h <host> -p<password> <database> | pv --size 100m > db_dump.sql


<https://dba.stackexchange.com/questions/83125/mysql-any-way-to-import-a-huge-32-gb-sql-dump-faster>

<https://newbedev.com/mysql-dump-exclude-some-table-data>

mysqldump -u USERNAME -pPASSWORD DATABASE --ignore-table=DATABASE.table1 > database.sql

mysqldump -h <host> -u <username> -p <schema>  -no-create-info mydb t1 t2 t3 > tables_x.sql

mysqldump -h <host> -u <username> -p <schema> --no-data > db-structure.sql

mysqldump -h <host> -u <username> -p <schema> --no-create-info --ignore-table=schema.table1 --ignore-table=schema.table2 > db-data.sql

mysqldump -u root -p DB_NAME --ignore-table=DB_NAME.table1 --ignore-table=DB_NAME.table3 > database.sql

pv /home/user/Downloads/magento_2_1_complete_02.sql | /opt/lampp/bin/mysqldump -u root -h localhost -p'' magento_2_1 > /home/user/Downloads/magento_2_1_complete_02.sql 

/opt/lampp/bin/mysql -h localhost -u root -p

/opt/lampp/bin/mysql -h localhost -u root -p '' torte < /home/user/Downloads/db_dump_magento_2_1.sql

pv /home/user/Downloads/db_dump_magento_2_1.sql | /opt/lampp/bin/mysql -h localhost -u root -p'' torte > /home/user/Downloads/error.log
