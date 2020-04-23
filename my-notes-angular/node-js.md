
### Install node js fedora
1) update and install it using yum 
```
curl -sL https://rpm.nodesource.com/setup_8.x | bash -

yum install -y nodejs
```

### Install node js mac

1) go to https://nodejs.org/en/download/ , download and install the mac version. 

2) check the installed version 
```
node -v
```


### Install packaged 

```
npm install 
```

### Update to latest packaged 

1) (force) clear you npm cache
```
sudo npm cache clean -f 
```
2) install n (this might take a while)
```
sudo npm install -g n 
```
3) to the current stable version
```
sudo n stable upgrade 
```

### Update to particular verson 12.14.1
```
sudo n 12.14.1
```

### Development server
```
npm start
```

