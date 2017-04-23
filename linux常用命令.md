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
  `ps -ef > log.txtx`    将显示`完全`的内容，存入到txt文件中  
  `shift+gg`             查看`完全 `  
  `vi log.txtx || cat log.txtx`  查看上步的文件  
  
   **本地启nginx+php-fpm**  
   
 ```markdown  
     nginx -c/Users/chuweijia/Workspace/etc/nginx/nginx.conf 
     php-fpm -p /var -y/etc/php-fpm.conf  
 ``` 
  
  **ps后，进程各个属性说明**  
  
 ```markdown  
     uid,   用户id
     pid,   子进程  
     ppid,  父进程  
     tty,   终端设备的统称（teletypes）
     time,  进程占用cpu的时间
     C,     进程生命周期cpu利用率
 ```  
 
   **常用端口号**  
  
 ```markdown  
     3306，数据库  
     9000，php-fpm  
     6379,redis  
     8080,浏览器  
     (docker中由于没有浏览器，则在本地输入 10.xx.13.xx : 6608,端口对接方式为：6608->80 即docker启端口6608对接浏览器的80端口)
     以上所有端口也适用于本地和**docker** 
 ```  
  `ifconfig`             类似于window下的`ipconfig`，可以查到本机各信息  
  
  
# svn命令  
  `svn co path`        checkout简写，用于将远程路径path，导出到本地  
  `svn add`            添加
  `svn ci`             commit简写，提交  
  `svn st`             status简写，状态  
  `svn info`           查看文件详细信息  
  `svn update`         更新 无后缀则更新全部  
  `svn delete`         删除  
  
