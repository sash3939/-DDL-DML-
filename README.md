# Домашнее задание к занятию «Работа с данными (DDL/DML)»

Задание можно выполнить как в любом IDE, так и в командной строке.

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp. 

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

1.4. Дайте все права для пользователя sys_temp. 

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос: 
```sql
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

### Решение 1

1.3 [users](https://github.com/sash3939/-DDL-DML-/assets/156709540/9e459129-cda9-48c4-8c28-91352d97471b)

1.4 [permissions](https://github.com/sash3939/-DDL-DML-/assets/156709540/e6aacd30-3f09-48f1-a3ca-14e23f01aeea)
1.5 [grants](https://github.com/sash3939/-DDL-DML-/assets/156709540/d462eab3-b54d-4d84-9843-e3d18ad6979d)
1.6 [done](https://github.com/sash3939/-DDL-DML-/assets/156709540/3924c0bf-f5c4-49a8-8add-d91880065105)
1.7 [dump](https://github.com/sash3939/-DDL-DML-/assets/156709540/20f9fe04-b177-42f3-b6e8-7d721f151bbb)
1.8 [show_tables](https://github.com/sash3939/-DDL-DML-/assets/156709540/927c76d3-1781-418d-b593-c147f696a5a1)
[ER-diagrama](https://github.com/sash3939/-DDL-DML-/assets/156709540/6c71d7c9-69b3-4a4f-8fb3-917d04744e7f)


Список запросов
SELECT user, host FROM mysql.user;

GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost' WITH GRANT OPTION;

SHOW GRANTS FOR 'sys_temp'@'localhost';

ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';



### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)
```
Название таблицы | Название первичного ключа
customer         | customer_id
```
### Решение 2
Название таблицы	Название первичного ключа
actor	| actor_id
address	| address_id
category	| category_id
city	| city_id
country	| country_id
customer	| customer_id
film	| film_id
film_actor	| actor_id, film_id
film_category	| film_id, category_id
film_text	| film_id
inventory	| inventory_id
language	| language_id
payment	| payment_id
rental	| rental_id
staff	| staff_id
store	| store_id

[screen](https://github.com/sash3939/-DDL-DML-/assets/156709540/7769c18f-f272-42a7-b32b-cb9ea5c71152)



## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 3*
3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.

3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

### Решение 3*

3.1 [revoke](https://github.com/sash3939/-DDL-DML-/assets/156709540/3d2751cc-faf2-449d-9ed8-75b16e9598ce)
3.2 [grants](https://github.com/sash3939/-DDL-DML-/assets/156709540/c911bf88-9703-48ef-9057-f7e755a2c42d)


GRANT ALL PRIVILEGES ON sakila.* TO 'sys_temp'@'localhost' WITH GRANT OPTION;

SHOW GRANTS FOR 'sys_temp'@'localhost';
REVOKE INSERT, UPDATE, DELETE ON sakila.* FROM sys_temp@localhost;
SHOW GRANTS FOR 'sys_temp'@'localhost';

