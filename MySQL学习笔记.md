# MySQL学习路线

![image-20220821171304267](C:\Users\11602\AppData\Roaming\Typora\typora-user-images\image-20220821171304267.png)

# MySQL学习技巧：==学习mysql videos时候，我先自己看着笔记自行先敲一次，弄好了再过一遍视频，这这样子会学的比较扎实！==

# 基础篇（学完就能处理大部分的数据库业务开发工作了）

（我直接在我的服务器上按照MySQL，然后用我的Vscode连接并进行学习即可！）

Ubuntu Linux MySQL的下载地址：https://dev.mysql.com/downloads/mysql/5.6.html#downloads

windows下：去官网下载mysql-installer-community-8.0.29.0.msi

==注意：一旦你的电脑之前下载过旧版本的mysql的话，要安装别的版本的mysql就必须要先卸载掉原来的mysql才可以去安装新的！==

真实开发环境中，99%都是在Linux的环境下操作MySQL的，因此必须要习惯在Linux上操作MySQL！！！

## 关于Centos8下安装MySQL所遇到的任何问题，可以在我自己的CSDN博客里面找到对应的文章记录！！！

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

**注**：其中，-u后可直接指定用户名，-p后可直接指定用户密码！

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

- **字符串**和**日期类型**数据应该包含在**引号''**中
- 插入的数据大小应该在字段的规定范围内
- 插入数据时，**==指定的字段==**顺序需要与**==值的顺序==**是**一一对应**的



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

##### 补充：正则表达式

![112](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/112.png)



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

在SQL的查询语句中==嵌套SELECT==语句，称为==嵌套查询==，又称==子查询==。
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
常用操作符：IN（==very 常用！！！==）

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
-- 创建薪资等级表
CREATE table salgrade(
	grade int comment '等级',
	losal int comment '最低薪资',
	hisal int comment '最高薪资'
)comment '薪资等级表';

INSERT into salgrade VALUES
(1,0,3000),(2,3001,5000),(3,5001,8000),(4,8001,10000),
(5,10001,15000),(6,15001,20000),(7,20001,25000),(8,25001,30000);

-- 需求1：查询员工的姓名、年龄、职位、部门信息。
SELECT e.`name`,e.age,e.job,d.`name`as '部门' from emp as e left outer join dept as d on d.id = e.dept_id;

-- 需求2：查询年龄小于40岁的员工姓名、年龄、职位、部门信息。
#way1:
SELECT new_e.`name`,new_e.age,new_e.job,new_e.`部门` from (SELECT e.`name`,e.age,e.job,d.`name`as '部门' from emp as e left outer join dept as d on d.id = e.dept_id) as new_e WHERE age < 40;
#way2:
SELECT e.`name`,e.age,e.job,d.`name`as '部门' from emp as e join dept as d on e.dept_id = d.id where e.age < 40;

-- 需求3：查询拥有员工的部门ID，部门名称。
SELECT DISTINCT e.dept_id ,d.`name` FROM emp as e JOIN dept d on e.dept_id = d.id;

-- 需求4：查询所有年龄大于40岁的员工，及其归属部门名称；如果员工没有部门也需要展示出来(说明要使用外连接的方式来查询)
SELECT e.*,d.`name` as '部门' FROM emp as e left outer join dept as d on e.dept_id = d.id WHERE e.age > 40;

-- 需求5：查询所有员工的工资等级
# 注意：因为该需求需要操作2张不同的表，因此要用到外连接！
# 表：emp,salgrade,连接条件：sg.losal <= e.salary && e.salary <= sg.hisal
# way1:
SELECT e.salary,sg.grade as '工资等级' from emp as e left outer join salgrade sg on sg.losal <= e.salary && e.salary <= sg.hisal;
# way2:
SELECT e.salary,sg.grade as '工资等级' from emp as e left outer join salgrade sg on e.salary BETWEEN sg.losal and sg.hisal;
-- 需求6：查询“研发部”所有员工的信息 及 工资等级
# 表：emp,dept,salgrade
# 连接条件（因为涉及到三张表格，因此有2个连接条件）：
# 条件1: dept.id = emp.dept_id
# 条件2: sg.losal <= e.salary && e.salary <= sg.hisal
# 查询条件：dept.`name` = '研发部'
-- 第一步：先查询查询“研发部”所有员工的信息
-- 第二步：再根据上述查询到达信息表格，来查询所有研发部员工的工资等级
# way1:
SELECT e.*,sg.grade as '工资等级' from (SELECT * from emp as e WHERE e.dept_id = (SELECT id from dept WHERE `name` = '研发部')) as e left outer join salgrade sg on sg.losal <= e.salary && e.salary <= sg.hisal;
# way2:
SELECT e.*,s.grade from emp e,dept d,salgrade s WHERE e.dept_id = d.id and (e.salary BETWEEN s.losal and s.hisal) and d.`name` = '研发部';

-- 需求7：查询“研发部”员工的平均工资
-- 第一步：先查询查询“研发部”所有员工的工资
SELECT salary from emp WHERE dept_id = (SELECT id from dept WHERE `name` = '研发部');
-- 第二步：在第一步的基础上后查询平均工资
# way1:
SELECT AVG(new_e.salary) '研发部的平均工资' from (SELECT salary from emp WHERE dept_id = (SELECT id from dept WHERE `name` = '研发部')) as new_e;
# way2:
SELECT avg(e.salary) from emp e,dept d WHERE e.dept_id = d.id and d.`name` = '研发部';
-- 需求8：查询工资比“灭绝”高的员工信息
-- 第一步：先查询查询所有员工的工资信息
SELECT salary from emp WHERE `name` = '灭绝';
-- 第二步：后求所有比“灭绝”高的员工信息
SELECT * from emp WHERE salary > (SELECT salary from emp WHERE `name` = '灭绝');

-- 需求9：查询工资比平均工资高的员工信息
-- 第一步：先查询所有员工的平均工资
SELECT avg(salary) from emp;
-- 第二步：再查询工资比平均工资高的员工信息
SELECT * from emp WHERE salary > (SELECT avg(salary) from emp);


-- 需求10：查询低于本部门平均工资的员工信息(真的难)
-- 表：dept,emp
-- 连接条件：dept.id = emp.dept_id
-- 查询条件：
-- 第一步：先查询指定部门的平均薪资
SELECT e.salary,e.dept_id from emp as e WHERE e.dept_id = 1;
-- 第二步：
# 求对应低于本部门平均工资的员工的信息
-- SELECT avg(e.salary),e.dept_id from emp as e WHERE e.dept_id = 1;
-- SELECT avg(e.salary),e.dept_id from emp as e WHERE e.dept_id = 3;
SELECT e2.*,( SELECT avg( e.salary ) FROM emp AS e WHERE e.dept_id = e2.dept_id ) AS '当前部门平均薪资' 
FROM
	emp e2 
WHERE
	salary < ( SELECT avg( e.salary ) FROM emp AS e WHERE e.dept_id = e2.dept_id );

-- 需求11：查询所有部门信息，并统计各个部门的员工人数(真的难)
#  表：emp,dept
#  连接条件：dept.id = emp.dept_id
SELECT d.id,d.`name`,(SELECT count(*) FROM emp e WHERE d.id = e.dept_id) as '部门人数' from dept d;


-- 需求12：查询所有学生的选课情况，并展示出学生的名字，学号，课程名称(学生和课程的关系就是多对多的关系)。
-- 涉及的表：student，course，student_course
-- 连接条件（3张表就有2个连接条件，N张表就有N-1个条件，这样才能够消除笛卡尔积，然后才能筛选出需要的数据记录！）：
#  条件1：student.id = student_course.studentid
#  条件2：course.id = student_course.courseid

SELECT s.`name`as '姓名',s.`no`as '学号',c.`name`as '课程名称' from student s,student_course sc,course c WHERE s.id = sc.studentid and c.id = sc.courseid; 
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
`START TRANSACTION; 或 BEGIN TRANSACTION;`
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

### MySQL-Server的体系结构

