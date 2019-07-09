#### install brew 
```
 ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

#### install 

`brew install  kubernetes-helm`

#### install a particular version

`brew search kubernetes-helm`

#### remove

`brew uninstall --ignore-dependencies kubernetes-helm`

#### versions 
`brew versions kubernetes-helm`

#### Update 

```
brew update
```

#### info

`brew info kubernetes-helm`


#### link 
brew always links the program with a current version.  when you do ``` brew search node```  you see the current linked. and available versions. 



#### unlink 
```brew unlink node```

#### search

```
brew search "java11" --casks
```
or 
```
brew cask info java11
```

#### search in cask repository

`brew cask info java`

#### install from cask repository

`brew cask install java`
