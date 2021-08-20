# Files commands

#### Change a directory recursive

```
chmod -R 777 MY_DIR
```

# Process 
#### Find all javba progrmas

```
ps -ef | grep java
```

#### Find who is using the 8080 port

```
lsof -i :8080 | grep LISTEN
```

# Network

#### Find the application which is using a particular port 

```
netstat -ap tcp | grep -i "listen"
```

In mac

```
sudo lsof -PiTCP -sTCP:LISTEN | grep 4452
```

