
### How to merge manually 


This in approach we update our branch WIFI-5886-add-billing-ref and push the changes in to our branch WIFI-5886-add-billing-ref.

* step1: Checkout WIFI-5886-add-billing-ref
* step2: Fetch from origin/master to update my local repo.
* step3: Merge my branch WIFI-5886-add-billing-ref with remote dev.
* step4: Commit changes in to WIFI-5886-add-billing-ref.
* step5: push my merged WIFI-5886-add-billing-ref.

1 
```text
git checkout WIFI-5886-add-billing-ref
git fetch origin
git merge origin/dev
```

2  If there are conflicts you will see something like this:
```text
     Auto-merging src/main/java/com/o2wifi/olympus/engine/OrderLogic.java
     CONFLICT (content): Merge conflict in src/main/java/com/o2wifi/olympus/engine/OrderLogic.java
     Auto-merging src/main/java/com/o2wifi/olympus/domain/order/ProvideOrderRequest.java
     Auto-merging src/main/java/com/o2wifi/olympus/btw/builder/OrderBuilder.java
     Automatic merge failed; fix conflicts and then commit the result.
```

3 resolve conflicts manually in src/main/java/com/o2wifi/olympus/engine/OrderLogic.java

4 Add the merged file src/main/java/com/o2wifi/olympus/engine/OrderLogic.java
 ```
 git add src/main/java/com/o2wifi/olympus/engine/OrderLogic.java
```

5 commit the changes and use -a  
```text
git commit -a
```


6 Push the code. 

```text
git push origin  WIFI-5886-add-billing-ref
```


