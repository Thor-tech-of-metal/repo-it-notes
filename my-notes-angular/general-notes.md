## Important consepts

There is an angular project with src and gnerates modules. 


## Important files 

*) package.json this is the file where the whole angular project is described, dependecies version and modules. 

*) package-lock.json

It is automatically generated for any operations where npm modifies either the node_modules tree, 
or package.json. It describes the exact tree that was generated, such that subsequent installs are able to generate identical trees, regardless of intermediate dependency updates.

Generates it package-lock.json

```
npm install --package-lock
```
*) yarn.lock this is the file with all dependecies and location to download the dependencies. 

*) angular.json file that describes the angular project.


### yarn

Yarn is a package manager that doubles down as project manager. Similar to gradel. 

0) Every command that you can run in npm, you can also run it using yarn wrapper. 

For instance: List dependencies.


```
npm list
```

```
yarn list
```

1) yarn.lock this is the file with all dependecies and location to download the dependencies. 

2) yarn install (or even just yarn as it will default to install..) and it'll create the yarn.lock if it doesn't already exist. All dependencies versions defined in the package.json will create the modules directories in the projects. 

```
yarn install
```
Force it !!

```
yarn install -f 
```
3) Build a yarn  
```
yarn build
```
4) Build a yarn module defined as script in package.json 
```
yarn build:esm
```

3) start the server
```
yarn start
```

4) start the server in DEBUG mode.
```
NODE_ENV=dev DEBUG='ccd-case-activity-api:*' yarn start
```
