# MySQL学习路线

![image-20220821171304267](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821171304267.png)

# MySQL学习技巧：==学习mysql videos时候，我先自己看着笔记自行先敲一次，弄好了再过一遍视频，这这样子会学的比较扎实！==

# 基础篇（学完就能处理大部分的数据库业务开发工作了）

（我直接在我的服务器上按照MySQL，然后用我的Vscode连接并进行学习即可！）

Ubuntu Linux MySQL的下载地址：https://dev.mysql.com/downloads/mysql/5.6.html#downloads

windows下：去官网下载mysql-installer-community-8.0.29.0.msi

==注意：一旦你的电脑之前下载过旧版本的mysql的话，要安装别的版本的mysql就必须要先卸载掉原来的mysql才可以去安装新的！==



## 概念：

①数据库：是存储数据的仓库。

②数据库管理系统：操作和管理数据库的大型软件。

③SQL：操作关系型数据库的编程语言。

对于任何==关系型数据库（MySQL,Oracle,SQL Server）==都是通过==SQL==这种编程语言来操作的！

（SQL语言为操作关系型数据库提供了一套统一的标准）

### windows下的mysql启动与停止：（在管理员的cmd黑窗口下执行）

```bash
启动命令：net start mysql80
停止命令：net stop mysql80
```

![image-20220821181123233](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821181123233.png)

==如何操作MySQL呢？==

①使用mysql命令行工具：

![image-20220821231234714](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821231234714.png)

②使用客户端工具：（来连接MySQL数据库）

③：

![image-20220821231345843](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821231345843.png)

配置环境变量：

添加：C:\Program Files\MySQL\MySQL Server 8.0\bin\

到系统高级环境变量的path路径下即可！

## 数据模型：

注意：通过表格的形式（类似于excel表的形式）来存储数据的方式我们就称之为：==关系型==

否则，就称之为==非关系型==

![image-20220821231859364](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821231859364.png)

==解释==：我们在一个电脑/服务器上安装完mysql之后，那么该电脑/服务器就成为了mysql服务器了！此时就需要客户端去连接该mysql服务器，通过这个服务器上到mysql数据库管理系统创建各数据库，然后通过操作SQL语句来创建各种表格以存储各类数据！！！

![image-20220821232050020](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821232050020.png)

## SQL的通用语法及分类

- DDL: 数据==定义==语言，用来定义数据库对象（数据库、表、字段、索引）

- DML: 数据==操作==语言，用来对数据库表中的数据进行增删改

- DQL: 数据==查询==语言，用来查询数据库中表的记录

- DCL: 数据==控制==语言，用来创建数据库用户、控制数据库的控制权限

  注意事项：

  1：SQL语句可单行or多行书写，并以==分号（;）==结尾。

  2：SQL语句可使用==空格/缩进（多少个无所谓）==来增强语句的可读性。

  3：MySQL数据库的SQL语句==不区分大小写==，关键字建议使用大写。

  4：对于注释：

  ​	4.1：单行注释：--注释内容 或 # 注释内容（MySQL特有）

  ​	4.2：多行注释：/* 注释内容 */

  

### MySQL的数据类型：

#### ①数值类型：

![image-20220821235405634](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821235405634.png)

注：对于==含有小数==的数据，比如对于123.45这个数字，其中 精度是5，标度是2

比如score变量，设置 score double(4,1)：表示分数score是double类型且精度为4，标度为1的这样的数据类型！

比如age变量，设置 age TINYINT UNSIGNED：表示年龄age是TINYINT UNSIGNED这种数据类型的数据！

#### ②字符串类型：

![image-20220822000958906](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220822000958906.png)

==注1==：带TEXT的是描述文本数据的，带BLOB的是描述二进制数据的。

==注2==：问：==那么何为二进制数据呢？==比如视频、音频、图像等都是可以以二进制的形式存储在数据库当中的！但是在真正开发项目时我们不会这么干，因为这么干效率不高且不方便管理！so，对于音视频这类的数据，我们会采用专门的文件服务器来进行存储！==so带BLOB的数据类型就相对来说笔记少使用！！！==

==注3==：使用字符串类型来描述索要存储的数据时，必须要在类型关键字后指定长度！比如：char(1)，指定大小为1个字节的字符串类型（==且是最多能存储1个字节的数据，一旦超过这个长度就会报错！！！==）

==注4==：变长字符串varchar和定长字符串char有啥区别呢？答：定长字符串类型比如char(10)，你几时真正存入的数据只占用1个字节，那么其他位置默认也会补0，但是如果是varchar(10)的话，系统会自动计算出你存入的数据是只占用1个字节，就只用1字节的空间来存储你这个变量！但是char比varchar的性能要好很多！因为不需要自动do计算变量所占用内存的工作！

#### ③日期时间类型：

![image-20220822001130329](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220822001130329.png)

==注1==：使用DATE TIME DATETIME这三个类型关键字会比较多！

案例：

![image-20220822001422922](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220822001422922.png)

```mysql
create table employee_Info(
	id TINYINT UNSIGNED  COMMENT '编号',
	workno  varchar(10)  COMMENT '员工工号',
	name    varchar(10)  COMMENT '员工姓名',
	gender  char(1)      COMMENT '性别',
    age TINYINT UNSIGNED COMMENT '年龄',
    idcard  char(18)     COMMENT '身份证号',
	entrydate DATE       COMMENT '入职时间'
)COMMENT '员工信息表';
```

![image-20220822002526230](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220822002526230.png)

### DDL（数据定义语言）

数据定义语言

#### 数据库操作

查询所有数据库：
`SHOW DATABASES;`
查询当前所处的（到底是哪个）数据库：
`SELECT DATABASE();`
创建数据库：
`CREATE DATABASE [ IF NOT EXISTS ] 数据库名 [ DEFAULT CHARSET 字符集] [COLLATE 排序规则 ];`

==注：其中，[]内的内容是可选可不选的，且字符集优先使用utf8mb4。比如：==

```bash
create database if not exists itheima default charset utf8mb4;
```

删除数据库：
`DROP DATABASE [ IF EXISTS ] 数据库名;`
使用数据库：（作用：切换/使用某指定的数据库）
`USE 数据库名;`

##### 注意事项

- UTF8字符集长度为3字节，有些符号占4字节，所以推荐用utf8mb4字符集（是utf8的超集合）

#### 表操作

##### DDL-表操作-创建：

查询当前数据库所有表：
`SHOW TABLES;`
查询表结构：
`DESC 表名;`
查询指定表的建表语句：
`SHOW CREATE TABLE 表名;`

创建表：
```mysql
CREATE TABLE 表名(
	字段1 字段1类型 [COMMENT 字段1注释],# COMMENT就是让你给字段1写个注释的意思，以下雷同！
	字段2 字段2类型 [COMMENT 字段2注释],
	字段3 字段3类型 [COMMENT 字段3注释],
	...
	字段n 字段n类型 [COMMENT 字段n注释] # 注意：最后一个字段后面没有逗号
)[ COMMENT 表注释 ];
```
==注意：最后一个字段后面没有逗号==

例子：![image-20220821235029490](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821235029490.png)

![image-20220821235020656](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821235020656.png)

![image-20220821235131763](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821235131763.png)

![image-20220821235233681](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821235233681.png)

##### DDL-表操作-修改：

添加字段
`ALTER TABLE 表名 ADD 字段名 类型(长度) [COMMENT 注释] [约束];`
例：`ALTER TABLE emp ADD nickname varchar(20) COMMENT '昵称';`

==（方括号[]中的内容都是可选可不选的！）==

修改数据类型：
`ALTER TABLE 表名 MODIFY 字段名 新数据类型(长度);`
修改字段名和字段类型：
`ALTER TABLE 表名 CHANGE 旧字段名 新字段名 类型(长度) [COMMENT 注释] [约束];`
例：将emp表的nickname字段修改为username，类型为varchar(30)
`ALTER TABLE emp CHANGE nickname username varchar(30) COMMENT '昵称';`

删除字段：
`ALTER TABLE 表名 DROP 字段名;`

修改表名：
`ALTER TABLE 表名 RENAME TO 新表名`

删除表：（较为常用）
`DROP TABLE [IF EXISTS] 表名;`
删除表，并重新==（以原表格的原形式）==创建该表：（较为少用）
`TRUNCATE TABLE 表名;`

==疑问：那为啥我要多此一举地重新创建这个表格呢？==

答：因为==你删除并重新创建此表格后，以前以该表格的形式存储的all的数据data都被删除了！！！==

而新创建的新表格与原表格形式一样，只是此时没有以前的所有数据了而已！！！

### DML（数据操作语言）

Data Manipulation Language,用来对数据库中表的数据记录进行增删改操作。

#### 添加数据（INSERT）

指定字段：
`INSERT INTO 表名 (字段名1, 字段名2, ...) VALUES (值1, 值2, ...);`
全部字段：
`INSERT INTO 表名 VALUES (值1, 值2, ...);`

批量添加数据：
`INSERT INTO 表名 (字段名1, 字段名2, ...) VALUES (值1, 值2, ...), (值1, 值2, ...), (值1, 值2, ...);`
`INSERT INTO 表名 VALUES (值1, 值2, ...), (值1, 值2, ...), (值1, 值2, ...);`

##### ==注意事项==

- 字符串和日期类型数据应该包含在引号''中
- 插入的数据大小应该在字段的规定范围内
- 插入数据时，==指定的字段==顺序需要与==值的顺序==是一一对应的



#### 更新（修改：UPDATE）和删除（DELETE）数据

修改数据： 
`UPDATE 表名 SET 字段名1 = 值1, 字段名2 = 值2, ... [ WHERE 条件 ];`
例：
`UPDATE emp SET name = 'Jack' WHERE id = 1;`

`UPDATE employee SET `name` = 'fanfanya' WHERE id = 1 OR id = 0;`

当id=1或者id=0时就把employee表中的name设置为'fanfanya'

`UPDATE employee SET id = 12 , `name` = '林玉凤是憨批' WHERE gender = '女';`

删除数据：
`DELETE FROM 表名 [ WHERE 条件 ];`

例：`DELETE from employee WHERE id = 1;` `DELETE from employee;`

##### ==注意事项==

- 修改语句的==WHERE条件==是可有，也可以没有的，即：==如果没有带WHERE条件，则会修改 或 删除 整张表的所有数据==。
- DELETE语句不能删除某个指定字段对应数据的值（但可以使用UPDATE 将对应字段set为NULL即可！）

### DQL（数据查询语言）

Data Query Language,用来对数据库中表的数据记录进行查询操作。

语法：

```mysql
SELECT
	字段列表
FROM
	表名字段
WHERE
	条件列表
GROUP BY
	分组字段列表
HAVING
	分组后的条件列表
ORDER BY
	排序字段列表
LIMIT
	分页参数
```

#### 基础查询-语法

查询多个字段：（==基础查询的关键字是SELECT FROM==）
`SELECT 字段1, 字段2, 字段3, ... FROM 表名;`
`SELECT * FROM 表名;`

设置别名：（对于所查询的字段，我们是可以设置别名的，从而增强sql语句的可读性）
`SELECT 字段1 [ AS 别名1 ], 字段2 [ AS 别名2 ], 字段3 [ AS 别名3 ], ... FROM 表名;`
`SELECT 字段1 [ 别名1 ], 字段2 [ 别名2 ], 字段3 [ 别名3 ], ... FROM 表名;`

例如：

`SELECT name AS employee_name,age as employee_age,workno as employee_workno,id FROM employee;`

###### 注意事项

- 别名的设置是==可选可不选的==。
- 设置别名的==AS==关键字是可以省略的。
- ==尽量少用通配符*号==，因为比如要查询表中all的字段，用\*就不明显！不利于我们程序员查看项目的mysql源码！

对于查询的结果==去除重复==记录：
`SELECT DISTINCT 字段列表 FROM 表名;`

转义：
`SELECT * FROM 表名 WHERE name LIKE '/_张三' ESCAPE '/'`
/ 之后的\_不作为通配符



#### 条件查询-语法

语法：（==分页查询的关键字是WHERE==）
`SELECT 字段列表 FROM 表名 WHERE 条件列表;`

条件：

| 比较运算符            | 功能                                                         |
| --------------------- | ------------------------------------------------------------ |
| >                     | 大于                                                         |
| >=                    | 大于等于                                                     |
| <                     | 小于                                                         |
| <=                    | 小于等于                                                     |
| =                     | 等于                                                         |
| <> 或 !=              | 不等于                                                       |
| BETWEEN ... AND ...   | 在某个范围内（含最小、最大值）                               |
| IN(...)               | 在in之后的列表中的值，多选一（多个选其中一个，简化了写多个OR的条件操作） |
| ==LIKE 占位符==(常用) | ==模糊匹配（\_匹配单个字符，%匹配任意个字符，只用来匹配字符）== |
| IS NULL               | 是NULL（判断字符串类型的字段所存数据是否为空的）             |
| IS NOT NULL           | 不是NULL（判断字符串类型的字段所存数据是否不为空的）         |

