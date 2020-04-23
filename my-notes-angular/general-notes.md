## Important consepts 

### yarn

Yarn is a package manager that doubles down as project manager. Similar to gradel. 

1) yarn.lock this is the file with all dependecies and location to download the dependencies. 

2) yarn install (or even just yarn as it will default to install..) and it'll create the yarn.lock if it doesn't already exist.

```
yarn install
```

## Important files 

package.json


package-lock.json

It is automatically generated for any operations where npm modifies either the node_modules tree, 
or package.json. It describes the exact tree that was generated, such that subsequent installs are able to generate identical trees, regardless of intermediate dependency updates.

Generates it package-lock.json

```
npm install --package-lock
```

npm
