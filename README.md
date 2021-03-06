EXEApps Snaplabs Backend
=========

A standard EXE Ubuntu DEV  box. It has pre-installed following extentions 

   
  - Redis
  - OrientDB 2.1.6 
  - Rabbit MQ
  - HBase
  - Java 8
  - OpenTBS
  

How Download and Install Vagrant
-----------
* [Download] - download vagrant from their officail website
* [Installation] - follow thier official  installation tutorial
* [Tutorial] - A nice tutorial on setting up dev environment

How to use it
--------------

To intigrate to your project, run following command

```sh
bash < <(curl -s -S -L https://raw.githubusercontent.com/exeapps/snaplabs-backend/master/installer)
```

With provision

```sh
vagrant provision
```

Add IP to your local /etc/host once in developing life circle
```sh
echo "192.168.33.10   local.backend.snaplabs.io" >> /etc/hosts
```


Access vagrant
```sh
vagrant ssh
```


Some important commands
```sh
su vagrant
   
	
sudo echo "JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64" >> /etc/environment
sudo echo "HBASE_HOME=/opt/hbase" >> /etc/environment
source /etc/environment

sudo chown -R vagrant:vagrant  /opt/hbase/bin/start-hbase.sh
sudo chown -R vagrant:vagrant /opt/opentsdb/start.sh
sudo chown -R vagrant:vagrant /opt/orientdb/start.sh 

/opt/orientdb/start.sh
/opt/hbase/bin/start-hbase.sh
/opt/opentsdb/start.sh
```

Vagrant 
--------------

```sh
username: vagrant 
password: vagrant
```

Redis
--------------

```sh
Port: 6379
Cli client: redis-cli -h 192.168.33.10 
```

OrientDB
--------------

```sh
Access Port: 2424
USERNAME : root
PASSWORD : exedev2015
Admin Panel: http://192.168.33.10:2480
```

Rabbit MQ
--------------

```sh
Port: 15672
Config URL: amqp://admin:admin@192.168.33.10
Admin Panel: http://192.168.33.10:15672/
```

HBsae
--------------
```sh
Port: 60010
Admin URL: http://192.168.33.10:60010
```
OpenTBS
--------------

```sh
Admin Panel: http://192.168.33.10:4242
```

Version
----
1.0


[Download]:http://www.vagrantup.com/downloads.html
[Installation]:http://docs.vagrantup.com/v2/installation/index.html
[Tutorial]:http://eftakhairul.com/setting-up-development-enviroment-with-vagrant/
