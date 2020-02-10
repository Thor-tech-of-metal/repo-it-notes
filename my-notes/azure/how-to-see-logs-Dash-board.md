### Subscription

My user has many subscriptions.  All searches are liked to the subscriptions visibility. Every time that we look for a resource (Azure Obejct such us insight, resource group, AKS cluster etc  )
We need to have selected all subscriptions.     [ See enclosed image.](./Checl-all-subcriptions-for-my-user.png) . 


### Azure Obejcts that I can see from the dashboard

* AKS clusters 
* Resource grup
* App Services (VM)
* Application insight
* Container registry for docker images.


### Application insight


you can see all insight for a resource or cluester.

1 From search just put the name of the application insight. It will be easier for search.

2 click search button for the insight

3 click the filter button and on the left chose cloud role by name .


Instrumentation Key 64f7ac38-53a2-44db-9dc6-384081b686c5



### How to see logs errors


1 chose your resource group ( make sure to have all Subscription selected. )

2 go to settings -->  Application Insights

3 chose view application "data-store-api-aat - Application Insights"

4 chose --> Failures --> chose one particular error and then chose --> Drill into... see logs

### Query from the longs


1 How to query from the longs for NoHttpResponseException
```
let startDateTime = datetime('2020-02-06T13:30:00.000Z');
let endDateTime = datetime('2020-02-06T14:40:00.000Z');
let ContainerIdList = KubePodInventory
| where TimeGenerated >= startDateTime and TimeGenerated < endDateTime
| where ClusterId contains 'perftest-0'
| distinct ContainerID;
ContainerLog
| where TimeGenerated >= startDateTime and TimeGenerated < endDateTime
| where ContainerID in (ContainerIdList)
| where LogEntry contains 'NoHttpResponseException'
| project LogEntrySource, LogEntry, TimeGenerated, Computer, Image, Name, ContainerID
| order by TimeGenerated desc
| render table

```

2 How to query from the longs for  request operation_Id . Every reaquest has a unique id which is called operation_Id.

```
requests
| where operation_Id =='b2d24ccef3ea43038b64edcfedb00b19'
| limit 10
````

### Images group

1) go to All resources --> search for "hmctspublic" --> chose repositories --> search  "ccd/data-store" --> click --> search "pr-xxx" Chose the latest one.


find my images: 1) check in your PR the images number 2) Go to azure and find it repository, search tete/definition-store-api and see all images versions . See enclosed picture images-repo.png






