
### yarn
It used to administarte packages dependencies and resolutions cves.  yarn will read package.json and generate yarn.lock and update node_modules  folder. 



### yarn files
```
package.json   //  --> this is the file where we add the dependences and resolutions etc
yarn.lock     //  --> this is the generated file by yarn with all dependences, resolutions and checksums
yarn-audit-known-issues // --> this is the file will all CVS resolutions and others
yarn-error.log  // --> build errors 
```



### Install a yarn version using npm 

1) see available version 
```
npm view webpack versions --yarn
```
2) install a version.
```
sudo npm install -g yarn@3.5.1 
```

### set verision of yarn for a particlar project. It will update the pakacke.json

```
yarn set version 3.5.1
yarn install 
```

### check version of yarn
```
yarn -v
```
### create yarn.lock file with the content of package.json  
```
yarn install 
```

### Add a package and modify package.json
```
yarn add "express@^4.15.4"
```

### See all possible ways to run yarn according the package.json
```
yarn run 
```


###  beautiful view 
```
 yarn set version berry
```

###  clean cache and modules

```
rm -rf node_modiles/
rm package-lock.json
rm yarn.lock
```
or 
```
yarn cache clean
```
###  set my yarn version
```
yarn set version 3.6.2 
```

 
### yarn to find deprecated dependencies
```
yarn audit
```
or use npm 
```
yarn npm audit --recursive --environment production
```

Cves can be fixed using resolutions section in the package . json
```
},
"resolutions": {
  ..
  "cookiejar": "2.1.4",
  "qs": "6.7.3"
}
```
### yarn to fix deprecated dependencies and add them in to the yarn-audit-known-issues file.
yarn-audit-known-issues this file has all already known dependencies issues

```
yarn npm audit --recursive --environment production --json > yarn-audit-known-issues
```
