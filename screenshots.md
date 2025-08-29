   ### Задание 1

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

В dbeaver: 
https://github.com/netology-code/sys-pattern-homework/blob/main/img/select_all_users.png 

Или в cmd:
https://github.com/netology-code/sys-pattern-homework/blob/main/img/select_tables_names_and_pk_cmd.png 

