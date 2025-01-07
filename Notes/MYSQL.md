# 0、网站

[MYSQL教程](https://www.runoob.com/mysql/mysql-tutorial.html)



# 一、基础

## 1.MySQL连接

您可以使用 MySQL 二进制方式进入到 mysql 命令提示符下来连接 MySQL 数据库，格式如下：

```mysql
mysql -u your_username -p
```

**参数说明：**

- `-u` 参数用于指定用户名。
- `-p` 参数表示需要输入密码。



**实例：**

以下是从命令行中连接 mysql 服务器的简单实例：

```mysql
[root@host]# mysql -u root -p
Enter password:******
```

按照提示输入密码，并按下 Enter 键。

在登录成功后会出现 **mysql>** 命令提示窗口，你可以在上面执行任何 SQL 语句。

以上命令执行后，登录成功输出结果如下:

```mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2854760 to server version: 5.0.9

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.
```

在以上实例中，我们使用了 root 用户登录到 MySQL 服务器，当然你也可以使用其他 MySQL 用户登录。

如果用户权限足够，任何用户都可以在 MySQL 的命令提示窗口中进行 SQL 操作。

成功连接到 MySQL 后，你可以在命令行中直接执行 SQL 查询。

列出所有可用的数据库：

```mysql
SHOW DATABASES;
```

选择要使用的数据库：

```mysql
USE your_database;
```

列出所选数据库中的所有表：

```mysql
SHOW TABLES;
```

退出 **mysql>** 命令提示窗口可以使用 **exit** 命令，如下所示：

```mysql
mysql> EXIT;
Bye
```

或者使用：

```mysql
mysql> QUIT;
```

## 2.MySQL 数据类型

MySQL 中定义数据字段的类型对你数据库的优化是非常重要的。

MySQL 支持多种类型，大致可以分为三类：数值、日期/时间和字符串(字符)类型。

**1.数据类型**

MySQL 支持所有标准 SQL 数值数据类型。

这些类型包括严格数值数据类型(INTEGER、SMALLINT、DECIMAL 和 NUMERIC)，以及近似数值数据类型(FLOAT、REAL 和 DOUBLE PRECISION)。

关键字INT是INTEGER的同义词，关键字DEC是DECIMAL的同义词。

BIT数据类型保存位字段值，并且支持 MyISAM、MEMORY、InnoDB 和 BDB表。

作为 SQL 标准的扩展，MySQL 也支持整数类型 TINYINT、MEDIUMINT 和 BIGINT。下面的表显示了需要的每个整数类型的存储和范围。

| 类型         | 大小                                     | 范围（有符号）                                               | 范围（无符号）                                               | 用途            |
| :----------- | :--------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :-------------- |
| TINYINT      | 1 Bytes                                  | (-128，127)                                                  | (0，255)                                                     | 小整数值        |
| SMALLINT     | 2 Bytes                                  | (-32 768，32 767)                                            | (0，65 535)                                                  | 大整数值        |
| MEDIUMINT    | 3 Bytes                                  | (-8 388 608，8 388 607)                                      | (0，16 777 215)                                              | 大整数值        |
| INT或INTEGER | 4 Bytes                                  | (-2 147 483 648，2 147 483 647)                              | (0，4 294 967 295)                                           | 大整数值        |
| BIGINT       | 8 Bytes                                  | (-9,223,372,036,854,775,808，9 223 372 036 854 775 807)      | (0，18 446 744 073 709 551 615)                              | 极大整数值      |
| FLOAT        | 4 Bytes                                  | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) | 0，(1.175 494 351 E-38，3.402 823 466 E+38)                  | 单精度 浮点数值 |
| DOUBLE       | 8 Bytes                                  | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度 浮点数值 |
| DECIMAL      | 对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2 | 依赖于M和D的值                                               | 依赖于M和D的值                                               | 小数值          |

**2.日期和时间类型**

表示时间值的日期和时间类型为DATETIME、DATE、TIMESTAMP、TIME和YEAR。

每个时间类型有一个有效值范围和一个"零"值，当指定不合法的MySQL不能表示的值时使用"零"值。

TIMESTAMP类型有专有的自动更新特性，将在后面描述。

| 类型      | 大小 ( bytes) | 范围                                                         | 格式                | 用途                     |
| :-------- | :------------ | :----------------------------------------------------------- | :------------------ | :----------------------- |
| DATE      | 3             | 1000-01-01/9999-12-31                                        | YYYY-MM-DD          | 日期值                   |
| TIME      | 3             | '-838:59:59'/'838:59:59'                                     | HH:MM:SS            | 时间值或持续时间         |
| YEAR      | 1             | 1901/2155                                                    | YYYY                | 年份值                   |
| DATETIME  | 8             | '1000-01-01 00:00:00' 到 '9999-12-31 23:59:59'               | YYYY-MM-DD hh:mm:ss | 混合日期和时间值         |
| TIMESTAMP | 4             | '1970-01-01 00:00:01' UTC 到 '2038-01-19 03:14:07' UTC结束时间是第 **2147483647** 秒，北京时间 **2038-1-19 11:14:07**，格林尼治时间 2038年1月19日 凌晨 03:14:07 | YYYY-MM-DD hh:mm:ss | 混合日期和时间值，时间戳 |

**3.字符串类型**

字符串类型指CHAR、VARCHAR、BINARY、VARBINARY、BLOB、TEXT、ENUM和SET。该节描述了这些类型如何工作以及如何在查询中使用这些类型。

| 类型       | 大小                  | 用途                            |
| :--------- | :-------------------- | :------------------------------ |
| CHAR       | 0-255 bytes           | 定长字符串                      |
| VARCHAR    | 0-65535 bytes         | 变长字符串                      |
| TINYBLOB   | 0-255 bytes           | 不超过 255 个字符的二进制字符串 |
| TINYTEXT   | 0-255 bytes           | 短文本字符串                    |
| BLOB       | 0-65 535 bytes        | 二进制形式的长文本数据          |
| TEXT       | 0-65 535 bytes        | 长文本数据                      |
| MEDIUMBLOB | 0-16 777 215 bytes    | 二进制形式的中等长度文本数据    |
| MEDIUMTEXT | 0-16 777 215 bytes    | 中等长度文本数据                |
| LONGBLOB   | 0-4 294 967 295 bytes | 二进制形式的极大文本数据        |
| LONGTEXT   | 0-4 294 967 295 bytes | 极大文本数据                    |

**注意**：char(n) 和 varchar(n) 中括号中 n 代表字符的个数，并不代表字节个数，比如 CHAR(30) 就可以存储 30 个字符。

CHAR 和 VARCHAR 类型类似，但它们保存和检索的方式不同。它们的最大长度和是否尾部空格被保留等方面也不同。在存储或检索过程中不进行大小写转换。

BINARY 和 VARBINARY 类似于 CHAR 和 VARCHAR，不同的是它们包含二进制字符串而不要非二进制字符串。也就是说，它们包含字节字符串而不是字符字符串。这说明它们没有字符集，并且排序和比较基于列值字节的数值值。

BLOB 是一个二进制大对象，可以容纳可变数量的数据。有 4 种 BLOB 类型：TINYBLOB、BLOB、MEDIUMBLOB 和 LONGBLOB。它们区别在于可容纳存储范围不同。

有 4 种 TEXT 类型：TINYTEXT、TEXT、MEDIUMTEXT 和 LONGTEXT。对应的这 4 种 BLOB 类型，可存储的最大长度不同，可根据实际情况选择。

**4.枚举与集合类型（Enumeration and Set Types**）

- **ENUM**: 枚举类型，用于存储单一值，可以选择一个预定义的集合。
- **SET**: 集合类型，用于存储多个值，可以选择多个预定义的集合。

**5.空间数据类型（Spatial Data Types）**

GEOMETRY, POINT, LINESTRING, POLYGON, MULTIPOINT, MULTILINESTRING, MULTIPOLYGON, GEOMETRYCOLLECTION: 用于存储空间数据（地理信息、几何图形等）。

## 3.DDL语句

### DDL-数据库操作

**1.查询**

查询所有数据库

```mysql
SHOW DATABASES;
```

查询当前数据库

```mysql
SELECT DATABASES();
```

**2.创建**

```mysql
CREATE DATABASE[IF NOT EXISTS] 数据库名 [DEFAULT CHARSET 字符集] [COLLATE 排序规则];
# 实例(方括号[]的内容是可选的)
# create database if not exists chart default charset utf8mb4;
```

**3.删除**

```mysql
DROP DATABASE[IF EXISTS]数据库名;
```

**4.使用**

```mysql
USE 数据库名;
```

**5.更改数据库名**

```mysql
ALTER DATABASE old_data_name RENAME TO new_database_name;
或者
RENAME DATABASE old_name TO new_name;
# 这两种方法在mysql5.1.23后被去掉了T^T
```



### DDL-表操作-创建&查询

**1.创建**

```mysql
CREATE TABLE 表名(
	字段1 字段1类型[COMMENT 字段1注释],
	字段2 字段2类型[COMMENT 字段2注释],
	......
	字段n 字段n类型[COMMENT 字段n注释]
)[COMMENT 表注释];
```

**注意：**最后一个字段后面没有逗号！

**2.查询**

查询当前数据库所有表

```mysql
SHOW TABLES;
```

查询表结构

```mysql
DESC 表名;
```

查询指定的建表语句

```mysql
SHOW CREATE TABLE 表名;
```

### DDL-表操作-修改&删除

**1.添加字段**

```mysql
ALTER TABLE 表名 ADD 字段名 类型(长度) [COMMENT 注释] [约束]；
```

**2.修改数据类型**

```mysql
ALTER TABLE 表名 MODIFY 字段名 新数据类型(长度);
```

**3.修改字段名和字段类型**

