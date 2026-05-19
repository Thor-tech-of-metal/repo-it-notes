## forkJoin Subscribe
What forkJoin is doing here
forkJoin (from RxJS) is used to execute multiple Observables in parallel and wait for all of them to complete before emitting a single combined result.

```
forkJoin({
      paymentGroup: this.paymentViewService.getApportionPaymentDetails(this.paymentLibComponent.paymentReference),
      statuses: this.statusHistoryService.getPaymentStatusesByReference(this.paymentLibComponent.paymentReference,
                                                                        this.paymentLibComponent.paymentMethod)
    }).subscribe(
      ({ paymentGroup, statuses }) => {
        this.statuses = statuses;
        statusHistory.status
        //some code 
       },
      (error: any) => this.errorMessage = <any>error.replace(/"/g, "")
    );
```
Two HTTP calls (Observables) are triggered at the same time:

* getApportionPaymentDetails(...)
* getPaymentStatusesByReference(...)

forkJoin:

* waits until both requests complete successfully
* then emits a single object:  TypeScript{  paymentGroup: <result of first call>,  statuses: <result of second call>}Show more lines
* The destructuring in .subscribe():

Important behavior:

* If either request fails, the entire forkJoin fails and goes to the error handler.
* It only emits once (after both complete), unlike combineLatest which emits continuously.

