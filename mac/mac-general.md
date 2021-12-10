#### How to  find your machine ip

*  System Preferences --> advanced -->  TCP/IP read router or IP.

* command line: 
```
ifconfig | grep "inet " | grep -v 127.0.0.1
```

#### How to  find process using a port
```
sudo lsof -PiTCP -sTCP:LISTEN | grep 9999
```


#### Change to root user in mac 
```
sudo su 
````
