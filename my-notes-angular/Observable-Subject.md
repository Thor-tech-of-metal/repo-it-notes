## Observable & Subject


The way to communicate between components is to use an **Observable and a Subject**  (which is a type of observable).
There are two methods that we're interested in: **Observable.subscribe() and Subject.next()**.


## Observables are lazy
You could think of lazy observables as newsletters. For each subscriber a new newsletter is created. They are then only send to those people, and not to anyone else.


##### Observable.subscribe()

The observable subscribe method is used by angular components to subscribe to messages that are sent to an observable.

##### Subject.next()

**this.subject.next(mesages)** The subject next method is used to send messages to an observable which are then sent to all angular components that are subscribers (a.k.a. observers) of that observable.
Many components can be  are subscribed to a  Subject. 

**this.subject.next()** without any arguments, the logic to clear the messages when an empty message is received is in the app component below.

```
@Injectable({ providedIn: 'root' })
export class MessageService {

    //This is the main topic or subject 
    private subject = new Subject<any>();
    
    //This is for sending a msg
    sendMessage(message: string) {
        this.subject.next({ text: message });
    }

    clearMessages() {
        this.subject.next();
    }
    
    //This return the subject or topic as Observable
    
    getMessage(): Observable<any> {
        return this.subject.asObservable();
    }
}
```

Then MessageService will be injected in the constructor

##### App Component that Receives Messages.

This component uses  this.messageService.getMessage().subscribe(message => { ... } )

```
export class AppComponent implements OnDestroy {
    messages: any[] = [];
    subscription: Subscription;

    constructor(private messageService: MessageService) {
        // subscribe to home component messages
        this.subscription = this.messageService.getMessage().subscribe(message => {
          if (message) {
            this.messages.push(message);
          } else {
            // clear messages when empty message received
            this.messages = [];
          }
        });
    }

    ngOnDestroy() {
        // unsubscribe to ensure no memory leaks
        this.subscription.unsubscribe();
    }
}
```
##### Component that Sends Messages.

```
export class HomeComponent {
    constructor(private messageService: MessageService) { }

    sendMessage(): void {
        // send message to subscribers via observable subject
        this.messageService.sendMessage('Message from Home Component to App Component!');
    }

    clearMessages(): void {
        // clear messages
        this.messageService.clearMessages();
    }
}
```

## The use of pipes. 

pipe() and map()  can be used to manipulate data before completing the Observable. pipe() also receive delay()

```
const appDiv: HTMLElement = document.getElementById('app');
appDiv.innerHTML = `<h1>Simulating HTTP Requests Using RxJs Delay</h1>`;

type Post = { title: string, content: string };

const post:Observable<Post> = of( {title: 'Simulating HTTP Requsts', content: 'This is off the hook!!'})
.pipe(delay(1000))
.pipe( p => { 
  console.log('after the delay'); 

  return of( { title: 'new value', content: 'new value !!'}) 
 } ) 
.pipe(delay(2000));


post.subscribe( post =>{ 
      console.log('this is the final value for post after all pipes')
      console.log(post);
    }
  );
```