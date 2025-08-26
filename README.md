Домашнее задание к занятию «Система мониторинга Zabbix» Ялов Л.В
ОТВЕТ 1
![alt text](https://github.com/lyalov/zabbix/blob/main/login.jpg)
![alt text](https://github.com/lyalov/zabbix/blob/main/start_zabbix-server.jpg)


<pre> ```apt update
nano /etc/ssh/sshd_config
systemctl restart ssh
wget https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest+debian13_all.deb
sudo dpkg -i zabbix-release_latest+debian13_all.deb
sudo apt update
dpkg -i zabbix-release_latest+debian13_all.deb
apt install apache2 libapache2-mod-php   php php-mysql php-ldap php-bcmath php-mbstring php-gd php-xml ``` </pre>


#Создаем учетку и базу в postgress
<pre> ``sudo -u postgres psql
CREATE USER zabbix WITH PASSWORD 'zabbix';
CREATE DATABASE zabbixdb OWNER zabbix;
\q ``` </pre>
#Копируем схему в базу 
<pre> ``` zcat /usr/share/zabbix/sql-scripts/postgresql/server.sql.gz | sudo -u postgres psql -d zabbixdb ``` </pre>
#Разрешаем ходит zabbix учетки в базу
# Редактируем фаил /etc/postgresql/17/main/pg_hba.conf

<pre> ```local   all             zabbix                                  md5``` </pre>

#В конфиг  /etc/zabbix/zabbix_server.conf добавляем подключение
<pre> ```DBHost=localhost
DBName=zabbixdb
DBUser=Zabbix
DBPassword=zabbix
#Добавляем права на папку 
chown zabbix:zabbix /run/zabbix``` </pre>
ОТВЕТ 2
![alt text](https://github.com/lyalov/zabbix/blob/main/agents.jpg)
![alt text](https://github.com/lyalov/zabbix/blob/main/statistic.jpg)
![alt text](https://github.com/lyalov/zabbix/blob/main/log_zabbix-b.jpg)
#Команды 
 <pre> ```apt install -y zabbix-agent``` </pre>
#Далее редактируем /etc/zabbix/zabbix_agentd.conf добавляем и раскоменчиваем строки 
<pre> ```Server=192.168.1.43
ServerActive=192.168.1.43
Hostname=zab-test``` </pre>


  <pre> ```sudo systemctl restart zabbix-agent
  sudo systemctl enable zabbix-agent
  sudo systemctl status zabbix-agent``` </pre>