![结构图](https://dhc.pythonanywhere.com/media/editor/MySQL体系结构_20220315034329549927.png "结构图")
![层级描述](https://dhc.pythonanywhere.com/media/editor/MySQL体系结构层级含义_20220315034359342837.png "层级描述")

### 存储引擎简介

存储引擎就是存储数据、建立索引、更新/查询数据等技术的实现方式。存储引擎是基于表而不是基于库的，所以存储引擎也可以被称为表引擎。
默认存储引擎是InnoDB。

相关操作：

```mysql
-- 查询建表语句
show create table account;
-- 建表时指定存储引擎（若指定INNODB的话，可以忽略 ENGINE=INNODB 这条SQL语句）
CREATE TABLE 表名(
	...
) ENGINE=INNODB;
-- 查看当前数据库支持的存储引擎
show engines;
```

#### InnoDB

InnoDB 是一种兼顾高可靠性和高性能的通用存储引擎，在 MySQL 5.5 之后，InnoDB 是**默认**的 MySQL 引擎。

特点：

- DML 操作遵循 ACID 模型，支持**事务**
- **行级锁**，提高并发访问性能
- 支持**外键**FOREIGN KEY约束，保证数据的完整性和正确性

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

#### MyISAM

MyISAM 是 MySQL 早期的默认存储引擎。

特点：

- 不支持事务，不支持外键
- 支持表锁，不支持行锁
- 访问速度快

文件：

- xxx.sdi: 存储表结构信息
- xxx.MYD: 存储数据
- xxx.MYI: 存储索引

#### Memory

Memory 引擎的表数据是存储在内存中的，受硬件问题、断电问题的影响，只能将这些表作为临时表或缓存使用。

特点：

- 存放在内存中，数据访问的速度快
- hash索引（默认）

文件：

- xxx.sdi: 存储表结构信息

### 存储引擎特点

| 特点  | InnoDB  | MyISAM  | Memory  |
| ------------ | ------------ | ------------ | ------------ |
| 存储限制  | 64TB  | 有  | 有  |
| 事务安全  | ==支持== | ==-== | -  |
| 锁机制  | ==行（级）锁== | ==表锁== | 表锁  |
| B+tree索引  | 支持  | 支持  | 支持  |
| Hash索引  | -  | -  | 支持  |
| 全文索引  | 支持（5.6版本之后）  | 支持  | -  |
| 空间使用  | 高  | 低  | N/A  |
| 内存使用  | 高  | 低  | 中等  |
| 批量插入速度  | 低  | 高  | 高  |
| 支持外键  | ==支持== | ==-== | -  |

补充问题：InnoDB和MyISAM的区别是什么？（==面试高频考题==）

答：

①InnoDB是支持==事务安全==的，而MyISAM不支持。

②InnoDB是支持==行锁==的，而MyISAM只支持==表锁==。

③InnoDB是支持==外键==的，而MyISAM不支持。

### 存储引擎的选择

存储引擎是没有好坏之分的，so当我们在选择存储引擎时，应该**根据应用系统的特点**选择**合适的存储引擎**。对于复杂的应用系统，还可以根据实际情况选择多种存储引擎进行组合。

- InnoDB: 如果应用对事物的完整性有比较高的要求，在并发条件下要求数据的一致性，数据操作除了插入和查询之外，还包含很多的更新、删除操作，则 InnoDB 是比较合适的选择（也是唯一的选择，因为只有INNODB支持事务）
- MyISAM: 如果应用是以读操作和插入操作为主，只有很少的更新和删除操作，并且对事务的完整性、并发性要求不高（认为偶尔丢那么一两条数据没多大的关系的话），那这个存储引擎是非常合适的。
- Memory: 将所有数据保存在内存中，访问速度快，通常用于临时表及缓存。Memory 的缺陷是对表的大小有限制，太大的表无法缓存在内存中，而且无法保障数据的安全性

电商中的足迹和评论适合使用 MyISAM 引擎，缓存适合使用 Memory 引擎。

**注意：**绝大多数业务场景下，我们使用的存储引擎是InnoDB！此时我们在创建表时就无需指定引擎，因为MySQL5.5版本之后就默认了存储引擎就是InnoDB了！

## ==索引==（进阶篇中最为重要的知识点）

### 概念

索引：索引是帮助 MySQL ==**高效获取数据**== 的 **==数据结构（且是一种有序的数据结构）==**。在数据之外，数据库系统还维护着满足特定查找算法的数据结构，这些数据结构以某种方式引用（指向）原始的数据，这样就可以在这些数据结构上实现高级查询算法，这种数据结构就是**索引**。(不同的存储引擎的索引结构是不一样的！！！)

优缺点：

优点：

- 提高数据检索效率，降低数据库的IO成本（数据库的数据是存放在磁盘中的，数据库IO就需要磁盘的IO，成本较高）
- 通过索引列对数据进行排序，降低数据排序的成本，降低CPU的消耗

缺点：

- 索引列（要维护这个数据结构）也是要占用（磁盘）空间的

- 索引大大提高了查询效率，但降低了更新的速度，比如 INSERT、UPDATE、DELETE

  对日常开发的业务系统来说，数据库的**增删改操作**相比**查询操作**是非常少的，因此在工作时我们几乎可以忽略索引的缺点！！！

  ![26](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/26.JPG)

### 索引结构

MySQL的索引是在**存储引擎层**实现的，不同的存储引擎有不同的结构，主要包含以下几种：

| 索引结构  | 描述  |
| ------------ | ------------ |
| **B+Tree** | **最常见**的索引类型，**大部分引擎**都支持**B+树索引** |
| Hash  | 底层数据结构是用哈希表实现，只有精确匹配索引列的查询才有效，不支持范围查询  |
| R-Tree(空间索引)  | 空间索引是 MyISAM 引擎的一个特殊索引类型，主要用于地理空间数据类型，通常使用较少  |
| Full-Text(全文索引)  | 是一种通过建立倒排索引，快速匹配文档的方式，类似于 Lucene, Solr, ES  |

| 索引  | InnoDB  | MyISAM  | Memory  |
| ------------ | ------------ | ------------ | ------------ |
| B+Tree索引  | 支持  | 支持  | 支持  |
| Hash索引  | 不支持  | 不支持  | 支持  |
| R-Tree索引  | 不支持  | 支持  | 不支持  |
| Full-text  | 5.6版本后支持  | 支持  | 不支持  |

**重点讨论和学习==B+树索引==！**

我们平常所说的索引，如果没有特别指名的话，都是指**B+树结构组织的索引**。

#### B-Tree

![二叉树](https://dhc.pythonanywhere.com/media/editor/二叉树_20220316153214227108.png "二叉树")

二叉树插入数据节点时顺序插入导致形成一个单项列表这样一个极其不平衡的二叉树这样的缺点可以利用红黑树（二叉平衡搜索树）来解决：
![红黑树](https://dhc.pythonanywhere.com/media/editor/红黑树_20220316163142686602.png "红黑树")
但红黑树也存在大数据量情况下，层级较深，检索速度慢的问题。（因为红黑树始终还是二叉树，每个节点只能有2个孩子节点，当数据量太大的时候依然会变得树的层级较深！)

为了解决上述问题，可以使用**B-Tree** 结构。
B-Tree (**多路**平衡查找树) 以一棵最大度数（max-degree，指一个节点的子节点的最大个数）为5（5阶）的 b-tree 为例（每个节点最多存储4个key，5个指针）

注：

①**多路**指的是一个树节点下可包含多个孩子节点。

②**树的度数**指的是一个树节点的孩子节点的个数。

![B-Tree结构](https://dhc.pythonanywhere.com/media/editor/B-Tree结构_20220316163813441163.png "B-Tree结构")

> B-Tree 的数据插入过程动画参照：https://www.bilibili.com/video/BV1Kr4y1i7ru?p=68
演示地址：https://www.cs.usfca.edu/~galles/visualization/BTree.html

#### B+Tree（是B-Tree的变种）

结构图：（以一棵最大度数为4的B+Tree树为例，该树有3个key（最多），4个指针（最多））

![B+Tree结构图](https://dhc.pythonanywhere.com/media/editor/B+Tree结构图_20220316170700591277.png "B+Tree结构图")

> 演示地址：https://www.cs.usfca.edu/~galles/visualization/BPlusTree.html

B+Tree与 B-Tree 的区别：

- B+Tree中**所有的元素节点**都会**出现在叶子节点**上。
- B+Tree中**所有的叶子节点**会形成一个**单向链表。**
- B+Tree中**除叶子节点外**其他层的节点都是**不存储数据**的，只是**起到一个索引的作用**而已。

在MySQL 索引数据结构中对经典的 B+Tree 进行了优化。在原 B+Tree 的基础上，增加一个**指向相邻叶子节点**的**链表指针**，就形成了带有顺序指针的 B+Tree，也即**在叶子结点之间**形成了一个**双向链表**。提高了区间查询访问的性能。

![MySQL B+Tree 结构图](https://dhc.pythonanywhere.com/media/editor/结构图_20220316171730865611.png "MySQL B+Tree 结构图")

#### Hash

哈希索引就是采用一定的hash算法，将键值换算成新的hash值，（通过哈希函数）映射到对应的槽位上，然后存储在hash表中。
如果两个（或多个）键值，映射到一个相同的槽位上，他们就产生了hash冲突（也称为hash碰撞），可以通过链表来解决。

![Hash索引原理图](https://dhc.pythonanywhere.com/media/editor/Hash索引原理图_20220317143226150679.png "Hash索引原理图")

特点：

- Hash索引只能用于对等比较（=、in），不支持范围查询（between、>、<、...）
- 无法利用索引完成排序操作
- 查询效率高，通常只需要一次检索就可以了，效率通常要高于 B+Tree 索引

存储引擎支持：

- Memory
- InnoDB: 具有自适应hash功能，hash索引是存储引擎根据 B+Tree 索引在指定条件下自动构建的

#### 面试题

1. 为什么 InnoDB 存储引擎选择使用 B+Tree 索引结构（而沒有采用B-Tree或者是其他二叉树）？

   答：

- 相对于二叉树，B+Tree的层级更少（因为允许一个节点有多个子节点），搜索效率更高。so用B+树
- 对于 B-Tree，无论是叶子节点还是非叶子节点，都会保存数据，这样导致一页中存储的键值减少，指针也跟着减少，当要同样保存大量数据，只能增加树的高度，导致性能降低。so用B+树
- 相对于 Hash 索引，B+Tree 支持==范围匹配==及==排序==操作。so用B+树

### 索引分类

| 分类  | 含义  | 特点  | 关键字  |
| ------------ | ------------ | ------------ | ------------ |
| 主键索引  | 针对于表中的主键创建的索引 | 默认自动创建，只能有一个  | PRIMARY  |
| 唯一索引  | 避免同一个表中某数据列中的值重复  | 可以有多个  | UNIQUE  |
| 常规索引  | 快速定位特定数据  | 可以有多个  |   |
| 全文索引  | 全文索引查找的是文本中的关键词，而不是比较索引中的值（用的比较少） | 可以有多个  | FULLTEXT  |

在**InnoDB 存储引擎**中，根据索引的存储形式，又可以分为以下两种：

| 分类  | 含义  | 特点  |
| ------------ | ------------ | ------------ |
| **聚集索引**(Clustered Index) | 将数据存储与索引放一块，索引结构的**叶子节点保存了行数据** | 必须有，而且只有一个  |
| **二级索引**(Secondary Index，称之为辅助索引or非聚集索引) | 将数据与索引**分开存储**，索引结构的**叶子节点关联的是对应的主键（哪个字段是主键就关联谁）** | 可以存在多个  |

演示图：

![大致原理](https://dhc.pythonanywhere.com/media/editor/原理图_20220318194454880073.png "大致原理")
![演示图](https://dhc.pythonanywhere.com/media/editor/演示图_20220319215403721066.png "演示图")

注：

- 所谓回标查询：指的是我们在MySQL中查找数据时，一般都是先通过**二级索引**查找对应的字段值，找到后就能够拿到该**二级索引所存储的主键**，然后再根据主键值回去聚集索引中查找对应的主键值，找到后就能够拿到该**聚集索引所存储的行数据**了！

聚集索引选取规则：

- 如果存在主键，**主键索引**就是**聚集索引**。
- 如果不存在主键，将使用第一个唯一(UNIQUE)索引作为聚集索引。
- 如果表没有主键或没有合适的唯一索引，则 InnoDB 会自动生成一个 rowid 作为隐藏的聚集索引。
- 无论如何，这个聚集索引都会存在！。

#### 思考题

1\. 以下 SQL 语句，哪个执行效率高？为什么？

```mysql
select * from user where id = 10;# 只需要在聚集索引中找id值对应的行数据即可，共需要一个步骤
select * from user where name = 'Arm';# 需要先在二级索引中找与name字段=Arm对应的id，然后再根据此id去聚集索引中找对应的行数据，共需要两个步骤
# 结论：第一条SQL语句执行效率更高！！！
-- 备注：id为主键，name字段创建的有索引
```

答：第一条语句，因为第二条需要回表查询，相当于两个步骤。

2\. InnoDB 主键索引的 B+Tree 高度为多少？

答：假设一行数据大小为1k，一页中可以存储16行这样的数据。InnoDB 中的指针占用6个字节的空间（固定了的），主键假设为bigint，占用字节数为8.
可得公式：`n * 8 + (n + 1) * 6 = 16 * 1024`（key存储的字节数+pointer存储的字节数=一个页的大小是16KB，1KB=1024个bytes字节），其中 8 表示 bigint 占用的字节数，n 表示当前节点存储的key的数量，(n + 1) 表示指针数量（指针数量总是比key多一个）。算出n约为1170。

如果树的高度为2，那么他能存储的数据量大概为：`1171 * 16 = 18736`；
如果树的高度为3，那么他能存储的数据量大概为：`1171 * 1171 * 16 = 21939856`。

另外，如果有成千上万的数据，那么就要考虑分表，涉及运维篇知识。

### 索引语法

**创建索引：**
`CREATE [ UNIQUE | FULLTEXT ] INDEX index_name ON table_name (index_col_name, ...);`

**注意事项：**

- 若 CREATE 后面不加索引类型参数，则表示创建的是**常规索引**。
- 若某字段**并不唯一**，则只能创建**常规索引**，而不能创建**唯一索引**。

- UNIQUE：表示创建的是**唯一索引**。

- FULLTEXT：表示创建的是**全文索引**。
- 一个索引可以关联多个字段，若**只关联一个字段**，则称之为**单列索引**；若关联了多个字段，则称之为**组合索引（联合索引）**。
- 在创建联合索引时，**字段填入的顺序**是**有讲究的！**后面在讲**索引的使用**时会提及到！
- **创建索引**时，索引的**名字规范**：**idx_tableName_字段Name**（这是良好的开发规范，应当学习起来！）

**查看索引：**
`SHOW INDEX FROM table_name;`

**删除索引：**
`DROP INDEX index_name ON table_name;`

案例：

```mysql
# 创建表tb_user
create table tb_user(
	id int auto_increment PRIMARY key comment '用户序号',
	name varchar(10) comment '姓名',
	phone varchar(11) comment '手机号',
	email varchar(30) comment '邮箱',
	profession varchar(10) comment '专业',
	age int CHECK(age > 0 and age <= 120) comment '姓名',
	gender TINYINT comment '性别（1：男，2：女）',
	status int comment '状态',
	createtime datetime comment '日期时间'
)comment 'tb_user';

# 添加数据到tb_user表中！
insert into tb_user values
(null,'吕布','17799990000','lvbu666@163.com','软件工程',23,1,6,'2001-02-02 00:00:00'),
(null,'曹操','17799990001','caocao666@163.com','通讯工程',33,1,0,'2001-03-02 00:00:00'),
(null,'赵云','17799990002','zhaoyun666@qq.com','英语',34,1,2,'2001-05-02 00:00:00'),
(null,'孙悟空','17799990003','sunwukon666@163.com','工程造价',54,1,0,'2002-07-02 00:00:00'),
(null,'花木兰','17799990004','huamulan666@163.com','软件工程',23,2,1,'2001-02-02 00:00:00'),
(null,'大乔','17799990005','daqiao666@360.com','舞蹈',22,2,0,'2001-02-02 00:00:00'),
(null,'露娜','17799990006','luna666@163.com','应用数学',24,2,0,'2001-12-02 00:00:00'),
(null,'程咬金','17799990007','chenyaojin666@163.com','化工',38,1,5,'2001-09-02 00:00:00'),
(null,'项羽','17799990008','xiangyu666@163.com','金属材料',43,1,0,'2001-03-22 00:00:00'),
(null,'白起','17799990009','baiqi666@163.com','机械工程及其自动化',27,1,2,'2001-02-12 00:00:00'),
(null,'韩信','17799990010','hanxin666@163.com','材料工程',27,1,0,'2003-05-11 00:00:00'),
(null,'荆轲','17799990011','jingke666@163.com','会计',29,2,1,'2001-05-15 00:00:00'),
(null,'兰陵王','17799990012','lanlinwang666@sina.com','软件工程',44,1,2,'2001-08-07 00:00:00'),
(null,'狂铁','17799990013','kuangtie666@126.com','国际贸易',51,1,3,'2002-10-12 00:00:00'),
(null,'貂蝉','17799990014','diaochan666@163.com','土木工程',52,2,4,'2005-03-04 00:00:00')
;

-- 需求1：name字段为姓名字段，该字段的值可能会重复，为该字段创建索引（因为可能重复，因此是一个常规索引）
create index idx_user_name on tb_user(name);
-- 需求2：phone手机号字段的值非空，且唯一，为该字段创建唯一索引
create unique index idx_user_phone on tb_user (phone);
-- 需求3：为profession, age, status创建联合索引
create index idx_user_pro_age_stat on tb_user(profession, age, status);
-- 需求4：为email建立合适的索引来提升查询效率
create index idx_user_email on tb_user(email);

-- 删除索引
drop index idx_user_email on tb_user;
```

### SQL性能分析(有利于do SQL的优化)

#### 性能分析手段1：查看SQL的执行频次

查看当前数据库的 INSERT, UPDATE, DELETE, SELECT 访问频次：（**以便于后续的SQL优化**，**哪个关键字访问频次高，就优化哪一类的SQL语句！**）

- 比如以 SELECT语句频次高，就说明当前数据库以查询语句为主，就优化查询语句即可即可达到SQL优化的目的了！

- 比如以 INSERT UPDATE DELETE频次高，就优化增删改语句即可达到SQL优化的目的了！

MYSQL客户端连接成功后，通过show [session | global] status;命令可以提供服务器当前状态信息。

`SHOW GLOBAL STATUS LIKE 'Com_______';` 或者 `SHOW SESSION STATUS LIKE 'Com_______';`
例：`show global status like 'Com_______'`

这里Com后共有**7**个**下划线**！

![27](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/27.JPG)

#### 性能分析手段2：慢查询日志

慢查询日志记录了所有执行时间超过指定参数（long_query_time，单位：秒，默认10秒）的所有SQL语句的日志。（**用慢查询日志就有助于我们==定位==到那些执行效率低下的SQL语句，然后再进行下一步的优化操作**）

**注：**MySQL认为，只要一个SQL语句执行时间超过默认的10s钟，就认为是慢执行操作！（即该SQL语句是待优化的）当然多少秒属于超时可以自定义！！！

MySQL的慢查询日志**默认没有开启**，需要在MySQL的配置文件（/etc/my.cnf）中配置如下信息：

```mysql
# 开启MySQL慢查询日志开关
slow_query_log=1
# 设置慢查询日志的时间为2秒，SQL语句执行时间超过2秒，就会视为慢查询，记录慢查询日志
long_query_time=2
# 更改后记得重启MySQL服务，日志文件位置：/var/lib/mysql/*-slow.log
systemctl restart mysqld
```

**查看慢查询日志开关状态**：
`show variables like 'slow_query_log';`

**查看慢查询日志开关状态超时时间**：

`show variables like 'long_query_time';`

开启慢日志开关前：

![image-20220830151322900](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220830151322900.png)

开启慢日志开关后：

![image-20220830151951411](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220830151951411.png)

![image-20220830152058662](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220830152058662.png)

查看MYSQL服务器的慢日志：

![image-20220830152523239](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220830152523239.png)

```mysql
# 创建表tb_sku
CREATE TABLE `tb_sku` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '商品id',
  `sn` varchar(100) NOT NULL COMMENT '商品条码',
  `name` varchar(200) NOT NULL COMMENT 'SKU名称',
  `price` int(20) NOT NULL COMMENT '价格（分）',
  `num` int(10) NOT NULL COMMENT '库存数量',
  `alert_num` int(11) DEFAULT NULL COMMENT '库存预警数量',
  `image` varchar(200) DEFAULT NULL COMMENT '商品图片',
  `images` varchar(2000) DEFAULT NULL COMMENT '商品图片列表',
  `weight` int(11) DEFAULT NULL COMMENT '重量（克）',
  `create_time` datetime DEFAULT NULL COMMENT '创建时间',
  `update_time` datetime DEFAULT NULL COMMENT '更新时间',
  `category_name` varchar(200) DEFAULT NULL COMMENT '类目名称',
  `brand_name` varchar(100) DEFAULT NULL COMMENT '品牌名称',
  `spec` varchar(200) DEFAULT NULL COMMENT '规格',
  `sale_num` int(11) DEFAULT '0' COMMENT '销量',
  `comment_num` int(11) DEFAULT '0' COMMENT '评论数',
  `status` char(1) DEFAULT '1' COMMENT '商品状态 1-正常，2-下架，3-删除',
  PRIMARY KEY (`id`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='商品表';
# 插入100w条数据...(这里省略)
```

![image-20220830160658143](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220830160658143.png)

![image-20220830160752324](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220830160752324.png)



#### 性能分析手段3：profile

show profile 能在做SQL优化时帮我们了解时间都耗费在哪里。通过 have_profiling 参数，能看到当前 MySQL 是否支持 profile 操作：
`SELECT @@have_profiling;`

![image-20220830161044260](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220830161044260.png)

profiling 默认关闭，可以通过set语句在session/global级别开启 profiling：
`SET profiling = 1;`
查看所有语句的耗时：
`show profiles;`

![image-20220830162952763](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220830162952763.png)

查看指定query_id的SQL语句各个阶段的耗时：
`show profile for query query_id;`

![36](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/36.JPG)

查看指定query_id的SQL语句CPU的使用情况
`show profile cpu for query query_id;`

![image-20220830163621213](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220830163621213.png)

注：**query_id**需要你自己实现用**show profiles;**命令来查看对应的id值！！！

#### 性能分析手段4：==explain(在SQL优化中非常常用)==

EXPLAIN 或者 DESC 命令获取 MySQL 如何执行 SELECT 语句的信息（也即**EXPLAIN/DESC可获取SELECT语句的执行计划**），包括在 SELECT 语句执行过程中表如何连接和连接的顺序。
语法：（**直接在select语句之前加上关键字 explain / desc**）

`EXPLAIN SELECT 字段列表 FROM 表名 HWERE 条件;`

例子：

![image-20220830164353190](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220830164353190.png)

EXPLAIN 各字段含义：

- **id**：select 查询的序列号，表示查询中执行 select 子句或者表的执行（操作）的顺序（id相同，执行顺序从上到下；id不同，值越大越先执行）

- select_type（了解即可）：表示 SELECT 的类型，常见取值有 SIMPLE（简单表，即不适用表连接或者子查询）、PRIMARY（主查询，即外层的查询）、UNION（UNION中的第二个或者后面的查询语句）、SUBQUERY（SELECT/WHERE之后包含了子查询）等

- ==**type**==：表示连接类型，性能由**好到差**的连接类型为 NULL、system、const、eq_ref、ref、range、index、all（因此当我们在做SQL优化时，尽量地把type的性能往左边优化！且尽量不要出现type=all，因为这样子的话会do全表扫描查询，性能是极其低的！）

- ==possible_key==：**可能应用**在这张表上的索引，一个或多个

- ==Key==：**实际使用**的索引，如果没有使用索引，则为 NULL

- ==Key_len==：表示索引中使用的字节数，该值为索引字段最大可能长度，并非实际使用长度，在不损失精确性的前提下，长度越短越好

- rows：MySQL认为必须要执行的行数，在InnoDB引擎的表中，是一个估计值，可能并不总是准确的

- filtered：表示返回结果的行数占需读取行数的百分比，filtered的值越大越好（当filtered=100时性能最高！）

- extra：当出现NULL时，说明此时使用对应的索引需要do回表查询操作，出现index时就说明不需要（因为此时用到了覆盖索引，就不需要回表查询了！）

  注：关注SQL语句的信息时，重点关注type，基本上就能知道该SQL语句的性能好坏了！

### 索引使用规则(如何正确使用索引)

#### 验证索引效率

在有大量数据记录时，给**某字段**增加**索引**后，的**查询效率**会**高出非常非常非常多倍**的！！！

![image-20220901150505197](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220901150505197.png)

![image-20220901150601389](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220901150601389.png)

![image-20220901150634659](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220901150634659.png)

![image-20220901150714078](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220901150714078.png)



#### 最左前缀法则（注意针对联合索引）

如果索引关联了多列|多个字段（即：联合索引），就要遵守最左前缀法则，**最左前缀法则**指的是查询**必须从索引的==最左列==**开始，并且不跳过索引中的列，若跳过了，则索引失效，就没法借助索引这种数据结构来高效查询数据记录了。
如果跳跃某一列，**索引将部分失效（即：这一列后面的字段索引失效）**。

#### 范围查询

联合索引中，若出现范围查询（**<**小于, **>**大于），**范围查询右侧的列索引失效**。（**在业务需要允许的case下**）可尽量用**>=**或者**<=**来规避索引失效问题。（而少去使用**<**小于 或  **>**大于）

例子演示：

具体可以看对应小节的视频：**https://www.bilibili.com/video/BV1Kr4y1i7ru?p=80&vd_source=b050ab0adaffa51f5ad24d77efa40057**

```mysql

```



#### ==索引失效==情况（我们==尽量规避==这些==索引失效case==以提高使用SQL-DML语句的效率！）

1. 在索引列上**进行运算操作**，**索引将失效**。如：`explain select * from tb_user where substring(phone, 10, 2) = '15';`查询性能将降低。

2. 字符串类型字段使用时，**不加引号**，**索引将失效**。如：`explain select * from tb_user where phone = 17799990015;`，此处phone的值没有加引号

3. 模糊查询中，如果仅仅是尾部模糊匹配，索引不会是失效；如果是头部模糊匹配，索引失效；若前后都有 %模糊匹配的话 也会失效。如：`explain select * from tb_user where profession like '%工程';`

   ```mysql
   EXPLAIN SELECT * from tb_user3 WHERE profession LIKE '软件%';#　索引不会失效！
   EXPLAIN SELECT * from tb_user3 WHERE profession LIKE '%工程';#　索引失效！
   EXPLAIN SELECT * from tb_user3 WHERE profession LIKE '%工%';#　索引失效！
   EXPLAIN SELECT * from tb_user3 WHERE profession LIKE '%工_';#　索引失效！
   # 结论：在大数据量时，必须要规避掉 头部模糊查询 的SQL语句写法，因为这样的话会导致索引失效（if有的话），从而只能进行全表扫描查询，性能极其低下！
   ```

4. 用 or 分割开的条件，如果 or 其中一个条件的列没有索引，那么涉及的索引都不会被用到。

   ```mysql
   EXPLAIN SELECT * FROM tb_user3 WHERE age = 23 or gender = 1; 
   # age和gender都没单独建立索引，so该SQL语句只能用全表查询而无法使用索引do高效的查询，效率低下！
   EXPLAIN SELECT * FROM tb_user3 WHERE profession = '软件工程' or gender = 1; 
   # gender没建立索引，so该SQL语句只能用全表查询而无法使用索引do高效的查询，效率低下！
   EXPLAIN SELECT * FROM tb_user3 WHERE phone = '17799990000' or age = 23;
   # phone有单独建立索引，但age没建立索引，so该SQL语句只能用全表查询而无法使用索引do高效的查询，效率低下！
   EXPLAIN SELECT * FROM tb_user3 WHERE profession = '软件工程' or name = '吕布'; 
   # profession联合索引生效，且name有单独建立的索引，so该SQL语句用索引do高效的查询，效率高！
   ```

   

5. 如果 MySQL 的优化器评估后，认为**若使用索引比全表扫描更慢**的话，则**不使用索引**。

   ```mysql
   EXPLAIN SELECT * from tb_user3 WHERE phone >= '17799990005';# 走了索引来查询数据
   EXPLAIN SELECT * from tb_user3 WHERE phone >= '17799990000';# 走了全表扫描来查询数据
   ```

   ![image-20220901163908064](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220901163908064.png)

   ![44](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/44.JPG)

6. 若索引**最左边开头的列不存在**，则**索引也会失效**。（最左前缀法则，也是最重要的索引原则）

#### SQL 提示

是优化数据库的一个重要手段，简单来说，就是在SQL语句中==加入==一些==人为的提示==来达到优化操作的目的。

我们在进行select 查询操作时，如果有很多索引，那么可以给mysql提示一下它应该用or不用or忽视哪个索引值！这就是SQL提示的真正作用！注意：SQL的提示语句必须要==跟在WHERE关键字之前，FROM之后==！

例如，使用索引：
`explain select * from tb_user use index(idx_user_pro) where profession="软件工程";`
不使用哪个索引：
`explain select * from tb_user ignore index(idx_user_pro) where profession="软件工程";`
必须使用哪个索引：
`explain select * from tb_user force index(idx_user_pro) where profession="软件工程";`

```mysql
# SQL的提示关键字只介绍以下3个：
use index(指定的索引名称);	  # 告诉MySQL数据库，建议其使用该索引（来do SQL的DML操作）
  		  	 			   # 但实际使用哪个索引 MySQL 还是会根据MySQL自己的优化器去权衡运行速度去更改的。
ignore index(指定的索引名称);# 告诉MySQL数据库，不使用哪个索引（来do SQL的DML操作）。
force index(指定的索引名称); # 告诉MySQL数据库，就是无论如何你都给我强制使用该索引（来do SQL的DML操作）。
```

例子：

![image-20220901170018744](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220901170018744.png)

<img src="C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/46.JPG" alt="46" style="zoom:80%;" />

<img src="C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220901170140869.png" alt="image-20220901170140869" style="zoom:80%;" />

<img src="C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220901170245106.png" alt="image-20220901170245106" style="zoom:80%;" />

#### ==覆盖索引==&==回表查询==

覆盖索引：查询的SQL语句中使用了索引，并且需要返回的列在该索引中已经==全部能找到==。

推荐以后使用SQL的DML语句时，==尽量使用覆盖索引==，而减少使用 select *。（即：尽量避免在select关键字后使用\*关键字）

explain 中 extra 字段含义：

![image-20220901172455049](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220901172455049.png)

`using index condition`：查找使用了索引，但是需要回表查询数据（==此时效率低==！）
`using where; using index;`：查找使用了索引，但是需要的数据都在索引列中能找到，所以不需要回表查询（==此时效率高==！）

**注意**：所谓的**回表查询**，其实就是先去二级索引处找到对应的主键索引（聚集索引），然后再在聚集索引中找到叶子节点中存储的行数据以查询相应字段的数据记录！（这在前面学习**聚集索引**时有笔记记录，可回看！）

如果在聚集索引中直接能找到对应的行，则直接返回行数据，只需要一次查询，哪怕是select \*；如果在辅助索引中找聚集索引，如`select id, name from xxx where name='xxx';`，也只需要通过辅助索引(name)查找到对应的id，返回name和name索引对应的id即可，只需要一次查询；如果是通过辅助索引查找其他字段，则需要回表查询，如`select id, name, gender from xxx where name='xxx';`

==所以尽量不要用`select *`，容易出现回表查询，降低效率，除非有联合索引包含了所有字段==

例子1：（可自行脑补查询的详细过程，非常简单的哈~）

<img src="C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220901173906402.png" alt="image-20220901173906402" style="zoom:80%;" />

例子2：

```mysql
EXPLAIN SELECT id,profession,age,status,name from tb_user3 WHERE profession = '软件工程' and age = 23 and status = '6';
/*
解释：
	因为我们已事先建立了二级索引:idx_user_pro_age_status ，聚集（主键）索引:PRIMARY (id)
	而 该索引结构已经包含了字段profession,age,status了，并且该索引结构的叶子节点处也已经包含了对应的主键索引字段id   	  了， 刚好囊括我们要查询的就是这四个字段，因此无需再do 回表查询去聚集索引处找其叶子节点的行数据了！！！
*/
EXPLAIN SELECT id,profession,age,status,name from tb_user3 WHERE profession = '软件工程' and age = 23 and status = '6';
/*
解释：
	因为我们已事先建立了二级索引:idx_user_pro_age_status ，聚集（主键）索引:PRIMARY (id)
	而 该索引结构已经包含了字段profession,age,status了，但是，并没包含字段name（即没完全囊括所要查询并返回的字段），	 因此就必须要通过 回表查询 去 聚集索引 根据在二级索引中找到的id值 去 其叶子节点的对应行数据中找到name字段对应的数据	记录才行！其效率是不高的！
*/

/*	结论：
	1-所谓的 覆盖索引，其实也就是说，当我要 查询并返回的字段数据 在我当前的这个聚集索引 or 二级索引 的结构中已经囊括了	  的话，就称该索引为覆盖索引，可直接返回给查询结果，其效率是高的（无需回表查询，一次遍历索引的B+Tree扫描完成查询操		作）！
	2-尽量不要使用select* 了，因为极其容易出现回表查询，效率低！（除非有联合索引包含了所有字段）
*/
```

**面试题**：一张表，有四个字段（id, username, password, status），由于数据量大，需要对以下SQL语句进行优化，该如何进行才是最优方案：
`select id, username, password from tb_user where username='itcast';`

解：给username和password字段建立联合索引，则不需要回表查询，直接就是覆盖索引返回查询的结果了！

#### 前缀索引

问题引入：当字段类型为字符串（varchar, text等）时，有时候需要**索引很长**的字符串，这会让索引变得很大，通过该索引进行查询时，会浪费大量的磁盘IO，影响查询效率！

为了deal这个问题，此时可以**只将字符串的一部分前缀**，用于**建立索引**，这样可以大大**节约索引空间**（降低索引体积），从而**提高索引的效率**。（这即是前缀索引！）

(比如：一个字段存储的数据是一整篇文章，如果根据其全文建立的索引来查询该篇文章的话会浪费大量的磁盘IO！)

语法：`create index idx_xxxx on table_name(columnn(n));`

其中，n：表示我要提取该字符串的**前面共n个字符**作为**索引**。指定一个n为5，那就说明要用该字符串的前5个字符来构建索引。

**注意**：==对于索引字段很长 或 是大文本 的索引字段，建立长度为n的前缀索引是比较合理的，这大大节约了索引空间（降低了索引的体积），且提高了索引的使用效率！==）

**前缀长度n**：可以根据**索引字段**的**选择性**来决定，而**选择性**是指**不重复**的**索引值（基数）**和数据表的**记录总数**的**比值**，索引选择性越高则查询效率越高，**唯一索引**的**选择性**是1。其中，1就是**最好的索引选择性的值**，性能也是最好的，即表明当选择长度为n的前缀来构建索引时，索引字段的区分度已经最高了！。

```mysql
# 求 选择性 的公式：
# tb_user表中 不重复的email个数是：
select count(distinct email) from tb_user;
# tb_user表中 email索引字段的选择性是：
select count(distinct email) / count(*) from tb_user;
# tb_user表中 email索引字段的前5个字符组成的子序列的选择性是：
select count(distinct substring(email, 1, 5)) / count(*) from tb_user;
#　在考虑了实际开发的业务需求后，在 选择性 差别不太大的情况下，若 前缀索引 的长度 能尽量少就尽量少吧，这样就可以节约索引空间，从而提高索引的效率！
# tb_user表中 给email索引字段建立前缀索引：
create index idx_user_email_5 on tb_user3(email(5));
```

![image-20220903151536349](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220903151536349.png)

show index 里面的**sub_part**关键字也可以看到所截取的字符串的前缀长度。

此时，**查询该索引字段的SQL操作**就会**使用该前缀索引**来do了！

![image-20220903154406615](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220903154406615.png)

前缀索引的查询流程：

![image-20220903155333833](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220903155333833.png)

当经过辅助索引和回表查询后，找到对应的id时，虽然已经对比了email字段的前5个字符找到了id，但还需要再通过这个id拿到对应的email字段的数据，并拿来对比剩下的字符看是否**真的完全匹配**我所传递进去的email值（'lvbu666@163.com'）然后再返回对应的*行数据到mysql客户端。

#### 单列索引&联合索引

先回顾下何为单列索引，何为联合索引。

单列索引：即一个索引只包含单个列
联合索引：即一个索引包含了多个列
**注意**：在业务场景中，**如果存在多个查询条件**，考虑针对于所要查询的字段来**建立索引**时，建议**建立联合索引（若联合索引使用得当则可以避免回表查询）**，**而不是单列索引**。

例子：（此时多个查询条件是：WHERE phone = 'xxx' and name = 'xxxx';存在多个索引，可能会使用phone这个单列索引，也可能使用name这个单列索引。但这里**只使用了phone这个单列索引**，而phone也是非聚集索引，so查询时若查询字段并没有被索引中的字段所覆盖电话，会涉及到回表查询操作（当然，若该联合索引是覆盖索引，也能够避免回表查询操作，但当使用单列索引时，极其容易造成回表查询的情况！），此时必然会拿到相应的哈给行数据，而行数据又会包含name对应字段的数据，因此就涉及到了覆盖索引和回表查询的问题，这样do查询的性能（效率）不高！）**（使用==单列==索引时，就需要do回表查询操作了！因为extra值为NULL）**

![image-20220903160336238](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220903160336238.png)

**（使用==联合==索引时，就不需要do回表查询操作了！因为extra值为using index）**

![image-20220903161349329](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220903161349329.png)

联合索引查询情况：

![image-20220903162059681](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220903162059681.png)

##### 注意事项

- 当进行**多条件**联合查询时，MySQL优化器会评估哪个字段的索引效率更高，就会选择该效率最高的索引完成本次查询

### 索引设计7原则

在具体的业务场景下，到底根据怎样的数据字段，怎样的表，建立怎样的索引才能使得使用索引变得高效呢？这就涉及到了索引的设计原则！

尽量：（==注意：索引只是拿来提高检索数据的效率而已，你要是不对数据库对应的表do查询操作，那么建立索引的意义也不大！==）

1. 针对于数据量较大（一般一张表的数据量>=100w时就是数据量大的表），且查询比较频繁的表来建立索引
2. 针对于常作为查询条件（where）、排序（order by）、分组（group by）操作的数据字段建立索引
3. 尽量选择区分度高的列（比如：身份证列/手机号列）作为索引，尽量建立唯一索引，区分度越高，使用索引的效率越高
4. 如果是字符串类型的字段，字段长度较长（甚至是大文本的字段），可以针对于字段的特点，建立前缀索引
5. 尽量使用联合索引，减少单列索引，查询时，联合索引很多时候可以是覆盖索引，节省存储空间，避免回表，提高查询效率
6. 要控制索引的数量，索引并不是多多益善，索引越多，维护索引这种数据结构的代价就越大，会影响增删改的效率（而且还会占用磁盘的空间，so只建立必要的索引即可）
7. 如果索引列不能存储NULL值，请在创建表时使用NOT NULL约束它。当MySQL的优化器知道每列是否包含NULL值时，它可以更好地确定哪个索引用于查询是最有效的。

## SQL 优化

### 插入数据 (时的SQL优化)

**普通插入：**

1. **采用批量插入**

   （一条插入SQL语句时，一次插入的数据不建议超过1000条,500-1000条是比较合适的）

   `insert into tb_user3 values(1,'Tom'),(2,'Cat'),(3,'Jerry')...;`

2. **手动提交事务**

   默认case下，MYSQL是启动自动提交事务操作的，这样你每写好一条SQL语句并执行后就会提交一次事务，这样频繁地提交事务的操作是不好的。

   `-- 查看事务提交方式
   SELECT @@AUTOCOMMIT;
   -- 设置事务提交方式，1为自动提交，0为手动提交，该设置 只对 当前会话 有效
   SET @@AUTOCOMMIT = 0;# 表示设置当前会话的事务提交方式为手动提交！
   start transaction;# 在start transaction; 和 commit;语句之间的SQL语句，要么直接执行完成，要么直接执行失败！
   insert into tb_user3 values(1,'Tom'),(2,'Cat'),(3,'Jerry');
   insert into tb_user3 values(4,'Tom'),(5,'Cat'),(6,'Jerry');
   insert into tb_user3 values(7,'Tom'),(8,'Cat'),(9,'Jerry');
   commit;-- 提交事务(的指令)`

3. **主键顺序插入**

主键乱序插入：8 1 9 21 88 2 4 15 89 5 7 3  <=> 不好！
主键顺序插入：1 2 3 4  5  6 7 8  9  15 21 88 89  <=> 好！

==主键顺序插入性能高于乱序插入！==（后面讲解主键优化的时候会讲why！）

**大批量插入**：
如果需要一次性插入大批量数据，使用insert语句插入性能较低，此时可以使用MySQL数据库提供的load指令插入。

```mysql
# 客户端连接服务端时，加上参数 --local-infile（这一行在bash/cmd界面输入，表示 客户端 此时 需要加载本地文件）
mysql --local-infile -u username -p
# 设置全局参数local_infile为1，开启从本地加载文件导入数据的开关
set global local_infile = 1;
select @@local_infile;
# 执行load指令将准备好的数据，加载到表结构中
load data local infile '/home/linzhuofan/xxx.sql' into table 'tb_user' fields terminated by ',' lines terminated by '\n';
# 其中，','表示每个字段之间用,号分割；而'\n'则表示每一行数据之间用换行符\n来分割；
# 其中，'/home/linzhuofan/xxx.sql'表示 需要被load的sql文本的绝对路径
# 其中，'tb_user'表示 你要load的数据到哪儿个表中的表格！
```

![image-20220903230559256](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220903230559256.png)



```mysql
# 登录上mysql服务器，然后在itheima这个数据库中添加如下表格：
CREATE TABLE `tb_user4` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `username` VARCHAR(50) NOT NULL,
  `password` VARCHAR(50) NOT NULL,
  `name` VARCHAR(20) NOT NULL,
  `birthday` DATE DEFAULT NULL,
  `sex` CHAR(1) DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `unique_user_username` (`username`)
) ENGINE=INNODB DEFAULT CHARSET=utf8 ;
# 然后使用load来加载大量数据：（前提是你把这份数据弄到你的服务器对应的路径上！我这里是/home/linzhuofan/load...）
```

![image-20220903232434410](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220903232434410.png)

### 主键优化

数据组织方式：在**InnoDB**存储引擎中，表数据都是根据主键**顺序**组织存放的，这种存储方式的表称为**索引组织表**（Index organized table, IOT）

若主键使用**乱序**插入的话，可能会造成**页分裂**的现象。而**页分裂**现象往往也会带着**页合并**现象。

**页分裂**：页可以为空，也可以填充一般，也可以填充100%，每个页包含了2-N行数据（如果一行数据过大，会行溢出），根据主键排列。
**页合并**：当删除一行记录时，实际上记录并没有被物理删除，只是记录被标记（flaged）为删除并且它的空间变得允许被其他记录声明使用。当页中删除的记录到达 MERGE_THRESHOLD（默认为页的50%），InnoDB会开始寻找最靠近的页（前或后）看看是否可以将这两个页合并以优化空间使用。

MERGE_THRESHOLD：是合并页的阈值，可以自己设置，在创建表或创建索引时指定

> 文字说明不够清晰明了，具体可以看视频里的PPT演示过程：https://www.bilibili.com/video/BV1Kr4y1i7ru?p=90

**主键设计原则**：

- 满足业务需求的情况下，尽量降低主键的长度（二级索引的叶子节点存储的是主键，若主键长度越大，则二级索引的叶子节点个数越多，此时遍历二级索引时耗时会变长，且检索数据时会耗费大量的磁盘IO）
- 插入数据时，尽量选择**顺序**插入，选择使用 **AUTO_INCREMENT** 自增主键
- 尽量不要使用 UUID 做主键或者是其他的自然主键，如身份证号（本身数据长度就大，so检索数据时会耗费大量的磁盘IO）
- 业务操作时，避免对主键的修改（因为若修改了主键，二级索引的数据结构会变化，这样代价很大！）

### order by优化（排序操作的优化）

例子：

![image-20220904165049533](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220904165049533.png)

![image-20220904165745212](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220904165745212.png)

在MYSQL中，有两种排序方式：

1. **Using filesort**：通过表的索引或全表扫描，读取满足条件的数据行，然后在排序缓冲区 sort buffer 中完成排序操作，所有不是通过索引直接返回排序结果的排序都叫 FileSort 排序
2. **Using index**：通过有序索引顺序扫描直接返回有序数据，这种情况即为 using index，不需要额外排序，操作效率高

如果order by字段**全部使用升序排序**或者**降序排序**，则**都会走索引**，但是如果一个字段升序排序，另一个字段降序排序，或反过来，则不会走索引，explain的extra信息显示的是`Using index, Using filesort`，如果要优化掉Using filesort，则需要另外再创建一个索引，如：`create index idx_user_age_phone_ad on tb_user(age asc, phone desc);`，此时使用`select id, age, phone from tb_user order by age asc, phone desc;`会全部走索引

总结：

- 根据排序字段建立合适的索引，多字段排序时，也遵循最左前缀法则

- 涉及到排序操作时，SQL的执行过程尽量优化为using index的。（通过EXPLAIN关键字可查看SQL语句的执行计划）

- 尽量使用覆盖索引（查询效率高）

- 多字段排序，一个升序一个降序，此时需要注意联合索引在创建时的规则（ASC/DESC）

- 如果不可避免出现filesort，大数据量排序时，可以适当增大排序缓冲区大小 sort_buffer_size（默认256k）

  ![image-20220904165947534](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220904165947534.png)

### group by优化（分组操作的优化）

- 在分组操作时，可以通过（建立适当的）索引来提高效率
- 分组操作时，索引的使用也是要满足最左前缀法则的

特殊case：如索引为`idx_user_pro_age_stat`，则这个SQL语句`EXPLAIN SELECT profession,age,count(*) from tb_user3 WHERE profession = '软件工程' GROUP BY age;`，这样也是符合最左前缀法则的。

![image-20220904215236461](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220904215236461.png)

其中，using temporary 是用到了临时表，性能是比较低的！

![image-20220904215745113](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220904215745113.png)

using index 则性能比较高！

![image-20220904215706420](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220904215706420.png)



### limit优化（分页查询的优化）

常见的问题如`limit 2000000, 10`，此时需要 MySQL 排序前2000000条记录，但仅仅返回2000000 - 2000010的记录，其他记录丢弃，查询排序的代价非常大。
优化方案：一般分页查询时，通过创建**覆盖索引**能够比较好地提高性能，可以通过覆盖索引加子查询形式进行优化

例如：

```mysql
-- 此语句耗时很长
select * from tb_sku limit 9000000, 10;
-- 通过覆盖索引加快速度，直接通过主键索引进行排序及查询
select id from tb_sku order by id limit 9000000, 10;
-- 下面的语句是错误的，因为 MySQL 不支持 in 里面使用 limit
-- select * from tb_sku where id in (select id from tb_sku order by id limit 9000000, 10);
-- 通过连表查询即可实现第一句的效果，并且能达到第二句的速度
select s.* from tb_sku as s, (select id from tb_sku order by id limit 9000000, 10) as a where s.id = a.id;
```

### count优化

在大数据量case下count操作是比较耗时的，这是由存储引擎来决定的！

MyISAM 引擎把一个表的总行数存在了磁盘上，因此执行 count(\*) 的时候会直接返回这个数，效率很高（前提该查询语句没使用where）；
InnoDB 在执行 count(\*) 时，需要把数据一行一行地从引擎里面读出来，然后累计计数。
优化方案：自己计数，如创建key-value表存储在内存或硬盘，或者是用redis

count的几种用法：(count本身是一个聚合函数，是用来求取符合条件的总数据量的)

- 如果count函数的参数（count里面写的那个字段）不是NULL（字段值不为NULL），累计值就加一，否则不加一，最后返回累计值
- 用法：count(\*)、count(主键)、count(字段)、count(1)
- count(主键)跟count(\*)一样，因为主键不能为空；count(字段)只计算字段值不为NULL的行；count(1)引擎会为每行添加一个1，然后就count这个1，返回结果也跟count(\*)一样；count(null)返回0

各种用法的性能：

- count(主键)：InnoDB引擎会遍历整张表，把每行的主键id值都取出来，返回给服务层，服务层拿到主键后，直接按行进行累加（主键不可能为空）
- count(字段)：没有not null约束的话，InnoDB引擎会遍历整张表把每一行的字段值都取出来，返回给服务层，服务层判断是否为null，不为null，计数累加；有not null约束的话，InnoDB引擎会遍历整张表把每一行的字段值都取出来，返回给服务层，直接按行进行累加
- count(1)：InnoDB 引擎遍历整张表，但不取值。服务层对于返回的每一层，放一个数字 1 进去，直接按行进行累加
- count(\*)：InnoDB 引擎并不会把全部字段取出来，而是专门做了优化，不取值，服务层直接按行进行累加

按效率排序：count(字段) < count(主键) < count(1) < count(\*)，所以当求取总数据记录数时应**尽量使用 count(\*)**

### update优化（避免行锁升级为表锁）

**InnoDB 的行锁**是针对**索引**加的锁，而不是针对记录加的锁，并且该索引不能失效，否则会从行锁升级为表锁。

==so我们在do Update操作时，尽量对有索引的字段 或 主键 进行Update！==这样的性能才好，效率才高！

若根据没有索引的字段来update某字段的数据，则行锁会升级为表锁，整张表都会锁住，你更新任一行数据都会锁住另一个MYSQL客户端更新该表其他数据的操作！（可以自己试试，按照B站视频里面的操作弄一次有索引的update和没有索引的update）也即一旦用没有索引的字段来doUpdate操作时，就会锁住整张表，从而造成**MYSQL客户端并发性==降低==**的局面。

如以下两条语句：
`update student set no = '123' where id = 1;`，这句由于id有主键索引，所以只会锁这一行；
`update student set no = '123' where name = 'test';`，这句由于name没有索引，所以会把整张表都锁住进行数据更新，解决方法是给name字段添加索引

### 章节总结：

![image-20220904232049976](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220904232049976.png)



对**==SQL的优化==**其实绝大部分情况下是在对**==索引==**进行优化！（so掌握好索引的优化也就deal了大部分的SQL优化的问题了！）



## 视图/存储过程/触发器

视图，存储过程和触发器称之为MYSQL数据库中的存储对象。

### 视图

#### 介绍

==**视图**（view）==是一种==**虚拟存在**==的==**表**==（也就是说：本质上视图也是表格！）。视图中的数据并不在数据库中实际存在，行和列数据来自视图的查询中使用的表，并且是在使用视图时动态生成的。

通俗的讲，视图只保存了查询的SQL逻辑，不保存查询的结果，所以我们在创建视图时，主要的工作就落在创建这条SQL查询语句上。即：视图不保存数据，数据都是保存在基表（创建视图的那张表格）中的。

#### 使用语法

- 创建

```mysql
create [or replace] view 视图名称[(列名列表)] as select查询语句 [with [cascaded | local] check option]
# or replace 关键字是当你需要去替换某个视图时 就可以使用了,但一般还是建议创建时带上把！
```

- 查询（查询视图时，视图可被当作一张表格那样，你怎么查别表格的，就怎么查视图即可了）

```mysql
# 查看创建视图语句：
show create view 视图名称;
# 查看视图数据：
select * from 视图名称 [条件语句];
```

- 修改（修改视图时，way1中的or replace 关键字是必须要带上的！）

```mysql
# way1:
create or replace view 视图名称[(列名列表)] as select查询语句 [with [cascaded | local] check option];
# way2:
alter view 视图名称[(列名列表)] as select语句 [with [cascaded | local] check option];
```

- 删除

```mysql
drop view [if exists] 视图名称;
```

- 例子

```mysql
# 创建
create or REPLACE VIEW v_1 as select id,name from tb_user3 where age <= 40;
# 查询
show create view v_1;
select * from v_1;
# 修改
create or REPLACE VIEW v_1 as select id,name,profession from tb_user3 where age <= 40;
alter view v_1 as select id,name from tb_user3 where age <= 40;
# 删除
drop VIEW if EXISTS v_1;
```



问题：既然视图是一张虚拟的表格，那么我往视图中插入数据记录时，效果如何呢？

答：

```mysql
# 用案例分析来回答这个问题
# 先基于一个学生表 创建一个视图
create or REPLACE view stu_v1 as select id,name from student WHERE id < 20;# id小于20才能插入数据记录进去！
# 用insert into 插入数据
insert into stu_v1 values(5,'Tom'),(6,'gary');# 这条插入语句执行完成后用select语句查看可以发现这2条记录出现在了视图和基表中。
insert into stu_v1 values(30,'Cherry');# 这条插入语句执行完成后用select语句查看可以发现这1条记录出现在了基表中，但是 并没有出现在视图中。
# 具体情况可自己在mysql客户端写一下代码即可！
```

为了防止上述情况发生，干脆在创建视图时，就添加检查选项with [cascaded | local] check option；这样do之后，插入数据记录到视图中时，就能防止插入一些不符合基本创建条件的数据记录了！

![image-20220907113229518](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220907113229518.png)



#### 视图的检查选项

若你在创建视图时不给视图加上这个检查选项，那么在你插入数据到这个视图后，该视图和其基表都不会检查应有的条件限制语句，这样是不行的！

当使用WITH CHECK OPTION 子句创建视图时，MYSQL会通过视图检查正在更改的每个行，例如：插入，更新，删除，以使其符合视图的定义（若不符合视图定义时的条件语句，则这些操作都会执行失败！）。MYSQL允许基于另一个视图来创建视图，它还会检查依赖视图中的规则以保持一致性。**为了确定检查的范围**，MYSQL提供了2个可选项：**CASCADED** 和 **LOCAL**，其中**默认值**为**CASCADED**。

##### CASCADED

cascaded中文是**级联**，表明，使用了该检查选项的话，那么当前视图以及其依赖的各个子视图（若有点话）在插入数据记录时都必须要检查其条件语句（各级条件语句都必须要同时满足了才能进行插入数据的操作，否则就是报错“check option failed!”）。

##### LOCAL

local中文是**本地**，表明，使用了该检查选项的话，那么当前视图也会递归地找其依赖的各个子视图（若有的话），在插入数据时，先判断当前视图的条件，然后递归到其子视图，若其子视图没有检查选项则不检查条件，若有检查选项就检查了条件再do是否插入的操作。这很明显和级联cascaded是不同的，对于级联检查选项来说，不论当前视图的子视图是否有检查选项语句，只要当前视图有cascaded检查选项，就必须要递归其all的子视图，当all的子视图的条件和当前视图的条件都满足的时候，才能够do插入数据的操作。



**注**：关于上面2种检查选项，文字说明可能不好理解，可观看视频（能==更好地理解why是这样的==）[B站对应位置处的视频](https://www.bilibili.com/video/BV1Kr4y1i7ru?p=99&spm_id_from=pageDriver&vd_source=b050ab0adaffa51f5ad24d77efa40057)



#### 视图的更新条件

并不是all的视图都能够进行增删改的操作的。是有条件的！

==若要使得视图**可更新**，视图中的行与基础表中的行之间必须存在**一对一**的关系==。如果视图包含以下任何一项，则该视图不可更新。

1. 聚合函数 或 窗口函数（SUM()、MIN()、MAX()、COUNT()等）

2. DISTINCT

3. GROUP BY

4. HAVING

5. UNION 或 UNION ALL

   例子：

<img src="C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/69.JPG" alt="69" style="zoom:80%;" />

![image-20220907143449211](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220907143449211.png)

![](C:/Users/11602/Desktop/MySQL%E5%AD%A6%E4%B9%A0/%E5%AD%A6%E4%B9%A0%E6%88%AA%E5%9B%BE/68.JPG)



#### 视图的作用

![image-20220907143825349](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220907143825349.png)



#### 案例（巩固练习视图操作）：

![image-20220907143929892](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220907143929892.png)

```mysql
# 注:以上这几个基表在前面知识点的介绍中已经有源码了，直接拿了创建这些表格即可！
# 需求1：
create or replace view 
 as SELECT id,name,profession,age,gender,status,createtime from tb_user3 with cascaded CHECK OPTION;

# 后续业务中直接操作该视图即可简化操作！
SELECT * from tb_user_v1;

# 需求2：
create or REPLACE view v2 as (SELECT c.`name` as '课程名字',s.`name` as '学生名字' from student_course sc ,student s,course c WHERE sc.studentid = s.id and sc.courseid = c.id) with CASCADED CHECK OPTION;

# 后续业务中直接操作该视图即可简化操作！
SELECT * from v2;
```



### **==从这里开始后面all的笔记我都记录在MySQL进阶篇对应的pdf上面了，用【pencil在ipad上写写画画一样的！】==**

### 存储过程



### 存储函数（可理解为SQL中的函数）



### 触发器



**总结：**

![image-20220913173431468](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220913173431468.png)



## 锁

![image-20220913173359316](C:/Users/11602/AppData/Roaming/Typora/typora-user-images/image-20220913173359316.png)

## InnoDB引擎



## MySQL管理







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