### Create the project 
```
cd /home/skynet/mis_cosas/synchronized-content/git-repositories/angular/example1

ng new ng7-pre
```


### Create components and serivies

```
ng generate component nav // output

ng g c about // output

ng g c contact // output

ng g c home // output

ng generate service data
```


###  Run ng serve
```
ng serve -o
```

### Deploy
```
ng build 

or in prod

ng build --prod
```

### Run in production
```
cd dist
http-server -o
```