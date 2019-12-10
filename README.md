# KEST2LG05DU
Dagbok linux

28.11 
reyndi að gera static ip, veit ekki hvort thad hafi virkad
static ip commands dæmi
sudo ifconfig
sudo nano /etc/hosts

Bjo til Groups!!!
sudo groupadd testgroup
IT
Management
Accounting
Manufacturing

https://www.howtogeek.com/50787/add-a-user-to-a-group-or-second-group-on-linux/
https://www.techrepublic.com/article/how-to-create-users-and-groups-in-linux-from-the-command-line/
		fullname https://www.tecmint.com/add-users-in-linux/ numer 9
Bjo til testuser,
useradd -m -G testgroup -c "Fyrstanafn Seinnanafn" testuser -p 123

Bæta users vid i groups(ef ekki gert þegar hann er buinn til)
sudo usermod -a -G testgroup testuser
osfv

athuga hvort users seu i group
grep testgroup /etc/group
Setti ovart alla users i primary group en ekki secondary group þannig eg eyddi þeim ollum og setti aftur inn...

https://linuxconfig.org/how-to-configure-samba-server-share-on-debian-9-stretch-linux

03/12/19
Samba server
https://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html

05/12
setup apache server with this guide https://www.tecmint.com/install-apache-with-virtual-hosts-on-debian-10/

setup ssh access but something went wrong, followed this guide https://phoenixnap.com/kb/how-to-enable-ssh-on-debian


08/12/19
MYSQL and PHPMYADMIN
apt get-install mysql-client mysql-server

apt get-install phpmyadmin
select apache2 for web server you are using and phpmyadmin is installed
nano /etc/apache2/apache2.conf
Include /etc/phpmyadmin/apache.conf

mysql -p to login to mysql

create user 'user'@'localhost' IDENTIFIED BY 'password';
grant all privileges on * . * to 'user' for the users in IT group

grant create ON * . * to 'user' and grant drop ON * . * to 'user' for users in Management group

config postfix
https://www.howtoforge.com/how-to-install-and-configure-mailman-with-postfix-on-debian-squeeze

Pure-FTPd
	apt-get install pure-ftpd

	groupadd ftpgroup
	useradd -g ftpgroup -d /dev/null -s /etc ftpuser
	pure-pw useradd remo -u ftpuser -g ftpgroup -d /home/pubftp/remo -N 10
	pure-pw mkdb
	pure-pw list
Quota; https://www.digitalocean.com/community/tutorials/how-to-enable-user-and-group-quotas
	apt-get install quota
	nano /etc/fstab
	edit /etc/fstab to enable quota
	
	mount -o remount /
	quotacheck -cum /
	quotaon /
