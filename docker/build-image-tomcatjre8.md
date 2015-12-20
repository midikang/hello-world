Build one image with tomcat and jre8
=============

# Run in the folder which Dockerfile inside, build image with tag 'midi_tcjre8'
$ docker build -t midi_tcjre8 .

Sending build context to Docker daemon 3.072 kB
Step 1 : FROM java:8-jre
8-jre: Pulling from library/java
0a769fec47c8: Pull complete 
f2f2db51695f: Pull complete 
e028e5cf8d99: Pull complete 
d9cd78bd89ff: Pull complete 
5555497d559b: Pull complete 
e0d4b742b7a8: Pull complete 
3f99f333ef6d: Pull complete 
504924f188c0: Pull complete 
2f5e20e831ff: Pull complete 
Digest: sha256:82918e45463e2b9ac87c0b4350954ea593c51cde7e943334d5e54b6ca5658eb8
Status: Downloaded newer image for java:8-jre
 ---> 2f5e20e831ff
Step 2 : ENV CATALINA_HOME /usr/local/tomcat
 ---> Running in 4d5f2fbcf5e1
 ---> 0c7c88cde6ae
Removing intermediate container 4d5f2fbcf5e1
Step 3 : ENV PATH $CATALINA_HOME/bin:$PATH
 ---> Running in fb99597d6b76
 ---> 0b4ed9b6c703
Removing intermediate container fb99597d6b76
Step 4 : RUN mkdir -p "$CATALINA_HOME"
 ---> Running in ee8dc6c37414
 ---> 75e65916a267
Removing intermediate container ee8dc6c37414
Step 5 : WORKDIR $CATALINA_HOME
 ---> Running in 570f3dfefed2
 ---> bffa33145b14
Removing intermediate container 570f3dfefed2
Step 6 : RUN gpg --keyserver pool.sks-keyservers.net --recv-keys 	05AB33110949707C93A279E3D3EFE6B686867BA6 	07E48665A34DCAFAE522E5E6266191C37C037D42 	47309207D818FFD8DCD3F83F1931D684307A10A5541FBE7D8F78B25E055DDEE13C370389288584E7 	61B832AC2F1C5A90F0F9B00A1C506407564C17A3 	79F7026C690BAA50B92CD8B66A3AD3F4F22C4FED 	9BA44C2621385CB966EBA586F72C284D731FABEE 	A27677289986DB50844682F8ACB77FC2E86E29AC 	A9C5DF4D22E99998D9875A5110C01C5A2F6059E7 	DCFD35E0BF8CA7344752DE8B6FB21E8933C60243 	F3A04C595DB5B6A5F1ECA43E3B7BBB100D811BBE 	F7DA48BB64BCB84ECBA7EE6935CD23C10D498E23
 ---> Running in ae8fd630b46d
gpg: directory `/root/.gnupg' created
gpg: new configuration file `/root/.gnupg/gpg.conf' created
gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/root/.gnupg/secring.gpg' created
gpg: keyring `/root/.gnupg/pubring.gpg' created
gpg: requesting key 86867BA6 from hkp server pool.sks-keyservers.net
gpg: requesting key 7C037D42 from hkp server pool.sks-keyservers.net
gpg: requesting key 307A10A5 from hkp server pool.sks-keyservers.net
gpg: requesting key 288584E7 from hkp server pool.sks-keyservers.net
gpg: requesting key 564C17A3 from hkp server pool.sks-keyservers.net
gpg: requesting key F22C4FED from hkp server pool.sks-keyservers.net
gpg: requesting key 731FABEE from hkp server pool.sks-keyservers.net
gpg: requesting key E86E29AC from hkp server pool.sks-keyservers.net
gpg: requesting key 2F6059E7 from hkp server pool.sks-keyservers.net
gpg: requesting key 33C60243 from hkp server pool.sks-keyservers.net
gpg: requesting key 0D811BBE from hkp server pool.sks-keyservers.net
gpg: requesting key 0D498E23 from hkp server pool.sks-keyservers.net
gpg: /root/.gnupg/trustdb.gpg: trustdb created
gpg: key 86867BA6: public key "Jean-Frederic Clere (jfclere) <JFrederic.Clere@fujitsu-siemens.com>" imported
gpg: key 7C037D42: public key "Yoav Shapira <yoavs@apache.org>" imported
gpg: key 307A10A5: public key "Henri Gomez <hgomez@users.sourceforge.net>" imported
gpg: key 288584E7: public key "Rémy Maucherat <remm@apache.org>" imported
gpg: key 564C17A3: public key "Mladen Turk (*** DEFAULT SIGNING KEY ***) <mturk@apache.org>" imported
gpg: key F22C4FED: public key "Andy Armstrong <andy@tagish.com>" imported
gpg: key 731FABEE: public key "Tim Whittington (CODE SIGNING KEY) <timw@apache.org>" imported
gpg: key E86E29AC: public key "kevin seguin <seguin@apache.org>" imported
gpg: key 2F6059E7: public key "Mark E D Thomas <markt@apache.org>" imported
gpg: key 33C60243: public key "Mark E D Thomas <markt@apache.org>" imported
gpg: key 0D811BBE: public key "Yoav Shapira <yoavs@computer.org>" imported
gpg: key 0D498E23: public key "Mladen Turk (Default signing key) <mturk@apache.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 12
gpg:               imported: 12  (RSA: 2)
 ---> 754914b4bc68
Removing intermediate container ae8fd630b46d
Step 7 : ENV TOMCAT_MAJOR 8
 ---> Running in 28177ccdfccd
 ---> a703f422170b
Removing intermediate container 28177ccdfccd
Step 8 : ENV TOMCAT_VERSION 8.0.30
 ---> Running in 63b721e51424
 ---> d4ef295ddf28
Removing intermediate container 63b721e51424
Step 9 : ENV TOMCAT_TGZ_URL https://www.apache.org/dist/tomcat/tomcat-$TOMCAT_MAJOR/v$TOMCAT_VERSION/bin/apache-tomcat-$TOMCAT_VERSION.tar.gz
 ---> Running in 834d9dcd6b96
 ---> 6b84dbac9ba8
Removing intermediate container 834d9dcd6b96
Step 10 : RUN set -x 	&& curl -fSL "$TOMCAT_TGZ_URL" -o tomcat.tar.gz 	&& curl -fSL "$TOMCAT_TGZ_URL.asc" -o tomcat.tar.gz.asc 	&& gpg --verify tomcat.tar.gz.asc 	&& tar -xvf tomcat.tar.gz --strip-components=1 	&& rm bin/*.bat 	&& rm tomcat.tar.gz*
 ---> Running in 15bf0f303928
+ curl -fSL https://www.apache.org/dist/tomcat/tomcat-8/v8.0.30/bin/apache-tomcat-8.0.30.tar.gz -o tomcat.tar.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 8936k  100 8936k    0     0  22177      0  0:06:52  0:06:52 --:--:-- 69556
+ curl -fSL https://www.apache.org/dist/tomcat/tomcat-8/v8.0.30/bin/apache-tomcat-8.0.30.tar.gz.asc -o tomcat.tar.gz.asc
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   836  100   836    0     0    498      0  0:00:01  0:00:01 --:--:--   498
+ gpg --verify tomcat.tar.gz.asc
gpg: assuming signed data in `tomcat.tar.gz'
gpg: Signature made Tue 01 Dec 2015 10:33:28 PM UTC using RSA key ID 2F6059E7
gpg: Good signature from "Mark E D Thomas <markt@apache.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: A9C5 DF4D 22E9 9998 D987  5A51 10C0 1C5A 2F60 59E7
+ tar -xvf tomcat.tar.gz --strip-components=1

