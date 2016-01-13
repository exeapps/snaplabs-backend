EXE Snaplabs Backend
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

```sh
mkdir snaplabs-backend
cd snaplabs-backend
downlaod Vagrantfile by wget https://eftakhairul_mtl@bitbucket.org/exerepo/snaplabs-backend.git
vagrant up
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
sudo apt-get update
chwon -R vagrant:vagrant  /opt/hbase/bin/start-hbase.sh
chwon -R vagrant:vagrant /opt/opentsdb/start.sh
chwon -R vagrant:vagrant /opt/orientdb/start.sh 
echo "JAVA_HOME=/usr/lib/jvm/java-7-oracle" >> /etc/environment
/opt/hbase/bin/start-hbase.sh
/opt/opentsdb/start.sh
/opt/orientdb/start.sh
env COMPRESSION=NONE /opt/hbase/create_tsdb_tables.sh
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
port: 6379
```

OrientDB
--------------

```sh
Studio Port: 2480
Access Port: 2424
USERNAME : root
PASSWORD : exedev2015
```

Rabbit MQ
--------------

```sh
port: 15672
url: amqp://admin:admin@192.168.33.10
```


OpenTBS
--------------

```sh
port: 4242
```

Version
----
1.0


[Download]:http://www.vagrantup.com/downloads.html
[Installation]:http://docs.vagrantup.com/v2/installation/index.html
[Tutorial]:http://eftakhairul.com/setting-up-development-enviroment-with-vagrant/