## 创建数据库：

CREATE DATABASE 数据库名;

## 删库：

DROP DATABASE <database_name>;

## 选择数据库：

USE database_name;

-------------------------------

## 创建数据表：

CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);

- `table_name` 是你要创建的表的名称。
- `column1`, `column2`, ... 是表中的列名。
- `datatype` 是每个列的数据类型。

## 删除数据表：

DROP TABLE table_name ;    -- 直接删除表，不检查是否存在
或
DROP TABLE [IF EXISTS] table_name;

- `table_name` 是要删除的表的名称。
- `IF EXISTS` 是一个可选的子句，表示如果表存在才执行删除操作，避免因为表不存在而引发错误。

## 插入数据：

INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

- `table_name` 是你要插入数据的表的名称。
- `column1`, `column2`, `column3`, ... 是表中的列名。
- `value1`, `value2`, `value3`, ... 是要插入的具体数值。

## 查询数据：

SELECT column1, column2, ...
FROM table_name
[WHERE condition]
[ORDER BY column_name [ASC | DESC]]
[LIMIT number];

- `column1`, `column2`, ... 是你想要选择的列的名称，如果使用 `*` 表示选择所有列。
- `table_name` 是你要从中查询数据的表的名称。
- `WHERE condition` 是一个可选的子句，用于指定过滤条件，只返回符合条件的行。
- `ORDER BY column_name [ASC | DESC]` 是一个可选的子句，用于指定结果集的排序顺序，默认是升序（ASC）。
- `LIMIT number` 是一个可选的子句，用于限制返回的行数。

## 更新数据：

UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

- `table_name` 是你要更新数据的表的名称。
- `column1`, `column2`, ... 是你要更新的列的名称。
- `value1`, `value2`, ... 是新的值，用于替换旧的值。
- `WHERE condition` 是一个可选的子句，用于指定更新的行。如果省略 `WHERE` 子句，将更新表中的所有行。

## DELETE 语句：



DELETE FROM table_name
WHERE condition;



- `table_name` 是你要删除数据的表的名称。
- `WHERE condition` 是一个可选的子句，用于指定删除的行。如果省略 `WHERE` 子句，将删除表中的所有行。

## LIKE 子句：

SELECT column1, column2, ...
FROM table_name
WHERE column_name LIKE pattern;

- `column1`, `column2`, ... 是你要选择的列的名称，如果使用 `*` 表示选择所有列。
- `table_name` 是你要从中查询数据的表的名称。
- `column_name` 是你要应用 `LIKE` 子句的列的名称。
- `pattern` 是用于匹配的模式，可以包含通配符。

## UNION:

SELECT column1, column2, ...
FROM table1
WHERE condition1
UNION
SELECT column1, column2, ...
FROM table2
WHERE condition2
[ORDER BY column1, column2, ...];

- `column1`, `column2`, ... 是你要选择的列的名称，如果使用 `*` 表示选择所有列。
- `table1`, `table2`, ... 是你要从中查询数据的表的名称。
- `condition1`, `condition2`, ... 是每个 `SELECT` 语句的过滤条件，是可选的。
- `ORDER BY` 子句是一个可选的子句，用于指定合并后的结果集的排序顺序。

## ORDER BY(排序) 语句:

SELECT column1, column2, ...
FROM table_name
ORDER BY column1 [ASC | DESC], column2 [ASC | DESC], ...;

- `column1`, `column2`, ... 是你要选择的列的名称，如果使用 `*` 表示选择所有列。
- `table_name` 是你要从中查询数据的表的名称。
- `ORDER BY column1 [ASC | DESC], column2 [ASC | DESC], ...` 是用于指定排序顺序的子句。`ASC` 表示升序（默认），`DESC` 表示降序。