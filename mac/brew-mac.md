#### install brew 
```
 ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

#### install 

```
brew install  kubernetes-helm
```

#### install from cask repository

```
brew cask install java
```

#### install a particular version

```
brew search "java11" --casks
```
or 
```
brew cask info java11
```

Install java11

```
brew install "java11"
```

#### remove

```
brew uninstall --ignore-dependencies kubernetes-helm
```

#### versions 

```
brew versions kubernetes-helm
```

#### search in cask repository

```
brew cask info java
```

#### info

```
brew info kubernetes-helm
```

#### Find where a package has been installed

all packages tends to be installed in /usr/local/Cellar/ and /usr/local/opt/
```
brew --prefix nodejs
```

#### Update 

```
brew update
```

#### link 

brew always links the program with a current version.  when you do ``` brew search node```  you see the current linked. and available versions. 

```
sudo chown -R $USER /usr/local
 
brew link --overwrite node
```

#### unlink 
```
brew unlink node
```


