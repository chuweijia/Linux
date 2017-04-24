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

 **docker启nginx+php-fpm**  
   
 ```markdown  
     /etc/init.d/nginx start || restart 
     /etc/php-fpm.conf start 
 ```   
 
  **docker中nginx配置文件目录**  
   
 ```markdown  
     vi /etc/nginx／nginx.conf  
     最后一句：include ／etc／nginx／conf.d/*.conf 代表引入的实际生效的配置文件

     vi /etc/nginx／conf.d/00-default.conf 
     root是 全局根目录  ！！！
     index是 默认入口文件 ！！！
 ```   
