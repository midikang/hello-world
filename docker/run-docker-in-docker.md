Run docker in docker
========

# Run docker in daemon
# --privileged=false              Give extended privileges to this container
# --name=                         Assign a name to the container
# -d, --detach=false              Run container in background and print container ID
$docker run -it --privileged --name some-docker -d docker:latest

# Link to some-docker which is running in daemon
#--rm=false                      Automatically remove the container when it exits
# --link=[]                       Add link to another container

$docker run --rm --link some-docker:docker docker:1.7 version


