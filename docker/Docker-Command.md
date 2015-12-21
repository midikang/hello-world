Docker Command List
========

Assume your docker machine is named 'default'

# To start VM
$docker-machine start default

# To stop VM
$docker-machine stop default

# To login docker via ssh to default VM
$docker-machiner ssh default

# To check if env of VM
$docker-machine env default

# To log into or run a command on a machine with SSH.
$docker-machine ssh default

# To check docker info
$docker info

Containers: 6
Images: 90
Server Version: 1.9.1
Storage Driver: aufs
 Root Dir: /mnt/sda1/var/lib/docker/aufs
 Backing Filesystem: extfs
 Dirs: 102
 Dirperm1 Supported: true
Execution Driver: native-0.2
Logging Driver: json-file
Kernel Version: 4.1.13-boot2docker
Operating System: Boot2Docker 1.9.1 (TCL 6.4.1); master : cef800b - Fri Nov 20 19:33:59 UTC 2015
CPUs: 1
Total Memory: 1.956 GiB
Name: default
ID: BJ7Y:B7DR:ZZPV:KHNW:3ZVA:422O:3UBR:5KFH:OTGR:TYPG:RR2R:NEOK
Debug mode (server): true
 File Descriptors: 12
 Goroutines: 18
 System Time: 2015-12-17T10:24:59.660050873Z
 EventsListeners: 0
 Init SHA1: 
 Init Path: /usr/local/bin/docker
 Docker Root Dir: /mnt/sda1/var/lib/docker
Labels:
 provider=virtualbox

# To get one image from Docker hub(repositor)
$docker pull ubuntu

# To check docker container is running
$docker ps

# To check all the running/stopped container
$docker ps -a
