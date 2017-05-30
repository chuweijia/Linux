# mysql指令  
  `mysqladmin -u root -p create chuDB`   `root`权限下，创建`数据库`  
  `create databases chuDB`                创建`数据库`  
   
  `show databases`     展示所有的数据库    
  `use chu`            使用指定的数据库    
  `show tables`        展示所有的数据表  
  `alter table 表名 add 列名 int(1) NOT NULL DEFAULT'0' COMMENT'0=未执行，1=已执行'`;    增加key（表的列）和key的属性    
  `alter table 表名 add KEY keyname(列名1，列名2，列名n)`;                               KEY与index 同级不同意义 也非primarykey..  
  `show create table test` ||  `desc test`    用于展示数据表的`索引`的格式  
  `select * from 表名`                         展示数据表中内容  
  `select * from 表名\G`                       展示数据表中内容  整洁版    
  `update 表名A set k1=v1,k2=v2 WHERE K3=V3 and K4=V4`     更新数据表 含条件  
  `insert into 表名B(k1,k2) VALUES(v1,v2),(v3,v4)`         数据表中插值  `多条`   
  `insert into 表名B set k1=v1,k2=v2;`                     数据表中插值  `单条`    
  `delete from 表名;`                                      删除表内的数据  
  `drop 表名;`                                             删除表  
  `/.env;`                                                项目下的数据库配置路径  
## mysql本地环境搭建  
 
  下载`mysql-server`，一种mysql的驱动服务  
  `mysqld`           启动服务  
  `mysql -u root -p` 以root权限，登陆mysql，即输入`root@localhost`的密码!! （chu030224）
  `show databases`   
  报错：you must reset password using alter user...   
  解释：表示进入库中，需要先`增加一列`，为`用户`   
  解决：如下，重置密码，保存，退出重登  
  
```markdown   
    mysql>  SET PASSWORD = PASSWORD('chu030224');
    mysql>  ALTER USER 'root'@'localhost' PASSWORD EXPIPE NEVER;
    mysql>  FLUSH PRIVILEGES; 
    mysql>  quit;
    **退出，重新以新密码进入**  
```  

或者  

```markdown    
    mysql>  use mysql;
    mysql>  create user 'chuweijia_user'@'%' IDENTIFIED BY '123456';
    mysql>  GRANT ALL ON chuweijia_db.* TO ''@'%' identified by "123456" with grant option; 
    mysql>  flush privileges;
    mysql>  quit;
    **退出，重新以新密码进入**  
```    

## sql shell  
    
   select * from tablename where cust_budget `in` ('a','b'); 注意in的使用  
   select distinct name from tablename ;对列去重  
   select username from user limit 4,10;其中4表示索引位置，10表示条数。表示查询5～14 共10条  
   select a.ad_id,c.cust_id from cust_tmp c `left join` ad_tmp a `on` c.cust_id = a.ad_id; 起别名并联表查询  
   select cust_id `as` custd ,sum(ad_budget) from ad_tmp `group by` cust_id; 按同名查询  
   
   `insert into` tablename set date = '2017';初次插值  
   `update` tablename set date = '2018' where cust_id = 8;非初次插值  
   `truncate` table tablename;清空表格数据  
   `primary key` 主键：不可有重复；多个，称为复合主键，当所有字段不同时 才认为这行不同  
   
   alter table camp_tmp `change` `camp_budget camp_budget` decimal(5,6),not null,default '0',comment '注释';改变某列值 全写上    
   
   if(exp1,exp2,exp3); exp是`表达式`，当exp1为true时，执行exp2否则3  
   
## mysql_query

   mysql_query(query,connection);其中前者（sql查询）必选，后者（规定sql连接标识符）可选（若无则使用上一个打开的连接）  
   $result = mysql_query($query,$connect);
   while($row = mysql_fetch_array($result,MYSQL_ASSOC));以关联数组输出 ，应用于输出多行结果  
   
   
 
   
   
