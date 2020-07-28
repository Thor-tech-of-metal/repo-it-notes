# Files commands

#### Change a directory recursive

chmod -R 777 MY_DIR



# Network

#### Find the application which is using a particular port 

*) netstat -ap tcp | grep -i "listen"

In mac 
*) sudo lsof -PiTCP -sTCP:LISTEN | grep 4452
