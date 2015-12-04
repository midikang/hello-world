How to set http proxy for git command
========
To set http proxy without authentication
* git config --global http://proxyserver:port

To set http proxy with user and password
* git config --global http.proxy http://user:password@proxyserver:port

To check http proxy settings
* git config --get --global http.proxy

To remove http proxy settings
* git config --system --unset http.proxy
