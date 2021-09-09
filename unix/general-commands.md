
# Files commands


#### cp - Copy files

```
cp  myfile yourfile
```
Copy the files "myfile" to the file "yourfile" in the current working directory. This command will create the file "yourfile" if it doesn't exist. It will normally overwrite it without warning if it exists.

With the "-i" option, if the file "yourfile" exists, you will be prompted before it is overwritten.
```
cp -i myfile yourfile
```

#### Change a directory recursive

```
chmod -R 777 MY_DIR
```

# Folders

#### Make directories
```
mkdir myDir
```

#### Find a file 

```
find /dir/to/search -name "file-to-search" -print
````

```
$ find . -name '*.pl'
```

#### mv - change the name of a directory
Type mv followed by the current name of a directory and the new name of the directory.

```
mv myDir newDirName
```

#### Remove an existing directory
```
rmdir myDir
```

#### Removes directories and files within the directories recursively.
```
rm -rf myDir
```

#### pwd - print working directory
It will show you the full path to the directory you are currently in. This is very handy to use, especially when performing some of the other commands on this pag

```
pwd
```

# Process 

#### stop a running process 
CTRL +C : stop a program execution.


#### prints all jobs in details.	

```
ps -A 
```

#### Find all javba progrmas

```
ps -ef | grep java
```

#### Kill a process and for it to stop 

```
kill + process_ids -9 
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

# Basic

#### Concatenate commands 

| this operator is used to concatenate commands.


For example: this example shows the grep command which is searching and printing all lines which contains teh "mysql"
```
chkconfig --list | grep mysql 
```

