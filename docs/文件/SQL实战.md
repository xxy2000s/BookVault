### 基本操作

```mysql
/* Windows服务 */
-- 启动MySQL
    net start mysql
-- 创建Windows服务
    sc create mysql binPath= mysqld_bin_path(注意：等号与值之间有空格)
/* 连接与断开服务器 */
	mysql -h 地址 -P 端口 -u 用户名 -p 密码
	SHOW PROCESSLIST -- 显示哪些线程正在运行
	SHOW VARIABLES -- 显示系统变量信息
```



### 数据库操作

```mysql
/* 数据库操作 */ ---------------------
-- 查看当前有哪些数据库
	show databases;
-- 查看当前数据库
	select database();   -- ··select 一般都是操作函数 类似的如下：
	-- 显示当前时间、用户、数据库版本
	select now(); select user(); select version();
-- 建立一个数据库
	create database [if not exists] nba charset=utf8;
-- 查看当前库的创建信息
	show create database nbateam;
-- 删除库
	drop database [if exists] nbateam;
-- 选取数据库
	use nbateam;
	
```



### 表的操作

```mysql
/* 表操作 */
-- 查看当前数据库下有哪些表
	show tables;
-- 建立一个表
	create [temporary] table [if not exists] [库名.]GSW(表的结构定义) [表选项]
	-- 实例
	create table GSW
	(id int unsigned not null primary key auto_increment,
     name varchar(30) not null,
     age tinyint unsigned not null,
     num int unsigned not null,
     position varchar(3) not null,
     high int unsigned not null,
     weight int unsigned not null,
     birthday date default '2000-01-01',
     salary int unsigned not null,
     is_old bit default 1
    );
    
-- 表选项
	-- 字符集
		charset=utf8(默认latin)
	-- 存储引擎
		engine=InnoDB
		表在管理数据时采用的不同的数据结构，结构不同会导致处理方式、提供的特性操作等不同
        常见的引擎：InnoDB MyISAM Memory/Heap BDB Merge Example CSV MaxDB       					Archive
        不同的引擎在保存表的结构和数据时采用不同的方式
        MyISAM表文件含义：.frm表定义，.MYD表数据，.MYI表索引
        InnoDB表文件含义：.frm表定义，表空间数据和日志文件
        SHOW ENGINES -- 显示存储引擎的状态信息
        SHOW ENGINE 引擎名 {LOGS|STATUS} -- 显示存储引擎的日志或状态信息
		
	-- 自增起始数
		auto_increment = 行数
	-- 数据文件目录
		data directory = '目录'
	-- 索引文件目录
	 	index directory = '目录'
	-- 表注释
		comment = 'string'
	-- 分区选项
		partition by ....(见手册)
		
		
-- 查看表 
	show tables[like 'pattern'];
	show tables from 库名；
-- 查看表机构
	show create table 表名
	desc 表名 / describe ·· / explain ·· / show columns from ··[like 				'pattern']
	show table status [from db_name] [like 'pattern']
-- 修改表   修改表都是alter table
	-- 修改表本身的选项
		alter table ·· 表的选项
		eg: alter table ·· engine=myisam;
	-- 添加字段
		alter table ·· add 列名 类型
	-- 修改字段：不重命名
		alter table ·· modify 列名 类型及约束
	-- 修改字段段：重命名
		alter table ·· change 原名 新名 类型及约束
    -- 删除字段
    	alter table ·· drop 字段名
	-- 对表进行重命名
		rename table ·· to 新表名
		rename table ·· to 库名.表名 (将表移动到另一个数据库)
		-- rename 可以交换两个表名
		
		
		
-- 删除表
	drop table [if exists] ··
-- 清空表数据
	truncate [table] ··
-- 复制表结构
	create table 新表 like ··
-- 复制表结构和数据
	create table 新表 [as] select * from 要复制的表名 
	
-- 检查表是否有错误
    CHECK TABLE tbl_name [, tbl_name] ... [option] ...
-- 优化表
    OPTIMIZE [LOCAL | NO_WRITE_TO_BINLOG] TABLE tbl_name [, tbl_name] ...
-- 修复表
    REPAIR [LOCAL | NO_WRITE_TO_BINLOG] TABLE tbl_name [, tbl_name] ... [QUICK] [EXTENDED] [USE_FRM]
-- 分析表
    ANALYZE [LOCAL | NO_WRITE_TO_BINLOG] TABLE tbl_name [, tbl_name] ...	
		
		
```