```mysql
ALTER TABLE 表名 CHANGE 旧字段名 新字段名 类型(长度) [COMMENT 注释] [约束];
```

**4.删除字段**

```mysql
ALTER TABLE 表名 DROP 字段名;
```

**5.修改表名**

```mysql
ALTER TABLE 表名 RENAME TO 新表名;
```

**6.删除表**

```mysql
DROP TABLE [IF EXISTS] 表名;
```

**7.删除指定表，并重新创建该表**

```mysql
TRUNCATE TABLE 表名;
```

## 4.DML语句

### DML-插入

**1.给指定字段添加数据**

```mysql
INSERT INTO 表名(字段名1,字段名2,...)VALUES(值1,值2,...);
```

**2.给全部字段添加数据**

```mysql
INSERT INTO 表名 VALUES(值1,值2，...);
```

**3.批量添加数据**

```mysql
INSERT INTO 表名(字段名1,字段名2,...);
```

```mysql
INSERT INTO 表名 VALUES(值1,值2,...),(值1,值2,...),(值1,值2,...);
```

**注意：**

- 插入数据时，指定的字段顺序需要与值的顺序是一一对应的。字符串和日期型数据应该包含在引号中。

- 插入的数据大小，应该在字段的规定范围内。

### DML-更新和删除

**1.修改数据**

```mysql
UPDATE 表名 SET 字段名1=值1,字段名2=值2,....[WHERE 条件];
```

**注意：**修改语句的条件可以有，也可以没有，如果没有条件，则会修改整张表的所有数据。

**2.删除数据**

```mysql
DELETE FROM 表名 [WHERE 条件];
```

**注意：**

- DELETE语句的条件可以有，也可以没有，如果没有条件，则会删除整张表的所有数据。

- DELETE语句不能删除某一个字段的值(可以使用UPDATE)。

## 5.DQL语句

### DQL-基础查询

**1.查询多个字段**

```mysql
SELECT 字段1,字段2,字段3...FROM 表名;
SELECT * FROM 表名;
```

**2.设置别名**

```mysql
SELECT 字段1 [AS 别名1],字段2[AS 别名2]...FROM 表名;
```

**3.去除重复记录**

> **语法:**

```mysql
SELECT DISTINCT 字段列表 FROM 表名;
```



> **实例：(多个字段去重)**

```sql
SELECT DISTINCT PLAN_NUMBER,PRODUCT_NAME FROM psur_list;
```

**期望结果：只对第一个参数PLAN_NUMBER取唯一值**

- 解决办法一：使用`group_concat` 函数

```sql
SELECT GROUP_CONCAT(DISTINCT PLAN_NUMBER) AS PLAN_NUMBER,PRODUCT_NAME from psur_list GROUP BY PLAN_NUMBER;
```

- 解决办法二：使用`group by`

```sql
SELECT PLAN_NUMBER,PRODUCT_NAME FROM psur_list GROUP BY PLAN_NUMBER;
```

### DQL-条件查询

**1.基本语法**

```mysql
SELECT 字段列表 FROM 表名 WHERE 条件列表;
```

**2.条件**

| 比较运算符       | 功能                                    |
| ---------------- | --------------------------------------- |
| >                | 大于                                    |
| >=               | 大于等于                                |
| <                | 小于                                    |
| <=               | 小于等于                                |
| =                | 等于                                    |
| <>或!=           | 不等于                                  |
| BETWEEN...AND... | 在某个范围之内(含最小、最大值)          |
| IN(...)          | 在in之后的列表中的值，多选一            |
| LIKE 占位符      | 模糊匹配(_匹配单个字符,%匹配任意个字符) |
| IS NULL          | 是NULL                                  |

| 逻辑运算符 | 功能                       |
| ---------- | -------------------------- |
| AND 或 &&  | 并且(多个条件同时成立)     |
| OR 或 \|\| | 或者(多个条件任意一个成立) |
| NOT 或 !   | 非，不是                   |

### DQL-聚合函数

**1.介绍**
	将一列数据作为一个整体，进行纵向计算。
**2.常见聚合函数**

| 函数  | 功能     |
| ----- | -------- |
| count | 统计数量 |
| max   | 最大值   |
| min   | 最小值   |
| avg   | 平均值   |
| sum   | 求和     |

**3.语法**

```mysql
SELECT 聚合函数(字段列表) FROM 表名;
```

**注：**null不参与所有聚合函数运算

### DQL-分组查询

**1.语法**

```mysql
SELECT 字段列表 FROM 表名 [WHERE 条件] GROUP BY 分组字段名 [HAVING 分组后过滤条件];
#分组字段名要和字段列表第一个字段相同，即根据job分组，查询平均工资
#其中having后面的条件要和第二个字段列表进行使用来达到过滤的效果
select job,avg(salary) as avg from emp where age>20 group by job having avg>=5000;
```

**2.where与having区别**

- 执行时机不同: where是分组之前进行过滤，不满足where条件，不参与分组;而having是分组之后对结果进行过滤。

- 判断条件不同: where不能对聚合函数进行判断，而having可以。

### DQL-排序查询

**1.语法**

```mysql
SELECT 字段列表 FROM 表名 ORDER BY 字段1 排序方式1，字段2 排序方式2;
#name，age作为一个标识，根据salary的降序来得到查询结果
select name,salary,age from emp order by salary desc;
```

**2.排序方式**

- ASC:升序（默认值)

- DESC:降序

**注意：**如果是多字段排序，当第一个字段值相同时，才会根据第二个字段进行排序

### DQL-分页查询

**1．语法**

```mysql
SELECT 字段列表 FROM 表名 LIMIT 起始索引,查询记录数;
#2是起始索引，查询10条记录，最终查询到的记录是第3~12条的name，salary，age
select name,salary,age from emp limit 2,10;
```

**注意**：

- 起始索引从0开始，起始索引=(查询页码-1)*每页显示记录数。
- 分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT。
- 如果查询的是第一页数据，起始索引可以省略，直接简写为limit 10。



### DQL-执行顺序

```mysql
FROM
	#表名列表
WHERE
	#条件列表
GROUP BY
	#分组字段列表
HAVING
	#分组后条件列表
SELECT
	#字段列表
ORDER BY
	#排序字段列表
LIMIT
	#分页参数
```

## 6.DCL语句

### DCL-管理用户

**1．查询用户**

```mysql
USE mysql;
SELECT * FROM user;
```

**2．创建用户**

```mysql
CREATE USER '用户名'@'主机名' IDENTIFIED BY '密码';
```

**3．修改用户密码**

```mysql
ALTER USER '用户名'@'主机名' IDENTIFIED WITH mysql_native_password BY
'新密码';
```

**4．删除用户**

```mysql
DROP USER'用户名'@'主机名';
```

### DCL-权限控制

**1．查询权限**

```mysql
SHOW GRANTS FOR '用户名'@'主机名';
```

**2．授予权限**

```mysql
GRANT 权限列表 ON 数据库名.表名 TO '用户名'@'主机名';
```

**3．撤销权限**

```mysql
REVOKE 权限列表 ON 数据库名.表名 FROM '用户名'@'主机名';
```

**注意:**

- 多个权限之间，使用逗号分隔。
- 授权时，数据库名和表名可以使用*进行通配，代表所有。



## 7.函数

### 1.字符串函数

MySQL中内置了很多字符串函数，常用的几个如下:

| 函数                     | 功能                                                      |
| ------------------------ | --------------------------------------------------------- |
| CONCAT(S1,S2,...Sn)      | 字符串拼接，将S1，S2，...Sn拼接成一个字符串               |
| LOWER(str)               | 将字符串str全部转为小写                                   |
| UPPER(str)               | 将字符串str全部转为大写                                   |
| LPAD(str,n,pad)          | 左填充，用字符串pad对str的左边进行填充，达到n个字符串长度 |
| RPAD(str,n,pad)          | 右填充，用字符串pad对str的右边进行填充，达到n个字符串长度 |
| TRIM(str)                | 去掉字符串头部和尾部的空格                                |
| SUBSTRING(str,start,len) | 返回从字符串str从start位置起的len个长度的字符串           |

### 2.数值函数

常见的数值函数如下:

| 函数       |                                    |
| ---------- | ---------------------------------- |
| CEIL(x)    | 向上取整                           |
| FLOOR(x)   | 向下取整                           |
| MOD(x,y)   | 返回x/y的模                        |
| RAND()     | 返回0~1内的随机数                  |
| ROUND(x,y) | 求参数x的四舍五入的值，保留y位小数 |

### 3.日期函数

常见的日期函数如下:

| 函数                               | 功能                                              |
| ---------------------------------- | ------------------------------------------------- |
| CURDATE()                          | 返回当前日期                                      |
| CURTIME()                          | 返回当前时间                                      |
| NOW()                              | 返回当前日期和时间                                |
| YEAR(date)                         | 获取指定date的年份                                |
| MONTH(date)                        | 获取指定date的月份                                |
| DAY(date)                          | 获取指定date的日期                                |
| DATE_ADD(date, INTERVAL expr type) | 返回一个日期/时间值加上一个时间间隔expr后的时间值 |
| DATEDIFF(date1,date2)              | 返回起始时间date1和结束时间date2之间的天数        |

### 4.流程函数

流程函数也是很常用的一类函数，可以在SQL语句中实现条件筛选，从而提高语句的效率。

| 函数                                                         | 功能                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| lF(value , t , f)                                            | 如果value为true，则返回t，否则返回f                     |
| IFNULL(value1 , value2)                                      | 如果value1不为空，返回value1，否则返回value2            |
| CASE WHEN [ val1 ] THEN [res1] ...ELSE [ default ] END       | 如果val1为true，返回res1，...否则返回default默认值      |
| CASE [ expr ] WHEN [ val1 ] THEN [res1] ...ELSE [ default ] END | 如果expr的值等于vall，返回res1，..否则返回default默认值 |

