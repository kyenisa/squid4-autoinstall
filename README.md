
# squid4 for autoinstall  with dns-crypt&unbound
* I use ubuntu 15.04 in session to install this squid4
* my ip address proxy server  192.168.1.200
* dns-nameservers 192.168.1.1 gateway 192.168.1.1

# replace with your ip address on the config below :
* unbound.conf ---->  replace with the your IP address proxy and domain
* squid.conf ----> replace with your ip address proxy
* rc.local ----> replace with your ip address proxy

# repository by indonesia server
```bash
# local repostiroy ubuntu 15.04:
* Indonesia-repository-server:
deb http://id.archive.ubuntu.com/ubuntu/ vivid main restricted universe multiverse
deb http://id.archive.ubuntu.com/ubuntu/ vivid-security main restricted universe multiverse 
deb http://id.archive.ubuntu.com/ubuntu/ vivid-updates main restricted universe multiverse
* local-repository-server-Kambing.ui.ac.id:
deb http://kambing.ui.ac.id/ubuntu/ vivid main restricted universe multiverse
deb http://kambing.ui.ac.id/ubuntu/ vivid-updates main restricted universe multiverse
deb http://kambing.ui.ac.id/ubuntu/ vivid-security main restricted universe multiverse
deb http://kambing.ui.ac.id/ubuntu/ vivid-backports main restricted universe multiverse
deb http://kambing.ui.ac.id/ubuntu/ vivid-proposed main restricted universe multiverse
```
#installation
###already finish installation server,webserver
start the installation with git clone
```bash
#installasi complete software 
apt-get install devscripts build-essential openssl libssl-dev fakeroot libcppunit-dev pkg-config libsasl2-dev cdbs ebtables bridge-utils libcap2 libcap-dev libcap2-dev sysv-rc-conf iproute kernel-package libncurses5-dev fakeroot wget bzip2 debhelper linuxdoc-tools libselinux1-dev htop iftop dnstop perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions python ccze pastebinit checkinstall libssl-dev htop iftop iptraf mtr-tiny bwm-ng ccze sysv-rc-conf devscripts build-essential openssl libssl-dev fakeroot libcppunit-dev libsasl2-dev cdbs ccze libfile-readbackwards-perl libcap2 libcap-dev libcap2-dev libnetfilter-conntrack-dev libfile-readbackwards-perl -y
apt-get install git g++-4.4 -y
git clone https://github.com/puji122/squid4-autoinstall.git
cd squid4-autoinstall
chmod +x squid4.sh
./squid4.sh
```

## after reboot 
```bash
delete dns-nameservers di /etc/network/interfaces or comment #dns-nameservers
/etc/init.d/networking restart
squid -k reconfigure
/etc/init.d/squid restart
/etc/init.d/unbound restart
dig google.com
unbound-control stats tail -16
tail -f /var/log/squid/access.log
```