### 数据操作

```mysql
/* 数据操作 */
-- 增
	insert [into] ·· [(字段列表)] values (值列表)[, (值列表)， ...] 
		-- replace 和 insert 完全一致，可互换
	insert [into] ·· set 字段名=值[, 字段名=值， ...]
-- 查
	  SELECT 字段列表 FROM 表名[ 其他子句]
        -- 可来自多个表的多个字段
        -- 其他子句可以不使用
        -- 字段列表可以用*代替，表示所有字段
-- 删
	delete from 表名[其他子句]
		如无条件子句，则全部删除
-- 改
	update ·· set 字段名=新值[, 字段名=新值...] [更新条件]
	
-- 数据实例
	insert into GSW values 
	(0,'Stephen_Curry',31,30,'PG',191,190,'1988-3-14',4023,1),
	(0,'Klay_Thompson',29,11,'SG',201,215,'1990-02-08',3274,1),
	(0,"D'Angelo_Russell",23,7,'PG',196,195,'1996-02-23',2728,0),
	(0,'Draymond_Green',29,23,'SF',201,230,'1990-03-04',1854,1),
	(0,'Willie_Cauley_Stein',26,0,'C',213,240,'1993-08-18',470,0),
	(0,'Kevon_Looney',23,5,'C',206,220,'1996-02-06',462,1),
	(0,'Alec_Burks',28,35,'SG',198,214,'1991-07-20',232,0),
	(0,'Jordan_Poole',20,3,'PG',196,194,'1999-06-19',196,0),
	(0,'Jacob_Evans',22,10,'PG',198,210,'1997-6-18',192,0),
	(0,'Omari_Spellman',22,21,'SF',206,245,'1997-07-21',190,0),
	(0,'Glenn_Robinson',25,22,'SF',198,222,'1994-01-08',188,0),
	(0,'Alfonzo_Mckinnie',27,28,'SF',203,215,'1992-09-17',142,1),
	(0,'Alen_Smailagic',19,6,'PF',208,216,'2000-08-18',89,0),
	(0,'Marcus_Derrickson',23,32,'SF',201,249,'1996-02-01',7,0),
	(0,'Damion_Lee',27,1,'SG',198,210,'1992-10-21',7,1),
	(0,'Xuyang_Xia',18,21,'SG',180,148,'2000-10-04',0,0);
	
	
-- 数据备份
	mysqldump -uroot -p 数据库名 >(重定向符，导入数据) python.slq;
	
-- 数据恢复
	连接mysql，创建新的数据库
	退出连接，执行如下命令
	mysql -uroot -p 新数据库库名 < python.sql;
```



#### 查询专题