## 8.约束

1.概念:约束是作用于表中字段上的规则，用于限制存储在表中的数据。

2.目的:保证数据库中数据的正确、有效性和完整性。

3.分类:

| 约束                     | 描述                                                     |
| ------------------------ | -------------------------------------------------------- |
| 非空约束                 | 限制该字段的数据不能为null                               |
| 唯一约束                 | 保证该字段的所有数据都是唯一、不重复的                   |
| 主键约束                 | 主键是一行数据的唯一标识，要求非空且唯一                 |
| 默认约束                 | 保存数据时，如果未指定该字段的值，则采用默认值           |
| 检查约束(8.0.16版本之后) | 保证字段值满足某一个条件                                 |
| 外键约束                 | 用来让两张表的数据之间建立连接，保证数据的一致性和完整性 |

### 8.1 SQL CREATE TABLE + CONSTRAINT 语法

```mysql
CREATE TABLE table_name
(
    column_name1 data_type(size) constraint_name,
    column_name2 data_type(size) constraint_name,
    column_name3 data_type(size) constraint_name,
    ....
);
```

在 SQL 中，我们有如下约束：

- **NOT NULL** - 指示某列不能存储 NULL 值。
- **UNIQUE** - 保证某列的每行必须有唯一的值。
- **PRIMARY KEY** - NOT NULL 和 UNIQUE 的结合。确保某列（或两个列多个列的结合）有唯一标识，有助于更容易更快速地找到表中的一个特定的记录。
- **FOREIGN KEY** - 保证一个表中的数据匹配另一个表中的值的参照完整性。
- **CHECK** - 保证列中的值符合指定的条件。
- **DEFAULT** - 规定没有给列赋值时的默认值。
- **INDEX** - 用于快速访问数据库表中的数据。

#### 1. NOT NULL

确保列不能有 NULL 值。

```mysql
CREATE TABLE Students (
    StudentID INT NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    FirstName VARCHAR(50),
    Age INT
);
```

#### 2. UNIQUE

确保列中的所有值都是唯一的。

```mysql
CREATE TABLE Employees (
    EmployeeID INT NOT NULL UNIQUE,
    LastName VARCHAR(50) NOT NULL,
    FirstName VARCHAR(50),
    Email VARCHAR(100) UNIQUE
);
```

#### 3. PRIMARY KEY

唯一标识表中的每一行记录。PRIMARY KEY 约束是 NOT NULL 和 UNIQUE 的结合。

```mysql
CREATE TABLE Orders (
    OrderID INT NOT NULL PRIMARY KEY,
    OrderNumber INT NOT NULL,
    OrderDate DATE NOT NULL
);
```

#### 4. FOREIGN KEY

确保一个表中的值匹配另一个表中的值，从而建立两表之间的关系。

```mysql
CREATE TABLE Orders (
    OrderID INT NOT NULL PRIMARY KEY,
    OrderNumber INT NOT NULL,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

#### 5. CHECK

确保列中的值满足特定的条件。

```mysql
CREATE TABLE Products (
    ProductID INT NOT NULL PRIMARY KEY,
    ProductName VARCHAR(100) NOT NULL,
    Price DECIMAL(10, 2) CHECK (Price >= 0)
);
```

#### 6. DEFAULT

为列设置默认值。

```mysql
CREATE TABLE Customers (
    CustomerID INT NOT NULL PRIMARY KEY,
    LastName VARCHAR(50) NOT NULL,
    FirstName VARCHAR(50),
    JoinDate DATE DEFAULT GETDATE()
);
```

```mysql
alter table fruit1 alter column Stock set default(100);
/*为表fruit1中的stock列添加默认值为100*/
```



#### 7. INDEX

用于快速访问数据库表中的数据。

```mysql
CREATE INDEX idx_lastname ON Employees (LastName);
```



### 8.2 外键约束--FOREIGN KEY

- 外键是表中引用另一表主键的列。
- 外键的值必须与被引用表的相应主键值匹配。
- 外键可以用于建立表之间的关系。

删除/更新行为

| 行为        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| NO ACTION   | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则不允许删除/更新。(与RESTRICT一致) |
| RESTRICT    | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则不允许删除/更新。(与NO ACTION一致) |
| CASCADE     | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有，则也删除/更新外键在子表中的记录。 |
| SET NULL    | 当在父表中删除对应记录时，首先检查该记录是否有对应外键，如果有则设置子表中该外键值为nul(这就要求该外键允许取null)。 |
| SET DEFAULT | 父表有变更时，子表将外键列设置成一个默认的值(Innodb不支持)   |

语法：

> 添加外键

```mysql
CREATE TABLE表名(
	字段名 数据类型
	...
	[CONSTRAINT][外键名称] FOREIGN KEY (外键字段名) REFERENCES主表(主表列名)
);
```

```mysql
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY(外键字段名) REFERENCES 主表(主表列名);
```

> 删除外键

```mysql
ALTER TABLE 表名 DROP FOREIGN KEY 外键名称;
```

### 8.3 主键约束--PRIMARY KEY

- 主键是表中唯一标识每行的列。
- 主键的值必须是唯一的，并且不能为 null。
- 每个表只能有一个主键。

**设置主键**

```mysql
ALTER TABLE table_name ADD PRIMARY KEY (column_name);
#例如，在 customers 表中设置 customer_id 列为主键：
ALTER TABLE customers ADD PRIMARY KEY (customer_id);
```



### 8.4 自增列--MODIFY

如果某一列是数值类型的，使用 auto_increment 可以来完成值得自动增长

方式1:创建表时，添加主键约束，并且完成主键自增长

```mysql
create table stu(
	id int primary key auto_increment, -- 给id添加主键约束
	name varchar(20)
);
```

方式2:创建完表之后添加自动增长

```mysql
ALTER TABLE stu MODIFY id INT AUTO_INCREMENT;

