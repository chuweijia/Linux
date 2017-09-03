# brew命令  
  `brew install mysql` brew 安装   
  `brew list`          brew 查看已安装  
  
  
# linux命令  
  `pwd`                Print Working Directory 查看当前操作路径  
  `ls`                 list 查看    
  `mv`                 移动，移动原点为当前目录，eg：`mv itermout ../` ,移动到上一级目录,  `tab键补全`  
  `mkdir`              新建文件夹  
  `rm`                 删除 指定文件 
  `rm -r`              删除 文件夹 递归  
  `rm -f`              强制性  
  `rm -i`              询问要删除的文件(夹)  
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
  
  
  `cat /etc/issue`             直接查看
  `cat -A /etc/issue`          完整显示
  `cat -n /etc/issue`          会打印行号
  
  `./nginx` 代表相对路径，指当前路径下的nginx，比如cd ./chu === cd chu，docker上得进入到`sbin`下  
  `User` 用户  
  `Group` 用户组
  `Others` 其他人  
  `chgrp users test.log`             改变文件所属用户组  
  `chgrp -R users 文件夹`             改变文件夹所属用户组  
  `chown [-R] 账号名称 文件或目录`      改变文件所属拥有者  
  
  
  `alias ll='ls -l'`     改ls命令为ll  有个空格    
  `ipconfig`  10.xxx开头的，是本机host，且浏览器输入curl访问的是本机的host！！你在服务器上curl就是服务器的host！  
  `vi /etc/hosts ` 配置host文件（本机、远程服务器），原来配置的147，会覆盖掉我线上的环境，记住！  
  `vi /etc/sudoers   加一行，wq!  保存退出 `   45上开sudo权限，让有权限的人以此方法登录并操作。     
  `head -n 10 mysql_read_debug.log`  只打印出10条  
  `du -sh * `  按文件大小查看文件（所有）  
  
   
  
  
  
  
  
  
   **本地启nginx+php-fpm**  
   
 ```markdown  
     nginx -c/Users/chuweijia/Workspace/etc/nginx/nginx.conf (-s stop || -s reload)
     php-fpm -p /var -y/etc/php-fpm.conf   (-s stop || -s reload)
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
  `svn cp old_url new_url -m "chu"`              这样写，即新建一个文件夹      
  `svn log -l 10`      查看svn的版本号，并且limit 10行  
  `svn merge -r 当前版本号:目标版本号 query.php`  回滚指定文件（就是query.php这项必须写！！，然后再svn ci -m ""）   
  
  svn 的几种状态   
  
      
        M     svn待commit  ，change了但未commit  
        ！    rm -rf 文件夹    ，是已删除的（或者重命名后即废弃的文件）  
        ？    no add  （未add 可能是重命名过了）  
        A     add了，但未commit 
        D     dele了，但未commit  
        svn up chu.php (更新指定文件，不会冲掉其他的！！！上线时候注意)  

           

 `svn mkdir url/newdir -m "chu"`         新建svn文件夹      
 `svn mv url1 url2`移动文件夹，必须得是svn mv，，你自己在本地mv没用（且还会报错）   
 `ls -al`  在文件夹下会有一个隐藏文件.svn 当出问题的时候可以del it  
 
 
 
 
 
 
   
   
  
# vim使用  
  `i`                  编辑模式  
  `esc（或ctrl+c）`     一般模式  
  `／`                 命令行模式，光标进入到最后一行，可以`搜索`，并`回车定位`  
  `ctrl+d/n`           半页移动  
  `ctrl+f/b`           整页移动  
  `u`                  反悔   
  `／+G`               从头预览  
  `ctrl+d/n`           半页移动  
  `$`                  跳到行尾
  `(`  `)`             跳到行首、尾
  `dw`                 删除当前光标的 右边的字母  
  `:set nu`            查看行标  
  
  
  
# vue  

`npm run dev`          本地调试  
`npm run build`        打包，会生成index.html  和一堆js文件，把这些推到服务器上  

  
  
