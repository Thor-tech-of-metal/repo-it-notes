
### git how to 


* How to recover uncommited changes after a reset --hard.


1) Enter “git fsck --lost-found”.  Running this saves the blobs to an invisible path: .git/lost-found/other

```text
git fsck --lost-found
see output :
dangling blob ed73fca6a51e3eda3585675c93d60ff97c3fa62d
dangling blob ee9377d8fb376b060f14f5461441e6b064b39d5a
dangling blob f1db4e00459096fa628590763f4c8efd6b4b587a
dangling blob f27b9faf629ff28a90d857bc64de23c0d8f130fd
```
These are the recovered files ! !!!

2)  cd .git/lost-found/other

This folder contains all recovered files without the name, location and extension. So .... how I can guess what is what !!

3) grep -rnw '.' -e  'import'
Running that will give us all files that have the object statement. these files are may be scala classes obejct TestAA {}

for example
./53070b26328d8804298a37e39960ba661f87584f:20:    
./2dd42e21c62a15da2643e90957fccf59c945f4be:23:

4) Check each possible scala file and copy it and rename it with the correct scala file name.

resource: https://medium.com/@CarrieGuss/how-to-recover-from-a-git-hard-reset-b830b5e3f60c