| 逻辑运算符         | 功能                         |
| ------------------ | ---------------------------- |
| AND 或 &&          | 并且（多个条件同时成立）     |
| OR 或 &#124;&#124; | 或者（多个条件任意一个成立） |
| NOT 或 !           | 非，不是                     |

例子：
```mysql
-- 年龄等于30
select * from employee where age = 30;
-- 年龄小于30
select * from employee where age < 30;
-- 小于等于
select * from employee where age <= 30;
-- 没有身份证
select * from employee where idcard is null or idcard = '';
-- 有身份证
select * from employee where idcard;
select * from employee where idcard is not null;
-- 不等于
select * from employee where age != 30;
-- 年龄在20到30之间
select * from employee where age between 20 and 30;
select * from employee where age >= 20 and age <= 30;
-- 下面语句不报错，但查不到任何信息
select * from employee where age between 30 and 20;
-- 性别为女且年龄小于30
select * from employee where age < 30 and gender = '女';
-- 年龄等于25或30或35
select * from employee where age = 25 or age = 30 or age = 35;
select * from employee where age in (25, 30, 35);
-- 姓名为两个字
select * from employee where name like '__';
-- 身份证最后为X
select * from employee where idcard like '%X';
-- 判断身份证是否为空字符串（前提是employee.idcard 已经被设置为NULL了）
SELECT * from employee where idcard IS NULL;
-- 判断身份证是否不为空字符串（即：查询all有身份证的employee）
SELECT * from employee where idcard IS NOT NULL;
```

######  注意事项：

- 对于LIKE 占位符：一个_就匹配单个字符，2个就匹配2个。而对于1个%，就能匹配任意个字符了！
- BETWEEN num1 and num2;其中num1必须 <= num2，否则你就没法使用该条件规则来do条件查询了！即使你do了也没有任何输出结果！

#### 聚合函数-语法

聚合函数：将==一列数据==作为==一个整体==，进行==纵向计算==。

常见聚合函数：（这些函数都是作用于table的某一列数据的）

| 函数  | 功能     |
| ----- | -------- |
| count | 统计数量 |
| max   | 最大值   |
| min   | 最小值   |
| avg   | 平均值   |
| sum   | 求和     |

语法：
`SELECT 聚合函数(字段列表) FROM 表名;`
例：
`SELECT count(id) from employee where workaddress = "广东省";`

例子：

```mysql
-- 1.统计企业员工数量
SELECT COUNT(*) FROM employee; 
-- 或者,因为每条记录都要对应的id号
SELECT COUNT(id) FROM employee;
-- 2.统计企业员工的平均年龄
SELECT AVG(age) FROM employee;
-- 3.统计企业员工的最大年龄
SELECT MAX(age) FROM employee;
-- 4.统计企业员工的最小年龄
SELECT MIN(age) FROM employee;
-- 5.统计企业all女性员工的年龄和
SELECT SUM(age) FROM employee WHERE gender = '女';
```

###### 注意事项：

- ==所有的NULL值==都不参与所有聚合函数的运算。

#### 分组查询（==分组操作通常会配合着前面介绍的聚合函数一起操作==）-语法

语法：（==分组查询的关键字是GROUP BY==）
`SELECT 字段列表 FROM 表名 [ WHERE 条件 ] GROUP BY 分组字段名 [ HAVING 分组后的过滤条件 ];`

一般而言，你的==分组字段是什么==，就==SELECT什么字段==！！！

==where 和 having 的区别==：

- 执行时机不同：where是==分组之前==进行过滤，不满足where条件不参与分组；having是==分组之后==对结果进行过滤。
- 判断条件不同：where不能对聚合函数进行判断（即where不能使用聚合函数），而having可以。

例子：

```mysql
-- 1.根据性别分组，统计男性和女性数量（仅显示分组数量，不显示哪个是男哪个是女）
select count(*) from employee group by gender;
-- 2.根据性别分组，统计男性和女性数量（既显示分组数量，又显示哪个是男哪个是女）
select gender, count(*) from employee group by gender;
-- 3.根据性别分组，统计男性和女性的平均年龄
select gender, avg(age) from employee group by gender;
-- 4.年龄小于45，并根据工作地址分组
select workaddress, count(*) from employee where age < 45 group by workaddress;
-- 5.年龄小于45，并根据工作地址分组，获取员工数量大于等于3的工作地址
select workaddress, count(*) as address_count from employee where age < 45 group by workaddress having address_count >= 3;
```

######  注意事项

- 执行顺序：where > 聚合函数 > having
- 分组之后，查询的字段一般为聚合函数和分组字段，查询其他字段无任何意义

#### 排序查询-语法

语法：（==排序查询的关键字是ORDER BY==）
`SELECT 字段列表 FROM 表名 ORDER BY 字段1 排序方式1, 字段2 排序方式2;`

排序方式：

- ASC: 升序（默认缺省排序方式时就是do升序的）
- DESC: 降序

例子：

```mysql
-- 根据年龄升序排序
SELECT * FROM employee ORDER BY age ASC;
SELECT * FROM employee ORDER BY age;
-- 两字段排序，先根据年龄升序排序，年龄相同，再根据入职时间降序排序
SELECT * FROM employee ORDER BY age ASC, entrydate DESC;
```

###### 注意事项

- 如果是多字段排序，当第一个字段值相同时，才会根据第二个字段进行排序(先按照第一个字段值进行排序，然后再按照第二个字段进行排序)


#### 分页查询-语法

语法：（==分页查询的关键字是LIMIT==）
`SELECT 字段列表 FROM 表名 LIMIT 起始索引, 查询记录数;`

例子：

```mysql
-- 查询第一页数据，展示10条
SELECT * FROM employee LIMIT 0, 10;# 从索引0开始查询10条数据
-- 查询第二页
SELECT * FROM employee LIMIT 10, 10;# 从索引1开始查询10条数据
```

###### 注意事项

- 起始索引从0开始，起始索引 = （查询页码 - 1） * 每页显示记录数
- 分页查询是数据库的方言，不同数据库有不同实现，MySQL是LIMIT
- 如果查询的是第一页数据，起始索引可以省略，直接简写 LIMIT 10

#### DQL执行顺序(这是非常重要的小细节！越往==右边==，执行==优先级越低==)

FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY -> LIMIT

比如：

```mysql
-- 查询性别为男，且年龄在20到40岁（含）以内的前5个员工的信息，并对查询结果按照年龄升序排序，年龄相同按照入职时间升序排序,其中前几个员工信息就是要用分页操作，索引为0，查询记录数是5而已。
SELECT * FROM employee WHERE gender = '男' and (age BETWEEN 20 and 40 ) ORDER BY age ASC,entrydate ASC LIMIT 0,6;
-- 为了你的sql语句更可读，加个括号()是ok的！没问题的！
```

### DCL

Data Control Language,数据控制语言，用来：

①管理数据库的用户：比如一个MySQL服务器，能给哪些用户来访问。

②控制数据库的访问权限（每个用户具体有什么样的访问权限）：比如用户能操作总数据库里面的哪几个数据库。

#### 管理用户

查询用户：

```mysql
USE mysql;
SELECT * FROM user;
```

创建用户:
`CREATE USER '用户名'@'主机名' IDENTIFIED BY '密码';`

修改用户密码：
`ALTER USER '用户名'@'主机名' IDENTIFIED WITH mysql_native_password BY '新密码';`

删除用户：
`DROP USER '用户名'@'主机名';`

其中，

用户名：哪个用户能够访问当前的mysql数据库服务器！

主机名：在哪个主机上能够访问当前的mysql数据库服务器！

```mysql
'localhost':表示当前本地主机
```

例子：

```mysql
-- 创建用户test，只能在当前主机localhost访问
create user 'test'@'localhost' identified by '123456';
-- 创建用户test，能在任意主机访问该mysql服务器,只需要用通配符%就可以实现！
create user 'test'@'%' identified by '123456';
create user 'test' identified by '123456';
-- 修改密码
alter user 'test'@'localhost' identified with mysql_native_password by '1234';
-- 删除用户
drop user 'test'@'localhost';
```

##### 注意事项

- 主机名可以使用 % 通配
- 这类SQL语句，对于开发人员来说操作的比较少，主要是运维和DBA（Database Administrator 数据库管理员）使用。

#### 权限控制

mysql中定义了许多种权限，但非常常用的权限就如下几种：

| 权限                | 说明                       |
| ------------------- | -------------------------- |
| ALL, ALL PRIVILEGES | 所有权限  的权限           |
| SELECT              | 查询数据  的权限           |
| INSERT              | 插入数据  的权限           |
| UPDATE              | 修改数据  的权限           |
| DELETE              | 删除数据  的权限           |
| ALTER               | 修改表      的权限         |
| DROP                | 删除数据库/表/视图  的权限 |
| CREATE              | 创建数据库/表  的权限      |

