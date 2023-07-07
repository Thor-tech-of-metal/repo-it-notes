#### install brew 
```
 ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```


#### brew instalation path 

All brew inslation ended up in this location

```
/usr/local/Cellar/gradle/5.5/libexec/bin/gradle
```


#### Brew short cuts instlations 

brew creates short cuts in /usr/local/bin/ for each instalation for instance for gradle it creates  /usr/local/bin/gradle file 
This file points to /usr/local/Cellar/gradle/5.5/libexec/bin/gradle

this file looks like this:
```
#!/bin/bash
JAVA_HOME="${JAVA_HOME:-$(/usr/libexec/java_home)}" exec "/usr/local/Cellar/gradle/5.5/libexec/bin/gradle" "$@"
```


#### install 

```
brew install kubernetes-helm
```

#### see all programs installed by brew
```
brew list 
```

#### remove a program 
```
 brew uninstall yarn  
```

#### remove

```
brew uninstall --ignore-dependencies kubernetes-helm
```


#### info about a program

```
brew info kubernetes-helm
```

#### Find where a package has been installed

all packages tends to be installed in /usr/local/Cellar/ and /usr/local/opt/
```
brew --prefix nodejs
```

#### Get possible packages in 

```
brew search gradle
```
output -- > gradle homebrew/versions/gradle@7

#### Install a specific package
```
brew install homebrew/versions/gradle@7 
```

#### versions 

```
brew versions kubernetes-helm
```

#### Update 

```
brew update
```
#### Update and upgrade

```
brew update && brew upgrade azure-cli
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



#### search in cask repository

```
brew cask info java
```






