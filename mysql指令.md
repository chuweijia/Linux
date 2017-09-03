# mysql指令  
  `mysqladmin -u root -p create chuDB`   `root`权限下，创建`数据库`  
  `CREATE DATABASE chuDB`                创建`数据库`  大小写敏感  
  `show databases`     展示所有的数据库    
  `use chu`            使用指定的数据库    
  `show tables`        展示所有的数据表  
  `alter table 表名 add 列名 int(1) NOT NULL DEFAULT'0' COMMENT'0=未执行，1=已执行'`;    增加key（表的列）和key的属性    
  `alter table 表名 add KEY keyname(列名1，列名2，列名n)`;                               KEY可以加快查询速度，不会影响插值  
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
   
   select pv from report_feed where order_id  = 3541311 
   and `UNIX_TIMESTAMP`(update_time)>1494158400
   and UNIX_TIMESTAMP(update_time)< 1494158400
   
   `insert into` tablename set date = '2017';初次插值  
   `update` tablename set date = '2018' where cust_id = 8;非初次插值  
   `truncate` table tablename;清空表格数据  
   `primary key` 主键：不可有重复；多个，称为复合主键，当所有字段不同时 才认为这行不同  
   
   alter table camp_tmp `change` `camp_budget camp_budget` decimal(5,6),not null,default '0',comment '注释';改变某列值 全写上    
   
   if(exp1,exp2,exp3); exp是`表达式`，当exp1为true时，执行exp2否则3  
   ```  
      create use `faraday` @ '%' IDENTIFIED BY '123456'  
      这里的 % 是通配符，使用户可以在任何远程主机上访问（数据库用户建立成功的前提下）。
      扩展知识：10.39.% 表示可以在任意前缀为10.39的机器上访问
   ```    
   
   
   
 
   
## mysql_query

   mysql_query(query,connection);其中前者（sql查询）必选，后者（规定sql连接标识符）可选（若无则使用上一个打开的连接）  
   $result = mysql_query($query,$connect);
   while($row = mysql_fetch_array($result,MYSQL_ASSOC));以关联数组输出 ，应用于输出多行结果    
   
   mysql 查询的语句，尽量不用联表方式查询，改为用php逻辑处理。
   
   
 
## mysql清理数据  
  
 现象：mysqld 查看cpu占用率高，删除某个表总是失败  
 解决（无效）：netstat -anp |grep 3306|grep ESTABLISHED //断开所有网络连接  || 删除过大的表  
 解决：show processlist;  // 查看当前进程  
      SELECT id FROM information_schema.processlist WHERE user='parse'; //parse为登陆的用户名  
      SELECT concat('Kill ',id,';') FROM information_schema.processlist WHERE user='parse';//手动执行kill id即可删除  
 原因：sql语句过长，导致在mysql中无法执行也无法退出，僵死挂起，导致占用cpu过高  
 
 
 
 `set global wait_timeout=120;` 数据库超时时间，若超时，给php返回false  
 `ps -ef|grep php|grep auto| awk '{print $2}'|xargs kill -9`   
 $2（表示第2列,即进程号PID）  
 kill -9(强杀进程)  
 xargs （使用上一个操作的结果作为下一个命令的参数使用）    
 
 
 ## mysql 导出数据  
 1. 本地启mysql，导出数据到本地  
 `mysql -hxx -uxx -pxx -e "select * from xx;" > /User/xx/log.txt`  确认本地能访问这个mysql  
 
 2. docker上启mysql，导出数据到本地    
 `mysql -hxx -uxx -pxx -e "select * from xx;" > /xx/log.txt`       在服务器上把结果导出到docker某处   
 `nc 10.236.30.24 1234 < sql.txt`   此步骤在docker上操作，目的是与本地建立连接。（ `/sbin/ifconfig`可以查看ip和端口号（我记得是本地的））  
 
 
 `nc -l 1234 > sql.txt`   此步骤在本地执行，目的是呼应上一步，最终sql.txt就在本地被导出了，也可以用rsync实现。（1234就是本地默认的端口号） 
 
 
 ## mysql常见报错  
 `mysql server has gone away` 连接超时，mysql服务挂了。解决方案，手动重连n次，for循环。  
 
 
 
 
 
 
 
 

 
 
 
 
   
