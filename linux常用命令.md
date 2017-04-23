# brew命令  
  `brew install mysql` brew 安装   
  `brew list`          brew 查看已安装  
  
  
# linux命令  
  `pwd`                Print Working Directory 查看当前操作路径  
  `ls`                 list 查看    
  `mv`                 移动，移动原点为当前目录，eg：`mv itermout ../` ,移动到上一级目录,  `tab键补全`  
  `mkdir`              新建文件夹  
  `rm`                 删除 指定文件 
  `rm -r`              删除 文件夹   
  `history`            历史命令记录   
  `which node`         安装node的绝对路径  
  `cd /etc`            命令行中直接进入到etc  触发原点为～
  `source ./profile`   更改完profile后，使之生效，但是会使环境变量重复，但是没关系。。
  
  `sudo su`            su，super user系统管理员    
  `ps -ef`             ps，process status，进程状态。-ef，显示所有信息包括命令行。权限是`所有人`  
  `ps -ef|grep nginx`  grep，global regular expression print，全局正则表达式，nginx，即可`指定打印某一项`进程的信息  
                  
  `nginx -c /Users/chuweijia/Workspace/etc/nginx/nginx.conf`  通过上述获取到`服务码`，再去启动nginx命令  
  `nginx -c /Users/chuweijia/Workspace/etc/nginx/nginx.conf -s stop`  关闭   
  `echo $PATH`   打印环境变量  
  `open .bash_profile`   新窗口打开  
  `cat .bash_profile`    终端打开  
  `/usr/local/bin`       存放了 brew  
  `/usr/local/Cellar`    存放了 brew install的文件  
  
  `ps -ef`               查看当前进程  
  `ps -ef > log.txtx`    将显示完全的内容，存入到txt文件中   
  
  
  
  
# svn命令  
  `svn co path`        checkout简写，用于将远程路径path，导出到本地  
  `svn add`            添加
  `svn ci`             commit简写，提交  
  `svn st`             status简写，状态  
  `svn info`           查看文件详细信息  
  `svn update`         更新 无后缀则更新全部  
  `svn delete`         删除  


# mysql指令
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
    
## mysql本地环境搭建  
  
  下载`mysql-server`，一种mysql的驱动服务  
  `mysqld`           启动服务  
  `mysql -u root -p` 以root权限，登陆mysql，即输入`root@localhost`的密码!!  
  `show databases`   
  报错：you must reset password using alter user...   
  解释：表示进入库中，需要先`增加一列`，为`用户`   
  解决：如下，重置密码，保存，退出重登  
  
```markdown   
mysql>  SET PASSWORD = PASSWORD('chu030224');
mysql>  ALTER USER 'root'@'localhost' PASSWORD EXPIPE NEVER;
mysql>  FLUSH PRIVILEGES; 
mysql>  quit;
** 退出，重新以新密码进入  **  
```  
  
  


   
  
# docker命令  
  `docker info`     docker的信息  
  `docker ps -a`    镜像的进程 所有更新的用户信息  
  `docker images`   docker中所有镜像  
  `docker ps -a`    镜像的进程 所有更新的用户信息 
  `docker run`      启动一个指令在一个新容器中 且运行`指定命令`  
  `-d`              deamon 守护进程，后台运行  
  `-e`              enviroment  环境变量 
  `-p`              指定端口映射，可绑定多个端口  
  `-P`              随机映射一个49000～49900 的端口  
  `-v`              指定文件夹映射  宿主机（默认是`/tmp/registry`）：docker机  
  `--name`          指定了启动后的容器名字  
  `-t`              让docker分配一个伪终端  
  `-i`              使容器的标准输入打开    
  
  `sudo docker ps -a|grep 端口号`       在宿主机中，查看指定端口号的docker的进程状态，docker命令`仅在宿主机中`存在，在docker容器内部不存在  
  `sudo docker exec -it 容器名 bash`    进入到指定容器名的docker   
  
  
  
  
  


  
