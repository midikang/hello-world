
docker command
========
$docker-machine

Commands:
  active		Print which machine is active
  config		Print the connection config for machine
  create		Create a machine
  env			Display the commands to set up the environment for the Docker client
  inspect		Inspect information about a machine
  ip			Get the IP address of a machine
  kill			Kill a machine
  ls			List machines
  regenerate-certs	Regenerate TLS Certificates for a machine
  restart		Restart a machine
  rm			Remove a machine
  ssh			Log into or run a command on a machine with SSH.
  scp			Copy files between machines
  start			Start a machine
  status		Get the status of a machine
  stop			Stop a machine
  upgrade		Upgrade a machine to the latest version of Docker
  url			Get the URL of a machine
  version		Show the Docker Machine version information
  help			Shows a list of commands or help for one command
  
  
  












  http://www.blogjava.net/yongboy/archive/2013/12/12/407498.html
  
  
  
Docker安装完毕，后台进程也自动启动了，可以安装虚拟机实例（这里直接拿官方演示使用的learn/tutorial镜像为例）：

  docker pull learn/tutorial
安装完成之后，看看效果

  docker run learn/tutorial /bin/echo hello world
交互式进入新安装的虚拟机中

  docker run -i -t learn/tutorial /bin/bash
会看到：

  root@51774a81beb3:/# 
说明已经进入交互式环境。

安装SSH终端服务器，便于我们外部使用SSH客户端登陆访问

  apt-get update
  apt-get install openssh-server
  which sshd
  /usr/sbin/sshd
  mkdir /var/run/sshd
  passwd #输入用户密码，我这里设置为123456，便于SSH客户端登陆使用
  exit #退出
获取到刚才操作的实例容器ID

  #docker ps -l
CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
51774a81beb3 learn/tutorial:latest /bin/bash 3 minutes ago Exit 0 thirsty_pasteur
可以看到当前操作的容器ID为：51774a81beb3。注意了，一旦进行所有操作，都需要提交保存，便于SSH登陆使用：

  docker commit 51774a81beb3 learn/tutorial
以后台进程方式长期运行此镜像实例：

  docker run -d -p 22 -p 80:8080 learn/tutorial /usr/sbin/sshd -D
ubuntu容器内运行着的SSH Server占用22端口，-p 22进行指定。-p 80:8080 指的是，我们ubuntu将会以8080端口运行tomcat，但对外（容器外）映射的端口为80。

这时，查看一下，是否成功运行。

#docker ps
CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
871769a4f5ea learn/tutorial:latest /usr/sbin/sshd -D About a minute ago Up About a minute 0.0.0.0:49154->22/tcp, 0.0.0.0:80->8080/tcp focused_poincare
注意这里的分配随机的SSH连接端口号为49154：

ssh root@127.0.0.1 -p 49154
输入可以口令，是不是可以进入了？你一旦控制了SSH，剩下的事情就很简单了，安装JDK，安装tomcat等，随你所愿了。以下为安装脚本：

  # 在ubuntu 12.04上安装oracle jdk 7
  apt-get install python-software-properties
  add-apt-repository ppa:webupd8team/java
  apt-get update
  apt-get install -y wget
  apt-get install oracle-java7-installer
  java -version
  # 下载tomcat 7.0.47
  wget http://mirror.bit.edu.cn/apache/tomcat/tomcat-7/v7.0.47/bin/apache-tomcat-7.0.47.tar.gz
  # 解压，运行
  tar xvf apache-tomcat-7.0.47.tar.gz
  cd apache-tomcat-7.0.47
  bin/startup.sh
默认情况下，tomcat会占用8080端口，刚才在启动镜像实例的时候，指定了 -p 80:8080，ubuntu镜像实例/容器，开放8080端口，映射到宿主机端口就是80。知道宿主机IP地址，那就可以自由访问了。在宿主机上，通过curl测试一下即可：

curl http://192.168.190.131  
  
  
  https://docs.docker.com/engine/userguide/basics/#running-an-interactive-shell
  
  https://docs.docker.com/engine/userguide/dockerizing/
