### build
```
npm install
```

### start the server
```
npm start
```


### Upgrade Node.Js Fedora
```
node -v 
```
 Now clean all npm cache from your system forcefully
```
sudo npm cache clean -f 
```
Install n module 
```
sudo npm install -g n 
```

Install Nodejs  latest
```
sudo n stable 
```
Setup Binary Link 
```
sudo ln -sf /usr/local/n/versions/node/11.8.0/bin/node /usr/bin/node
```

```
node -v
```

### Evaluate the health of one dependency
```
npm ls @angular/compiler-cli 
```
### Evaluate the health of the dependencies
```
npm audit --force
```


