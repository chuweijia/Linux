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
  
  `telnet 127.0.0.1 6608` docker下查看端口的占用情况，127.0.0.1 表示docker中的浏览器访问地址！  
  
## docker创建容器  

 **docker 本地**

/Users/chuweijia/Workspace/etc/nginx/conf.d/  这里面是nginx的配置文件地址  
/Users/chuweijia/Workspace/etc/nginx／nginx.conf 这里可以启动nginx    


nginx -c/Users/chuweijia/Workspace/etc/nginx/nginx.conf (-s stop || -s reload)  
php-fpm -p /var -y/etc/php-fpm.conf   (-s stop || -s reload)

 **docker启nginx+php-fpm**  
   
 ```markdown    
     /etc/init.d/nginx start || restart 
     /etc/php-fpm.conf start 
 ```    
 
  **docker中nginx配置文件目录**  
   
 ```markdown    
      vi /etc/nginx/nginx.conf  
     最后一句：include ／etc／nginx／conf.d/*.conf 代表引入的实际生效的配置文件

     vi /etc/nginx／conf.d/00-default.conf 
     root是 全局根目录  ！！！
     index是 默认入口文件 ！！！
 ```   
 
 **docker中使用svn**  
   
 ```markdown    
    yum install svn   在docker内部安装svn，其中关系，npm～node，yum～linux  
    svn co path  其中要输入sina账号密码  
    etc/nginx/conf.d/00-default   其中在etc/nginx/conf.d下建access_log文件  
    启动nginx start  
    启动php-fpm start
    
 
     vi /etc/nginx/nginx.conf  
     最后一句：include ／etc／nginx／conf.d/*.conf 代表引入的实际生效的配置文件

     vi /etc/nginx／conf.d/00-default.conf 
     root是 全局根目录  ！！！
     index是 默认入口文件 ！！！
 ``` 
 
 
 
 
 ##本机docker的情况说明  
 docker server启动着（就是那个小鲸鱼），但电脑关闭了，docker镜像也会挂掉（即使deamon在 也会挂掉）  
 `docker ps -a`   如果显示exited，代表docker退出了  
 `docker start chu_docker`手动重启docker    
 
 

 
