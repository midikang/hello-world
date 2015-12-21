docker images
====

The content of Dockerfile
# Run Lynx in a conatiner 
#
# docker run --rm -it \
#	--name lynx \
#	jess/lynx github.com/jfrazelle
#
FROM debian:jessie
MAINTAINER Jessica Frazelle <jess@docker.com>

RUN apt-get update && apt-get install -y \
	lynx \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

ENTRYPOINT [ "lynx" ]

========


# build lynx image myself
$docker build .

Sending build context to Docker daemon 2.048 kB
Step 1 : FROM debian:jessie
jessie: Pulling from library/debian
Digest: sha256:24a900d1671b269d6640b4224e7b63801880d8e3cb2bcbfaa10a5dddcf4469ed
Status: Downloaded newer image for debian:jessie
 ---> 23cb15b0fcec
Step 2 : MAINTAINER Jessica Frazelle <jess@docker.com>
 ---> Running in b0992e25600d
 ---> c98bf795d23b
Removing intermediate container b0992e25600d
Step 3 : RUN apt-get update && apt-get install -y 	lynx 	--no-install-recommends 	&& rm -rf /var/lib/apt/lists/*
 ---> Running in 167e2e25b8ff
Get:1 http://security.debian.org jessie/updates InRelease [63.1 kB]
Ign http://httpredir.debian.org jessie InRelease
Get:2 http://httpredir.debian.org jessie-updates InRelease [136 kB]
Get:3 http://httpredir.debian.org jessie Release.gpg [2373 B]
Get:4 http://httpredir.debian.org jessie Release [148 kB]
Get:5 http://security.debian.org jessie/updates/main amd64 Packages [215 kB]
Get:6 http://httpredir.debian.org jessie-updates/main amd64 Packages [3619 B]
Get:7 http://httpredir.debian.org jessie/main amd64 Packages [9035 kB]
Fetched 9604 kB in 15s (604 kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  libbsd0 libffi6 libgmp10 libgnutls-deb0-28 libhogweed2 libidn11 libnettle4
  libp11-kit0 libtasn1-6 lynx-cur
Suggested packages:
  gnutls-bin
Recommended packages:
  mime-support
The following NEW packages will be installed:
  libbsd0 libffi6 libgmp10 libgnutls-deb0-28 libhogweed2 libidn11 libnettle4
  libp11-kit0 libtasn1-6 lynx lynx-cur
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 3456 kB of archives.
After this operation, 9265 kB of additional disk space will be used.
Get:1 http://httpredir.debian.org/debian/ jessie/main libgmp10 amd64 2:6.0.0+dfsg-6 [253 kB]
Get:2 http://httpredir.debian.org/debian/ jessie/main libnettle4 amd64 2.7.1-5 [176 kB]
Get:3 http://httpredir.debian.org/debian/ jessie/main libhogweed2 amd64 2.7.1-5 [125 kB]
Get:4 http://httpredir.debian.org/debian/ jessie/main libffi6 amd64 3.1-2+b2 [20.1 kB]
Get:5 http://httpredir.debian.org/debian/ jessie/main libp11-kit0 amd64 0.20.7-1 [81.2 kB]
Get:6 http://httpredir.debian.org/debian/ jessie/main libtasn1-6 amd64 4.2-3+deb8u1 [48.9 kB]
Get:7 http://httpredir.debian.org/debian/ jessie/main libgnutls-deb0-28 amd64 3.3.8-6+deb8u3 [694 kB]
Get:8 http://httpredir.debian.org/debian/ jessie/main libidn11 amd64 1.29-1+b2 [136 kB]
Get:9 http://httpredir.debian.org/debian/ jessie/main libbsd0 amd64 0.7.0-2 [67.9 kB]
Get:10 http://httpredir.debian.org/debian/ jessie/main lynx-cur amd64 2.8.9dev1-2+deb8u1 [1623 kB]
Get:11 http://httpredir.debian.org/debian/ jessie/main lynx all 2.8.9dev1-2+deb8u1 [232 kB]
debconf: delaying package configuration, since apt-utils is not installed
Fetched 3456 kB in 1min 39s (34.7 kB/s)
Selecting previously unselected package libgmp10:amd64.
(Reading database ... 7531 files and directories currently installed.)
Preparing to unpack .../libgmp10_2%3a6.0.0+dfsg-6_amd64.deb ...
Unpacking libgmp10:amd64 (2:6.0.0+dfsg-6) ...
Selecting previously unselected package libnettle4:amd64.
Preparing to unpack .../libnettle4_2.7.1-5_amd64.deb ...
Unpacking libnettle4:amd64 (2.7.1-5) ...
Selecting previously unselected package libhogweed2:amd64.
Preparing to unpack .../libhogweed2_2.7.1-5_amd64.deb ...
Unpacking libhogweed2:amd64 (2.7.1-5) ...
Selecting previously unselected package libffi6:amd64.
Preparing to unpack .../libffi6_3.1-2+b2_amd64.deb ...
Unpacking libffi6:amd64 (3.1-2+b2) ...
Selecting previously unselected package libp11-kit0:amd64.
Preparing to unpack .../libp11-kit0_0.20.7-1_amd64.deb ...
Unpacking libp11-kit0:amd64 (0.20.7-1) ...
Selecting previously unselected package libtasn1-6:amd64.
Preparing to unpack .../libtasn1-6_4.2-3+deb8u1_amd64.deb ...
Unpacking libtasn1-6:amd64 (4.2-3+deb8u1) ...
Selecting previously unselected package libgnutls-deb0-28:amd64.
Preparing to unpack .../libgnutls-deb0-28_3.3.8-6+deb8u3_amd64.deb ...
Unpacking libgnutls-deb0-28:amd64 (3.3.8-6+deb8u3) ...
Selecting previously unselected package libidn11:amd64.
Preparing to unpack .../libidn11_1.29-1+b2_amd64.deb ...
Unpacking libidn11:amd64 (1.29-1+b2) ...
Selecting previously unselected package libbsd0:amd64.
Preparing to unpack .../libbsd0_0.7.0-2_amd64.deb ...
Unpacking libbsd0:amd64 (0.7.0-2) ...
Selecting previously unselected package lynx-cur.
Preparing to unpack .../lynx-cur_2.8.9dev1-2+deb8u1_amd64.deb ...
Unpacking lynx-cur (2.8.9dev1-2+deb8u1) ...
Selecting previously unselected package lynx.
Preparing to unpack .../lynx_2.8.9dev1-2+deb8u1_all.deb ...
Unpacking lynx (2.8.9dev1-2+deb8u1) ...
Setting up libgmp10:amd64 (2:6.0.0+dfsg-6) ...
Setting up libnettle4:amd64 (2.7.1-5) ...
Setting up libhogweed2:amd64 (2.7.1-5) ...
Setting up libffi6:amd64 (3.1-2+b2) ...
Setting up libp11-kit0:amd64 (0.20.7-1) ...
Setting up libtasn1-6:amd64 (4.2-3+deb8u1) ...
Setting up libgnutls-deb0-28:amd64 (3.3.8-6+deb8u3) ...
Setting up libidn11:amd64 (1.29-1+b2) ...
Setting up libbsd0:amd64 (0.7.0-2) ...
Setting up lynx-cur (2.8.9dev1-2+deb8u1) ...
update-alternatives: using /usr/bin/lynx to provide /usr/bin/www-browser (www-browser) in auto mode
Setting up lynx (2.8.9dev1-2+deb8u1) ...
Processing triggers for libc-bin (2.19-18+deb8u1) ...
 ---> 615e84bb764a
Removing intermediate container 167e2e25b8ff
Step 4 : ENTRYPOINT lynx
 ---> Running in 9c59e2c5c635
 ---> d2d67e93231a
Removing intermediate container 9c59e2c5c635
Successfully built d2d67e93231a

