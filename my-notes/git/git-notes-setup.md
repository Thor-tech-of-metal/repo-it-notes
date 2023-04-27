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


### Change remote to use ssh

for instance  befta-fw.git was not using ssh and we would like to move ssh . Assuming all keys have been uploaded in git. 

1  see current settings.
```
git config --list
```

result remote.origin.url=https://github.com/hmcts/befta-fw.git

2 change to ssh 
```
git remote set-url origin git@github.com:hmcts/befta-fw.git
```


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


###  Change repo remote from https security mechanism to RSA key
1) see remote 
```
git remote -v
> origin  https://github.com/USERNAME/REPOSITORY.git (fetch)
> origin  https://github.com/USERNAME/REPOSITORY.git (push)

```
2)  Change remote, 

Remote URL has this format 
```
git@github.com:hmcts/something-store-api.git
```
Local has this format:

```
https://github.com/hmcts/something-store-api.git
```

Change using set 

```
$ git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
```
 or simply edit .giit/config file.
 
 
 ###  Troubleshooting 

* Issue 1 
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
SHA256:uNiVztksCsDhcc0u9e8BujQXVUpKZIDTMczCvj3tD2s.
Please contact your system administrator.
Add correct host key in /Users/skynet/.ssh/known_hosts to get rid of this message.
Offending RSA key in /Users/skynet/.ssh/known_hosts:1
RSA host key for github.com has changed and you have requested strict checking.
Host key verification failed.
fatal: Could not read from remote repository.

* Solution 

```
ssh-keygen -R github.com
```

* Issue 2
The authenticity of host 'github.com (140.82.121.3)' can't be established.

* Solution 2

```
ssh-keygen -R 140.82.121.3
```