apache-tomcat-8.0.30/bin/catalina.sh
apache-tomcat-8.0.30/bin/configtest.sh
apache-tomcat-8.0.30/bin/daemon.sh
apache-tomcat-8.0.30/bin/digest.sh
apache-tomcat-8.0.30/bin/setclasspath.sh
apache-tomcat-8.0.30/bin/shutdown.sh
apache-tomcat-8.0.30/bin/startup.sh
apache-tomcat-8.0.30/bin/tool-wrapper.sh
apache-tomcat-8.0.30/bin/version.sh
apache-tomcat-8.0.30/conf/
apache-tomcat-8.0.30/conf/catalina.policy
apache-tomcat-8.0.30/conf/catalina.properties
apache-tomcat-8.0.30/conf/context.xml
apache-tomcat-8.0.30/conf/logging.properties
apache-tomcat-8.0.30/conf/server.xml
apache-tomcat-8.0.30/conf/tomcat-users.xml
apache-tomcat-8.0.30/conf/tomcat-users.xsd
apache-tomcat-8.0.30/conf/web.xml
apache-tomcat-8.0.30/bin/
apache-tomcat-8.0.30/lib/
apache-tomcat-8.0.30/logs/
apache-tomcat-8.0.30/temp/
apache-tomcat-8.0.30/webapps/
apache-tomcat-8.0.30/webapps/ROOT/
apache-tomcat-8.0.30/webapps/ROOT/WEB-INF/
apache-tomcat-8.0.30/webapps/docs/
apache-tomcat-8.0.30/webapps/docs/WEB-INF/
apache-tomcat-8.0.30/webapps/docs/api/
apache-tomcat-8.0.30/webapps/docs/appdev/
apache-tomcat-8.0.30/webapps/docs/appdev/sample/
apache-tomcat-8.0.30/webapps/docs/appdev/sample/docs/
apache-tomcat-8.0.30/webapps/docs/appdev/sample/src/
apache-tomcat-8.0.30/webapps/docs/appdev/sample/src/mypackage/
apache-tomcat-8.0.30/webapps/docs/appdev/sample/web/
apache-tomcat-8.0.30/webapps/docs/appdev/sample/web/WEB-INF/
apache-tomcat-8.0.30/webapps/docs/appdev/sample/web/images/
apache-tomcat-8.0.30/webapps/docs/architecture/
apache-tomcat-8.0.30/webapps/docs/architecture/requestProcess/
apache-tomcat-8.0.30/webapps/docs/architecture/startup/
apache-tomcat-8.0.30/webapps/docs/config/
apache-tomcat-8.0.30/webapps/docs/elapi/
apache-tomcat-8.0.30/webapps/docs/funcspecs/
apache-tomcat-8.0.30/webapps/docs/images/
apache-tomcat-8.0.30/webapps/docs/images/fonts/
apache-tomcat-8.0.30/webapps/docs/jspapi/
apache-tomcat-8.0.30/webapps/docs/servletapi/
apache-tomcat-8.0.30/webapps/docs/tribes/
apache-tomcat-8.0.30/webapps/docs/websocketapi/
apache-tomcat-8.0.30/webapps/examples/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/cal/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/chat/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/checkbox/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/colors/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/compressionFilters/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/dates/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/error/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/filters/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/el/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/listeners/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/nonblocking/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/num/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/sessions/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/util/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/validators/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/chat/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/wsmessages/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/jsp/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/jsp2/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/jsp/applet/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/lib/
apache-tomcat-8.0.30/webapps/examples/WEB-INF/tags/
apache-tomcat-8.0.30/webapps/examples/jsp/
apache-tomcat-8.0.30/webapps/examples/jsp/async/
apache-tomcat-8.0.30/webapps/examples/jsp/cal/
apache-tomcat-8.0.30/webapps/examples/jsp/checkbox/
apache-tomcat-8.0.30/webapps/examples/jsp/colors/
apache-tomcat-8.0.30/webapps/examples/jsp/dates/
apache-tomcat-8.0.30/webapps/examples/jsp/error/
apache-tomcat-8.0.30/webapps/examples/jsp/forward/
apache-tomcat-8.0.30/webapps/examples/jsp/images/
apache-tomcat-8.0.30/webapps/examples/jsp/include/
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspx/
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/
apache-tomcat-8.0.30/webapps/examples/jsp/jsptoserv/
apache-tomcat-8.0.30/webapps/examples/jsp/num/
apache-tomcat-8.0.30/webapps/examples/jsp/plugin/
apache-tomcat-8.0.30/webapps/examples/jsp/plugin/applet/
apache-tomcat-8.0.30/webapps/examples/jsp/security/
apache-tomcat-8.0.30/webapps/examples/jsp/security/protected/
apache-tomcat-8.0.30/webapps/examples/jsp/sessions/
apache-tomcat-8.0.30/webapps/examples/jsp/simpletag/
apache-tomcat-8.0.30/webapps/examples/jsp/snp/
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/
apache-tomcat-8.0.30/webapps/examples/jsp/xml/
apache-tomcat-8.0.30/webapps/examples/servlets/
apache-tomcat-8.0.30/webapps/examples/servlets/chat/
apache-tomcat-8.0.30/webapps/examples/servlets/images/
apache-tomcat-8.0.30/webapps/examples/servlets/nonblocking/
apache-tomcat-8.0.30/webapps/examples/websocket/
apache-tomcat-8.0.30/webapps/host-manager/
apache-tomcat-8.0.30/webapps/host-manager/META-INF/
apache-tomcat-8.0.30/webapps/host-manager/WEB-INF/
apache-tomcat-8.0.30/webapps/host-manager/WEB-INF/jsp/
apache-tomcat-8.0.30/webapps/host-manager/images/
apache-tomcat-8.0.30/webapps/manager/
apache-tomcat-8.0.30/webapps/manager/META-INF/
apache-tomcat-8.0.30/webapps/manager/WEB-INF/
apache-tomcat-8.0.30/webapps/manager/WEB-INF/jsp/
apache-tomcat-8.0.30/webapps/manager/images/
apache-tomcat-8.0.30/work/
apache-tomcat-8.0.30/LICENSE
apache-tomcat-8.0.30/NOTICE
apache-tomcat-8.0.30/RELEASE-NOTES
apache-tomcat-8.0.30/RUNNING.txt
apache-tomcat-8.0.30/bin/bootstrap.jar
apache-tomcat-8.0.30/bin/catalina-tasks.xml
apache-tomcat-8.0.30/bin/catalina.bat
apache-tomcat-8.0.30/bin/commons-daemon-native.tar.gz
apache-tomcat-8.0.30/bin/commons-daemon.jar
apache-tomcat-8.0.30/bin/configtest.bat
apache-tomcat-8.0.30/bin/digest.bat
apache-tomcat-8.0.30/bin/setclasspath.bat
apache-tomcat-8.0.30/bin/shutdown.bat
apache-tomcat-8.0.30/bin/startup.bat
apache-tomcat-8.0.30/bin/tomcat-juli.jar
apache-tomcat-8.0.30/bin/tomcat-native.tar.gz
apache-tomcat-8.0.30/bin/tool-wrapper.bat
apache-tomcat-8.0.30/bin/version.bat
apache-tomcat-8.0.30/lib/annotations-api.jar
apache-tomcat-8.0.30/lib/catalina-ant.jar
apache-tomcat-8.0.30/lib/catalina-ha.jar
apache-tomcat-8.0.30/lib/catalina-storeconfig.jar
apache-tomcat-8.0.30/lib/catalina-tribes.jar
apache-tomcat-8.0.30/lib/catalina.jar
apache-tomcat-8.0.30/lib/ecj-4.4.2.jar
apache-tomcat-8.0.30/lib/el-api.jar
apache-tomcat-8.0.30/lib/jasper-el.jar
apache-tomcat-8.0.30/lib/jasper.jar
apache-tomcat-8.0.30/lib/jsp-api.jar
apache-tomcat-8.0.30/lib/servlet-api.jar
apache-tomcat-8.0.30/lib/tomcat-api.jar
apache-tomcat-8.0.30/lib/tomcat-coyote.jar
apache-tomcat-8.0.30/lib/tomcat-dbcp.jar
apache-tomcat-8.0.30/lib/tomcat-i18n-es.jar
apache-tomcat-8.0.30/lib/tomcat-i18n-fr.jar
apache-tomcat-8.0.30/lib/tomcat-i18n-ja.jar
apache-tomcat-8.0.30/lib/tomcat-jdbc.jar
apache-tomcat-8.0.30/lib/tomcat-jni.jar
apache-tomcat-8.0.30/lib/tomcat-util-scan.jar
apache-tomcat-8.0.30/lib/tomcat-util.jar
apache-tomcat-8.0.30/lib/tomcat-websocket.jar
apache-tomcat-8.0.30/lib/websocket-api.jar
apache-tomcat-8.0.30/temp/safeToDelete.tmp
apache-tomcat-8.0.30/webapps/ROOT/RELEASE-NOTES.txt
apache-tomcat-8.0.30/webapps/ROOT/WEB-INF/web.xml
apache-tomcat-8.0.30/webapps/ROOT/asf-logo-wide.gif
apache-tomcat-8.0.30/webapps/ROOT/asf-logo.png
apache-tomcat-8.0.30/webapps/ROOT/bg-button.png
apache-tomcat-8.0.30/webapps/ROOT/bg-middle.png
apache-tomcat-8.0.30/webapps/ROOT/bg-nav-item.png
apache-tomcat-8.0.30/webapps/ROOT/bg-nav.png
apache-tomcat-8.0.30/webapps/ROOT/bg-upper.png
apache-tomcat-8.0.30/webapps/ROOT/build.xml
apache-tomcat-8.0.30/webapps/ROOT/favicon.ico
apache-tomcat-8.0.30/webapps/ROOT/index.jsp
apache-tomcat-8.0.30/webapps/ROOT/tomcat-power.gif
apache-tomcat-8.0.30/webapps/ROOT/tomcat.css
apache-tomcat-8.0.30/webapps/ROOT/tomcat.gif
apache-tomcat-8.0.30/webapps/ROOT/tomcat.png
apache-tomcat-8.0.30/webapps/ROOT/tomcat.svg
apache-tomcat-8.0.30/webapps/docs/BUILDING.txt
apache-tomcat-8.0.30/webapps/docs/RELEASE-NOTES.txt
apache-tomcat-8.0.30/webapps/docs/RUNNING.txt
apache-tomcat-8.0.30/webapps/docs/WEB-INF/web.xml
apache-tomcat-8.0.30/webapps/docs/aio.html
apache-tomcat-8.0.30/webapps/docs/api/index.html
apache-tomcat-8.0.30/webapps/docs/appdev/build.xml.txt
apache-tomcat-8.0.30/webapps/docs/appdev/deployment.html
apache-tomcat-8.0.30/webapps/docs/appdev/index.html
apache-tomcat-8.0.30/webapps/docs/appdev/installation.html
apache-tomcat-8.0.30/webapps/docs/appdev/introduction.html
apache-tomcat-8.0.30/webapps/docs/appdev/processes.html
apache-tomcat-8.0.30/webapps/docs/appdev/sample/build.xml
apache-tomcat-8.0.30/webapps/docs/appdev/sample/docs/README.txt
apache-tomcat-8.0.30/webapps/docs/appdev/sample/index.html
apache-tomcat-8.0.30/webapps/docs/appdev/sample/sample.war
apache-tomcat-8.0.30/webapps/docs/appdev/sample/src/mypackage/Hello.java
apache-tomcat-8.0.30/webapps/docs/appdev/sample/web/WEB-INF/web.xml
apache-tomcat-8.0.30/webapps/docs/appdev/sample/web/hello.jsp
apache-tomcat-8.0.30/webapps/docs/appdev/sample/web/images/tomcat.gif
apache-tomcat-8.0.30/webapps/docs/appdev/sample/web/index.html
apache-tomcat-8.0.30/webapps/docs/appdev/source.html
apache-tomcat-8.0.30/webapps/docs/appdev/web.xml.txt
apache-tomcat-8.0.30/webapps/docs/apr.html
apache-tomcat-8.0.30/webapps/docs/architecture/index.html
apache-tomcat-8.0.30/webapps/docs/architecture/overview.html
apache-tomcat-8.0.30/webapps/docs/architecture/requestProcess.html
apache-tomcat-8.0.30/webapps/docs/architecture/requestProcess/authentication-process.png
apache-tomcat-8.0.30/webapps/docs/architecture/requestProcess/request-process.png
apache-tomcat-8.0.30/webapps/docs/architecture/startup.html
apache-tomcat-8.0.30/webapps/docs/architecture/startup/serverStartup.pdf
apache-tomcat-8.0.30/webapps/docs/architecture/startup/serverStartup.txt
apache-tomcat-8.0.30/webapps/docs/balancer-howto.html
apache-tomcat-8.0.30/webapps/docs/building.html
apache-tomcat-8.0.30/webapps/docs/cgi-howto.html
apache-tomcat-8.0.30/webapps/docs/changelog.html
apache-tomcat-8.0.30/webapps/docs/class-loader-howto.html
apache-tomcat-8.0.30/webapps/docs/cluster-howto.html
apache-tomcat-8.0.30/webapps/docs/comments.html
apache-tomcat-8.0.30/webapps/docs/config/ajp.html
apache-tomcat-8.0.30/webapps/docs/config/automatic-deployment.html
apache-tomcat-8.0.30/webapps/docs/config/cluster-channel.html
apache-tomcat-8.0.30/webapps/docs/config/cluster-deployer.html
apache-tomcat-8.0.30/webapps/docs/config/cluster-interceptor.html
apache-tomcat-8.0.30/webapps/docs/config/cluster-listener.html
apache-tomcat-8.0.30/webapps/docs/config/cluster-manager.html
apache-tomcat-8.0.30/webapps/docs/config/cluster-membership.html
apache-tomcat-8.0.30/webapps/docs/config/cluster-receiver.html
apache-tomcat-8.0.30/webapps/docs/config/cluster-sender.html
apache-tomcat-8.0.30/webapps/docs/config/cluster-valve.html
apache-tomcat-8.0.30/webapps/docs/config/cluster.html
apache-tomcat-8.0.30/webapps/docs/config/context.html
apache-tomcat-8.0.30/webapps/docs/config/cookie-processor.html
apache-tomcat-8.0.30/webapps/docs/config/credentialhandler.html
apache-tomcat-8.0.30/webapps/docs/config/engine.html
apache-tomcat-8.0.30/webapps/docs/config/executor.html
apache-tomcat-8.0.30/webapps/docs/config/filter.html
apache-tomcat-8.0.30/webapps/docs/config/globalresources.html
apache-tomcat-8.0.30/webapps/docs/config/host.html
apache-tomcat-8.0.30/webapps/docs/config/http.html
apache-tomcat-8.0.30/webapps/docs/config/index.html
apache-tomcat-8.0.30/webapps/docs/config/jar-scan-filter.html
apache-tomcat-8.0.30/webapps/docs/config/jar-scanner.html
apache-tomcat-8.0.30/webapps/docs/config/listeners.html
apache-tomcat-8.0.30/webapps/docs/config/loader.html
apache-tomcat-8.0.30/webapps/docs/config/manager.html
apache-tomcat-8.0.30/webapps/docs/config/realm.html
apache-tomcat-8.0.30/webapps/docs/config/resources.html
apache-tomcat-8.0.30/webapps/docs/config/server.html
apache-tomcat-8.0.30/webapps/docs/config/service.html
apache-tomcat-8.0.30/webapps/docs/config/sessionidgenerator.html
apache-tomcat-8.0.30/webapps/docs/config/systemprops.html
apache-tomcat-8.0.30/webapps/docs/config/valve.html
apache-tomcat-8.0.30/webapps/docs/connectors.html
apache-tomcat-8.0.30/webapps/docs/default-servlet.html
apache-tomcat-8.0.30/webapps/docs/deployer-howto.html
apache-tomcat-8.0.30/webapps/docs/developers.html
apache-tomcat-8.0.30/webapps/docs/elapi/index.html
apache-tomcat-8.0.30/webapps/docs/extras.html
apache-tomcat-8.0.30/webapps/docs/funcspecs/fs-admin-apps.html
apache-tomcat-8.0.30/webapps/docs/funcspecs/fs-admin-objects.html
apache-tomcat-8.0.30/webapps/docs/funcspecs/fs-admin-opers.html
apache-tomcat-8.0.30/webapps/docs/funcspecs/fs-default.html
apache-tomcat-8.0.30/webapps/docs/funcspecs/fs-jdbc-realm.html
apache-tomcat-8.0.30/webapps/docs/funcspecs/fs-jndi-realm.html
apache-tomcat-8.0.30/webapps/docs/funcspecs/fs-memory-realm.html
apache-tomcat-8.0.30/webapps/docs/funcspecs/index.html
apache-tomcat-8.0.30/webapps/docs/funcspecs/mbean-names.html
apache-tomcat-8.0.30/webapps/docs/html-manager-howto.html
apache-tomcat-8.0.30/webapps/docs/images/add.gif
apache-tomcat-8.0.30/webapps/docs/images/asf-feather.png
apache-tomcat-8.0.30/webapps/docs/images/asf-logo.gif
apache-tomcat-8.0.30/webapps/docs/images/code.gif
apache-tomcat-8.0.30/webapps/docs/images/cors-flowchart.png
apache-tomcat-8.0.30/webapps/docs/images/design.gif
apache-tomcat-8.0.30/webapps/docs/images/docs-stylesheet.css
apache-tomcat-8.0.30/webapps/docs/images/docs.gif
apache-tomcat-8.0.30/webapps/docs/images/fix.gif
apache-tomcat-8.0.30/webapps/docs/images/fonts/OpenSans400.woff
apache-tomcat-8.0.30/webapps/docs/images/fonts/OpenSans400italic.woff
apache-tomcat-8.0.30/webapps/docs/images/fonts/OpenSans600.woff
apache-tomcat-8.0.30/webapps/docs/images/fonts/OpenSans600italic.woff
apache-tomcat-8.0.30/webapps/docs/images/fonts/OpenSans700.woff
apache-tomcat-8.0.30/webapps/docs/images/fonts/OpenSans700italic.woff
apache-tomcat-8.0.30/webapps/docs/images/fonts/fonts.css
apache-tomcat-8.0.30/webapps/docs/images/printer.gif
apache-tomcat-8.0.30/webapps/docs/images/tomcat.gif
apache-tomcat-8.0.30/webapps/docs/images/tomcat.png
apache-tomcat-8.0.30/webapps/docs/images/tomcat.svg
apache-tomcat-8.0.30/webapps/docs/images/update.gif
apache-tomcat-8.0.30/webapps/docs/images/void.gif
apache-tomcat-8.0.30/webapps/docs/index.html
apache-tomcat-8.0.30/webapps/docs/introduction.html
apache-tomcat-8.0.30/webapps/docs/jasper-howto.html
apache-tomcat-8.0.30/webapps/docs/jdbc-pool.html
apache-tomcat-8.0.30/webapps/docs/jndi-datasource-examples-howto.html
apache-tomcat-8.0.30/webapps/docs/jndi-resources-howto.html
apache-tomcat-8.0.30/webapps/docs/jspapi/index.html
apache-tomcat-8.0.30/webapps/docs/logging.html
apache-tomcat-8.0.30/webapps/docs/manager-howto.html
apache-tomcat-8.0.30/webapps/docs/maven-jars.html
apache-tomcat-8.0.30/webapps/docs/mbeans-descriptor-howto.html
apache-tomcat-8.0.30/webapps/docs/monitoring.html
apache-tomcat-8.0.30/webapps/docs/proxy-howto.html
apache-tomcat-8.0.30/webapps/docs/realm-howto.html
apache-tomcat-8.0.30/webapps/docs/rewrite.html
apache-tomcat-8.0.30/webapps/docs/security-howto.html
apache-tomcat-8.0.30/webapps/docs/security-manager-howto.html
apache-tomcat-8.0.30/webapps/docs/servletapi/index.html
apache-tomcat-8.0.30/webapps/docs/setup.html
apache-tomcat-8.0.30/webapps/docs/ssi-howto.html
apache-tomcat-8.0.30/webapps/docs/ssl-howto.html
apache-tomcat-8.0.30/webapps/docs/tribes/developers.html
apache-tomcat-8.0.30/webapps/docs/tribes/faq.html
apache-tomcat-8.0.30/webapps/docs/tribes/interceptors.html
apache-tomcat-8.0.30/webapps/docs/tribes/introduction.html
apache-tomcat-8.0.30/webapps/docs/tribes/membership.html
apache-tomcat-8.0.30/webapps/docs/tribes/setup.html
apache-tomcat-8.0.30/webapps/docs/tribes/status.html
apache-tomcat-8.0.30/webapps/docs/tribes/transport.html
apache-tomcat-8.0.30/webapps/docs/virtual-hosting-howto.html
apache-tomcat-8.0.30/webapps/docs/web-socket-howto.html
apache-tomcat-8.0.30/webapps/docs/websocketapi/index.html
apache-tomcat-8.0.30/webapps/docs/windows-auth-howto.html
apache-tomcat-8.0.30/webapps/docs/windows-service-howto.html
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/CookieExample.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/CookieExample.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/HelloWorldExample.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/HelloWorldExample.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/LocalStrings.properties
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/LocalStrings_en.properties
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/LocalStrings_es.properties
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/LocalStrings_fr.properties
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/LocalStrings_pt.properties
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/RequestHeaderExample.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/RequestHeaderExample.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/RequestInfoExample.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/RequestInfoExample.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/RequestParamExample.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/RequestParamExample.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/ServletToJsp.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/ServletToJsp.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/SessionExample.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/SessionExample.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async0$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async0.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async0.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async1$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async1.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async2$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async2.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async2.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async3.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Async3.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/AsyncStockServlet.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/AsyncStockServlet.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Stockticker$Stock.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Stockticker$TickListener.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Stockticker.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/async/Stockticker.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/cal/Entries.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/cal/Entries.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/cal/Entry.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/cal/Entry.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/cal/JspCalendar.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/cal/JspCalendar.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/cal/TableBean.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/cal/TableBean.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/chat/ChatServlet$MessageSender.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/chat/ChatServlet.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/chat/ChatServlet.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/checkbox/CheckTest.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/checkbox/CheckTest.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/colors/ColorGameBean.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/colors/ColorGameBean.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/compressionFilters/CompressionFilter.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/compressionFilters/CompressionFilter.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/compressionFilters/CompressionFilterTestServlet.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/compressionFilters/CompressionFilterTestServlet.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/compressionFilters/CompressionResponseStream.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/compressionFilters/CompressionResponseStream.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/compressionFilters/CompressionServletResponseWrapper.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/compressionFilters/CompressionServletResponseWrapper.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/dates/JspCalendar.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/dates/JspCalendar.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/error/Smart.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/error/Smart.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/ExampleTagBase.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/ExampleTagBase.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/FooTag.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/FooTag.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/FooTagExtraInfo.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/FooTagExtraInfo.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/LogTag.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/LogTag.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/ShowSource.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/ShowSource.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/ValuesTag.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/examples/ValuesTag.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/filters/ExampleFilter.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/filters/ExampleFilter.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/BookBean.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/BookBean.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/FooBean.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/FooBean.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/ValuesBean.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/ValuesBean.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/el/Functions.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/el/Functions.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/EchoAttributesTag.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/EchoAttributesTag.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/FindBookSimpleTag.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/FindBookSimpleTag.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/HelloWorldSimpleTag.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/HelloWorldSimpleTag.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/RepeatSimpleTag.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/RepeatSimpleTag.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/ShuffleSimpleTag.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/ShuffleSimpleTag.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/TileSimpleTag.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/jsp2/examples/simpletag/TileSimpleTag.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/listeners/ContextListener.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/listeners/ContextListener.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/listeners/SessionListener.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/listeners/SessionListener.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/nonblocking/ByteCounter$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/nonblocking/ByteCounter$CounterListener.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/nonblocking/ByteCounter.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/nonblocking/ByteCounter.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/nonblocking/NumberWriter$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/nonblocking/NumberWriter$NumberWriterListener.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/nonblocking/NumberWriter.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/nonblocking/NumberWriter.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/num/NumberGuessBean.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/num/NumberGuessBean.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/sessions/DummyCart.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/sessions/DummyCart.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/util/CookieFilter.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/util/CookieFilter.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/util/HTMLFilter.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/util/HTMLFilter.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/validators/DebugValidator.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/validators/DebugValidator.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/ExamplesConfig.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/ExamplesConfig.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/chat/ChatAnnotation.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/chat/ChatAnnotation.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/Client$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/Client.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/Client.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawMessage$ParseException.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawMessage.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawMessage.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawboardContextListener.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawboardContextListener.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawboardEndpoint$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawboardEndpoint$2.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawboardEndpoint$3$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawboardEndpoint$3.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawboardEndpoint.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/DrawboardEndpoint.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/Room$1$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/Room$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/Room$2.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/Room$MessageType.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/Room$Player.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/Room.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/Room.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/wsmessages/AbstractWebsocketMessage.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/wsmessages/AbstractWebsocketMessage.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/wsmessages/BinaryWebsocketMessage.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/wsmessages/BinaryWebsocketMessage.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/wsmessages/CloseWebsocketMessage.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/wsmessages/CloseWebsocketMessage.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/wsmessages/StringWebsocketMessage.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/drawboard/wsmessages/StringWebsocketMessage.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoAnnotation.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoAnnotation.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoAsyncAnnotation$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoAsyncAnnotation$CompletedFuture.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoAsyncAnnotation.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoAsyncAnnotation.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoEndpoint$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoEndpoint$EchoMessageHandlerBinary.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoEndpoint$EchoMessageHandlerText.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoEndpoint.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoEndpoint.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoStreamAnnotation.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/EchoStreamAnnotation.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/echo/servers.json
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/Direction.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/Direction.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/Location$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/Location.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/Location.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/Snake.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/Snake.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/SnakeAnnotation.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/SnakeAnnotation.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/SnakeTimer$1.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/SnakeTimer.class
apache-tomcat-8.0.30/webapps/examples/WEB-INF/classes/websocket/snake/SnakeTimer.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/jsp2/jsp2-example-taglib.tld
apache-tomcat-8.0.30/webapps/examples/WEB-INF/jsp/applet/Clock2.java
apache-tomcat-8.0.30/webapps/examples/WEB-INF/jsp/debug-taglib.tld
apache-tomcat-8.0.30/webapps/examples/WEB-INF/jsp/example-taglib.tld
apache-tomcat-8.0.30/webapps/examples/WEB-INF/lib/taglibs-standard-impl-1.2.5.jar
apache-tomcat-8.0.30/webapps/examples/WEB-INF/lib/taglibs-standard-spec-1.2.5.jar
apache-tomcat-8.0.30/webapps/examples/WEB-INF/tags/displayProducts.tag
apache-tomcat-8.0.30/webapps/examples/WEB-INF/tags/helloWorld.tag
apache-tomcat-8.0.30/webapps/examples/WEB-INF/tags/panel.tag
apache-tomcat-8.0.30/webapps/examples/WEB-INF/web.xml
apache-tomcat-8.0.30/webapps/examples/index.html
apache-tomcat-8.0.30/webapps/examples/jsp/async/async1.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/async/async1.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/async/async3.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/async/async3.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/async/index.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/async/index.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/cal/Entries.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/cal/Entry.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/cal/JspCalendar.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/cal/TableBean.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/cal/cal1.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/cal/cal1.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/cal/cal2.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/cal/cal2.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/cal/calendar.html
apache-tomcat-8.0.30/webapps/examples/jsp/cal/login.html
apache-tomcat-8.0.30/webapps/examples/jsp/checkbox/CheckTest.html
apache-tomcat-8.0.30/webapps/examples/jsp/checkbox/check.html
apache-tomcat-8.0.30/webapps/examples/jsp/checkbox/checkresult.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/checkbox/checkresult.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/checkbox/cresult.html
apache-tomcat-8.0.30/webapps/examples/jsp/colors/ColorGameBean.html
apache-tomcat-8.0.30/webapps/examples/jsp/colors/clr.html
apache-tomcat-8.0.30/webapps/examples/jsp/colors/colors.html
apache-tomcat-8.0.30/webapps/examples/jsp/colors/colrs.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/colors/colrs.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/dates/date.html
apache-tomcat-8.0.30/webapps/examples/jsp/dates/date.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/dates/date.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/error/er.html
apache-tomcat-8.0.30/webapps/examples/jsp/error/err.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/error/err.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/error/error.html
apache-tomcat-8.0.30/webapps/examples/jsp/error/errorpge.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/error/errorpge.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/forward/forward.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/forward/forward.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/forward/fwd.html
apache-tomcat-8.0.30/webapps/examples/jsp/forward/one.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/forward/one.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/forward/two.html
apache-tomcat-8.0.30/webapps/examples/jsp/images/code.gif
apache-tomcat-8.0.30/webapps/examples/jsp/images/execute.gif
apache-tomcat-8.0.30/webapps/examples/jsp/images/read.gif
apache-tomcat-8.0.30/webapps/examples/jsp/images/return.gif
apache-tomcat-8.0.30/webapps/examples/jsp/include/foo.html
apache-tomcat-8.0.30/webapps/examples/jsp/include/foo.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/include/foo.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/include/inc.html
apache-tomcat-8.0.30/webapps/examples/jsp/include/include.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/include/include.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/index.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/Functions.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/ValuesBean.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/ValuesTag.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/basic-arithmetic.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/basic-arithmetic.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/basic-arithmetic.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/basic-comparisons.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/basic-comparisons.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/basic-comparisons.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/composite.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/composite.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/composite.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/functions.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/functions.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/functions.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/implicit-objects.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/implicit-objects.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/el/implicit-objects.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/FooBean.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/HelloWorldSimpleTag.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/ShuffleSimpleTag.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/TileSimpleTag.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/jspattribute.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/jspattribute.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/jspattribute.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/shuffle.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/shuffle.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspattribute/shuffle.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspx/basic.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspx/basic.jspx
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspx/basic.jspx.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspx/svgexample.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspx/textRotate.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspx/textRotate.jpg
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspx/textRotate.jspx
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/jspx/textRotate.jspx.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/EchoAttributesTag.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/coda.jspf
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/coda.jspf.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/config.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/config.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/config.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/dynamicattrs.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/dynamicattrs.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/dynamicattrs.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/prelude.jspf
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/misc/prelude.jspf.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/BookBean.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/FindBookSimpleTag.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/Functions.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/HelloWorldSimpleTag.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/RepeatSimpleTag.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/book.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/book.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/book.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/hello.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/hello.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/hello.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/repeat.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/repeat.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/simpletag/repeat.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/displayProducts.tag.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/hello.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/hello.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/hello.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/helloWorld.tag.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/panel.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/panel.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/panel.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/panel.tag.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/products.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/products.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsp2/tagfiles/products.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsptoserv/ServletToJsp.java.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsptoserv/hello.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsptoserv/hello.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsptoserv/jsptoservlet.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/jsptoserv/jsptoservlet.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/jsptoserv/jts.html
apache-tomcat-8.0.30/webapps/examples/jsp/num/numguess.html
apache-tomcat-8.0.30/webapps/examples/jsp/num/numguess.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/num/numguess.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/plugin/applet/Clock2.class
apache-tomcat-8.0.30/webapps/examples/jsp/plugin/applet/Clock2.java
apache-tomcat-8.0.30/webapps/examples/jsp/plugin/plugin.html
apache-tomcat-8.0.30/webapps/examples/jsp/plugin/plugin.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/plugin/plugin.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/security/protected/error.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/security/protected/error.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/security/protected/index.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/security/protected/index.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/security/protected/login.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/security/protected/login.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/sessions/DummyCart.html
apache-tomcat-8.0.30/webapps/examples/jsp/sessions/carts.html
apache-tomcat-8.0.30/webapps/examples/jsp/sessions/carts.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/sessions/carts.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/sessions/crt.html
apache-tomcat-8.0.30/webapps/examples/jsp/simpletag/foo.html
apache-tomcat-8.0.30/webapps/examples/jsp/simpletag/foo.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/simpletag/foo.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/snp/snoop.html
apache-tomcat-8.0.30/webapps/examples/jsp/snp/snoop.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/snp/snoop.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/source.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/source.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/choose.html
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/choose.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/choose.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/foreach.html
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/foreach.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/foreach.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/howto.html
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/if.html
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/if.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/if.jsp.html
apache-tomcat-8.0.30/webapps/examples/jsp/tagplugin/notes.html
apache-tomcat-8.0.30/webapps/examples/jsp/xml/xml.html
apache-tomcat-8.0.30/webapps/examples/jsp/xml/xml.jsp
apache-tomcat-8.0.30/webapps/examples/jsp/xml/xml.jsp.html
apache-tomcat-8.0.30/webapps/examples/servlets/chat/index.jsp
apache-tomcat-8.0.30/webapps/examples/servlets/chat/index.jsp.html
apache-tomcat-8.0.30/webapps/examples/servlets/chat/login.jsp
apache-tomcat-8.0.30/webapps/examples/servlets/chat/login.jsp.html
apache-tomcat-8.0.30/webapps/examples/servlets/chat/post.jsp
apache-tomcat-8.0.30/webapps/examples/servlets/chat/post.jsp.html
apache-tomcat-8.0.30/webapps/examples/servlets/cookies.html
apache-tomcat-8.0.30/webapps/examples/servlets/helloworld.html
apache-tomcat-8.0.30/webapps/examples/servlets/images/code.gif
apache-tomcat-8.0.30/webapps/examples/servlets/images/execute.gif
apache-tomcat-8.0.30/webapps/examples/servlets/images/return.gif
apache-tomcat-8.0.30/webapps/examples/servlets/index.html
apache-tomcat-8.0.30/webapps/examples/servlets/nonblocking/bytecounter.html
apache-tomcat-8.0.30/webapps/examples/servlets/reqheaders.html
apache-tomcat-8.0.30/webapps/examples/servlets/reqinfo.html
apache-tomcat-8.0.30/webapps/examples/servlets/reqparams.html
apache-tomcat-8.0.30/webapps/examples/servlets/sessions.html
apache-tomcat-8.0.30/webapps/examples/websocket/chat.xhtml
apache-tomcat-8.0.30/webapps/examples/websocket/drawboard.xhtml
apache-tomcat-8.0.30/webapps/examples/websocket/echo.xhtml
apache-tomcat-8.0.30/webapps/examples/websocket/index.xhtml
apache-tomcat-8.0.30/webapps/examples/websocket/snake.xhtml
apache-tomcat-8.0.30/webapps/host-manager/META-INF/context.xml
apache-tomcat-8.0.30/webapps/host-manager/WEB-INF/jsp/401.jsp
apache-tomcat-8.0.30/webapps/host-manager/WEB-INF/jsp/403.jsp
apache-tomcat-8.0.30/webapps/host-manager/WEB-INF/jsp/404.jsp
apache-tomcat-8.0.30/webapps/host-manager/WEB-INF/web.xml
apache-tomcat-8.0.30/webapps/host-manager/images/add.gif
apache-tomcat-8.0.30/webapps/host-manager/images/asf-logo.gif
apache-tomcat-8.0.30/webapps/host-manager/images/code.gif
apache-tomcat-8.0.30/webapps/host-manager/images/design.gif
apache-tomcat-8.0.30/webapps/host-manager/images/docs.gif
apache-tomcat-8.0.30/webapps/host-manager/images/fix.gif
apache-tomcat-8.0.30/webapps/host-manager/images/tomcat.gif
apache-tomcat-8.0.30/webapps/host-manager/images/update.gif
apache-tomcat-8.0.30/webapps/host-manager/images/void.gif
apache-tomcat-8.0.30/webapps/host-manager/index.jsp
apache-tomcat-8.0.30/webapps/host-manager/manager.xml
apache-tomcat-8.0.30/webapps/manager/META-INF/context.xml
apache-tomcat-8.0.30/webapps/manager/WEB-INF/jsp/401.jsp
apache-tomcat-8.0.30/webapps/manager/WEB-INF/jsp/403.jsp
apache-tomcat-8.0.30/webapps/manager/WEB-INF/jsp/404.jsp
apache-tomcat-8.0.30/webapps/manager/WEB-INF/jsp/connectorCiphers.jsp
apache-tomcat-8.0.30/webapps/manager/WEB-INF/jsp/sessionDetail.jsp
apache-tomcat-8.0.30/webapps/manager/WEB-INF/jsp/sessionsList.jsp
apache-tomcat-8.0.30/webapps/manager/WEB-INF/web.xml
apache-tomcat-8.0.30/webapps/manager/images/add.gif
apache-tomcat-8.0.30/webapps/manager/images/asf-logo.gif
apache-tomcat-8.0.30/webapps/manager/images/code.gif
apache-tomcat-8.0.30/webapps/manager/images/design.gif
apache-tomcat-8.0.30/webapps/manager/images/docs.gif
apache-tomcat-8.0.30/webapps/manager/images/fix.gif
apache-tomcat-8.0.30/webapps/manager/images/tomcat.gif
apache-tomcat-8.0.30/webapps/manager/images/update.gif
apache-tomcat-8.0.30/webapps/manager/images/void.gif
apache-tomcat-8.0.30/webapps/manager/index.jsp
apache-tomcat-8.0.30/webapps/manager/status.xsd
apache-tomcat-8.0.30/webapps/manager/xform.xsl
+ rm bin/catalina.bat bin/configtest.bat bin/digest.bat bin/setclasspath.bat bin/shutdown.bat bin/startup.bat bin/tool-wrapper.bat bin/version.bat
+ rm tomcat.tar.gz tomcat.tar.gz.asc
 ---> 6e41a6a72e86
Removing intermediate container 15bf0f303928
Step 11 : EXPOSE 8080
 ---> Running in 2c5a34a5ac8c
 ---> 099290bc73f1
Removing intermediate container 2c5a34a5ac8c
Step 12 : CMD catalina.sh run
 ---> Running in 4ee51e34d75f
 ---> d9fc27780016
Removing intermediate container 4ee51e34d75f
Successfully built d9fc27780016

