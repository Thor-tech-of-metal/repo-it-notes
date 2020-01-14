

## Envs
Mac can use bash or Zsh


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


#### print all env vars 

```
printenv
```
