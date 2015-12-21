Build image openvpn
========

The content of Dockerfile



The log when build image:
========

Sending build context to Docker daemon 2.048 kB
Step 1 : FROM alpine:latest
latest: Pulling from library/alpine
d6ead20d5571: Pull complete 
Digest: sha256:74afbca89e77413792fc46cbfc71528c47504c1e5e42a3828ffad9891ad166b2
Status: Downloaded newer image for alpine:latest
 ---> d6ead20d5571
Step 2 : RUN apk update && apk add 	openvpn 	&& rm -rf /var/cache/apk/*
 ---> Running in 606b8660a330
fetch http://dl-4.alpinelinux.org/alpine/v3.2/main/x86_64/APKINDEX.tar.gz
v3.2.3-144-gb61c35e [http://dl-4.alpinelinux.org/alpine/v3.2/main]
OK: 5291 distinct packages available
(1/4) Installing iptables (1.4.21-r3)
(2/4) Installing iproute2 (3.18.0-r0)
Executing iproute2-3.18.0-r0.post-install
(3/4) Installing lzo (2.09-r0)
(4/4) Installing openvpn (2.3.7-r0)
Executing openvpn-2.3.7-r0.pre-install
Executing busybox-1.23.2-r0.trigger
OK: 9 MiB in 19 packages
 ---> 2352d1639d38
Removing intermediate container 606b8660a330
Step 3 : WORKDIR /etc/openvpn
 ---> Running in 733df9c70600
 ---> 184491c03fd1
Removing intermediate container 733df9c70600
Step 4 : ENTRYPOINT openvpn
 ---> Running in 63d2128067e4
 ---> 35d77beb18c9
Removing intermediate container 63d2128067e4
Successfully built 35d77beb18c9






