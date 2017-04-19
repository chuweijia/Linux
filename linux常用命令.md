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
  
  
  
  
# svn命令  
  `svn co path`        checkout简写，用于将远程路径path，导出到本地  
  `svn add`            添加
  `svn ci`             commit简写，提交  
  `svn st`             status简写，状态  
  `svn info`           查看文件详细信息  
  `svn update`         更新 无后缀则更新全部  
  `svn delete`         删除  

  
  
