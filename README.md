Домашнее задание к занятию «Система мониторинга Zabbix» Ялов Л.В
ОТВЕТ 1
![alt text](https://github.com/lyalov/zabbix/blob/main/login.jpg)
![alt text](https://github.com/lyalov/zabbix/blob/main/start_zabbix-server.jpg)


apt update
nano /etc/ssh/sshd_config
systemctl restart ssh
wget https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest+debian13_all.deb
sudo dpkg -i zabbix-release_latest+debian13_all.deb
sudo apt update
dpkg -i zabbix-release_latest+debian13_all.deb
apt install apache2 libapache2-mod-php   php php-mysql php-ldap php-bcmath php-mbstring php-gd php-xml


#Создаем учетку и базу в postgress
sudo -u postgres psql
CREATE USER zabbix WITH PASSWORD 'zabbix';
CREATE DATABASE zabbixdb OWNER zabbix;
\q
#Копируем схему в базу 
zcat /usr/share/zabbix/sql-scripts/postgresql/server.sql.gz | sudo -u postgres psql -d zabbixdb
#Разрешаем ходит zabbix учетки в базу
# Редактируем фаил /etc/postgresql/17/main/pg_hba.conf

local   all             zabbix                                  md5

#В конфиг  /etc/zabbix/zabbix_server.conf добавляем подключение
DBHost=localhost
DBName=zabbixdb
DBUser=Zabbix
DBPassword=zabbix
#Добавляем права на папку 
chown zabbix:zabbix /run/zabbix
ОТВЕТ 2
![alt text](https://github.com/lyalov/zabbix/blob/main/agents.jpg)
![alt text](https://github.com/lyalov/zabbix/blob/main/statistic.jpg)
