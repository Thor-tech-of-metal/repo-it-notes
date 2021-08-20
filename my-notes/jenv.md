
Install jenv
============

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

See java version
================

```
jenv versions
```

Set local java version
=======================

Set java home locally directory.

1) just in case export your vars 
```
export PATH="$HOME/.jenv/bin:$PATH"
export JENV_ROOT=/usr/local/var/jenv
eval "$(jenv init -)"
```

2) run this commands 
```
jenv local oracle64-1.6.0.65

```

https://andrew-jones.com/blog/managing-multiple-versions-of-java-on-os-x/


https://gist.github.com/tomysmile/a9a7aee85ff73454bd57e198ad90e614

