Install cassandra and general useful commands
==============================================

####Install cassandra mac
```
bash> ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
bash> brew install python
bash> sudo easy_install pip
bash> brew install cassandra
```


####Install cassandra Fedora
```
bash> echo $JAVA_HOME 
bash> nano /etc/yum.repos.d/cassandra.repo

add the following: 

[cassandra]
name=Apache Cassandra
baseurl=https://www.apache.org/dist/cassandra/redhat/311x/
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://www.apache.org/dist/cassandra/KEYS

bash> yum -y install cassandra


bash>  systemctl daemon-reload 
```

General Commands
===============

####Start casandra
```
1) bash> cd /usr/local/Cellar/cassandra/3.11.0/bin
2) bash> ./cassandra
```

#### Stop cassandra
```
1) bash> ps -ef|grep cassandra
2) bash> kill -9 34598
```


####Start casandra fedora
```
1) bash> systemctl start cassandra
```


#### Connect to cql cassandra
```
1)  bash> cqlsh 127.0.0.1
```
#### Connect to cql cassandra with credentials
```
bash> cd /usr/local/opt/cassandra22/bin
bash> cql sh  f2d-staging-01 9042 -u cassandra -p cassandra
```

#### Check the node status
```
bash> nodetool status
```

####Stop cassasndra
```
bash>$ ps -ax | grep cassandra
bash> kill PID
```

####Stop cassandra
```
bash>   launchctl stop  /usr/local/opt/cassandra22//homebrew.mxcl.cassandra22.plist
```

#### Restart cassandra  in fedora
```
bash> sudo systemctl restart cassandra
```
#### Cassandra check node status
```
bash>nodetool status
```

#### Cassandra logs
```
bash> tail -f -n 1000 /var/log/cassandra/*.log
bash> tail -n 100 /var/log/cassandra/system.log -f
```

General information and directories
===============


#### Importnat directories
```
conf files: /etc/cassandra
```

####Where's my Cassandra yaml and other property files?
```
/usr/local/etc/cassandra
```

####Where are  my logs?
```
/usr/local/var/log/cassandra/
```

####This can be updated by modifying
```
/usr/local/etc/cassandra/log4j-server.properties
```

####Where's the data/commit log etc (you may need to delete this when playing with different versions / partitioners) ?
```
/usr/local/var/lib/cassandra/data
```

#### Users

cassandra@cqlsh:system_auth> CREATE USER admin WITH PASSWORD '!ns0P0r' SUPERUSER;

####  Tunning memory and others

change  /usr/local/etc/cassandra/cassandra-env.sh

MAX_HEAP_SIZE="400M"
HEAP_NEWSIZE="200M"