```mysql
-- 条件查询
	-- 逻辑运算符  (and, or, not)
-- 模糊查询	
	-- like
	-- %替换一个或多个（0个也行）
	-- _替换一个
	
	-- rlike 正则
-- 范围查询
	-- (in, not in, between ... and, not between ... and )
	select age from GSW where age [not] in (34,32,23)
	select age from GSW where age [not] between 18 and 28
-- 空判断
	-- is null, is not null
	
-- 排序
	-- order by 字段(多个字段)
	-- asc 升序(默认)
	-- desc 降序
	
-- 聚合函数
	-- 总数count
	-- max
	-- min
	-- avg
	-- sum
	-- round
	
-- 分组(和聚合函数一起使用)
	-- group by
		-- eg:select position, count(*) from GSW group by position;
			group by 后面的字段为区分依据，在select后面只能接该字段
	-- group_concat()  (括号里面为想查询的字段信息) 
		-- 查看组（表）里信息
	-- having
		-- 在新查询的表出来后，having后为附加条件，同where的筛选功能
			having 的附加条件必须为新表的字段
			
-- 分页
	-- limit start, count (必须为数，不可以为表达式)
		(0,n) (n,n) (2n,n)....
		#limit 必须在语句最后	
		
-- 链接查询（多个表合并数据）
	-- inner join ... on
		select * from GSW inner join status;  
		不用on条件的话会出现重复数据，无法对应
		-- 查询
		select * from GSW as g inner join status as s on g.play_id=s.id; 
		select g.*, s.name from GSW as g inner join status as s on g.play_id 				=s.id;
	-- left join
		select * from GSW as g left join status as s on g.play_id=s.id;
		以左表为基准，没有对应的值则为null
	-- 自连接
		把一个表用两个别名当两个表用
```



### 视图

```mysql
-- 创建一个视图
	create view 视图名(最好以v开头) as select 语句
	视图是一个虚拟的表，查询用，用时则执行相应的sql语句
	查看只需select * from 视图名
	eg: create view v_GSW_old as select * from GSW where is_old=1;
-- 删除视图
	drop view 视图名
```



### 事务

```mysql
-- 四大特性(ACID)
	-- 原子性(Atomicity)
	-- 一致性(Consistency)
	-- 隔离性(Isolation)
	-- 持久性(Durability)
	
-- 开启事务
	begin 或 start transaction;
	
-- 提交事务
	commit；
-- 回滚事务
	rollback；
```



### 索引

```mysql
-- 查看索引
	show index from 表名

-- 建立索引
	create index 索引名 on 表名(字段名称(长度))
	如果指定字段是字符串，则需指定长度，建议一致
	若不是，则不需要
	eg:create index player_search on GSW(name(30));
	
-- 删除索引
	drop index 索引名称 on 表名
	
	
-- 查询
	-- 开启运行时间监测
		set profiling=1;
	-- 查看执行时间
		show profiles;
```



### 账户管理

```mysql
-- 创建用户
	先root账户登录，再创建
	grant 权限列表 on 数据库 to '用户名'@'访问主机' identified by '密码';
	
-- 查看用户有哪些权限
	show grants for 用户名@访问主机
-- 修改权限
	grant 权限名称 on 数据库 to 账户@主机 with grant option;
	之后刷新权限 flush privileges 使权限生效
	
-- 修改密码
	使用root登录，修改mysql数据库中的user表
	-- 使用password()函数加密
	update user set authentication_string=password('新密码') where user='用户名'
	之后刷新权限 flush privileges
-- 删除用户
	drop user '用户名'@'主机[如(%)]';
	
-- 远程连接慎用，用时再查资料
```



### 主从数据库

```mysql

```



### Python与数据库交互

```python
from pymysql import *

def main():

        #创建Connection连接
        conn =  Connect(host='localhost',port=3306,user='root',\
    	        password='x1048844361',database='nbateam',charset='utf8')
        #获得cursor对象
        cs1 = conn.cursor()
        #执行select语句，并返回受影响的行数：查询一条数据
        #execute会返回生效行数
        count = cs1.execute('select id,name from GSW where is_old=1')
        #打印受影响的行数
        print('查询到%d条数据:' % count)

        for i in range(count):
                #获取查询结果
                #fetchall() fetchmany(数量) fetchone() 返回元组
                #游标自动移动
                result = cs1.fetchone()
                #打印查询的结果 
                print(result)

        #关闭cursor对象
        #conn先开后关
        cs1.close()
        conn.close()

if __name__ == '__main__':
        main()

```

