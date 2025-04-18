Домашнее задание к занятию "Система мониторинга Zabbix" - Гречихин Юрий

1 Задание
![image](https://github.com/user-attachments/assets/f0c3d96d-c8ed-4018-921d-52836a262150)
![image](https://github.com/user-attachments/assets/30d8967f-8b2e-419a-aa8a-fe965e797d10)

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
![image](https://github.com/user-attachments/assets/41cd58a4-f440-4568-8e10-50c6f643b050)
![image](https://github.com/user-attachments/assets/6eda8035-fd03-4afe-b481-6cd285e63daf)
![image](https://github.com/user-attachments/assets/e495e99f-345e-44b2-830a-fd808732fc80)
![image](https://github.com/user-attachments/assets/9e75a853-1496-4144-b0b1-7bd51454888e)

 
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
