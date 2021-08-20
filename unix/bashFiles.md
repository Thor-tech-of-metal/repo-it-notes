How to run a sh file.
=====================

0) make sure that file.sh contains the magic commnad.
```
#!/bin/sh
```
1)change permissions
```
[root@thor worspaces_development]# chmod u+x file.sh
```
2) run it
```
[root@thor worspaces_development]# ./file.sh
```
How to use and pass parameters
==============================

Use $1" or $2" to retrive command line arguements.
```
[root@thor worspaces_development]# ./backup.sh pepe.zip
```
```
fileName="$1"
zip $fileName $directory -r
```
