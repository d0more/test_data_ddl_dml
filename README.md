# `Тестовое задание для лектора курса “DevOps-инженер”` - `Григорьев Дмитрий`
## Домашнее задание к занятию "`Работа с данными (DDL/DML)`"

### Задание 1

#### 1.1. `Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.`

Решение: скриншот 1.1

#### 1.2. `Создайте учётную запись sys_temp.`

Решение: скриншот 1.2

#### 1.3. `Выполните запрос на получение списка пользователей в базе данных. (скриншот)`

Решение: скриншот 1.3

#### 1.4. `Дайте все права для пользователя sys_temp.`

Решение: скриншот 1.4

#### 1.5. `Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)`

Решение: скриншот 1.5

#### 1.6. `Переподключитесь к базе данных от имени sys_temp.`

Решение: скриншот 1.6

#### 1.6.1 `По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.`

Решение: скриншот 1.6.1

#### 1.7. `Восстановите дамп в базу данных.`

Решение: скриншот 1.7

#### 1.8. `При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)`

Решение: скриншот 1.8

```
SELECT User FROM mysql.user;
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'%';
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'sys_temp'@'%';
```

[скриншот 1.1](https://drive.google.com/file/d/1cgQxSGXPvI_UCxwmpU566tgJzGH6roJI/view?usp=sharing)

[скриншот 1.2](https://drive.google.com/file/d/18OvtIsu85MTcPGH66xFwF-qHXOzDriMA/view?usp=sharing)

[скриншот 1.3](https://drive.google.com/file/d/10poNIB1uy4ZzWdGTytASoVhL5_MXktMI/view?usp=sharing)

[скриншот 1.4](https://drive.google.com/file/d/18pJ96ttswtqSey46qTPsm8cQFUftRwc1/view?usp=sharing)

[скриншот 1.5](https://drive.google.com/file/d/1PQ4W2GJA2xYsUteReWYFOgnU2VKnsdRP/view?usp=sharing)

[скриншот 1.6](https://drive.google.com/file/d/1IXJCCtyLhFDPhkHFTSfN7Ma9TKaeL548/view?usp=sharing)

[скриншот 1.6.1](https://drive.google.com/file/d/17Wn6Yrd2tU3XcpopqBWCLd0ifQIAL_9U/view?usp=sharing)

[скриншот 1.7](https://drive.google.com/file/d/1UiJLRaDFo6d5P00tvbr-snhonPeYwjyk/view?usp=sharing)

[скриншот 1.8](https://drive.google.com/file/d/16f2-M6tZ6wwNBsejyjoqDjqu_kLpwRf6/view?usp=sharing)

---

### Задание 2

#### 2. `Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц.  Пример: (скриншот/текст)`

Решение: скриншот 2

```
USE sakila;
#SHOW TABLES;
SELECT 
	t.table_name AS 'Название таблицы',
    c.column_name AS 'Название первичного ключа'
FROM
	information_schema.tables t
LEFT JOIN
	information_schema.key_column_usage c
    ON t.table_name = c.table_name
    AND t.table_schema = c.table_schema
    AND c.constraint_name = 'PRIMARY'
WHERE
	t.table_schema = 'sakila'
    AND t.table_type = 'BASE TABLE';
```

[скриншот 2](https://drive.google.com/file/d/1LvKUSeCOhXsqK2swLn7TmBHkr2cuGvEc/view?usp=sharing)

---

### Задание 3

#### 3.1. `Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.`

Решение: скриншот 3.1

#### 3.2. `Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)`

Решение: скриншот 3.2

```
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'sys_temp'@'%';
FLUSH PRIVILEGES;
GRANT ALL PRIVILEGES ON sakila.* TO 'sys_temp'@'%';
FLUSH PRIVILEGES;
REVOKE INSERT, UPDATE, DELETE ON sakila.* FROM 'sys_temp'@'%';
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'sys_temp'@'%';
```

[скриншот 3.1](https://drive.google.com/file/d/1JhHVr3Sa-H57jU0Hiq_VtkSqysJKgMWT/view?usp=sharing)

[скриншот 3.2](https://drive.google.com/file/d/1Tfh4I49XuzRxHKxiwBEKG4r-KQXGuF8m/view?usp=sharing)
