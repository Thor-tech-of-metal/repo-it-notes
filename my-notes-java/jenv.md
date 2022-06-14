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