更多权限请看[权限一览表](#权限一览表 "权限一览表")

下面只介绍3种常用权限的语法：

1.查询权限：
`SHOW GRANTS FOR '用户名'@'主机名';`

2.授予权限：
`GRANT 权限列表 ON 数据库名.表名 TO '用户名'@'主机名';`

3.撤销权限：
`REVOKE 权限列表 ON 数据库名.表名 FROM '用户名'@'主机名';`

##### 注意事项

- 多个权限 应 使用逗号,分隔

- 授权时，数据库名和表名可以用 * 进行通配，代表所有

- 若授权给一个用户 \*.\*的权限就相当于这个用户就是另一个root用户的意思了！

  (比如：GRANT ALL on *.* TO 'linzhuofan'@'%';)

例子：

```mysql
-- 1.查询权限
show GRANTS FOR 'linzhuofan'@'%';
result:
GRANT USAGE ON *.* TO `linzhuofan`@`%`
-- 其中，USAGE表示该用户仅仅拥有登录并连接上mysql服务器的权限而已
-- 2.授予权限
GRANT ALL on itcast.* TO 'linzhuofan'@'%';
show GRANTS FOR 'linzhuofan'@'%';
result:
GRANT USAGE ON *.* TO `linzhuofan`@`%`
GRANT ALL PRIVILEGES ON `itcast`.* TO `linzhuofan`@`%`
-- 3.撤销权限
REVOKE all on itcast.* from 'linzhuofan'@'%';
show GRANTS FOR 'linzhuofan'@'%';
result:
GRANT USAGE ON *.* TO `linzhuofan`@`%`
```

## 函数

函数：指的是可以直接被另一段程序调用的程序或代码。在mysql中已经内置好了许多函数，我们要do的就是调用这些函数来实现我们的业务需求！

- 字符串函数
- 数值函数
- 日期函数
- 流程函数

### 字符串函数

常用的字符串函数：

| 函数  | 功能  |
| ------------ | ------------ |
| CONCAT(s1, s2, ..., sn)  | 字符串拼接，将s1, s2, ..., sn拼接成一个字符串  |
| LOWER(str)  | 将字符串全部转为小写  |
| UPPER(str)  | 将字符串全部转为大写  |
| LPAD(str, n, pad)  | ==左==填充，用字符串pad对str的左边进行填充，达到n个字符串长度（拿pad填充str的左边部分字符串，然后达到总字符串长度为n） |
| RPAD(str, n, pad)  | ==右==填充，用字符串pad对str的右边进行填充，达到n个字符串长度（拿pad填充str的右边部分字符串，然后达到总字符串长度为n） |
| TRIM(str)  | 去掉字符串头部和尾部的空格（中间的空格子不管！） |
| SUBSTRING(str, start, len)  | 返回从字符串str从start位置起的len个长度的字符串,其中起始索引是1！而不是0！SELECT SUBSTR('linzhuofan',1,3); ==> 'lin' |

使用示例：

```mysql
# 使用方式：SELECT 函数(params);
-- 拼接
SELECT CONCAT('Hello', 'World');
-- 小写
SELECT LOWER('Hello');
-- 大写
SELECT UPPER('Hello');
-- 左填充
SELECT LPAD('01', 5, '-');
-- 右填充
SELECT RPAD('01', 5, '-');
-- 去除空格
SELECT TRIM(' Hello World ');
-- 切片（起始索引为1）
SELECT SUBSTRING('Hello World', 1, 5);

# 小需求：员工中workno不为5位数的就在其前面补齐0！补到共长为5位数为止。
# 比如，1号员工workno=00001,100号员工workno=00100
UPDATE employee SET workno = LPAD(employee.workno,5,'0');
```

### 数值函数

常见函数：

| 函数  | 功能  |
| ------------ | ------------ |
| CEIL(x)  | 向上取整 (比如1.1向上取整==》2)只要小数位不为0都能够取成功！ |
| FLOOR(x)  | 向下取整 (比如3.8向下取整==》3)只要小数位不为0都能够取成功！ |
| MOD(x, y)  | 返回x/y的模  |
| RAND() | 返回0~1内的随机数 |
| ROUND(x, y) | 求参数x的四舍五入值，保留y位小数 |

使用示例：

```mysql
SELECT FLOOR(3.8);
SELECT CEIL(3.8);
SELECT FLOOR(3.8);
SELECT MOD(6,2);
select RAND();
SELECT ROUND(3.384612,3);
# 小需求：通过数据库函数，生成一个6位数的随机验证码
-- 考虑到0.099999*1000000还是个5位数
-- way1:不足6位数就补齐0！在前面补'0' or 在后面补'0'都ok！
SELECT LPAD(ROUND(RAND()*1000000,0),6,'0') as'6位数随机验证码';
SELECT RPAD(ROUND(RAND()*1000000,0),6,'0') as'6位数随机验证码';
-- way2:
SELECT if(RAND() < 0.1,ROUND(RAND()*10000000,0),ROUND(RAND()*1000000,0))as '6位数随机验证码';
```

### 日期函数

常用函数：

| 函数  | 功能  |
| ------------ | ------------ |
| CURDATE()  | 返回当前日期  |
| CURTIME()  | 返回当前时间  |
| NOW()  | 返回当前日期和时间  |
| YEAR(date)  | 获取指定date的年份  |
| MONTH(date)  | 获取指定date的月份  |
| DAY(date)  | 获取指定date的日期  |
| DATE_ADD(date, INTERVAL expr type)  | 返回一个指定日期/时间值的基础上再加上一个时间间隔expr后的时间值，单位是type：可选（YEAR/MONTH/DAY） |
| DATEDIFF(date1, date2)  | 返回 起始时间date1 和 结束时间date2 之间的==天数==,即（date1-date2） |

使用示例：

```mysql
SELECT CURDATE();
SELECT CURTIME();
SELECT NOW();
SELECT YEAR('2021.10.1');
SELECT YEAR('2000-8-1');
SELECT MONTH('2021.10.1');
SELECT MONTH('2000-8-1');
SELECT DAY('2000-8-12');
SELECT DAY('2021.10.1');
-- DATE_ADD 当前时间往后加10年
SELECT DATE_ADD(NOW(),INTERVAL 10 YEAR);
-- DATE_ADD 当前时间往后加70个月
SELECT DATE_ADD(NOW(),INTERVAL 70 MONTH);
-- DATE_ADD 当前时间往后加70天
SELECT DATE_ADD(NOW(),INTERVAL 70 DAY);
SELECT DATEDIFF('2022.8.25',NOW());

# 小需求：查询所有员工的入职天数，并根据入职天数进行倒序排序
SELECT `name`,entrydate as '入职时间',DATEDIFF(CURDATE(),entrydate) as '入职天数/天' FROM employee ORDER BY '入职天数/天' DESC;
```

### 流程函数

流程控制函数可以在SQL语句中实现条件的筛选，从而提高语句的效率。

常用函数：

| 函数  | 功能  |
| ------------ | ------------ |
| IF(value, t, f)  | 如果value为true，则返回t，否则返回f  |
| IFNULL(value1, value2)  | 如果value1不为空，返回value1，否则返回value2  |
| CASE WHEN [ val1 ] THEN [ res1 ] WHEN [ val2 ] THEN [ res2 ]... ELSE [ default ] END | 如果val1为true，返回res1，... 否则返回default默认值（==好用==） |
| CASE [ expr ] WHEN [ val1 ] THEN [ res1 ] WHEN [ val2 ] THEN [ res2 ]... ELSE [ default ] END | 如果expr的值等于val1，返回res1，... 否则返回default默认值  |

其中，第三个和第四个常用case end函数是差不多的，你择一用之即可！但我个人认为==第1种case end语法上非常好用！！！==

例子：

```mysql
-- IF(value, t, f)
SELECT IF(TRUE,'ok','no');
SELECT IF(FALSE,'ok','no');
-- IFNULL(value1, value2)
SELECT IFNULL('ok','no');# result: 'ok'
SELECT IFNULL('','no');	 # result: ''
SELECT IFNULL(NULL,'no');# result: 'no'
-- CASE WHEN [ val1 ] THEN [ res1 ] WHEN [ val2 ] THEN [ res2 ]... ELSE [ default ] END，可简记为：CASE WHEN THEN WHEN THEN ELSE END;
select
	name,
	(case when age > 30 then '中年' else '青年' END)
from employee;
select
	name,
	(case workaddress when '北京市' then '一线城市' when '上海市' then '一线城市' else '二线城市' END) as '工作地址'
from employee;

# 在员工表中，idcard 若为空，则只打印男性的信息，否则，打印女性的信息
SELECT * FROM employee WHERE IF(employee.idcard IS NULL,gender = '男',gender = '女');

# 在员工表中，idcard 若不为空，则只打印次条件下idcar='449'的员工信息
# 若idcar为空，且age不为空，则纸打印次条件下age=21的员工的信息
SELECT * FROM employee WHERE IFNULL(employee.idcard,employee.age) IN('449',21);
# 在员工表中判断每个人的年龄段
SELECT `name`,age, (CASE WHEN age <= 21 THEN '青年' ELSE '中年' END) as '年龄段' FROM employee;
SELECT * FROM employee WHERE DATEDIFF(entrydate,'2022-8-10')=0;
# 在员工表中判断每个人的新老类型
SELECT `name`,AGE,( CASE age WHEN 21 THEN '老员工' WHEN 10 THEN '新员工' ELSE '不老不新员工'END)as '员工类型' FROM employee;
# 在员工表中判断每个人的男女or不男不女类型
SELECT `name`,entrydate,( CASE WHEN DATEDIFF(entrydate,'2022-8-7')='0' THEN '老员工' WHEN DATEDIFF(entrydate,'2022-8-7')='3' THEN '新员工' ELSE '不老不新员工'END )as '员工类型' FROM employee;
SELECT `name`,gender,( CASE gender WHEN '女' THEN '女员工' WHEN '男' THEN '男员工' ELSE '不男不女员工'END)as '员工类型' FROM employee;
# 小需求：
/*
	统计班上各个学员的成绩，展示的规则如下：
	>= 85,展示优秀
	>= 60,展示及格
	否则，展示不及格
*/
CREATE TABLE score(
	id int COMMENT 'ID',
	name VARCHAR(20) COMMENT '姓名',
	math int COMMENT '数学',
	english int COMMENT '英语',
	chinese int COMMENT '语文'
)COMMENT '学生成绩表';
INSERT INTO score(id,name,math,english,chinese)
VALUES(1,'Tom',67,88,95),(2,'Rose',23,66,90),(3,'Jack',56,98,76);
# 需求实现：
SELECT 
id,
`name`,
(case when score.math >= 85 then'优秀' when score.math >= 60 then '及格' else '不及格'end) as'数学成绩',
(case when score.english >= 85 then'优秀' when score.english >= 60 then '及格' else '不及格'end) as'英语成绩',
(case when score.chinese >= 85 then'优秀' when score.english >= 60 then '及格' else '不及格'end) as'语文成绩'
FROM score;

```

##### 注意事项

- 一定不要忘记对于==CASE==流程语句要加==END==!!!

## 约束

概念：约束就是束缚和限制，是作用于表中字段上的规则。用来限制表中存储的数据。

目的：保证数据库中数据的==正确==、==有效==和==完整性==。

分类：

| 约束  | 描述  | 关键字  |
| ------------ | ------------ | ------------ |
| 非空约束  | 限制该字段的数据不能为null  | NOT NULL  |
| 唯一约束  | 保证该字段在整张表格中的所有数据都是唯一、不重复的（比如用户注册时的手机号，身份证号等数据） | UNIQUE  |
| ==主键约束== | 主键是一张表格中数据的==唯一标识==，要求非空且唯一（许多规范认为，我们设计一张表格时必须要有主键约束） | PRIMARY KEY  |
| 默认约束  | 保存数据时，如果未指定该字段的值，则采用默认值  | DEFAULT  |
| 检查约束（MySQL自8.0.1版本后才支持这个检查约束） | 保证字段值满足某一个 或 多个 条件 | CHECK  |
| 外键约束（一旦谈到外键，则至少要有两张表格） | 用来让两张图的数据之间建立连接，保证数据的一致性和完整性  | FOREIGN KEY  |

注意：约束是作用于==表中的字段==上的，so我们可以在创建表/修改表的时候添加约束。

### 常用约束

| 约束条件  | 关键字  |
| ------------ | ------------ |
| 主键  | PRIMARY KEY（==对于主键约束来说，其本来就是非空和唯一的了！！！==） |
| 自动增长  | AUTO_INCREMENT  |
| 不为空  | NOT NULL  |
| 唯一  | UNIQUE  |
| 逻辑条件  | CHECK  |
| 默认值  | DEFAULT  |

例子：

![2](C:\Users\11602\Desktop\MySQL学习\学习截图\2.JPG)

```mysql
-- 创建表
CREATE TABLE user(
	id int primary key auto_increment COMMENT '主键',
	name varchar(10) not null UNIQUE COMMENT '姓名',
	age int CHECK(age > 0 and age <= 120) COMMENT '年龄',
	status char(1) DEFAULT('1') COMMENT '状态',
	gender char(1) COMMENT '性别'
)comment '用户信息表';
-- 插入数据 测试以上约束关键字 是否起作用
INSERT into user (name,age,status,gender) VALUES('Tom1',19,'1','男'),('Tom2',25,'0','男');

INSERT into user (name,age,status,gender) VALUES('Tom3',29,'1','男');
INSERT into user (name,age,status,gender) VALUES('Tom3',29,'1','男');

INSERT into user (name,age,status,gender) VALUES('Tom5',10,'','男');
INSERT into user (name,age,status,gender) VALUES(NULL,12,'1','男');
INSERT into user (name,age,status,gender) VALUES('Tom6',80,'2','男');
INSERT into user (name,age,gender) VALUES('Tom7',89,'男');
```

### 外键约束

概念：外键用来让两张表的数据之间建立连接，从而保证数据的==一致性==和==完整性==。

①==具有==外键约束的表称之为 ==子表（从表）==

②外键约束==所关联==的这张表称之为 ==父表（主表）==

![3](C:\Users\11602\Desktop\MySQL学习\学习截图\3.JPG)

##### ==注意事项==

- 目前上述的两张表，在数据库层面，并未建立外键关联，so是无法保证数据的一致性和完整性的。（==人话==就是：当前的这两张表是没有任何物理外键关系的，当我删除了主表的id后，子表的dept_id不会有任何的影响！）
- 若当两张表有外键关联后，你要是==删除主表==中==外键对应的字段==的数据的话，MySQL管理工具就会报错！即你无法删除！这就保证了关联数据之间的一致性和完整性了！当然，你只是删除子表中外键对应的字段那当前是没事儿的！

添加==外键约束==关联的语法：

```mysql
CREATE TABLE 表名(
	字段名 字段类型,
	...
	[CONSTRAINT] [外键名称] FOREIGN KEY(外键字段名) REFERENCES 主表(主表列名)
);
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (子表中的外键字段名) REFERENCES 主表(主表列名);

-- 例子：其中，外键名称自拟！
alter table emp add constraint fk_emp_dept_id foreign key(dept_id) references dept(id);
```

删除外键：
`ALTER TABLE 表名 DROP FOREIGN KEY 外键名;`

例子：

```mysql
-- 创建部门表
create table dept(
	id int primary key auto_increment comment 'ID',
	name varchar(10) NOT NULL comment '部门名称' 
)comment '部门表';
INSERT INTO dept(id,name) VALUES(1,'研发部'),(2,'市场部'),(3,'财务部'),(4,'销售部'),(5,'总经办');
-- 创建员工表
CREATE table emp(
	id int primary key auto_increment comment 'ID',
	name varchar(50) NOT NULL COMMENT '姓名',
	age int comment '年龄',
	job varchar(20) COMMENT '职位',
	salary int COMMENT '薪资',
	entrydate date comment '入职时间',
	managerid int COMMENT '直属领导ID',
	dept_id int comment '部门ID'
)COMMENT '员工表';
-- 添加数据
INSERT INTO emp(id,name,age,job,salary,entrydate,managerid,dept_id)VALUES
(1,'金莲',66,'总裁',20000,'2000-01-01',null,5),
(2,'张无忌',20,'项目经理',12500,'2005-12-05',1,1),
(3,'逍遥',33,'开发',8400,'2000-11-03',2,1),
(4,'韦一笑',48,'开发',11000,'2002-02-05',2,1),
(5,'常遇春',43,'开发',10500,'2004-09-07',3,1),
(6,'小昭',19,'程序员鼓励师',6600,'2004-10-12',2,1);

-- 添加外键
ALTER table emp ADD CONSTRAINT fk_emp_dept_id FOREIGN key (dept_id) REFERENCES dept(id);
-- 删除外键
alter table emp drop FOREIGN key fk_emp_dept_id;
```



#### 删除/更新行为

| 行为  | 说明  |
| ------------ | ------------ |
| NO ACTION  | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则不允许删除/更新（与RESTRICT一致）  |
| RESTRICT  | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则不允许删除/更新（与NO ACTION一致）  |
| CASCADE  | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则也删除/更新外键在子表中的记录  |
| SET NULL  | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则设置子表中该外键值为null（要求该外键允许为null）  |
| SET DEFAULT  | 当父表有变更时，子表将外键设为一个默认值（==在当前MySQL的默认引擎Innodb中是不支持的==），==so这个关键字基本不用==！ |

更改 外键约束的 删除/更新行为 的语法：
`ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段) REFERENCES 主表名(主表字段名) ON UPDATE 行为 ON DELETE 行为;`

例子：

```mysql
-- 承接上面所创建的dept部门表与emp员工表
-- 添加外键约束 并 设置 删除/更新行为是CASCADE的
alter table emp add constraint fk_emp_dept_id foreign key(dept_id) references dept(id) on update cascade on delete cascade;
alter table emp drop foreign key fk_emp_dept_id;
-- 添加外键约束 并 设置 删除/更新行为是SET NULL的
alter table emp add constraint fk_emp_dept_id foreign key(dept_id) references dept(id)
on update set null on delete set null;
alter table emp drop foreign key fk_emp_dept_id;
```

##### ==注意事项==

- NO ACTION 和 RESTRICT 是外键约束的默认行为属性
- ON UPDATE：指名在 主表 更新数据记录时 怎么操作（行为）
- ON DELETE：指名在 主表 删除数据记录时 怎么操作（行为）

## 多表查询（较为抽象，需要看视频配合学习）

### 多表关系

实际项目开发时，在进行数据库表结构设计时，会根据业务需求及业务模块之间的关系，分析并设计表结构，由于业务之间相互关联，所以各个表结构之间也存在着各种联系，不论业务有多复杂，基本上关系就分为三种：

- 一对多（多对一）
- 多对多
- 一对一

#### ①一对多（多对一）

案例：部门与员工
关系：一个部门对应多个员工，一个员工对应一个部门
==实现==：在多数据记录的一方建立外键，指向少的一方的主键

![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/4.JPG)

#### ②多对多

案例：学生与课程
关系：一个学生可以选多门课程，一门课程也可以供多个学生选修
实现：建立第三张中间表，中间表至少包含两个外键，分别关联两方主键

![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/5.JPG)

例子：

```mysql
-- 多对多
# 创建学生表
create table student(
	id int auto_increment primary key comment '主键ID',
	name varchar(10) comment '姓名',
	no varchar(10) 	 comment '学号'
)comment '学生表';
insert into student values
(null,'戴倚丝','2000100101'),
(null,'谢逊','2000100102'),
(null,'殷天正','2000100103'),
(null,'韦一笑','2000100104');

# 创建课程表
create table course(
	id int auto_increment primary key comment '主键ID',
	name varchar(10) comment '课程名称'
)comment '课程表';
insert into course values(null,'Java'),(null,'PHP'),(null,'MySQL'),(null,'Hadoop');
# 学生-课程中间表
create table student_course(
	id int auto_increment primary key COMMENT '',
	studentid int not null comment '学生ID',
	courseid int not null comment '课程ID',
	constraint fk_studentid foreign key(studentid) references student(id),
	constraint fk_courseid foreign key(courseid) references course(id)
)comment '学生-课程中间表';

insert into student_course values(null,1,1),(null,1,2),(null,1,3),(null,2,2),(null,2,3),(null,3,4);
```

#### ③一对一

案例：用户与用户详情
关系：一对一关系，==多用于do单表拆分==，将一张表的基础字段放在一张表中，其他详情字段放在另一张表中，以提升操作效率
实现：在任意一方加入外键，关联另外一方的主键，并且设置外键为唯一的（UNIQUE）

![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/6.1.JPG)

![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/6.JPG)

例子：

```mysql
-- 一对于
# 创建 用户基本信息表
create table tb_user(
	id int auto_increment primary key comment '主键ID',
	name varchar(10) comment'姓名',
	age int comment '年龄',
	gender char(1) comment '1：男，2：女',
	phone char(11) comment '手机号'
)comment '用户基本信息表';

# 创建 用户教育信息表
create table tb_user_edu(
	id int auto_increment primary key comment '主键ID',
	degree varchar(20) comment '学历',
	major varchar(50) comment '专业',
	primaryschool varchar(50) comment '小学',
	middleschool varchar(50) comment '中学',
	university varchar(50) comment '大学',
	userid int unique comment '用户ID',# unique保证了一对一的关系
	constraint fk_userid foreign key (userid) REFERENCES
	tb_user(id)
)comment '用户教育信息表';

insert into tb_user values
(null,'黄渤',45,'1','18800001111'),
(null,'冰冰',35,'2','18800002222'),
(null,'肖会清',55,'1','18800001234'),
(null,'马云',50,'1','18800008888');
insert into tb_user_edu values
(null,'本科','舞蹈','静安区第一小学','静安区第一中学','北京舞蹈学院',1),
(null,'硕士','表演','朝阳区第一小学','朝阳区第一中学','北京电影学院',2),
(null,'本科','日语','杭州市第一小学','杭州市第一中学','杭州师范大学',3),
(null,'本科','应用数学','阳泉区第一小学','阳泉区第一中学','清华大学',4);
```

### 多表查询

概述：多表查询指的是从多张表格中查询数据

合并查询（笛卡尔积，会展示==所有组合==结果）：
`select * from emp, dept;`

> 笛卡尔积：两个集合A集合和B集合的所有组合情况（==在多表查询时，需要消除无效的笛卡尔积==因为我们根本不需要查询all情况，all情况会包含大量的无效且无用的情况）

消除无效笛卡尔积：
`select * from emp, dept where employee.dept = dept.id;`

例子：（emp和dept表格沿用之前上面学习中所创建的）

```mysql
SELECT * from emp,dept where emp.dept_id = dept.id;
# 因为要查询多张表格，因此直接在from 表1,表2,... 
```

![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/7.JPG)

### 内连接查询

内连接查询的是两张表==交集==的部分（如上图的==绿色==部分）

隐式内连接：(相比于显式，隐式非常好理解也容易记忆)
`SELECT 字段列表 FROM 表1, 表2 WHERE 查询条件1 and 查询条件2 ...;`

显式内连接：
`SELECT 字段列表 FROM 表1 [ INNER ] JOIN 表2 ON 连接条件 WHERE 查询条件...;`

==注意事项：==

- 显式性能比隐式高（显式的意思，就是关键字里面多了个JOIN字，表示是表1内连了表2的...）
- 对于显式内连接，INNER关键字是可省略的。
- 如果我们已经为==表格==起了==别名==的话，那么就==不能够==再使用表格的==原名==来进行sql操作了！

例子：

```mysql
-- 需求：查询员工姓名 以及所关联的部门的名称
-- 隐式内连接形式实现
SELECT e.`name`,d.`name` as '部门名称' from emp as e,dept as d where e.dept_id = d.id;
-- 显式内连接形式实现
SELECT e.`name`,d.`name` as '部门名称' from emp as e inner join dept as d on e.dept_id = d.id;
```

### 外连接查询

左外连接：
查询左表所有数据，以及两张表==交集==部分数据（如上图的==蓝色+绿色==部分）
`SELECT 字段列表 FROM 表1 LEFT [ OUTER ] JOIN 表2 ON 条件 ...;`
相当于查询表1的所有数据，包含表1和表2交集部分数据

右外连接：
查询右表所有数据，以及两张表==交集==部分数据（如上图的==红色+绿色==部分）
`SELECT 字段列表 FROM 表1 RIGHT [ OUTER ] JOIN 表2 ON 条件 ...;`

==注意事项：==

- 对于外连接，OUTER关键字也是可省略的。
- 左外连接，可理解为主要展示的是Left左表+左右表交叉的内容
- 右外连接，可理解为主要展示的是Right右表+左右表交叉的内容
- 从上面的注意事项可看出，左右外连接主要的区别就是看你主要想展示左表还是右表了，左表就把关键字改为left，右表就把关键字改为right即可！其他按照sql语句的基本语法一一对应着写即可了！
- 总结：==左右外连接都是可以相互转换的，因此常用其中一个即可！==重要的是要实现你想要的需求而已！

例子：

```mysql
-- 需求：查询emp表格中的所有数据，和对应的部门信息
-- 左外连接
select e.*, d.name as '部门名称'from employee as e left outer join dept as d on e.dept = d.id;
select d.name as '部门名称', e.* from dept d left outer join emp e on e.dept = d.id;  -- 这条语句与下面的语句效果一样
-- 右外连接
select d.name as '部门名称', e.* from employee as e right outer join dept as d on e.dept = d.id;
```

注意：左外连接可以查询到没有dept的employee，右外连接可以查询到没有employee的dept

### 自连接查询

当前表与自身的连接查询（我自己连接join自己来查询数据信息），==自连接==必须==使用表别名==

语法：
`SELECT 字段列表 FROM 表A 别名A JOIN 表A 别名B ON 条件 ...;`

对于，自连接查询，既可以是内连接查询，也可以是外连接查询

例子：

```mysql
-- 需求1：查询员工名字信息 及 其所属领导的名字
SELECT ea.`name`,eb.`name`as '领导名字' from emp as ea,emp as eb WHERE ea.managerid = eb.id;
-- 需求2：查询所有员工名字信息 及 其所属领导(没有领导也要查询出来)的名字
-- 因为要完全包含员工的数据，那么就应该使用外连接方式（因左右外连接都可相互转化，此处随便用一种即可）
select ea.`name`,eb.`name` as '领导名字' from emp as ea left join emp as eb on ea.managerid = eb.id;
```

注意：依然要把自连接查询中当前表格看成是2个一模一样的表格，只不过是要把不同的字段关联不同的字段以便于查询而已！

### 联合查询 union, union all

对于union查询，就是把多次查询的结果合并起来，形成一个新的查询结果集。

语法：

```mysql
SELECT 字段列表 FROM 表A ...
UNION [ALL]
SELECT 字段列表 FROM 表B ...;
```

#### 注意事项

- UNION ALL 会有重复结果(因为是直接将结果进行合并，不考虑重复项的数据)，而UNION 不会

- 联合查询比使用or效率高，不会使索引失效

- 一般推荐使用UNION，而不加ALL关键字！！！这样就会自动合并+去重了！

- ==要十分注意的是！在第一次SELECT后的语句中不需要加分号;，在最后一次SELECT语句后才加;号！==

- 对于联合查询的，多张表，的列数，必须要保持一致，字段类型也需要保持一致！

  ![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/12.JPG)

例子需求：既将 薪资低于9000的员工 又将 年龄大于40岁 的员工全部查询出来
注意：这是满足2个条件==其一==即可的！

```mysql
-- 错误示范1：使用单表查询方式
SELECT e.`name`as'员工名字',e.salary as'薪资',e.age '年龄' from emp as e WHERE e.salary < 9000 && e.age > 40;
# 这个是要满足2个条件同时成立的单表查询，error！
```

![11](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/11.JPG)

```mysql
-- 错误示范2：在查询语句的中途加分号;
SELECT e.`name`as'员工名字',e.salary as'薪资',e.age '年龄' from emp as e WHERE e.salary < 9000; -- 就是这里的分号导致联合语句失效！！！是不是非常的隐蔽呢？？？我差点忽略了这个bug！！！
union
SELECT e.`name`as'员工名字',e.salary as'薪资',e.age '年龄' from emp as e WHERE e.age > 40;
# 这个是在查询语句的中途加分号;，error！
```

![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/10.JPG)

```mysql
-- 正确示范1：使用多表查询的联合查询方式！（组合起来）
SELECT e.`name`as'员工名字',e.salary as'薪资',e.age '年龄' from emp as e WHERE e.salary < 9000
union all
SELECT e.`name`as'员工名字',e.salary as'薪资',e.age '年龄' from emp as e WHERE e.age > 40;
# 这个是满足2个条件其一成立即可的多表联合查询，right！
```

![8](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/8.JPG)

```mysql
# 正确示范2：组合+去重（一起来）
SELECT e.`name`as'员工名字',e.salary as'薪资',e.age '年龄' from emp as e WHERE e.salary < 9000
union
SELECT e.`name`as'员工名字',e.salary as'薪资',e.age '年龄' from emp as e WHERE e.age > 40;
```

![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/9.JPG)

### 子查询(嵌套查询)

在SQL语句中==嵌套SELECT==语句，称为==嵌套查询==，又称==子查询==。
`SELECT * FROM t1 WHERE column1 = ( SELECT column1 FROM t2);`

**子查询的位置即可以出现在WHERE后，SELECT后，也可以出现在FROM后！**

**子查询内部的语句( SELECT column1 FROM t2)就是子查询！**

**子查询外部的语句可以是 INSERT / UPDATE / DELETE / SELECT 的任何一个**

根据子查询结果可以分为：

- 标量子查询（子查询的结果为单个值，即一行一列的数据）
- 列子查询（子查询的结果为只有一列的数据）
- 行子查询（子查询的结果为只有一行的数据）
- 表子查询（子查询的结果为多行多列的数据）

根据子查询位置可分为：

- WHERE 之后（出现的子查询）
- FROM 之后（出现的子查询）
- SELECT 之后（出现的子查询）

#### 标量子查询

子查询返回的结果是单个值（数字、字符串、日期等），是最简单的形式。
常用操作符：= <> > >= < <=

例子：

```mysql
-- 需求1：查询属于研发部所有员工
-- 第一步：先查询研发部的所有ID
SELECT d.id FROM dept as d WHERE d.`name` = '研发部';
-- 第二部：后根据研发部的ID来 查询员工信息
SELECT * FROM emp as e WHERE e.dept_id =  (SELECT d.id FROM dept as d WHERE d.`name` = '研发部');

-- 需求2：查询在小昭之后入职的员工的信息
-- 第一步：先查询小昭的入职日期信息
SELECT e.entrydate FROM emp as e WHERE e.`name` = '小昭';
-- 第二部：后根据指定的入职日期信息来 查询员工信息
SELECT * FROM emp WHERE entrydate > (SELECT e.entrydate FROM emp as e WHERE e.`name` = '小昭');
```

#### 列子查询

返回的结果是只有一列（可以是多行）。

常用操作符：

| 操作符  | 描述  |
| ------------ | ------------ |
| IN  | 在指定的集合范围内，多选一  |
| NOT IN  | 不在指定的集合范围内  |
| ANY  | 在子查询返回列表中，有==任意其中一个满足即可== |
| SOME  | 与ANY等同，使用SOME的地方都可以使用ANY  |
| ALL  | 子查询返回列表的==所有值都必须满足== |

例子：

```mysql
-- 需求1：查询“研发部” 和 “财务部”的所有员工信息 
-- 第一步：先找到研发部和财务部的部门ID
(SELECT d.id from dept as d WHERE d.`name` = '研发部' OR d.`name` = '财务部');
-- 第二步：根据部门ID查询员工的信息
SELECT * FROM emp as e WHERE e.dept_id IN (SELECT d.id from dept as d WHERE d.`name` = '研发部' OR d.`name` = '财务部');

-- 需求2：查询比“研发部” 所有人工资都高的员工信息
-- WAY1:
-- 第一步：先找到研发部的所有人的工资
SELECT salary from emp WHERE dept_id = (SELECT id from dept WHERE `name` = '研发部');
-- 第二步：根据上面的信息，查询比研发部所有人工资都高的员工信息
SELECT * FROM emp WHERE salary > ALL(SELECT salary from emp WHERE dept_id = (SELECT id from dept WHERE `name` = '研发部'));
-- WAY2:
SELECT * from emp WHERE salary > (SELECT MAX(salary) from emp WHERE dept_id = (SELECT id from dept WHERE `name` = '研发部'));

-- 需求3：查询比“研发部” 中任意一人工资都高的员工信息
-- WAY1:
-- 第一步：先找到研发部的所有人的工资
SELECT salary from emp WHERE dept_id = (SELECT id from dept WHERE `name` = '研发部');
-- 第二步：根据上面的信息，查询比研发部任意一人工资高的员工信息
SELECT * from emp WHERE salary > ANY(SELECT salary from emp WHERE dept_id = (SELECT id from dept WHERE `name` = '研发部'));
-- WAY2:
SELECT * from emp WHERE salary > (SELECT MIN(salary) from emp WHERE dept_id = (SELECT id from dept WHERE `name` = '研发部'));
```

#### 行子查询

返回的结果是只有一行（可以是多列）。
常用操作符：=, <>(!=), IN, NOT IN

例子：

```mysql
-- 需求：查询与“杨晓君”的薪资及直属领导相同的员工信息
-- 第一步：查询与“杨晓君”的薪资及直属领导的信息
SELECT salary,managerid from emp WHERE `name` = '杨晓君';
-- 第二步：按照上述信息查询与其相同信息的员工的信息
SELECT * FROM emp WHERE (salary,managerid) =  (SELECT salary,managerid from emp WHERE `name` = '杨晓君');
```

#### 表子查询

返回的结果是多行多列（就类似于一张表格一样）。
常用操作符：IN

注意：表子查询常用语FROM关键字后，用于返回一个临时的表格以供需求而继续操作。

例子：

```mysql
-- 需求1：查询与“杨晓君”与“灭绝”的职位和薪资相同的员工信息
-- 第一步：查询与“杨晓君”与“灭绝”的职位和薪资
SELECT job,salary from emp WHERE `name` = '杨晓君' or `name` = '灭绝';
-- 第二步：查询与“杨晓君”与“灭绝”的职位和薪资相同的员工信息
SELECT * from emp WHERE (job,salary) IN (SELECT job,salary from emp WHERE `name` = '杨晓君' or `name` = '灭绝');

-- 需求2：查询入职日期是“2006-01-01”之后的员工信息，及其部门信息
-- 第一步：查询入职日期是“2006-01-01”之后的员工信息
SELECT * from emp WHERE entrydate > '2006-01-01';
-- 第二步：根据如上信息，来查询其部门信息
SELECT e.*, d.* FROM (SELECT * from emp WHERE entrydate > '2006-01-01')as e left outer join dept as d on d.id = e.dept_id;
```

#### 多表查询案例：（对前面几种多表查询方式进行加强和巩固学习！）

```mysql

```





## ==查询==表格数据记录的==万能模板（三部曲）==：

```
不论3721，先给老子列出以下三部曲：
-- 1-需求（是什么？）：...
-- 2-涉及的表（有哪些？有哪几个？）：...
-- 3-连接条件（是什么？注意：N张表就必有N-1个连接条件，这样才能够消除笛卡尔积，然后才能筛选出需要的数据记录！）：
...
例子：
-- 需求12：查询所有学生的选课情况，并展示出学生的名字，学号，课程名称(学生和课程的关系就是多对多的关系)。
-- 涉及的表：student，course，student_course
-- 连接条件（3张表就有2个连接条件，N张表就有N-1个条件，这样才能够消除笛卡尔积，然后才能筛选出需要的数据记录！）：
```

==注意：==

①有N张表就必有N-1个连接条件，这样才能够消除笛卡尔积，然后才能筛选出需要的数据记录！）

②有N张表就必有N-1个连接条件，这样才能够消除笛卡尔积，然后才能筛选出需要的数据记录！）

③有N张表就必有N-1个连接条件，这样才能够消除笛卡尔积，然后才能筛选出需要的数据记录！）

④只要是能够满足需求的SQL查询语句，就都是好语句！满足需求CRUD即可！so==很多时候同一需求解法不一==！

## 事务

### 简介：

事务是一组操作的集合，事务会把所  有操作作为一个整体一起向系统提交或撤销操作请求，即这些操作==要么同时成功==，==要么同时失败（失败后要手动回滚数据）==,以保证数据的完整性和一致性！！！（事务的概念其实是有点儿类似于互斥锁的概念的，防止共享资源被同时读写引起异常！）

![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/13.JPG)

#### 注意事项：

默认情况下MySQL的事务是==自动提交==的，也就是说，当执行一条SQL-DML语句，MySQL会立即隐式地提交事务。（==一条SQL语句就是一个事务==）

因此，当我们在写SQL语句时，若可能遇到会抛出异常的事件，就必须要我们自己手动==开启事务==并==提交事务==，并在抛出异常后手动==回滚事务==,以保证数据的==完整性==和==一致性==！！！！

### 事务的基本操作（==控制事务==的基本操作）：

```mysql
-- 1. 查询张三账户余额
select * from account where name = '张三';
-- 2. 将张三账户余额-1000
update account set money = money - 1000 where name = '张三';
-- 此语句出错后张三钱减少但是李四钱没有增加
模拟sql语句错误
-- 3. 将李四账户余额+1000
update account set money = money + 1000 where name = '李四';

-- 查看事务提交方式
SELECT @@AUTOCOMMIT;
-- 设置事务提交方式，1为自动提交，0为手动提交，该设置 只对 当前会话 有效
SET @@AUTOCOMMIT = 0;# 表示设置当前会话的事务提交方式为手动提交！
-- 提交事务(的指令)
COMMIT;
-- 回滚事务(的指令)
ROLLBACK;

-- 设置手动提交后上面代码改为：
select * from account where name = '张三';
update account set money = money - 1000 where name = '张三';
update account set money = money + 1000 where name = '李四';
commit;
```

##### 操作方式二：(我个人认为这是比较好理解的,至少比上面的操作方式一好理解多了！)

开启事务：
`START TRANSACTION 或 BEGIN TRANSACTION;`
提交事务：
`COMMIT;`
回滚事务：
`ROLLBACK;`

操作实例：

```mysql
start transaction;
select * from account where name = '张三';
update account set money = money - 1000 where name = '张三';
update account set money = money + 1000 where name = '李四';
commit;
# 在start transaction; 和 commit;语句之间的SQL语句，要么直接执行完成，要么直接执行失败！
start transaction;
select * from account where name = '张三';
update account set money = money - 1000 where name = '张三';
update account set money = money + 1000 where name = '李四';
异常抛出。。。
rollback;
```

#### 注意事项：

- COMMIT和ROLLBACK关键字只能二者选其一！！！当事务都正常执行时，选COMMIT,否则，就选ROLLBACK即可了！！！

### 事务的四大特性ACID（==面试比较爱考==）

- 原子性(Atomicity)：事务是不可分割的最小操作但愿，要么全部成功，要么全部失败
- 一致性(Consistency)：事务完成时，必须使所有数据都保持一致状态
- 隔离性(Isolation)：数据库系统提供的隔离机制，保证事务在不受外部并发操作影响的独立环境下运行
- 持久性(Durability)：事务一旦提交commit或回滚rollback，它对数据库中的数据的改变就是永久的(数据库中的数据时存储在磁盘上面的，你提交or回滚的话那么就是持久地修改了磁盘上面的数据了)

### 并发事务(引发的)问题

所谓并发事务所引发的问题：指的是当==多个事务==在==同时操作（并发操作）==同一个数据库 或者 同一张表格的时候所引发的一些脏读、不可重复读、幻读等的问题。

常见的并发事务引发的问题主要有以下三种：

| 问题  | 描述  |
| ------------ | ------------ |
| 脏读  | 一个事务读到另一个事务修改/更新了的但还没提交的数据！ |
| 不可重复读  | 一个事务先后读取同一条记录，但多次读取后发现读取到的数据有不同！ |
| 幻读  | 一个事务按照条件查询数据时，没有对应的数据行，但是再插入数据时，又发现这行数据已经存在（我查询的时候明明没有该数据记录，但是我想插入该对应数据行的数据记录时又显示是重复了的！！！这就叫做是幻读！） |

> 这三个问题的详细演示：https://www.bilibili.com/video/BV1Kr4y1i7ru?p=55cd 

![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/14.JPG)

![15](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/15.JPG)



![16](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/16.JPG)



![17](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/17.JPG)

### 事务隔离级别：就是用来==deal事务的并发执行问题==的

| 隔离级别  | 脏读  | 不可重复读  | 幻读  |
| ------------ | ------------ | ------------ | ------------ |
| Read uncommitted（读未提交） | √  | √  | √  |
| Read committed（读已提交，是Oracle的默认隔离级别） | ×  | √  | √  |
| Repeatable Read（是MySQL的默认隔离级别，可重复读） | ×  | ×  | √  |
| Serializable（可串行化） | ×  | ×  | ×  |

- √：表示在当前隔离级别下该问题==会出现==
- Serializable 性能最低（但是任何事务并发执行问题都可以deal）；Read uncommitted 性能最高，数据安全性最差

查看事务隔离级别：
`SELECT @@TRANSACTION_ISOLATION;`
设置事务隔离级别：
`SET [ SESSION | GLOBAL ] TRANSACTION ISOLATION LEVEL {READ UNCOMMITTED | READ COMMITTED | REPEATABLE READ | SERIALIZABLE };`

#### 注意事项：

①==SESSION==是会话级别，表示==只针对当前会话窗口有效==，==GLOBAL== 表示==针对所有会话窗口都有效==

②SELECT @@中的两个==@==符号就表示的是查看==当前系统==的==变量==信息。

③Serializable这种隔离级别使得事务与事务之间串行执行！！！只有前面一个事务A执行完毕后，后面的事务B才能继续执行！否则的话事务B以及后续事务都只能够阻塞等待前面的事务执行完成！！！

④事务隔离级别越高，则数据越安全，但是性能越低。

事务隔离级别越低，则数据越不安全，但是性能越高。

我们在选择事务的隔离级别时，一般都需要考虑数据的安全性与系统的性能。所以我们在使用MYSQL时一般都只是使用默认的隔离级别（即是：Repeatable read）

# 进阶篇（原理）

## 存储引擎

MySQL体系结构：

![结构图](https://dhc.pythonanywhere.com/media/editor/MySQL体系结构_20220315034329549927.png "结构图")
![层级描述](https://dhc.pythonanywhere.com/media/editor/MySQL体系结构层级含义_20220315034359342837.png "层级描述")

存储引擎就是存储数据、建立索引、更新/查询数据等技术的实现方式。存储引擎是基于表而不是基于库的，所以存储引擎也可以被称为表引擎。
默认存储引擎是InnoDB。

相关操作：

```mysql
-- 查询建表语句
show create table account;
-- 建表时指定存储引擎
CREATE TABLE 表名(
	...
) ENGINE=INNODB;
-- 查看当前数据库支持的存储引擎
show engines;
```

### InnoDB

InnoDB 是一种兼顾高可靠性和高性能的通用存储引擎，在 MySQL 5.5 之后，InnoDB 是默认的 MySQL 引擎。

特点：

- DML 操作遵循 ACID 模型，支持**事务**
- **行级锁**，提高并发访问性能
- 支持**外键**约束，保证数据的完整性和正确性

文件：

- xxx.ibd: xxx代表表名，InnoDB 引擎的每张表都会对应这样一个表空间文件，存储该表的表结构（frm、sdi）、数据和索引。

参数：innodb_file_per_table，决定多张表共享一个表空间还是每张表对应一个表空间

知识点：

查看 Mysql 变量：
`show variables like 'innodb_file_per_table';`

从idb文件提取表结构数据：
（在cmd运行）
`ibd2sdi xxx.ibd`

InnoDB 逻辑存储结构：
![InnoDB逻辑存储结构](https://dhc.pythonanywhere.com/media/editor/逻辑存储结构_20220316030616590001.png "InnoDB逻辑存储结构")

### MyISAM

MyISAM 是 MySQL 早期的默认存储引擎。

特点：

- 不支持事务，不支持外键
- 支持表锁，不支持行锁
- 访问速度快

文件：

- xxx.sdi: 存储表结构信息
- xxx.MYD: 存储数据
- xxx.MYI: 存储索引

### Memory

Memory 引擎的表数据是存储在内存中的，受硬件问题、断电问题的影响，只能将这些表作为临时表或缓存使用。

特点：

- 存放在内存中，速度快
- hash索引（默认）

文件：

- xxx.sdi: 存储表结构信息

### 存储引擎特点

| 特点  | InnoDB  | MyISAM  | Memory  |
| ------------ | ------------ | ------------ | ------------ |
| 存储限制  | 64TB  | 有  | 有  |
| 事务安全  | 支持  | -  | -  |
| 锁机制  | 行锁  | 表锁  | 表锁  |
| B+tree索引  | 支持  | 支持  | 支持  |
| Hash索引  | -  | -  | 支持  |
| 全文索引  | 支持（5.6版本之后）  | 支持  | -  |
| 空间使用  | 高  | 低  | N/A  |
| 内存使用  | 高  | 低  | 中等  |
| 批量插入速度  | 低  | 高  | 高  |
| 支持外键  | 支持  | -  | -  |

### 存储引擎的选择

在选择存储引擎时，应该根据应用系统的特点选择合适的存储引擎。对于复杂的应用系统，还可以根据实际情况选择多种存储引擎进行组合。

- InnoDB: 如果应用对事物的完整性有比较高的要求，在并发条件下要求数据的一致性，数据操作除了插入和查询之外，还包含很多的更新、删除操作，则 InnoDB 是比较合适的选择
- MyISAM: 如果应用是以读操作和插入操作为主，只有很少的更新和删除操作，并且对事务的完整性、并发性要求不高，那这个存储引擎是非常合适的。
- Memory: 将所有数据保存在内存中，访问速度快，通常用于临时表及缓存。Memory 的缺陷是对表的大小有限制，太大的表无法缓存在内存中，而且无法保障数据的安全性

电商中的足迹和评论适合使用 MyISAM 引擎，缓存适合使用 Memory 引擎。

## 性能分析

### 查看执行频次

查看当前数据库的 INSERT, UPDATE, DELETE, SELECT 访问频次：
`SHOW GLOBAL STATUS LIKE 'Com_______';` 或者 `SHOW SESSION STATUS LIKE 'Com_______';`
例：`show global status like 'Com_______'`

### 慢查询日志

慢查询日志记录了所有执行时间超过指定参数（long_query_time，单位：秒，默认10秒）的所有SQL语句的日志。
MySQL的慢查询日志默认没有开启，需要在MySQL的配置文件（/etc/my.cnf）中配置如下信息：
	# 开启慢查询日志开关
	slow_query_log=1
	# 设置慢查询日志的时间为2秒，SQL语句执行时间超过2秒，就会视为慢查询，记录慢查询日志
	long_query_time=2
更改后记得重启MySQL服务，日志文件位置：/var/lib/mysql/localhost-slow.log

查看慢查询日志开关状态：
`show variables like 'slow_query_log';`

### profile

show profile 能在做SQL优化时帮我们了解时间都耗费在哪里。通过 have_profiling 参数，能看到当前 MySQL 是否支持 profile 操作：
`SELECT @@have_profiling;`
profiling 默认关闭，可以通过set语句在session/global级别开启 profiling：
`SET profiling = 1;`
查看所有语句的耗时：
`show profiles;`
查看指定query_id的SQL语句各个阶段的耗时：
`show profile for query query_id;`
查看指定query_id的SQL语句CPU的使用情况
`show profile cpu for query query_id;`

### explain

EXPLAIN 或者 DESC 命令获取 MySQL 如何执行 SELECT 语句的信息，包括在 SELECT 语句执行过程中表如何连接和连接的顺序。
语法：
	# 直接在select语句之前加上关键字 explain / desc
	EXPLAIN SELECT 字段列表 FROM 表名 HWERE 条件;

EXPLAIN 各字段含义：

- id：select 查询的序列号，表示查询中执行 select 子句或者操作表的顺序（id相同，执行顺序从上到下；id不同，值越大越先执行）
- select_type：表示 SELECT 的类型，常见取值有 SIMPLE（简单表，即不适用表连接或者子查询）、PRIMARY（主查询，即外层的查询）、UNION（UNION中的第二个或者后面的查询语句）、SUBQUERY（SELECT/WHERE之后包含了子查询）等
- type：表示连接类型，性能由好到差的连接类型为 NULL、system、const、eq_ref、ref、range、index、all
- possible_key：可能应用在这张表上的索引，一个或多个
- Key：实际使用的索引，如果为 NULL，则没有使用索引
- Key_len：表示索引中使用的字节数，该值为索引字段最大可能长度，并非实际使用长度，在不损失精确性的前提下，长度越短越好
- rows：MySQL认为必须要执行的行数，在InnoDB引擎的表中，是一个估计值，可能并不总是准确的
- filtered：表示返回结果的行数占需读取行数的百分比，filtered的值越大越好

## 索引

索引是帮助 MySQL **高效获取数据**的**数据结构（有序）**。在数据之外，数据库系统还维护着满足特定查找算法的数据结构，这些数据结构以某种方式引用（指向）数据，这样就可以在这些数据结构上实现高级查询算法，这种数据结构就是索引。

优缺点：

优点：

- 提高数据检索效率，降低数据库的IO成本
- 通过索引列对数据进行排序，降低数据排序的成本，降低CPU的消耗

缺点：

- 索引列也是要占用空间的
- 索引大大提高了查询效率，但降低了更新的速度，比如 INSERT、UPDATE、DELETE

### 索引结构

| 索引结构  | 描述  |
| ------------ | ------------ |
| B+Tree  | 最常见的索引类型，大部分引擎都支持B+树索引  |
| Hash  | 底层数据结构是用哈希表实现，只有精确匹配索引列的查询才有效，不支持范围查询  |
| R-Tree(空间索引)  | 空间索引是 MyISAM 引擎的一个特殊索引类型，主要用于地理空间数据类型，通常使用较少  |
| Full-Text(全文索引)  | 是一种通过建立倒排索引，快速匹配文档的方式，类似于 Lucene, Solr, ES  |

| 索引  | InnoDB  | MyISAM  | Memory  |
| ------------ | ------------ | ------------ | ------------ |
| B+Tree索引  | 支持  | 支持  | 支持  |
| Hash索引  | 不支持  | 不支持  | 支持  |
| R-Tree索引  | 不支持  | 支持  | 不支持  |
| Full-text  | 5.6版本后支持  | 支持  | 不支持  |

#### B-Tree

![二叉树](https://dhc.pythonanywhere.com/media/editor/二叉树_20220316153214227108.png "二叉树")

二叉树的缺点可以用红黑树来解决：
![红黑树](https://dhc.pythonanywhere.com/media/editor/红黑树_20220316163142686602.png "红黑树")
红黑树也存在大数据量情况下，层级较深，检索速度慢的问题。

为了解决上述问题，可以使用 B-Tree 结构。
B-Tree (多路平衡查找树) 以一棵最大度数（max-degree，指一个节点的子节点个数）为5（5阶）的 b-tree 为例（每个节点最多存储4个key，5个指针）

![B-Tree结构](https://dhc.pythonanywhere.com/media/editor/B-Tree结构_20220316163813441163.png "B-Tree结构")

> B-Tree 的数据插入过程动画参照：https://www.bilibili.com/video/BV1Kr4y1i7ru?p=68
演示地址：https://www.cs.usfca.edu/~galles/visualization/BTree.html

#### B+Tree

结构图：

![B+Tree结构图](https://dhc.pythonanywhere.com/media/editor/B+Tree结构图_20220316170700591277.png "B+Tree结构图")

> 演示地址：https://www.cs.usfca.edu/~galles/visualization/BPlusTree.html

与 B-Tree 的区别：

- 所有的数据都会出现在叶子节点
- 叶子节点形成一个单向链表

MySQL 索引数据结构对经典的 B+Tree 进行了优化。在原 B+Tree 的基础上，增加一个指向相邻叶子节点的链表指针，就形成了带有顺序指针的 B+Tree，提高区间访问的性能。

![MySQL B+Tree 结构图](https://dhc.pythonanywhere.com/media/editor/结构图_20220316171730865611.png "MySQL B+Tree 结构图")

#### Hash

哈希索引就是采用一定的hash算法，将键值换算成新的hash值，映射到对应的槽位上，然后存储在hash表中。
如果两个（或多个）键值，映射到一个相同的槽位上，他们就产生了hash冲突（也称为hash碰撞），可以通过链表来解决。

![Hash索引原理图](https://dhc.pythonanywhere.com/media/editor/Hash索引原理图_20220317143226150679.png "Hash索引原理图")

特点：

- Hash索引只能用于对等比较（=、in），不支持范围查询（betwwn、>、<、...）
- 无法利用索引完成排序操作
- 查询效率高，通常只需要一次检索就可以了，效率通常要高于 B+Tree 索引

存储引擎支持：

- Memory
- InnoDB: 具有自适应hash功能，hash索引是存储引擎根据 B+Tree 索引在指定条件下自动构建的

#### 面试题

1. 为什么 InnoDB 存储引擎选择使用 B+Tree 索引结构？

- 相对于二叉树，层级更少，搜索效率高
- 对于 B-Tree，无论是叶子节点还是非叶子节点，都会保存数据，这样导致一页中存储的键值减少，指针也跟着减少，要同样保存大量数据，只能增加树的高度，导致性能降低
- 相对于 Hash 索引，B+Tree 支持范围匹配及排序操作

### 索引分类

| 分类  | 含义  | 特点  | 关键字  |
| ------------ | ------------ | ------------ | ------------ |
| 主键索引  | 针对于表中主键创建的索引  | 默认自动创建，只能有一个  | PRIMARY  |
| 唯一索引  | 避免同一个表中某数据列中的值重复  | 可以有多个  | UNIQUE  |
| 常规索引  | 快速定位特定数据  | 可以有多个  |   |
| 全文索引  | 全文索引查找的是文本中的关键词，而不是比较索引中的值  | 可以有多个  | FULLTEXT  |

在 InnoDB 存储引擎中，根据索引的存储形式，又可以分为以下两种：

| 分类  | 含义  | 特点  |
| ------------ | ------------ | ------------ |
| 聚集索引(Clustered Index)  | 将数据存储与索引放一块，索引结构的叶子节点保存了行数据  | 必须有，而且只有一个  |
| 二级索引(Secondary Index)  | 将数据与索引分开存储，索引结构的叶子节点关联的是对应的主键  | 可以存在多个  |

演示图：

![大致原理](https://dhc.pythonanywhere.com/media/editor/原理图_20220318194454880073.png "大致原理")
![演示图](https://dhc.pythonanywhere.com/media/editor/演示图_20220319215403721066.png "演示图")

聚集索引选取规则：

- 如果存在主键，主键索引就是聚集索引
- 如果不存在主键，将使用第一个唯一(UNIQUE)索引作为聚集索引
- 如果表没有主键或没有合适的唯一索引，则 InnoDB 会自动生成一个 rowid 作为隐藏的聚集索引

#### 思考题

1\. 以下 SQL 语句，哪个执行效率高？为什么？

```mysql
select * from user where id = 10;
select * from user where name = 'Arm';
-- 备注：id为主键，name字段创建的有索引
```

答：第一条语句，因为第二条需要回表查询，相当于两个步骤。

2\. InnoDB 主键索引的 B+Tree 高度为多少？

答：假设一行数据大小为1k，一页中可以存储16行这样的数据。InnoDB 的指针占用6个字节的空间，主键假设为bigint，占用字节数为8.
可得公式：`n * 8 + (n + 1) * 6 = 16 * 1024`，其中 8 表示 bigint 占用的字节数，n 表示当前节点存储的key的数量，(n + 1) 表示指针数量（比key多一个）。算出n约为1170。

如果树的高度为2，那么他能存储的数据量大概为：`1171 * 16 = 18736`；
如果树的高度为3，那么他能存储的数据量大概为：`1171 * 1171 * 16 = 21939856`。

另外，如果有成千上万的数据，那么就要考虑分表，涉及运维篇知识。

### 语法

创建索引：
`CREATE [ UNIQUE | FULLTEXT ] INDEX index_name ON table_name (index_col_name, ...);`
如果不加 CREATE 后面不加索引类型参数，则创建的是常规索引

查看索引：
`SHOW INDEX FROM table_name;`

删除索引：
`DROP INDEX index_name ON table_name;`

案例：

```mysql
-- name字段为姓名字段，该字段的值可能会重复，为该字段创建索引
create index idx_user_name on tb_user(name);
-- phone手机号字段的值非空，且唯一，为该字段创建唯一索引
create unique index idx_user_phone on tb_user (phone);
-- 为profession, age, status创建联合索引
create index idx_user_pro_age_stat on tb_user(profession, age, status);
-- 为email建立合适的索引来提升查询效率
create index idx_user_email on tb_user(email);

-- 删除索引
drop index idx_user_email on tb_user;
```

### 使用规则

#### 最左前缀法则

如果索引关联了多列（联合索引），要遵守最左前缀法则，最左前缀法则指的是查询从索引的最左列开始，并且不跳过索引中的列。
如果跳跃某一列，索引将部分失效（后面的字段索引失效）。

联合索引中，出现范围查询（<, >），范围查询右侧的列索引失效。可以用>=或者<=来规避索引失效问题。

#### 索引失效情况

1. 在索引列上进行运算操作，索引将失效。如：`explain select * from tb_user where substring(phone, 10, 2) = '15';`
2. 字符串类型字段使用时，不加引号，索引将失效。如：`explain select * from tb_user where phone = 17799990015;`，此处phone的值没有加引号
3. 模糊查询中，如果仅仅是尾部模糊匹配，索引不会是失效；如果是头部模糊匹配，索引失效。如：`explain select * from tb_user where profession like '%工程';`，前后都有 % 也会失效。
4. 用 or 分割开的条件，如果 or 其中一个条件的列没有索引，那么涉及的索引都不会被用到。
5. 如果 MySQL 评估使用索引比全表更慢，则不使用索引。

#### SQL 提示

是优化数据库的一个重要手段，简单来说，就是在SQL语句中加入一些人为的提示来达到优化操作的目的。

例如，使用索引：
`explain select * from tb_user use index(idx_user_pro) where profession="软件工程";`
不使用哪个索引：
`explain select * from tb_user ignore index(idx_user_pro) where profession="软件工程";`
必须使用哪个索引：
`explain select * from tb_user force index(idx_user_pro) where profession="软件工程";`

use 是建议，实际使用哪个索引 MySQL 还会自己权衡运行速度去更改，force就是无论如何都强制使用该索引。

#### 覆盖索引&回表查询

尽量使用覆盖索引（查询使用了索引，并且需要返回的列，在该索引中已经全部能找到），减少 select *。

explain 中 extra 字段含义：
`using index condition`：查找使用了索引，但是需要回表查询数据
`using where; using index;`：查找使用了索引，但是需要的数据都在索引列中能找到，所以不需要回表查询

如果在聚集索引中直接能找到对应的行，则直接返回行数据，只需要一次查询，哪怕是select \*；如果在辅助索引中找聚集索引，如`select id, name from xxx where name='xxx';`，也只需要通过辅助索引(name)查找到对应的id，返回name和name索引对应的id即可，只需要一次查询；如果是通过辅助索引查找其他字段，则需要回表查询，如`select id, name, gender from xxx where name='xxx';`

所以尽量不要用`select *`，容易出现回表查询，降低效率，除非有联合索引包含了所有字段

面试题：一张表，有四个字段（id, username, password, status），由于数据量大，需要对以下SQL语句进行优化，该如何进行才是最优方案：
`select id, username, password from tb_user where username='itcast';`

解：给username和password字段建立联合索引，则不需要回表查询，直接覆盖索引

#### 前缀索引

当字段类型为字符串（varchar, text等）时，有时候需要索引很长的字符串，这会让索引变得很大，查询时，浪费大量的磁盘IO，影响查询效率，此时可以只降字符串的一部分前缀，建立索引，这样可以大大节约索引空间，从而提高索引效率。

语法：`create index idx_xxxx on table_name(columnn(n));`
前缀长度：可以根据索引的选择性来决定，而选择性是指不重复的索引值（基数）和数据表的记录总数的比值，索引选择性越高则查询效率越高，唯一索引的选择性是1，这是最好的索引选择性，性能也是最好的。
求选择性公式：
```mysql
select count(distinct email) / count(*) from tb_user;
select count(distinct substring(email, 1, 5)) / count(*) from tb_user;
```

show index 里面的sub_part可以看到接取的长度

#### 单列索引&联合索引

单列索引：即一个索引只包含单个列
联合索引：即一个索引包含了多个列
在业务场景中，如果存在多个查询条件，考虑针对于查询字段建立索引时，建议建立联合索引，而非单列索引。

单列索引情况：
`explain select id, phone, name from tb_user where phone = '17799990010' and name = '韩信';`
这句只会用到phone索引字段

##### 注意事项

- 多条件联合查询时，MySQL优化器会评估哪个字段的索引效率更高，会选择该索引完成本次查询

### 设计原则

1. 针对于数据量较大，且查询比较频繁的表建立索引
2. 针对于常作为查询条件（where）、排序（order by）、分组（group by）操作的字段建立索引
3. 尽量选择区分度高的列作为索引，尽量建立唯一索引，区分度越高，使用索引的效率越高
4. 如果是字符串类型的字段，字段长度较长，可以针对于字段的特点，建立前缀索引
5. 尽量使用联合索引，减少单列索引，查询时，联合索引很多时候可以覆盖索引，节省存储空间，避免回表，提高查询效率
6. 要控制索引的数量，索引并不是多多益善，索引越多，维护索引结构的代价就越大，会影响增删改的效率
7. 如果索引列不能存储NULL值，请在创建表时使用NOT NULL约束它。当优化器知道每列是否包含NULL值时，它可以更好地确定哪个索引最有效地用于查询

## SQL 优化

### 插入数据

普通插入：

1. 采用批量插入（一次插入的数据不建议超过1000条）
2. 手动提交事务
3. 主键顺序插入

大批量插入：
如果一次性需要插入大批量数据，使用insert语句插入性能较低，此时可以使用MySQL数据库提供的load指令插入。

```mysql
# 客户端连接服务端时，加上参数 --local-infile（这一行在bash/cmd界面输入）
mysql --local-infile -u root -p
# 设置全局参数local_infile为1，开启从本地加载文件导入数据的开关
set global local_infile = 1;
select @@local_infile;
# 执行load指令将准备好的数据，加载到表结构中
load data local infile '/root/sql1.log' into table 'tb_user' fields terminated by ',' lines terminated by '\n';
```

### 主键优化

数据组织方式：在InnoDB存储引擎中，表数据都是根据主键顺序组织存放的，这种存储方式的表称为索引组织表（Index organized table, IOT）

页分裂：页可以为空，也可以填充一般，也可以填充100%，每个页包含了2-N行数据（如果一行数据过大，会行溢出），根据主键排列。
页合并：当删除一行记录时，实际上记录并没有被物理删除，只是记录被标记（flaged）为删除并且它的空间变得允许被其他记录声明使用。当页中删除的记录到达 MERGE_THRESHOLD（默认为页的50%），InnoDB会开始寻找最靠近的页（前后）看看是否可以将这两个页合并以优化空间使用。

MERGE_THRESHOLD：合并页的阈值，可以自己设置，在创建表或创建索引时指定

> 文字说明不够清晰明了，具体可以看视频里的PPT演示过程：https://www.bilibili.com/video/BV1Kr4y1i7ru?p=90

主键设计原则：

- 满足业务需求的情况下，尽量降低主键的长度
- 插入数据时，尽量选择顺序插入，选择使用 AUTO_INCREMENT 自增主键
- 尽量不要使用 UUID 做主键或者是其他的自然主键，如身份证号
- 业务操作时，避免对主键的修改

### order by优化

1. Using filesort：通过表的索引或全表扫描，读取满足条件的数据行，然后在排序缓冲区 sort buffer 中完成排序操作，所有不是通过索引直接返回排序结果的排序都叫 FileSort 排序
2. Using index：通过有序索引顺序扫描直接返回有序数据，这种情况即为 using index，不需要额外排序，操作效率高

如果order by字段全部使用升序排序或者降序排序，则都会走索引，但是如果一个字段升序排序，另一个字段降序排序，则不会走索引，explain的extra信息显示的是`Using index, Using filesort`，如果要优化掉Using filesort，则需要另外再创建一个索引，如：`create index idx_user_age_phone_ad on tb_user(age asc, phone desc);`，此时使用`select id, age, phone from tb_user order by age asc, phone desc;`会全部走索引

总结：

- 根据排序字段建立合适的索引，多字段排序时，也遵循最左前缀法则
- 尽量使用覆盖索引
- 多字段排序，一个升序一个降序，此时需要注意联合索引在创建时的规则（ASC/DESC）
- 如果不可避免出现filesort，大数据量排序时，可以适当增大排序缓冲区大小 sort_buffer_size（默认256k）

### group by优化

- 在分组操作时，可以通过索引来提高效率
- 分组操作时，索引的使用也是满足最左前缀法则的

如索引为`idx_user_pro_age_stat`，则句式可以是`select ... where profession order by age`，这样也符合最左前缀法则

### limit优化

常见的问题如`limit 2000000, 10`，此时需要 MySQL 排序前2000000条记录，但仅仅返回2000000 - 2000010的记录，其他记录丢弃，查询排序的代价非常大。
优化方案：一般分页查询时，通过创建覆盖索引能够比较好地提高性能，可以通过覆盖索引加子查询形式进行优化

例如：

```mysql
-- 此语句耗时很长
select * from tb_sku limit 9000000, 10;
-- 通过覆盖索引加快速度，直接通过主键索引进行排序及查询
select id from tb_sku order by id limit 9000000, 10;
-- 下面的语句是错误的，因为 MySQL 不支持 in 里面使用 limit
-- select * from tb_sku where id in (select id from tb_sku order by id limit 9000000, 10);
-- 通过连表查询即可实现第一句的效果，并且能达到第二句的速度
select * from tb_sku as s, (select id from tb_sku order by id limit 9000000, 10) as a where s.id = a.id;
```

### count优化

MyISAM 引擎把一个表的总行数存在了磁盘上，因此执行 count(\*) 的时候会直接返回这个数，效率很高（前提是不适用where）；
InnoDB 在执行 count(\*) 时，需要把数据一行一行地从引擎里面读出来，然后累计计数。
优化方案：自己计数，如创建key-value表存储在内存或硬盘，或者是用redis

count的几种用法：

- 如果count函数的参数（count里面写的那个字段）不是NULL（字段值不为NULL），累计值就加一，最后返回累计值
- 用法：count(\*)、count(主键)、count(字段)、count(1)
- count(主键)跟count(\*)一样，因为主键不能为空；count(字段)只计算字段值不为NULL的行；count(1)引擎会为每行添加一个1，然后就count这个1，返回结果也跟count(\*)一样；count(null)返回0

各种用法的性能：

- count(主键)：InnoDB引擎会遍历整张表，把每行的主键id值都取出来，返回给服务层，服务层拿到主键后，直接按行进行累加（主键不可能为空）
- count(字段)：没有not null约束的话，InnoDB引擎会遍历整张表把每一行的字段值都取出来，返回给服务层，服务层判断是否为null，不为null，计数累加；有not null约束的话，InnoDB引擎会遍历整张表把每一行的字段值都取出来，返回给服务层，直接按行进行累加
- count(1)：InnoDB 引擎遍历整张表，但不取值。服务层对于返回的每一层，放一个数字 1 进去，直接按行进行累加
- count(\*)：InnoDB 引擎并不会把全部字段取出来，而是专门做了优化，不取值，服务层直接按行进行累加

按效率排序：count(字段) < count(主键) < count(1) < count(\*)，所以尽量使用 count(\*)

### update优化（避免行锁升级为表锁）

InnoDB 的行锁是针对索引加的锁，不是针对记录加的锁，并且该索引不能失效，否则会从行锁升级为表锁。

如以下两条语句：
`update student set no = '123' where id = 1;`，这句由于id有主键索引，所以只会锁这一行；
`update student set no = '123' where name = 'test';`，这句由于name没有索引，所以会把整张表都锁住进行数据更新，解决方法是给name字段添加索引

# 数据类型

## 整型

| 类型名称      | 取值范围                                  | 大小    |
| ------------- | ----------------------------------------- | ------- |
| TINYINT       | -128〜127                                 | 1个字节 |
| SMALLINT      | -32768〜32767                             | 2个宇节 |
| MEDIUMINT     | -8388608〜8388607                         | 3个字节 |
| INT (INTEGHR) | -2147483648〜2147483647                   | 4个字节 |
| BIGINT        | -9223372036854775808〜9223372036854775807 | 8个字节 |

无符号在数据类型后加 unsigned 关键字。

## 浮点型

| 类型名称            | 说明               | 存储需求   |
| ------------------- | ------------------ | ---------- |
| FLOAT               | 单精度浮点数       | 4 个字节   |
| DOUBLE              | 双精度浮点数       | 8 个字节   |
| DECIMAL (M, D)，DEC | 压缩的“严格”定点数 | M+2 个字节 |

## 日期和时间

| 类型名称  | 日期格式            | 日期范围                                          | 存储需求 |
| --------- | ------------------- | ------------------------------------------------- | -------- |
| YEAR      | YYYY                | 1901 ~ 2155                                       | 1 个字节 |
| TIME      | HH:MM:SS            | -838:59:59 ~ 838:59:59                            | 3 个字节 |
| DATE      | YYYY-MM-DD          | 1000-01-01 ~ 9999-12-3                            | 3 个字节 |
| DATETIME  | YYYY-MM-DD HH:MM:SS | 1000-01-01 00:00:00 ~ 9999-12-31 23:59:59         | 8 个字节 |
| TIMESTAMP | YYYY-MM-DD HH:MM:SS | 1980-01-01 00:00:01 UTC ~ 2040-01-19 03:14:07 UTC | 4 个字节 |

## 字符串

| 类型名称   | 说明                                         | 存储需求                                                   |
| ---------- | -------------------------------------------- | ---------------------------------------------------------- |
| CHAR(M)    | 固定长度非二进制字符串                       | M 字节，1<=M<=255                                          |
| VARCHAR(M) | 变长非二进制字符串                           | L+1字节，在此，L< = M和 1<=M<=255                          |
| TINYTEXT   | 非常小的非二进制字符串                       | L+1字节，在此，L<2^8                                       |
| TEXT       | 小的非二进制字符串                           | L+2字节，在此，L<2^16                                      |
| MEDIUMTEXT | 中等大小的非二进制字符串                     | L+3字节，在此，L<2^24                                      |
| LONGTEXT   | 大的非二进制字符串                           | L+4字节，在此，L<2^32                                      |
| ENUM       | 枚举类型，只能有一个枚举字符串值             | 1或2个字节，取决于枚举值的数目 (最大值为65535)             |
| SET        | 一个设置，字符串对象可以有零个或 多个SET成员 | 1、2、3、4或8个字节，取决于集合 成员的数量（最多64个成员） |

## 二进制类型

| 类型名称       | 说明                 | 存储需求               |
| -------------- | -------------------- | ---------------------- |
| BIT(M)         | 位字段类型           | 大约 (M+7)/8 字节      |
| BINARY(M)      | 固定长度二进制字符串 | M 字节                 |
| VARBINARY (M)  | 可变长度二进制字符串 | M+1 字节               |
| TINYBLOB (M)   | 非常小的BLOB         | L+1 字节，在此，L<2^8  |
| BLOB (M)       | 小 BLOB              | L+2 字节，在此，L<2^16 |
| MEDIUMBLOB (M) | 中等大小的BLOB       | L+3 字节，在此，L<2^24 |
| LONGBLOB (M)   | 非常大的BLOB         | L+4 字节，在此，L<2^32 |

# 权限一览表

> 具体权限的作用详见[官方文档](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html "官方文档")

GRANT 和 REVOKE 允许的静态权限

| Privilege                                                    | Grant Table Column           | Context                               |
| :----------------------------------------------------------- | :--------------------------- | :------------------------------------ |
| [`ALL [PRIVILEGES]`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_all) | Synonym for “all privileges” | Server administration                 |
| [`ALTER`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_alter) | `Alter_priv`                 | Tables                                |
| [`ALTER ROUTINE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_alter-routine) | `Alter_routine_priv`         | Stored routines                       |
| [`CREATE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_create) | `Create_priv`                | Databases, tables, or indexes         |
| [`CREATE ROLE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_create-role) | `Create_role_priv`           | Server administration                 |
| [`CREATE ROUTINE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_create-routine) | `Create_routine_priv`        | Stored routines                       |
| [`CREATE TABLESPACE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_create-tablespace) | `Create_tablespace_priv`     | Server administration                 |
| [`CREATE TEMPORARY TABLES`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_create-temporary-tables) | `Create_tmp_table_priv`      | Tables                                |
| [`CREATE USER`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_create-user) | `Create_user_priv`           | Server administration                 |
| [`CREATE VIEW`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_create-view) | `Create_view_priv`           | Views                                 |
| [`DELETE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_delete) | `Delete_priv`                | Tables                                |
| [`DROP`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_drop) | `Drop_priv`                  | Databases, tables, or views           |
| [`DROP ROLE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_drop-role) | `Drop_role_priv`             | Server administration                 |
| [`EVENT`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_event) | `Event_priv`                 | Databases                             |
| [`EXECUTE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_execute) | `Execute_priv`               | Stored routines                       |
| [`FILE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_file) | `File_priv`                  | File access on server host            |
| [`GRANT OPTION`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_grant-option) | `Grant_priv`                 | Databases, tables, or stored routines |
| [`INDEX`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_index) | `Index_priv`                 | Tables                                |
| [`INSERT`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_insert) | `Insert_priv`                | Tables or columns                     |
| [`LOCK TABLES`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_lock-tables) | `Lock_tables_priv`           | Databases                             |
| [`PROCESS`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_process) | `Process_priv`               | Server administration                 |
| [`PROXY`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_proxy) | See `proxies_priv` table     | Server administration                 |
| [`REFERENCES`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_references) | `References_priv`            | Databases or tables                   |
| [`RELOAD`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_reload) | `Reload_priv`                | Server administration                 |
| [`REPLICATION CLIENT`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_replication-client) | `Repl_client_priv`           | Server administration                 |
| [`REPLICATION SLAVE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_replication-slave) | `Repl_slave_priv`            | Server administration                 |
| [`SELECT`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_select) | `Select_priv`                | Tables or columns                     |
| [`SHOW DATABASES`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_show-databases) | `Show_db_priv`               | Server administration                 |
| [`SHOW VIEW`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_show-view) | `Show_view_priv`             | Views                                 |
| [`SHUTDOWN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_shutdown) | `Shutdown_priv`              | Server administration                 |
| [`SUPER`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_super) | `Super_priv`                 | Server administration                 |
| [`TRIGGER`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_trigger) | `Trigger_priv`               | Tables                                |
| [`UPDATE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_update) | `Update_priv`                | Tables or columns                     |
| [`USAGE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_usage) | Synonym for “no privileges”  | Server administration                 |

GRANT 和 REVOKE 允许的动态权限

| Privilege                                                    | Context                                           |
| :----------------------------------------------------------- | :------------------------------------------------ |
| [`APPLICATION_PASSWORD_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_application-password-admin) | Dual password administration                      |
| [`AUDIT_ABORT_EXEMPT`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_audit-abort-exempt) | Allow queries blocked by audit log filter         |
| [`AUDIT_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_audit-admin) | Audit log administration                          |
| [`AUTHENTICATION_POLICY_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_authentication-policy-admin) | Authentication administration                     |
| [`BACKUP_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_backup-admin) | Backup administration                             |
| [`BINLOG_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_binlog-admin) | Backup and Replication administration             |
| [`BINLOG_ENCRYPTION_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_binlog-encryption-admin) | Backup and Replication administration             |
| [`CLONE_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_clone-admin) | Clone administration                              |
| [`CONNECTION_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_connection-admin) | Server administration                             |
| [`ENCRYPTION_KEY_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_encryption-key-admin) | Server administration                             |
| [`FIREWALL_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_firewall-admin) | Firewall administration                           |
| [`FIREWALL_EXEMPT`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_firewall-exempt) | Firewall administration                           |
| [`FIREWALL_USER`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_firewall-user) | Firewall administration                           |
| [`FLUSH_OPTIMIZER_COSTS`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_flush-optimizer-costs) | Server administration                             |
| [`FLUSH_STATUS`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_flush-status) | Server administration                             |
| [`FLUSH_TABLES`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_flush-tables) | Server administration                             |
| [`FLUSH_USER_RESOURCES`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_flush-user-resources) | Server administration                             |
| [`GROUP_REPLICATION_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_group-replication-admin) | Replication administration                        |
| [`GROUP_REPLICATION_STREAM`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_group-replication-stream) | Replication administration                        |
| [`INNODB_REDO_LOG_ARCHIVE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_innodb-redo-log-archive) | Redo log archiving administration                 |
| [`NDB_STORED_USER`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_ndb-stored-user) | NDB Cluster                                       |
| [`PASSWORDLESS_USER_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_passwordless-user-admin) | Authentication administration                     |
| [`PERSIST_RO_VARIABLES_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_persist-ro-variables-admin) | Server administration                             |
| [`REPLICATION_APPLIER`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_replication-applier) | `PRIVILEGE_CHECKS_USER` for a replication channel |
| [`REPLICATION_SLAVE_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_replication-slave-admin) | Replication administration                        |
| [`RESOURCE_GROUP_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_resource-group-admin) | Resource group administration                     |
| [`RESOURCE_GROUP_USER`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_resource-group-user) | Resource group administration                     |
| [`ROLE_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_role-admin) | Server administration                             |
| [`SESSION_VARIABLES_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_session-variables-admin) | Server administration                             |
| [`SET_USER_ID`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_set-user-id) | Server administration                             |
| [`SHOW_ROUTINE`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_show-routine) | Server administration                             |
| [`SYSTEM_USER`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_system-user) | Server administration                             |
| [`SYSTEM_VARIABLES_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_system-variables-admin) | Server administration                             |
| [`TABLE_ENCRYPTION_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_table-encryption-admin) | Server administration                             |
| [`VERSION_TOKEN_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_version-token-admin) | Server administration                             |
| [`XA_RECOVER_ADMIN`](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html#priv_xa-recover-admin) | Server administration                             |

# 图形化界面工具

- Workbench(免费): http://dev.mysql.com/downloads/workbench/
- navicat(收费，试用版30天): https://www.navicat.com/en/download/navicat-for-mysql
- Sequel Pro(开源免费，仅支持Mac OS): http://www.sequelpro.com/
- HeidiSQL(免费): http://www.heidisql.com/
- phpMyAdmin(免费): https://www.phpmyadmin.net/
- SQLyog: https://sqlyog.en.softonic.com/

# 安装

# 小技巧

1. 在SQL语句之后加上`\G`会将结果的表格形式转换成行文本形式
2. 查看Mysql数据库占用空间：
```mysql
SELECT table_schema "Database Name"
     , SUM(data_length + index_length) / (1024 * 1024) "Database Size in MB"
FROM information_schema.TABLES
GROUP BY table_schema;
```