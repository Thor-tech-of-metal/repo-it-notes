#### Install jenv

```
brew install jenv
```

1) Add in the  ~/.bash_profile

```
# Init jenv
if which jenv > /dev/null; then eval "$(jenv init -)"; fi
export JENV_ROOT=/usr/local/var/jenv
```


2) Go to  /Library/Java/JavaVirtualMachines/ and make sure you add all SDK /Library/Java/JavaVirtualMachines/


```
jenv add /Library/Java/JavaVirtualMachines/jdk1.7.0_79.jdk/Contents/Home/
jenv add /Library/Java/JavaVirtualMachines/jdk1.8.0_66.jdk/Contents/Home/
```

#### How to run jenv 

Set java home  version.

```
export PATH="$HOME/.jenv/bin:$PATH"
export JENV_ROOT=/usr/local/var/jenv
eval "$(jenv init -)"
```


#### Add a VM 
Find all installed java VM in /Library/Java/JavaVirtualMachines/

```
jenv add jenv add  /Library/Java/JavaVirtualMachines/jdk-17.0.3.1.jdk/Contents/Home 
```


#### See all versions

```
jenv versions
```

#### select a VM in a local directory
```
cd myDir

jenv local openjdk64-12.0.1
```
