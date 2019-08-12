## Observable http

Given the http example here are ways to fetch data.

```
@Injectable()
export class HttpClient {

    constructor(
        public http: Http
    ) {}

    public fetchUsers() {
        return this.http.get("/api/users").map((res: Response) => res.json())
    }
}
```
#### Example 1: 
We subscribe to an observable in our template using the async pipe.

```
@Component({ selector: "user-list", templateUrl:  "./template.html", })
export class UserList {

    public users$: Observable<IUser[]>

    constructor(
        public client: HttpClient,
    ) {}

    // do a call to fetch the users on init of component
    // the fetchUsers method returns an observable
    // which we assign to the users$ property of our class
    public ngOnInit() {
        this.users$ = this.client.fetchUsers()
    }
}
```
Template: We use the async pipe to automatically subscribe/unsubscribe to our observable 

```
<!-- -->
<ul class="user__list" *ngIf="(users$ | async).length">
    <li class="user" *ngFor="let user of users$ | async">
        {{ user.name }} - {{ user.birth_date }}
    </li>
</ul>
```

#### Example 2:

We subscribe to the observable ourselves using the actual subscribe() method.

```
@Component({ selector: "user-list", templateUrl:  "./template.html", })
export class UserList {

    public users: IUser[]

    constructor( public client: HttpClient, ) {}
    
    public ngOnInit() {
        this.client.fetchUsers().subscribe((users: IUser[]) => {

            // do stuff with our data here.
            this.users = users
        })
    }
}    
```
template: Easy  

```
<ul class="user__list" *ngIf="users.length">
    <li class="user" *ngFor="let user of users">
        {{ user.name }} - {{ user.birth_date }}
    </li>
</ul>
```