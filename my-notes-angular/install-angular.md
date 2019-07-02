
###Install node js 

curl -sL https://rpm.nodesource.com/setup_8.x | bash -

yum install -y nodejs


###Install angular

npm install -g @angular/cli@6.1.1

###Create the project 

cd /home/skynet/mis_cosas/synchronized-content/git-repositories/angular/example1

ng new ng7-pre


###Star the server 

ng serve -o