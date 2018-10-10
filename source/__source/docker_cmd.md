找環境源
sudo docker search ubuntu -f is-official=true
 
拉下環境源
docker pull ubuntu
 
目前image
docker images
 
執行image
docker run -it ubuntu /bin/bash 

docker run -it test_img /bin/bash 

docker rm
docker rmi

sudo docker build . -t test_img --no-cache



<!-- apt-get -y install libsnmp-dev
apt-get install snmpd -->
<!-- RUN apt-get -y install libsnmp-dev -->
<!--  -->

pip install --upgrade pip
pip install robotframework
pip install requests


apt-get install libperl-dev
apt-get install wget -y
mkdir netsnmp_download
cd netsnmp_download
wget -P /netsnmp_download https://sourceforge.net/projects/net-snmp/files/net-snmp/5.8/net-snmp-5.8.tar.gz
tar zxvf net-snmp-5.8.tar.gz
cd net-snmp-5.8


tar -zxvf net-snmp-5.7.2.tar.gz
cd net-snmp-5.7.2
./configure --prefix=/usr/local/netsnmp --with-python-modules
make
make install

cd python
python setup.py build
python setup.py test    


cd /home/william_chang

robot -i 4510 --outputdir /home/william_chang/iorobot_suggest/result --variablefile /home/william_chang/iorobot_suggest/device/4510-archlinux/env.py /home/william_chang/iorobot_suggest/testcases/




pip list


