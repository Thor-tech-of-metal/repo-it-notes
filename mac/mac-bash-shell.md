

## Envs
Mac can use bash or Zsh


#### Set up Zsh

Make sure that your terminal start with /bin/zsh/ , Open the Terminal, go to preferences and add in shells open with: "/bin/zsh/" 

#### Change the default schema

install ohmyzsh

https://github.com/ohmyzsh/ohmyzsh


#### set up your env vars Zsh

Mac uses bash shell, so the environment variables can be added to the .zshrc file, for the current user. 
The path to this file can be found using the command

1) Edit your .zshrc
```
cd ~/

vi .zshrc
```
2) Add the following line 

```
export DATA_STORE_DB_HOST="localhost"
```
3) Close the termial and open another one


#### set up your env vars bash

Mac uses bash shell, so the environment variables can be added to the .bash_profile file, for the current user. 
The path to this file can be found using the command

1) Edit your .bash_profile
```
cd ~/

vi .bash_profile
```
2) Add the following line 

```
export DATA_STORE_DB_HOST="localhost"
```
3) Close the termial and open another one 


#### set up  entries in the PATH 

0) cd  edit .bash_profile. or  .zshrc
```
cd ~/
vi  .bash_profile. 
or 
vi  .zshrc
```

1) Add the value between ":" for instance :/my/dir/bin:

```
export PATH=$HOME/bin:$HOME/.nvm:/my/dir/bin:/usr/local/bin:$PATH
```
2) Close the termial and open another one 

NOTE: sometimes it does not work because the /my/dir/bin has not execution permissions.


#### print all env vars 

```
printenv
```

#### Find port in use 
```
sudo lsof -PiTCP -sTCP:LISTEN | grep 4650
```

