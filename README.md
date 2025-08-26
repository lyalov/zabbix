Домашнее задание к занятию «Система мониторинга Zabbix» Ялов Л.В
![alt text](https://github.com/lyalov/zabbix/blob/main/login.jpg)
![alt text](https://github.com/lyalov/zabbix/blob/main/login.jpg)


apt update
nano /etc/ssh/sshd_config
systemctl restart ssh
wget https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest+debian13_all.deb
sudo dpkg -i zabbix-release_latest+debian13_all.deb
sudo apt update
dpkg -i zabbix-release_latest+debian13_all.deb
apt install apache2 libapache2-mod-php   php php-mysql php-ldap php-bcmath php-mbstring php-gd php-xml