ALTER TABLE stu MODIFY id INT; -- 删除自动增长
```



## 9.多表查询

多表查询分类

**1.连接查询**

内连接:相当于查询A、B交集部分数据

外连接:

​		左外连接:查询左表所有数据，以及两张表交集部分数据

​		右外连接:查询右表所有数据，以及两张表交集部分数据

自连接:当前表与自身的连接查询，自连接必须使用表别名

**2.子查询**

概念:SQL语句中嵌套SELECT语句，称为嵌套查询，又称子查询。

```mysql
SELECT * FROM t1 WHERE column1 =(SELECT column1 FROM t2);
```

子查询外部的语句可以是INSERT /UPDATE/ DELETE/ SELECT的任何一个。

- 根据子查询结果不同，分为:

  - 标量子查询(子查询结果为单个值)

  - 列子查询(子查询结果为一列)

  - 行子查询(子查询结果为一行)

  - 表子查询(子查询结果为多行多列)

根据子查询位置，分为:WHERE之后、FROM之后、SELECT 之后。



### 连接查询-内连接

内连接查询语法:

- 隐式内连接

```mysql
SELECT 字段列表 FROM 表1,表2 WHERE 条件...;
```

- 显式内连接

```mysql
SELECT 字段列表 FROM 表1[INNER] JOIN 表2 ON 连接条件...;
#emp和dept是两张表,d是dept的别名
select emp.name,emp.job as 'job' from emp join dept d on emp.dept_id = d.id;
```

内连接查询的是两张表交集的部分。



### 连接查询-外连接

外连接查询语法:

- 左外连接

> 左连接又称左外连接，我们查询两张表时，会将左表所有数据都查出来，而右表数据只展示和左表有匹配的数据（如左表id和右边id有相等的数据），如果没有匹配上（如左表有id=4 ，但是右表没有id等于4的数据时）右表对应行就展示为Null。

```mysql
SELECT 字段列表 FROM 表1 LEFT [OUTER] JOIN 表2 ON 条件....;
```

- 右外连接

> 右连接也称为右外连接，我们查询两张表时，会将右表所有数据都查出来，而左表数据只展示和右表有匹配的数据，如果没有匹配上左表的对应行就展示为Null。

```mysql
SELECT 字段列表 FROM 表1 RIGHT [OUTER] JOIN 表2 ON 条件....;
```

相当于查询表2(右表)的所有数据包含表1和表2交集部分的数据



### 连接查询-自连接

自连接查询语法:

```mysql
SELECT 字段列表 FROM 表A 别名A JOIN 表A 别名B ON 条件...;
```

自连接查询，可以是内连接查询，也可以是外连接查询。



### 联合查询-union

对于union查询，就是把多次查询的结果合并起来，形成一个新的查询结果集。

```mysql
SELECT 字段列表 FROM 表A ....
UNION [ALL]
SELECT 字段列表 FROM 表B ....;
```

对于联合查询的多张表的列数必须保持一致，字段类型也需要保持一致。

union all会将全部的数据直接合并在一起，union会对合并之后的数据去重。



### 子查询-标量子查询

子查询返回的结果是单个值（数字、字符串、日期等)，最简单的形式，这种子查询成为标量子查询。

常用的操作符:`=`、 `>`、 `>=`、 `<`、 `<=`

### 子查询-列子查询

子查询返回的结果是一列（可以是多行)，这种子查询称为列子查询。

常用的操作符:IN 、NOT IN、ANY 、SOME、ALL

| 操作符   | 描述                                   |
| -------- | -------------------------------------- |
| `IN`     | 在指定的集合范围之内，多选一           |
| `NOT IN` | 不在指定的集合范围之内                 |
| `ANY`    | 子查询返回列表中，有任意一个满足即可   |
| `SOME`   | 与ANY等同，使用SOME的地方都可以使用ANY |
| `ALL`    | 子查询返回列表的所有值都必须满足       |

### 子查询-行子查询

子查询返回的结果是一行（可以是多列），这种子查询称为行子查询。

常用的操作符:`=` 、`<>`、`IN` 、`NOT IN`

### 子查询-表子查询

子查询返回的结果是多行多列，这种子查询称为表子查询。

常用的操作符:`IN`



## 10.事务

事务是一组操作的集合，它是一个不可分割的工作单位，事务会把所有的操作作为一个整体一起向系统提交或撤销操作请求，即这些操作要么同时成功，要么同时失败。

> 默认MySQL的事务是自动提交的，也就是说，当执行一条DML语句，MySQL会立即隐式的提交事务。

事务四大特性:

- 原子性(Atomicity)∶事务是不可分割的最小操作单元，要么全部成功，要么全部失败。
- 一致性（Consistency):事务完成时，必须使所有的数据都保持一致状态。
- 隔离性（Ilsolation):数据库系统提供的隔离机制，保证事务在不受外部并发操作影响的独立环境下运行。
- 持久性（Durability):事务一旦提交或回滚，它对数据库中的数据的改变就是永久的。

### 事务操作

**1.查看/设置事务提交方式**

```mysql
SELECT @@autocommit;
SET @@autocommit = 0;
```

**2.开始事务**

```mysql
START TRANSACTION;  -- 开始事务
-- 或者Begin;
```

**3.提交事务**

```mysql
COMMIT;
```

**4.回滚事务**

```mysql
ROLLBACK;
```

### 并发事务问题

| 问题       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| 脏读       | 一个事务读到另外一个事务还没有提交的数据。                   |
| 不可重复读 | 一个事务先后读取同一条记录，但两次读取的数据不同，称之为不可重复读。 |
| 幻读       | 一个事务按照条件查询数据时，没有对应的数据行，但是在插入数据时，又发现这行数据已经存在，好像出现了"幻影”。 |

### 事务隔离级别

| 隔离级别              | 赃读 | 不可重复读 | 幻读 |
| --------------------- | ---- | ---------- | ---- |
| Read uncommitted      | √    | √          | √    |
| Read committed        | ×    | √          | √    |
| Repeatable Read(默认) | ×    | ×          | √    |
| Serializable          | ×    | ×          | ×    |

> √表示会出现这种情况，×表示不会。

--**查看事务隔离级别**

```mysql
SELECT @@TRANSACTION_ISOLATION;
```

--**设置事务隔离级别**

```mysql
SET[SESSiON|GLOBAL] TRANSACTION ISOLATION LEVEL {READ UNCOMMITTED | READ COMMITTED |REPEATABLE READ | SERIALIZABLE}
```

注意:事务隔离级别越高、数据越安全，但是性能越低。

### 事物原理

- `redo log`

​		重做日志，记录的是事务提交时数据页的物理修改，是用来实现事务的持久性。

​		该日志文件由两部分组成：重做日志缓冲(redolog buffer)以及重做日志文件(redolog file),前者是在内存中，后者在磁盘中。当事务提交之后会把所有修改信息都存到该日志文件中,用于在刷新脏页到磁盘,发生错误时,进行数据恢复使用。

- `undo log`

  回滚日志，用于记录数据被修改前的信息，作用包含两个:提供回滚 和 MVCC(多版本并发控制)。

​		undo log和redo log记录物理日志不一样，它是逻辑日志。可以认为当delete一条记录时，undo log中会记录一条对应的insert记录，反之亦然，当update一条记录时，它记录一条对应相反的update记录。当执行rolback时，就可以从undo log中的逻辑记录读取到相应的内容并进行回滚。

​		Undo log销毁：undolog在事务执行时产生，事务提交时，并不会立即删除undolog，因为这些日志可能还用于MVCC,

​		Undo log存储：undolog采用段的方式进行管理和记录，存放在前面介绍的 rollbacksegment 回滚段中，内部包含1024个undolog
segment.

> MVCC

MVCC-基本概念

- 当前读

​		读取的是记录的最新版本，读取时还要保证其他并发事务不能修改当前记录，会对读取的记录进行加锁。对于我们日常的操作，如
select.... lock in share mode(共享锁)，select.... for update、update、insert、delete(排他锁)都是一种当前读。

- 快照读

​		简单的select(不加锁)就是快照读，快照读，读取的是记录数据的可见版本，有可能是历史数据，不加锁，是非阻塞读。
​		Read committed:每次select，都生成一个快照读。
​		Repeatable Read:开启事务后第一个select语句才是快照读的地方。
​		Serializable:快照读会退化为当前读。

- MVCC

  全称 Multi-Version Concurrency Control，多版本并发控制。指维护一个数据的多个版本，使得读写操作没有冲突，快照读为MySQL实现。MVCC提供了一个非阻塞读功能。MVCC的具体实现，还需要依赖于数据库记录中的三个隐式字段、undolog日志、readView。

# 二、MYSQL

## 1.存储引擎

**1.MySQL体系结构**

- 连接层

最上层是一些客户端和链接服务，主要完成一些类似于连接处理、授权认证、及相关的安全方案。服务器也会为安全接入的每个客户端验证它所具有的操作权限。

- 服务层

第二层架构主要完成大多数的核心服务功能，如SQL接口，并完成缓存的查询，SQL的分析和优化，部分内置函数的执行。所有跨存储引擎的功能也在这一层实现，如过程、函数等。

- 引擎层

存储引擎真正的负责了MySQL中数据的存储和提取，服务器通过API和存储引擎进行通信。不同的存储引擎具有不同的功能，这样我们可以根据自己的需要,来选取合适的存储引擎。

- 存储层

主要是将数据存储在文件系统之上，并完成与存储引擎的交互。

**2.存储引擎特点**

- lnnoDB

> 介绍

InnoDB是一种兼顾高可靠性和高性能的通用存储引擎，在MySQL5.5之后，InnoDB是默认的MySQL存储引擎。

>特点

DML操作遵循ACID模型，支持事务；

行级锁，提高并发访问性能;

支持外键FOREIGN KEY约束，保证数据的完整性和正确性;

> 文件

xxx.ibd: xxx代表的是表名，innoDB引擎的每张表都会对应这样一个表空间文件，存储该表的表结构(frm、sdi )、数据和索引。

参数: innodb_file_per_table

- MylSAM

> 介绍

MyISAM是MySQL早期的默认存储引擎。

> 特点

不支持事务，不支持外键

支持表锁，不支持行锁

访问速度快

> 文件

xxx.sdi:存储表结构信息

xxx.MYD:存储数据

xxx.MYI:存储索引

- Memory

> 介绍

Memory引擎的表数据时存储在内存中的，由于受到硬件问题、或断电问题的影响，只能将这些表作为临时表或缓存使用。

> 特点

内存存放

hash索引（默认)

文件
xxx.sdi:存储表结构信息

**3.存储引擎选择**
在选择存储引擎时，应该根据应用系统的特点选择合适的存储引擎。对于复杂的应用系统，还可以根据实际情况选择多种存储引擎进行组合。

InnoDB:是Mysql的默认存储引擎，支持事务、外键。如果应用对事务的完整性有比较高的要求，在并发条件下要求数据的一致性，数据操作除了插入和查询之外，还包含很多的更新、删除操作，那么InnoDB存储引擎是比较合适的选择。

MyISAM:如果应用是以读操作和插入操作为主，只有很少的更新和删除操作，并且对事务的完整性、并发性要求不是很高，那
么选择这个存储引擎是非常合适的。

MEMORY:将所有数据保存在内存中，访问速度快，通常用于临时表及缓存。MEMORY的缺陷就是对表的大小有限制，太大的表无法缓存在内存中，而且无法保障数据的安全性。

# 三、索引

## 1.结构

**Biglnteger构造方法**

- 如果BigInteger表示的数字没有超出long的范围，可以用静态方法获取。
- 如果BigInteger表示的超出long的范围，可以用构造方法获取。
- 对象一旦创建，BigInteger内部记录的值不能发生改变。
- 只要进行计算都会产生一个新的BigInteger对象


**Hash**

>Hash索引特点
1. Hash索引只能用于对等比较(=，in)，不支持范围查询（between，>，<，...)
2. 无法利用索引完成排序操作
3. 查询效率高，通常只需要一次检索就可以了，效率通常要高于B+tree索引
>存储引擎支持

在MysaL中，支持hash索引的是Memory引擎，而InoDB中具有自适应hash功能，hash索引是存储引擎根据B+Tree索引在指定条件下自动构建的。



**为什么InnoDB存储引擎选择使用B+tree索引结构?**

- 相对于二叉树，层级更少，搜索效率高;
- 对于B-tree，无论是叶子节点还是非叶子节点，都会保存数据，这样导致一页中存储的键值减少，指针跟着减少，要同样保存大量数据，只能增加树的高度，导致性能降低;
- 相对Hash索引，B+tree支持范围匹配及排序操作;



## 2.分类

| 分类     | 含义                                                 | 特点                    | 关键字   |
| -------- | ---------------------------------------------------- | ----------------------- | -------- |
| 主键索引 | 针对于表中主键创建的索引                             | 默认自动创建,只能有一个 | PRIMARY  |
| 唯一索引 | 避免同一个表中某数据列中的值重复                     | 可以有多个              | UNIQUE   |
| 常规索引 | 快速定位特定数据                                     | 可以有多个              |          |
| 全文索引 | 全文索引查找的是文本中的关键词，而不是比较索引中的值 | 可以有多个              | FULLTEXT |

在InnoDB存储引擎中，根据索引的存储形式，又可以分为以下两种:

| 分类                      | 含义                                                       | 特点                |
| ------------------------- | ---------------------------------------------------------- | ------------------- |
| 聚集索引(Clustered Index) | 将数据存储与索引放到了一块，索引结构的叶子节点保存了行数据 | 必须有,而且只有一个 |
| 二级索引(Secondary Index) | 将数据与索引分开存储，索引结构的叶子节点关联的是对应的主键 | 可以存在多个        |

聚集索引选取规则:

> 如果存在主键，主键索引就是聚集索引。

> 如果不存在主键，将使用第一个唯一（UNIQUE）索引作为聚集索引。

> 如果表没有主键，或没有合适的唯一索引，则nnoDB会自动生成一个rowid作为隐藏的聚集索引。

## 3.语法

**1.创建索引**

```mysql
CREATE [UNIQUE | FULLTEXT ] INDEX index_name ON table_name(index_col_name...);
# 在水果类型表的类型名上创建唯一索引
create unique index Categoryname_index on fruitcategory(CategoryName);
```

**2.查看索引**

```mysql
SHOW INDEX FROM table_name;
# 查询水果表上所有的索引信息。
show index from fruitcategory;
```

**3.删除索引**

```mysql
DROP INDEX index_name ON table_name;
# 删除水果表上原有的所有非聚集索引。
drop index CategoryName_Index on FruitCategory;
# 如有主键对应的聚集索引，则需要把主键删除。
alter table FruitCategory drop primary key;
```

## 4.性能分析

**1.SQL执行频率**

MySQL客户端连接成功后，通过show [sessionlglobal status 命令可以提供服务器状态信息。通过如下指令，可以查看当前数据库的

INSERT、UPDATE、DELETE、SELECT的访问频次:

```mysql
SHOW GLOBAL STATUS LIKE 'Com%';
```

**2.慢查询日志**
慢查询日志记录了所有执行时间超过指定参数(long_query_time，单位:秒，默认10秒）的所有SQL语句的日志。

MySQL的慢查询日志默认没有开启，需要在MySQL的配置文件(/etc/my.cnf)中配置如下信息:

```mysql
#开启MySQL慢日志查询开关
slow_query_log=1

