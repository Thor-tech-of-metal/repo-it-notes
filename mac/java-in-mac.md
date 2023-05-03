#### install java manually 

In mac all java SDK are located on /Library/Java/JavaVirtualMachines/

1) download your SDK from https://www.openlogic.com/openjdk-downloads
2) unzip the file in /Library/Java/JavaVirtualMachines/
3) make sure to follow the directories conventions for insatnce for openjdk 11 openjdk-11.0.18.jdk/Contents/Home
4) add it using jenv 
```
jenv add  /Library/Java/JavaVirtualMachines/openjdk-11.0.18.jdk/Contents/Home
```

#### install latest java using brew

```
brew cask install java
```

#### Information

* install location '/Library/Java/JavaVirtualMachines/openjdk-12.0.1.jdk'.


### Install an specific version

0) update brew 
```
brew update --cask 
brew tap caskroom/cask
brew install brew-cask-completion
```

1) search for the available versions 
```
brew search "java11" --casks
```
or 

```
brew cask info java11
```
2) Install the version 

```
brew cask install java11
```

### all about java SDK and brew

http://kabiliravi.com/index.php/software/programming/my-java-tutorial/install-java/install-java-on-mac/

### Java 8 or any SDK nor supported by brew 

* you need to download it from oracle. 
* install in /Library/Java/JavaVirtualMachines
