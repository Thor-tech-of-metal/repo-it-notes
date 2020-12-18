### Git clone

```
git clone HTTPS_URL
```

### Git status
List which files are staged, unstaged, and untracked. It shows files to be added and files to be commit-ed.

*)Show the status of between the repository and the working directory

* It is used to monitor the state between the repository and the working directory.
* It shows what is for committing and what is not synchronized with the remote repo. 
* Git status always suggest what to do. 
```text

git status
     # On branch master
     # Changes to be committed:
     #   (use "git reset HEAD <file>..." to unstage)
     #
     #     modified:   hello.rb
     #
     # Changes not staged for commit:
     #   (use "git add <file>..." to update what will be committed)
     #   (use "git checkout -- <file>..." to discard changes in working directory)
     #
     #     modified:   hello.rb

```

* Changes to be committed: The first change is staged and is ready "to be committed".
* Changes not staged for commit: The second change is unstaged and not ready to commit.


### Branch commands


* See all local branches 

```
git branch
```

* List remote Branches commands
```
git branch -r
```

* Build a new branch based on a remote branch

```
git checkout -b myLoalBranch  origin/develop
```

* Build a new branch base on the current branch. When the current branch is RDM-9939 
```
git branch RDM-9939-backUp
```

* It will create a new branch from a specific commit point.
 
 1 get the commit point 
 ```text
 git reflog  
```

2 use it in the command line for instance 04e2ab5 HEAD@{8}:
```text
git checkout -b PRE_REBASE 04e2ab5 

```


### Commits commands

* How to commit a new file 

1 git status see the files that needs to added to git
```text
git status
```
2 add the new file to the repo. 
```text
git add myFiles.txt

```
3 commit 

```text
git commit -m 'my hola mundo changes'
```

* Show files in a commit.

```
git diff-tree --no-commit-id --name-only -r 6f112e80ef702af6f2e8b1381828fc148d9f262c
```

```
git show --pretty="" --name-only 6f112e80ef702af6f2e8b1381828fc148d9f262c
```

* Rewrite your last commit message
```
git commit -v --amend -m"new message !!"
```
The -v is optional, but I like it because it shows a lot of information about the changes which helps me to write a more descriptive commit message.

* Commit files with resolver merge conflicts

```text
git commit -a
```

* How amend deleted file/s to previous commit
```text
 delete tobias.txt
 git add -u    ---------> This tells git to automatically stage all tracked files -- including deleting the previously tracked files. 
 git commit --amend
```

### Log commits messages

* print log tree
```
git log --pretty=oneline --graph --decorate --all
```

* View the log for a specific date range

```
git log --since='FEB 10 2016' --until='FEB 19 2016'
```

* Search for commits that include a keyword
```
git log -S"config.menu_items"
```

* View the log without merge commits

```
git log --oneline --no-merges
```



### Merging code  


* Merge your local branch with a local remote branch 

1 Bring latest from remote in your local remote  
```
git fetch
```

2 Merge your local branch with a local remote branch 
 
```
git merge origin/develop
```

* Pull changes. It brings remote in your local remote and merge it in your local branch
```
git pull origin RDM-5398-BASED-RC1+MV
```

### Merging code in inteliJ 

* go to CVS--> Git--> Pull --> select the branch that you wish to pull from and enjoy the 3 windows merge view!!!

1 Watch this video, it is good.

https://www.youtube.com/watch?v=RxunYSzMNKM

2 At the end after the merge, COMMIT ALL CHANGES.

###  git Stash

Git has a temp directory where you can pup files grouped by stash@{id}. 

```text

git stash --> This create a stash in to the stash stack
git stash list --> Show the whole stack ! 
git stash pop- -> This will return those files added in to the last stash stack to the working directory and allow you to work as before.

git stash clear --> clean the whole stack ! 

git stash apply + ID --> It applies an specific stash change.
git stash apply stash@{2}.git

git stash drop file.txt

```

### Git Reset

*  Reset the staging area to match the most recent commit, but leave the working directory unchanged.
```
git reset
```

* Reset the staging area and the working directory to match the most recent commit.The --hard flag tells Git to overwrite all changes in the working directory, too.
Delete all local changes.
```text
git reset --hard
```


* It reset in to one specific point in the history.
```
git reset <commit number>
```

* It HARD reset in to one specific point in the history. hard reset means it will modify files content.
```text
    git reset --hard <commit number>
```

* Delete a commit without losing local file changes
```text
git reset --soft <commit number>
```

###  Rebase command

git rebase 

* continue 
```
git rebase  --continue 
```
* skip
```
git rebase  --skip
```

* abort
```
git rebase  --abort
```


### Reset

How to undo git added files 
```
git reset my-file.txt
```
### Tricks

* How to revert file changes to local branch version.
```text
git checkout  server/app/controllers/dynamic/EntityController.scala
``` 


* Checkout a single file from another branch
```
git checkout some-other-branch -- yarn.lock
```

*  Checkout a single file from another commit
```
git checkout 9146367 -- yarn.lock
```

*  Get rid of all untracked changes
```
git clean .
```

* Get rid of all untracked changes
```
git clean -f -d
```

