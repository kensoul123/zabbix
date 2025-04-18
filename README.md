1 Задание
# wget https://repo.zabbix.com/zabbix/7.2/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.2+ubuntu22.04_all.deb
# dpkg -i zabbix-release_latest_7.2+ubuntu22.04_all.deb
# apt update
apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent
# mysql -uroot -p
password
mysql> create database zabbix character set utf8mb4 collate utf8mb4_bin;
mysql> create user zabbix@localhost identified by 'password';
mysql> grant all privileges on zabbix.* to zabbix@localhost;
mysql> set global log_bin_trust_function_creators = 1;
mysql> quit;
# zcat /usr/share/zabbix/sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix
# mysql -uroot -p
password
mysql> set global log_bin_trust_function_creators = 0;
mysql> quit;
DBPassword=password
# systemctl restart zabbix-server zabbix-agent apache2
# systemctl enable zabbix-server zabbix-agent apache2
2 задание 
# wget https://repo.zabbix.com/zabbix/7.2/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.2+ubuntu22.04_all.deb
# dpkg -i zabbix-release_latest_7.2+ubuntu22.04_all.deb
# apt update
# apt install zabbix-agent
# systemctl restart zabbix-agent
# systemctl enable zabbix-agent
 nano /etc/zabbix/zabbix_agentd.conf
 systemctl restart zabbix-agent.service
 sed -i 's/Server=127.0.0.1/Server=192.168.99.106/g' /etc/zabbix/zabbix_agentd.conf
 systemctl restart zabbix-agent.service
 systemctl restart zabbix-agent.service
 tail -f /var/log/zabbix/zabbix_agentd.log
