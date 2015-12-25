Install wget in Mac OS X
========
curl -O http://ftp.gnu.org/gnu/wget/wget-1.14.tar.gz
tar xvzf wget-1.14.tar.gz
cd wget-1.14
./configure --with-ssl=openssl
make
sudo make install

