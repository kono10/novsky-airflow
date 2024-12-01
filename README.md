# novsky-airflow

### docker
```

sudo yum install docker -y
sudo systemctl start docker
sudo usermod -a -G docker ec2-user
```
check that docker is running
```
sudo systemctl status docker
```
### postgres
```
sudo dnf install postgresql15 postgresql15-server 
sudo postgresql-setup --initdb
sudo systemctl start postgresql
sudo systemctl enable postgresql
sudo systemctl status postgresql
sudo -u postgresql psql
```
```
CREATE USER yourusername WITH PASSWORD 'password';
CREATE DATABASE database_name;
GRANT ALL PRIVILEGES ON DATABASE database_name TO yourusername;
```
https://stackoverflow.com/questions/18580066/how-to-allow-remote-access-to-postgresql-database

```
sudo vim /var/lib/pgsql/

# "local" is for Unix domain socket connections only
local   all             all                                     peer
# IPv4 local connections:
host    all             all             127.0.0.1/32            md5
# IPv6 local connections:
host    all             all             ::1/128                 md5
# Allow replication connections from localhost, by a user with the
# replication privilege.
local   replication     all                                     peer
host    replication     all             127.0.0.1/32            md5
host    replication     all             ::1/128                 md5

host    replication     all             0.0.0.0/0               md5
host    replication     all             ::/0                    md5
```
Uncomment the below line ...
```
sudo vim /var/lib/pgsql/

listen_addresses = '*'                  # what IP address(es) to listen on;
```
```
sudo systemctl restart postgresql
```


* rabbitmq
* python
  * airflow 
