
### npm
npm isused  to administrate packages , install programs and versioning. It will update package.json and also generate package-lock.json



### install
```
npm install
```

### see verision availables , for instance yarn
```
npm view webpack versions --yarn
```

### install a specific version, it will update package.json
```
sudo npm install -g yarn@3.5.1 
```



### Installl a module specific version it will update package.json
```
npm install -g @angular/cli@7.1.4 
```

### Evaluate the health of one dependency
```
npm ls @angular/compiler-cli 
```
### Evaluate the health of the dependencies
```
npm audit --force
```

### print transitive dependecies
```
npm list 
```

### Evaluate transitive dependecies 

install npm-remote-ls
```
npm install npm-remote-ls -g
```
use npm-remote-ls to print transitive dependecies of sha@1.2.4
```
npm-remote-ls sha@1.2.4
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
sudo npm stable 
```
Setup Binary Link 
```
sudo ln -sf /usr/local/n/versions/node/11.8.0/bin/node /usr/bin/node
```

```
node -v
```

