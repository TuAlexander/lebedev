Лебедев Николай "Система мониторинга Zabbix"


### Задание 1

Скриншот авторизации в Zabbix под админом
https://github.com/Niko1a/lebedev/blob/main/Снимок%20экрана%20от%202023-10-27%2009-45-07.png

wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.0-4+ubuntu22.04_all.deb
dpkg -i zabbix-release_6.0-4+ubuntu22.04_all.deb
apt update
apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
sed -i 's/# DBPassword=/DBPassword=123456789/g' /etc/zabbix/zabbix_server.conf 
su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD '\'123456789\'';"'
su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'
find / -name zabbix agentd.conf
nano /etc/zabbix/zabbix_server.conf

### Задание 2

Скриншоты по выполненому заданию
https://github.com/Niko1a/lebedev/blob/main/Снимок%20экрана%20от%202023-10-27%2011-51-33.png
https://github.com/Niko1a/lebedev/blob/main/Снимок%20экрана%20от%202023-10-27%2011-52-36.png
https://github.com/Niko1a/lebedev/blob/main/Снимок%20экрана%20от%202023-10-27%2011-53-41.png

find / -name zabbix_agentd.conf
cat /etc/zabbix/zabbix_agentd.conf | grep Server=
sed -i 's/Server=127.0.0.1/Server=192.168.245.17/g' /etc/zabbix/zabbix_agentd.conf
systemctl restart zabbix-agent.service 
systemctl status zabbix-agent.service 
cat /etc/zabbix/zabbix_agentd.conf | grep Server=