#设置慢日志的时间为2秒，SQL语句执行时间超过2秒，就会视为慢查询，记录慢查询日志
long_query_time=2
```

配置完毕之后，通过以下指令重新启动MySQL服务器进行测试，查看慢日志文件中记录的信息/var/lib/mysql/localhost-slow.log.

**3.profile详情**

show profiles能够在做SQL优化时帮助我们了解时间都耗费到哪里去了。通过have_profiling参数，能够看到当前MySQL是否支持

profile操作:

```mysql
SELECT @@have_profiling;
```

默认profiling是关闭的，可以通过set语句在session/global级别开启profiling:

```mysql
SET profiling =1;
```

执行一系列的业务SQL的操作，然后通过如下指令查看指令的执行耗时:

```mysql
#查看每一条SQL的耗时基本情况
show profiles;

#查看指定query_id的SQL语句各个阶段的耗时情况
show profile for query query_id;

#查看指定query_id的SQL语句CPU的使用情况
show profile cpu for query query_id;
```

**4.explain执行计划**

EXPLAIN或者DESC命令获取MySQL如何执行SELECT语句的信息，包括在SELECT语句执行过程中表如何连接和连接的顺序。

语法:

```mysql
#直接在select语句之前加上关键字explain/desc
EXPLAIN SELECT 字段列表 FROM 表名 WHERE 条件;
# 验证未创建索引时的执行计划。
# select * from FruitCategory where CategoryName='浆果'
explain select * from fruitcategory where CategoryName='浆果';
```

EXPLAIN执行计划各字段含义:

> ld

- select查询的序列号，表示查询中执行select子句或者是操作表的顺序(id相同，执行顺序从上到下; id不同，值越大，越先执行)。

> select_type

- 表示SELECT的类型，常见的取值有SIMPLE（(简单表，即不使用表连接或者子查询)、PRIMARY（主查询，即外层的查询)、
- UNION(UNION中的第二个或者后面的查询语句)、SUBQUERY (SELECT/WHERE之后包含了子查询）等

> type

- 表示连接类型，性能由好到差的连接类型为NULL、system、const、eq_ref、ref、range、index、all。

> possible_key

- 显示可能应用在这张表上的索引，一个或多个。

## 5.使用规则

**1.验证索引效率**

在未建立索引之前，执行如下SQL语句，查看SQL的耗时

```mysql
SELECT * FROM tb_sku WHERE sn='100000003145001';
```

针对字段创建索引

```mysql
create index idx_sku_sn on tb_sku(sn);
```

然后再次执行相同的SQL语句，再次查看SQL的耗时

```mysql
SELECT * FROM tb_sku WHERE sn='100000003145001';
```

**2.最左前缀法则**

如果索引了多列(联合索引)，要遵守最左前缀法则。最左前缀法则指的是查询从索引的最左列开始，并且不跳过索引中的列。

如果跳跃某一列，索引将部分失效(后面的字段索引失效)。

```mysql
explain select * from tb_user where profesion='软件工程' and age=31 and status='0;
```

**3.范围查询**

联合查询中，出现范围查询(<，>)，范围查询右侧的列索引失效。

```mysql
explain select * from tb_user where profession='软件工程' and age>30 and status='0';
#假设age和status都有索引，则status的索引失效
```

**4.索引列运算**

不要在索引列上进行运算操作，索引将失效。

```mysql
explain select * from tb_user where substring(phone,10,2)='15';
```

**5.字符串不加引号**

字符串类型字段使用时，不加引号，索引将失效。

```mysql
explain select * from tb_user where phone=17799990015;
#phone number要加引号
```

**6.or连接的条件**

用or分割开的条件，如果or前的条件中的列有索引，而后面的列中没有索引，那么涉及的索引都不会被用到。

```mysql
explain select * from tb_user where id=10 or age=23;s
#假设id有索引，age没有索引，则涉及的索引都不会被用到。
```

**7.数据分布影响**

如果MYSQL评估使用索引会比全表更慢，则不使用索引。

**8.模糊查询**

如果仅仅是尾部模糊匹配，索引不会失效。如果是头部模糊匹配，索引失效。

```mysql
explain select * from tb_user where profession like '软件%';   #索引不失效
explain select * from tb_user where profession like '%工程';   #索引失效
explain select * from tb_user where profession like '%工%';    #只要是头部模糊匹配，索引就会失效
```

**9.覆盖索引**

尽量使用覆盖索引(查询使用了索引，并且需要返回的列，在该索引中已经全部能够找到)，减少select *。

> using index condition：查找使用的索引，但是需要回表查询数据。
>
> using where；using index：查找使用了索引，但是需要的数据都在索引列中能找到，所以不需要回表查询数据。

## 6.SQL提示

SQL提示，是优化数据库的一个重要手段，简单来说，就是在SQL语句中加入一些人为的提示来达到优化操作的目的。

**1.use index**

```mysql
explain select * from tb_user use index(idx_user_pro) where profession='软件工程'
```

**2.ignore index**

```mysql
explain select * from tb_user ignore index(idx_user_pro) where profession='软件工程'
```

**3.force index**

```mysql
explain select * from tb_user force index(idx_user_pro) where profession='软件工程'
```

## 7.前缀索引

当字段类型为字符串(varchar、text等)时，有时候需要索引很长的字符串，这会让索引变得很大，查询时，浪费大量的磁盘IO，影响查询效率。此时可以只将字符串的一部分前缀，建立索引，这样可以大大节约索引空间，从而提高索引效率。

> 语法

```mysql
create index idx_xxxx on table_name(column(n));
```

> 前缀长度

可以根据索引的选择性来决定，而选择性是指不重复的索引值(基数)和数据表的记录总数的比值，索引选择性越高则查询效率越高，唯一索引的选择性是1，这是最好的索引选择性，性能也是最好的。

```mysql
select count(distinct email)/count(*) from tb_user;
select count(distinct substring(email,1,5))/count(*) from tb_user;
```

## 8.单列索引和联合索引

- 单列索引:即一个索引只包含单个列。
- 联合索引:即一个索引包含了多个列。

在业务场景中，如果存在多个查询条件，考虑针对于查询字段建立索引时，建议建立联合索引，而非单列索引。

**1.单列索引情况**

```mysql
explain select id, phone, name from tb user where phone= '17799990010' and name ='韩信’;
```

> 多条件联合查询时，MVSOL优化器会评估哪个字段的索引效率更高，会选择该索引完成本次查询。

**2.联合索引情况**

```mysql
create unique index idx_phone_name on tb_user(phone, name);
```

## 9.索引设计原则

1. 针对于数据量较大，且查询比较频繁的表建立索引，
2. 针对于常作为查询条件(where)、排序(orderby)、分组(groupby)操作的字段建立索引。
3. 尽量选择区分度高的列作为索引，尽量建立唯一索引，区分度越高，使用索引的效率越高。
4. 如果是字符串类型的字段，字段的长度较长，可以针对于字段的特点，建立前缀索引。
5. 尽量使用联合索引，减少单列索引，查询时，联合索引很多时候可以覆盖索引，节省存储空间，避免回表，提高查询效率。
6. 要控制索引的数量，索引并不是多多益善，索引越多，维护索引结构的代价也就越大，会影响增删改的效率。
7. 如果索引列不能存储NULL值，请在创建表时使用NOT NULL约束它。当优化器知道每列是否包含NULL值时，它可以更好地确定哪个索引最有效地用于查询。

# 四、SQL优化

## 1.插入数据-insert优化

> 批量插入

```mysql
Insert into tb test values(1,'Tom'),(2,'Cat'),(3, jerry');
```

> 手动提交事务

```mysql
start transaction;
insert into tb_ test values(1,'Tom'),(2,' Cat'),(3, jerr')
insert into tb test values(4,'Tom'),(5,'cat'),(6,erry')
insert into tb test values(7,'Tom'),8,'Cat'),(9,erry')
commit;
```

> 主键顺序插入

```mysql
主键乱序插入:8 1 9 21 88 2 4 15 89 5 7 3
主键顺序插入:1 2 3 4 5 7 8 9 15 21 88 89
```

> 大批量插入数据

如果一次性需要插入大批量数据，使用insert语句插入性能较低，此时可以使用MySQL数据库提供的load指令进行插入。操作如下:

```mysql
#客户端连接服务端时，加上参数 --local-infile
mysql--local-infile -u root -p
#设置全局参数local_infile为1，开启从本地加载文件导入数据的开关
set global local_infile=1;
#执行load指令将准备好的数据，加载到表结构中
load data local infile '/root/sql.log' into table 'tb user' fields terminated by ',’ lines terminated by '\n';
```

## 2.主键优化

主键设计原则

- 满足业务需求的情况下，尽量降低主键的长度。
- 
  插入数据时，尽量选择顺序插入，选择使用AUTO_INCREMENT自增主键，

- 尽量不要使用UUID做主键或者是其他自然主键，如身份证号。

- 业务操作时，避免对主键的修改。

## 3.order by优化

①.Using filesort:通过表的索引或全表扫描，读取满足条件的数据行，然后在排序缓冲区sort buffer中完成排序操作，所有不是通过索引直
接返回排序结果的排序都叫 FileSort 排序。
②.Using index:通过有序索引顺序扫描直接返回有序数据，这种情况即为using index，不需要额外排序，操作效率高。

```mysql
#没有创建索引时，根据age,phone进行排序。
explain select id,age,phone from tb_user order by age,phone;
#创建索引
create index idx_user_age_phone_aa on tb_user(age,phone);
#创建索引后，根据age,phone进行升序排序
explain select id,age,phone from tb_user order by age,phone;
#创建索引后，根据age,phone进行降序排序
explain select id,age,phone from tb_user order by age desc,phone desc;
```

- 根据排序字段建立合适的索引，多字段排序时，也遵循最左前缀法则。
- 尽量使用覆盖索引。
- 多字段排序,一个升序一个降序，此时需要注意联合索引在创建时的规则(ASC/DESC)。
- 如果不可避免的出现filesort，大数据量排序时，可以适当增大排序缓冲区大小sort_buffer_size(默认256k).

## 4.group by优化

```mysql
#删除掉目前的联合索引idx_user_pro_age_sta
drop index idx_use_pro_age_sta on tb_user;
#执行分组操作，根据profession字段分组
explain select profession,count(*) from tb_user group by profession;
#创建索引
Create index idx_user_pro_age_sta on tb_user(profession,age,status);
#执行分组操作，根据profession字段分组
explain select profession,count(*) from tb_user group by profession;
#执行分组操作，根据profession字段分组
explain select profession,count(*)from tb_user group by profession,age;
```

- 在分组操作时，可以通过索引来提高效率，
- 分组操作时，索引的使用也是满足最左前缀法则的。

## 4.count优化

count的几种用法：

- count(主键)

  InnoD8 引擎会遍历整张表，把每一行的主键id值都取出来，返回给服务层。服务层拿到主键后，直接按行进行累加(主键不可能为null)。

- count(字段)

  没有not null约束:InnoD8 引擎会遍历整张表把每一行的字段值都取出来，返回给服务层，服务层判断是否为null，不为null，计数累加。

  有not null 约束:InnoDB 引擎会遍历整张表把每一行的字段值都取出来，返回给服务层，直接按行进行累加。

- count(1)

  InnoDB 引擎遍历整张表，但不取值。服务层对于返回的每一行，放一个数字“1”进去，直接按行进行累加。

- count(*)

  InnoDB引擎并不会把全部字段取出来，而是专门做了优化，不取值，服务层直接按行进行累加。


`按照效率排序的话，count(字段)<count(主键 id)<count(1)≈count(*)，所以尽量使用 count(*)。`

## 5.limit优化

一个常见又非常头疼的问题就是limit 2000000,10 ，此时需要MYSQL排序前2000010 记录，仅仅返回2000000-2000010
的记录，其他记录丢弃，查询排序的代价非常大。

优化思路:一般分页查询时，通过创建 覆盖索引 能够比较好地提高性能，可以通过覆盖索引加子查询形式进行优化。

```mysql
explain select * from tb_sku t,(select id from tb_sku order by id limit 2000000,10) a where t.id = a.id;
```

## 6.update优化

```mysql
update student set no='2000100100'where id =1;
```

```mysql
update student set no='2000100105'where name='韦一笑';
```

InnoDB的行锁是针对索引加的锁，不是针对记录加的锁,并且该索引不能失效，否则会从行锁升级为表锁。

# 五、视图

## 1.概念

视图(View)是一种虚拟存在的表。视图中的数据并不在数据库中实际存在，行和列数据来自定义视图的查询中使用的表，并且是在使用视

图时动态生成的。

通俗的讲，视图只保存了查询的SOL逻辑，不保存查询结果。所以我们在创建视图的时候，主要的工作就落在创建这条SOL查询语句上。

> 作用

- 视图不仅可以简化用户对数据的理解，也可以简化他们的操作。那些被经常使用的查询可以被定义为视图，从而使得用户不必为以后的操作每次指定全部的条件。
- 数据库可以授权，但不能授权到数据库特定行和特定的列上。通过视图用户只能查询和修改他们所能见到的数据。
- 视图可帮助用户屏蔽真实表结构变化带来的影响。

## 2.语法

在 SQL 中，视图是基于 SQL 语句的结果集的可视化的表。

视图包含行和列，就像一个真实的表。视图中的字段就是来自一个或多个数据库中的真实的表中的字段。

您可以向视图添加 SQL 函数、WHERE 以及 JOIN 语句，也可以呈现数据，就像这些数据来自于某个单一的表一样。

**1.创建**

```mysql
CREATE [OR REPLACE] VIEW 视图名称[(列名列表)]AS SELECT语句 [WITH[CASCADED | LOCAL] CHECK OPTION]
```

**2.查询**

```sql
#查看创建视图语句:
SHOW CREATE VIEW 视图名称;
#查看视图数据:
SELECT * FROM 视图名称……;
```

**3.修改**

```sql
#方式一:
CREATE [OR REPLACE] VIEW 视图名称(列名列表)] AS SELECT语句 [WITH [CASCADED | LOCAL ] CHECK OPTION]
#方式二:
ALTER VIEW 视图名称[(列名列表)] AS SELECT语句 [WITH [CASCADED | LOCAL] CHECK OPTION]
```

**4.删除**

```sql
DROP VIEW [IF EXISTS] 视图名称 [,视图名称]...
```

## 3.检查选项CASCADED 和 LOCAL

当使用WITH CHECKOPTION子句创建视图时，MYSQL会通过视图检查正在更改的每个行，例如 插入，更新，删除，以使其符合视图的定义。MySQL允许基于另一个视图创建视图，它还会检查依赖视图中的规则以保持一致性。为了确定检查的范围，mysql提供了两个选项:`CASCADED` 和 `LOCAL`，默认值为 `CASCADED`。

**1.`CASCADED` :**

```sql
create view v1 as select id,name from student where id <= 20 with cascaded check option;
```

**2.`LOCAL`：**

```sql
create view v2 as select id , name from v1 where id >= 10 with local check option;
```

## 4.视图的更新

要使视图可更新，视图中的行与基础表中的行之间必须存在一对一的关系。如果视图包含以下任何一项，则该视图不可更新:

- 聚合函数或窗口函数(SUM()、MIN()、MAX()、COUNT()等)
- DISTINCT
- GROUP BY
- HAVING
- UNION 或者 UNION ALL

在 SQL 中，你不能直接使用 UPDATE 语句来更新视图，因为视图是基于查询结果生成的虚拟表，而不是实际存储数据的表。

更新视图的实质是通过更新视图所基于的表中的数据，然后视图会反映这些变化。

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

其中，table_name 是基础表的名称，column1, column2, ... 是要更新的列，value1, value2, ... 是新的值，condition 是更新的条件。

现在，我们希望向 "Current Product List" 视图添加 "Category" 列。我们将通过下列 SQL 更新视图：

举例来说，如果你有一个名为 high_salary_employees 的视图，显示工资高于 50000 的员工信息，而这个视图基于 employees 表的查询结果，你可以通过以下步骤来更新数据：

```sql
-- 步骤 1: 更新 employees 表中的数据
UPDATE employees
SET salary = 60000
WHERE employee_id = 1001;

-- 步骤 2: 查询更新后的高工资员工视图
SELECT *
FROM high_salary_employees;
```

这样，你更新了 employees 表中的数据，而视图 high_salary_employees 将反映出这些变化。

# 六、存储过程

存储过程是事先经过编译并存储在数据库中的一段SQL语句的集合，调用存储过程可以简化应用开发人员的很多工作，减少数据在数据

库和应用服务器之间的传输，对于提高数据处理的效率是有好处的。存储过程思想上很简单，就是数据库 SOL语言层面的代码封装与重用。

> 特点

- 封装，复用
- 可以接收参数，也可以返回数据
- 减少网络交互，效率提升

## 1.语法

**1.创建**

```sql
CREATE PROCEDURE 存储过程名称([参数列表])
BEGIN
	--SQL语句
END;
/* 
create procedure p1()
begin
	select count(*) from student;
end;
*/
```

**2.调用**

```sql
CALL 名称([参数]);
# 如 call q1();
```

**3.查看**

```sql
SELECT * FROM INFORMATION_SCHEMA.ROUTINES WHERE ROUTINE_SCHEMA='xxx'; /*查询指定数据库的存储过程及状态信息*/
SHOW CREATE PROCEDURE 存储过程名称; /*--查询某个存储过程的定义*/
```

**4.删除**

```sql
DROP PROCEDURE [IF EXISTS]存储过程名称;
```

**注意:**在命令行中，执行创建存储过程的SQL时，需要通过关键字 `delimiter` 指定SQL语句的结束。

```sql
delimiter $$;
/*将$$设置为结束符*/
/* 
create procedure p1()
begin
	select count(*) from student;
end$$
*/
```

## 2.变量

### 1.系统变量

系统变量 是MySQL服务器提供，不是用户定义的，属于服务器层面。分为全局变量(GLOBAL)、会话变量(SESSION)。

> 查看系统变量

```sql
SHOW [SESSION | GLOBAL] VARIABLES;        -- 查看所有系统变量
SHOW[SESSION | GLOBAL] VARIABLES LIKE'......';   -- 可以通过LKE模糊匹配方式查找变量
SELECT @@[SESSION | GLOBAL] 系统变量名;       -- 查看指定变量的值
```

> 设置系统变量

```sql
SET [SESSION | GLOBAL]系统变量名=值;
SET @@[SESSION | GLOBAL]系统变量名=值;
```

**注意：**
如果没有指定SESSION/GLOBAL，默认是SESSION，会话变量。

mysql服务重新启动之后，所设置的全局参数会失效，要想不失效，可以在/etc/mvcnf 中配置。

### 2.用户自定义变量

**用户定义变量**是用户根据需要自己定义的变量，用户变量不用提前声明，在用的时候直接用“@变量名”使用就可以。其作用域为当前连接。

> 赋值

```sql
SET @var_name = expr [, @var_name = expr] ...;
SET @var_name := expr [, @var_name := expr]...;
SELECT @var_name := expr [, @var_name :=expr]...;
SELECT 字段名 INTO @var_name FROM 表名;
```

> 使用

```sql
SELECT @var_name;
```

**注意:**

用户定义的变量无需对其进行声明或初始化，只不过获取到的值为NULL.

**实例：**

```sql
-- 将传入的200分制的分数,进行换算,换算成百分制,然后返回分数 --->
create procedure p5(inout score double)
begin
	set score :=score*0.5;
end;

set @score=78;
call p5(@score);
select @score;
```

### 3.局部变量

局部变量是根据需要定义的在局部生效的变量，访问之前，需要DECLARE声明。可用作存储过程内的局部变量和输入参数，局部变量的范

围是在其内声明的BEGIN...END块。

> 声明

```sql
DECLARE 变量名 变量类型 [DEFAULT...];
```

变量类型就是数据库字段类型:INT、BIGINT、CHAR、VARCHAR、DATE、TIME等

> 赋值

```sql
SET 变量名=值;
SET 变量名:=值;
SELECT 字段名 INTO 变量名 FROM 表名;
```

### 4.参数

| 类型  | 含义                                         | 备注 |
| ----- | -------------------------------------------- | ---- |
| IN    | 该类参数作为输入，也就是需要调用时传入值     | 默认 |
| OUT   | 该类参数作为输出，也就是该参数可以作为返回值 |      |
| INOUT | 既可以作为输入参数，也可以作为输出参数       |      |

```sql
CREATE PROCEDURE 存储过程名称([IN/OUT/INOUT 参数名 参数类型])
BEGIN
	-SQL语句
END
```

> 实例

```mysql
create procedure p4(in score int,out result varchar(10))
begin
	if score >=85 then
		set result := '优秀';
	elseif score >=60 then
    	set result := '及格';
    else
    	set result := '不及格';
    end if;
end;
```



## 3.if语句

语法:

```sql
IF 条件1 THEN
	....
ELSEIF 条件2 THEN -- 可选
	....
ELSE             -- 可选   
	....
END IF;
```

> 实例

```mysql
create procedure p3()
begin
	declare score int default 58;
	declare result varchar(10);
	
	if score >=85 then
		set result := '优秀';
	elseif score >=60 then
    	set result := '及格';
    else
    	set result := '不及格';
    end if;
    select result;
    
end;
```

## 4.case语句

**1.语法**

> 语法一

```sql
CASE case_value
	WHEN when_valuel THEN statement_list1
	[WHEN when_value2 THEN statement_list2]...
	[ELSE statement_list]
END CASE;
```



> 语法二

```sql
CASE
	WHEN search_condition1 THEN statement_list1
	[WHEN search_condition2 THEN statement_list2]...
	[ELSE statement_list]
END CASE;
```

**实例：**

```sql
create procedure p6(in month int)
begin
	declare result varchar(10);

	case
		when month>=1 and month <= 3 then
			set result :='第一季度';
		when month>=4and month <= 6 then
			set result :='第二季度';
		when month>=7 and month <= 9 then
			set result :='第三季度';
		when month>=10 and month <= 12 then
			set result:='第四季度';
		else
			set result:='非法参数';
end case;
select concat('您输入的月份为:',month,'，所属的季度为:'result);
end;
```

## 5.循环语句

### 1.while循环

while 循环是有条件的循环控制语句。满足条件后，再执行循环体中的SQL语句。具体语法为:

```sql
# 先判定条件，如果条件为true，则执行逻辑，否则，不执行逻辑
WHILE 条件 DO
	SQL逻辑...
END WHILE;
```

> 实例

```sql
# 计算从1累加到n的值,n为传入的参数值
# A.定义局部变量,记录累加之后的值
# B.每循环一次,就会对n进行减1,如果n减到0,则退出循环
create procedure p7(in n int)
begin
	declare total int default 0;
	while n>0 do
		set total :=total+n;
		set n :=n-1;
	end while;
	select total;
end;
```

### 2.repeat循环

repeat是有条件的循环控制语句,当满足条件的时候退出循环。具体语法为:

```sql
#先执行一次逻辑，然后判定逻辑是否满足，如果满足，则退出。如果不满足，则继续下一次循环
REPEAT
	SQL逻辑...
	UNTIL 条件
END REPEAT;
```

> 实例

```sql
create procedure p8(in n int)
begin
	declare total int default 0;
	
	repeat
		set total :=total +n;
		set n:=n-1;
	until n<= 0
	end repeat;
	
	select total;
end;
```

### 3.loop循环

LOOP 实现简单的循环，如果不在SQL逻辑中增加退出循环的条件，可以用其来实现简单的死循环。LOOP可以配合一下两个语句使用。

- LEAVE:配合循环使用，退出循环。
- ITERATE:必须用在循环中，作用是跳过当前循环剩下的语句，直接进入下一次循环。

```sql
[begin_label:] LOOP
	SQL逻辑...
	END LOOP [end label];
```

```sql
LEAVE label;-- 退出指定标记的循环体
ITERATE label;-- 直接进入下一次循环
```

> 实例

```sql
create procedure p9(in n int)
begin
	declare total int default 0;
	
	sum:loop
		if n<=0 then
			leave sum;
		end if;
		
		set total :=total+n;
		set n :=n-1;
	end loop sum;
	
	select total;
end;
```

## 6.游标

游标(CURSOR)是用来存储查询结果集的数据类型,在存储过程和函数中可以使用游标对结果集进行循环的处理。游标的使用包括游标的声明、OPEN、FETCH 和 CLOSE，其语法分别如下。

> 声明游标

```sql
DECLARE 游标名称 CURSOR FOR 查询语句;
```

> 打开游标

```sql
OPEN 游标名称;
```

> 获取游标记录

```sql
FETCH 游标名称 INTO 变量[,变量 ];
```

> 关闭游标

```sql
CLOSE 游标名称;
```

## 7.条件处理程序

条件处理程序(Handler)可以用来定义在流程控制结构执行过程中遇到问题时相应的处理步骤。具体语法为:

```sql
DECLARE handler_action HANDLER FOR condition value [,condition_value... statement ;

handler_action
	-- CONTINUE: 继续执行当前程序
	-- EXIT:终止执行当前程序
condition_value
	-- SOLSTATE sqlstate_value:状态码，如 02000
	-- SQLWARNING: 所有以01开头的SQLSTATE代码的简写
	-- NOT FOUND:所有以02开头的SQLSTATE代码的简写
	-- SQLEXCEPTION:所有没有被SQLWARNING 或 NOT FOUND捕获的SQLSTATE代码的简写
```

> 实例：

```sql
create procedure p11(in uage int)
begin
	declare uname varchar(100);
	declare upro varchar(100);
	declare u_cursor cursor for select name,profession from tb_user where age <= uage;
	declare exit handler for SQLSTATE '02000' close u_cursor;
	-- exit(handler_action),SQLSTATE '02000'(SQLWARNING)
	-- 这里的SQLSTATE '02000'可用NOT FOUND代替

	drop table if exists tb_user_pro;
	create table if not exists tb user pro(
		id int primary key auto_increment,
		name varchar(100),
		profession varchar(100)
);

	open u_cursor;
	while true do
		fetch u cursor into uname,upro;
		insert into tb_user_pro values(null,uname, upro);
	end while;
	close u_cursor;

end;
```



## 8.存储函数

存储函数是有返回值的存储过程，存储函数的参数只能是IN类型的。具体语法如下:

```sql
CREATE FUNCTION 存储函数名称([参数列表])
RETURNS type [characteristic ...]
BEGIN
	-- SQL语句
	RETURN ...
END;
```

> **characteristic说明:**

- `DETERMINISTIC`:相同的输入参数总是产生相同的结果
- `NO SOL`:不包含 SOL语句。
- `READS SOL DATA`:包含读取数据的语句，但不包含写入数据的语句。

> 实例

```sql
create function fun1(n int)
returns int deterministic
begin
	declare total int default 0;
	
	while n>0 do
		set total := total + n;
		set n := n- 1;
	end while;
	
	return total;
end;
```

## 9.触发器

触发器是与表有关的数据库对象，指在 insert/update/delete 之前或之后，触发并执行触发器中定义的SOL语句集合。触发器的这种特性可以协助应用在数据库端确保数据的完整性，日志记录，数据校验等操作，

使用别名 `OLD` 和 `NEW` 来引用触发器中发生变化的记录内容，这与其他的数据库是相似的。现在触发器还只支持行级触发，不支持语句级触发。

| 触发器类型      | NEW 和 OLD                                             |
| --------------- | ------------------------------------------------------ |
| INSERT 型触发器 | NEW 表示将要或者已经新增的数据                         |
| UPDATE 型触发器 | OLD 表示修改之前的数据，NEW 表示将要或已经修改后的数据 |
| DELETE型触发器  | OLD 表示将要或者已经删除的数据                         |

**语法**

> 创建

```sql
CREATE TRIGGER trigger_name
BEFORE/AFTER INSERT/UPDATE/DELETE
ON tbl_name FOR EACH ROW -- 行级触发器
BEGIN
	trigger_stmt ;
END; 
```

> 查看

```sql
SHOW TRIGGERS ;
```

> 删除

```sql
DROP TRIGGER [schema_name.]trigger_name;-- 如果没有指定 schema_name,默认为当前数据库。
```

### 1.插入数据触发器

```sql
/*4．创建一个触发器，如果新注册的消费者用户用户名已经存在，则不允许该用户注册，并提示：“该用户已经存在，请更改用户名后重新注册”。*/
create trigger b1
    before insert on consumer for each row
begin
    declare count int;
    select count(*) into count from consumer where UserName=new.UserName;

    if count>0 then
        signal sqlstate '45000' set message_text ='该用户已经存在，请更改用户名后重新注册';
    end if;
end;
/*测试数据*/
insert into consumer values ('00000006','qiqi','wq17','柒柒','女','15979444602','江西','qiiqi','M0000001');
```

### 2.修改数据触发器

```sql
create trigger tb_user_update_trigger
	after update on tb_user for each row
begin
	insert into user_logs(id, operation, operate_time, operate_id, operate_params) VALUES
	(null,'update',now(),new.id,
		concat('更新之前的数据:id=',old.id,',name='old.name，',phone='old.phone,
               ',email=',old.email,',profession',old.profession,
			'|更新之后的数据:id=',new.id,',name=',new.name，',phone=',NEW.phone,
               ',email=',NEW.email,'profession=',NEW.profession));
end;
```

### 3.删除数据触发器

```sql
/*7．创建一个触发器，当从水果表中删除一条记录时，其对应的订单也一起删除。*/
create trigger t4 after
    delete on fruit for each row
    begin
        delete from orders
        where orders.FruitID=old.FruitID;
    end;
    
/*测试数据*/
delete from fruit where FruitID='F0001';
```

# 七、锁

锁是计算机协调多个进程或线程并发访问某一资源的机制。在数据库中，除传统的计算资源(CPU、RAM、I/O)的争用以外，数据也是一种供许多用户共享的资源。如何保证数据并发访问的一致性、有效性是所有数据库必须解决的一个问题，锁冲突也是影响数据库并发访问性能的一个重要因素。从这个角度来说，锁对数据库而言显得尤其重要，也更加复杂。

MySOL中的锁，按照锁的粒度分，分为以下三类:

- 全局锁:锁定数据库中的所有表。
- 表级锁:每次操作锁住整张表
- 行级锁:每次操作锁住对应的行数据。

## 1.全局锁

全局锁就是对整个数据库实例加锁，加锁后整个实例就处于只读状态，后续的DML的写语句，DDL语句，已经更新操作的事务提交语句都将被阻塞。

其典型的使用场景是做全库的逻辑备份，对所有的表进行锁定，从而获取一致性视图，保证数据的完整性。

**语法**

```sql
flush tables with read lock;/*上锁*/

mysqldump -uroot-p1234 qiqizizzz>qiqizizzz1.sql;
-- 1234是密码
-- qiqizizzz是数据库

unlock tables; /*开锁*/
```

数据库中加全局锁，是一个比较重的操作，存在以下问题

1.如果在主库上备份，那么在备份期间都不能执行更新，业务基本上就得停摆。

2.如果在从库上备份，那么在备份期间从库不能执行主库同步过来的二进制日志(binlog)，会导致主从延迟，

在InnoDB引擎中，我们可以在备份时加上参数--single-transaction 参数来完成不加锁的一致性数据备份,

```sql
mysqldump --single-transaction -uroot-p123456 qiqizizzz>qiqizizzz.sql
```

## 2.表级锁

对于表锁，分为两类:

1.表共享读锁(read lock)

2.表独占写锁(write lock)

**语法**

```sql
lock tables 表名... read/write -- 加锁
unlock tables/客户端断开连接 -- 释放锁
```

元数据锁(meta data lock，MDL)

MDL加锁过程是系统自动控制，无需显式使用，在访问一张表的时候会自动加上。MDL锁主要作用是维护表元数据的数据一致性，在表上有活动事务的时候，不可以对元数据进行写入操作。为了避免DML与DDL冲突，保证读写的正确性。

在MVSOL5.5中引入了MDL，当对一张表进行增删改查的时候，加MDL读锁(共享);当对表结构进行变更操作的时候，加MDL写锁(排他)。

| 对应SQL                                      | 锁类型                                | 说明                                             |
| -------------------------------------------- | ------------------------------------- | ------------------------------------------------ |
| lock tables xxx read /write                  | SHARED_READ_ONLY/SHARED_NO_READ_WRITE |                                                  |
| select、select ... lock in share mode        | SHARED_READ                           | 与SHARED_READ、SHARED_WRITE兼容，与EXCLUSIVE互斥 |
| insert 、update、delete、select...for update | SHARED_WRITE                          | 与SHARED_READ、SHARED_WRITE兼容，与EXCLUSIVE互斥 |
| alter table ...                              | EXCLUSIVE                             | 与其他的MDL都互斥                                |

查看元数据锁:

```sql
select object_type,object_schema,object_name,lock_type,lock_duration from performance_schema.metadata locks;
```

### 意向锁

为了避免DML在执行时，加的行锁与表锁的冲突，在InnoDB中引入了意向锁，使得表锁不用检查每行数据是否加锁，使用意向锁来减少表锁的检查。

意向锁

- 意向共享锁(IS):与表锁共享锁(read)兼容，与表锁排它锁(write)互斥。
- 意向排他锁(IX):与表锁共享锁(read)及排它锁(write)都互斥。意向锁之间不会互斥。

可以通过以下SOL，查看意向锁及行锁的加锁情况:

```sql
select object_schema,object_name,index_name,lock_type,lock_mode,lock_data 
from performance_schema.data_locks;
```

## 3.行级锁

行级锁，每次操作锁住对应的行数据。锁定粒度最小，发生锁冲突的概率最低，并发度最高。应用在InnoDB存储引擎中。

InnoDB的数据是基于索引组织的，行锁是通过对索引上的索引项加锁来实现的，而不是对记录加的锁。对于行级锁，主要分为以下三类:

- 行锁(Record Lock):锁定单个行记录的锁，防止其他事务对此行进行update和delete。在RC、RR隔离级别下都支持。
- 间隙锁(GapLock):锁定索引记录间隙(不含该记录)，确保索引记录间隙不变，防止其他事务在这个间隙进行inser，产生幻读。在RR隔离级别下都支持。
- 3.临键锁(Next-KeyLock):行锁和间隙锁组合，同时锁住数据，并锁住数据前面的间隙Gap。在RR隔离级别下支持。

InnoDB实现了以下两种类型的行锁:

1.共享锁(S):允许一个事务去读一行，阻止其他事务获得相同数据集的排它锁。

2.排他锁(X):允许获取排他锁的事务更新数据，阻止其他事务获得相同数据集的共享锁和排他锁。

| 当前锁类型\请求锁类型 | S(共享锁) | X(排他锁) |
| --------------------- | --------- | --------- |
| S(共享锁)             | 兼容      | 冲突      |
| X(排他锁)             | 冲突      | 冲突      |



| SQL                           | 行锁类型       | 说明                                   |
| ----------------------------- | -------------- | -------------------------------------- |
| INSERT ...                    | 排他锁         | 自动加锁                               |
| UPDATE ...                    | 排他锁         | 自动加锁                               |
| DELETE ..                     | 排他锁         | 自动加锁                               |
| SELECT(正常)                  | **不加任何锁** |                                        |
| SELECT ... LOCK IN SHARE MODE | 共享锁         | 需要手动在SELECT之后加LOCKINSHARE MODE |
| SELECT ... FOR UPDATE         | 排他锁         | 需要手动在SELECT之后加FOR UPDATE       |


默认情况下，InnODB在 REPEATABLE READ事务隔离级别运行，InnoDB使用 next-key锁进行搜索和索引扫描，以防止幻读。

1.针对唯一索引进行检索时，对已存在的记录进行等值匹配时，将会自动优化为行锁。

2.nnoDB的行锁是针对于索引加的锁，不通过索引条件检索数据，那么InnoDB将对表中的所有记录加锁，此时 就会升级为表锁。
可以通过以下SOL，查看意向锁及行锁的加锁情况:

```sql
select object_schema,object_name,index_name,lock_type,lock_mode,lock_data 
from performance_schema.data_locks;
```



间隙锁/临键锁

默认情况下，InnoDB在 REPEATABLE READ事务隔离级别运行，InnoDB使用 next-key 锁进行搜索和索引扫描，以防止幻读。

- 索引上的等值查询(唯一索引)，给不存在的记录加锁时,优化为间隙锁 。
- 索引上的等值查询(普通索引)，向右遍历时最后一个值不满足查询需求时，next-keylock退化为间隙锁。
- 索引上的范围查询(唯一索引)--会访问到不满足条件的第一个值为止。



**注意**:间隙锁唯一目的是防止其他事务插入间隙。间隙锁可以共存，一个事务采用的间隙锁不会阻止另一个事务在同一间隙上采用间隙锁。
