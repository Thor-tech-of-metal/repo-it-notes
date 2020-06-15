###  General 

In git we can use HTTPS or SSH.  

a) HTTP uses personal tokens, thes ones are created in your git account.

b) SSH public and privete keys.  These are created per computer under you local (/Users//.ssh/XXX). Then we need to add in git hub the public key.


###  Create SSH in git for MAC

1 create the keys : 

https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

or  
https://github.com/Thor-tech-of-metal/repo-it-notes/blob/master/unix/creating-rsa-keys.md

2) Add the new keys in to the github account.

https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account



### git clone


* git clone ssh

```
[MY REPOSITORY PATH]>git clone ssh://thor@gerrit.dev.monitisechota.net:29418/ep-crap-test


[NOT REPO DIR]>git clone ssh://deroset@gerrit.dev.monitisechota.net:29418/monitisechota-mrs-blackberry-parser  C:\dev-workspaces\repositories\blackberry-parser

```

* git clone git@
```
[MY REPOSITORY PATH]>git clone git@172.16.9.25:dev/api.git
```

* git clone https

```
[MY REPOSITORY PATH] git clone https://github.com/spring-projects/spring-security-oauth.git
```


###  See repo configuration 
```
git config --list
```
###  Change git configuration repo configuration 

```
git config --global --edit
```

```
git config --global user.name "USER_USER"
```


###  Change repo remote 
1) see remote 
```
git remote -v
> origin  https://github.com/USERNAME/REPOSITORY.git (fetch)
> origin  https://github.com/USERNAME/REPOSITORY.git (push)

```
2)  change remote 

```
$ git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
```
