# Домашнее задание к занятию «Работа с данными (DDL/DML)» - `Рыбенцов Геннадий`

### Задание 1

## Простыня запросов 

1.2. Создайте учётную запись sys_temp: 

CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY '***';

1.3. Выполните запрос на получение списка пользователей в базе данных: 

SELECT user, host FROM mysql.user;

1.4. Дайте все права для пользователя sys_temp: 

GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost' WITH GRANT OPTION; 

1.5. Выполните запрос на получение списка прав для пользователя sys_temp: 

SHOW GRANTS FOR 'sys_temp'@'localhost'; 

1.6. Переподключитесь к базе данных от имени sys_temp.
     Для смены типа аутентификации с sha2 используйте запрос: 
     ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; 

Вместо этого для новой версии MySQL, где используется plugin caching_sha2_password: 
     ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'systemp';

Создание БД, куда будет восстановлен дамп: 

mysql -h 127.0.0.1 -P 3306 -u sys_temp -p

password

CREATE DATABASE sakila;

EXIT;

1.7. Восстановите дамп в базу данных. 

mysql -h 127.0.0.1 -P 3306 -u sys_temp -p sakila < C:\Users\Asus\Desktop\Netology\sakila-db\sakila-schema.sql

password

mysql -h 127.0.0.1 -P 3306 -u sys_temp -p sakila < C:\Users\Asus\Desktop\Netology\sakila-db\sakila-data.sql

password

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. 
При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

mysql -h 127.0.0.1 -P 3306 -u sys_temp -p 

password 

mysql> USE sakila;

mysql> SHOW TABLES;

<b>Скриншот диаграммы из dbeaver прилагаю. 

1. Создание учетной записи sys_temp, выдача всех прав для пользователя sys_temp: 
https://github.com/netology-code/sys-pattern-homework/blob/main/img/grant_all_privileges_to_sys_temp.png

2. Получение списка пользователей в базе данных: 
https://github.com/netology-code/sys-pattern-homework/blob/main/img/select_all_users.png

3. Запрос на получение списка прав для пользователя sys_temp: 
https://github.com/netology-code/sys-pattern-homework/blob/main/img/show_grants_for_sys_temp.png 

4. Переподключение к базе данных от имени sys_temp.
Для смены типа аутентификации с sha2 вместо - ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; я использовал: 
ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'systemp'; для новой версии MySQL, где используется plugin caching_sha2_password. 

https://github.com/netology-code/sys-pattern-homework/blob/main/img/connect_to_db_as_sys_temp.png

5. Восстановление дампа в базу данных.
https://github.com/netology-code/sys-pattern-homework/blob/main/img/create_db_sakila.png
и 
https://github.com/netology-code/sys-pattern-homework/blob/main/img/recover_sakila_from_dump.png

6. ER-диаграмму получившейся базы данных: 
https://github.com/netology-code/sys-pattern-homework/blob/main/img/sakila_diagram.png

В командной строке использована команда для получения всех таблиц базы данных: 
https://github.com/netology-code/sys-pattern-homework/blob/main/img/show_all_tables.png


### Задание 2

Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц.

Для этого в dbeaver (для удобства) сделал запрос: 

SELECT
        TABLE_NAME,
        COLUMN_NAME
    FROM
        INFORMATION_SCHEMA.COLUMNS
    WHERE
        TABLE_SCHEMA = 'sakila'
    AND
        COLUMN_KEY = 'PRI';

https://github.com/netology-code/sys-pattern-homework/blob/main/img/select_tables_names_and_pk.png 

Или в cmd:

select TABLE_NAME, COLUMN_NAME from INFORMATION_SCHEMA.columns where TABLE_SCHEMA = 'sakila' and COLUMN_KEY = 'PRI';

https://github.com/netology-code/sys-pattern-homework/blob/main/img/select_tables_names_and_pk_cmd.png 