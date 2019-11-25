## Angular notes

#### @Component 

```
@Component is a decorator function that specifies the Angular metadata for the component.
  selector— the component's CSS element selector
  templateUrl— the location of the component's template file.
  styleUrls— the location of the component's private CSS styles.
```
#### export class

export class : This is for make it visible so other component can import it.


#### @Injectable any @Injectable Component then can be used by other components

providedIn: 'root':  allows the services to be injected as singleton.

```
@Injectable({ providedIn: 'root' })
export class MessageService { ...... } 
```
<br/>
**For instance: MessageService will be injected in the constructor.**
<br/> <br/>

```
export class AppComponent implements OnDestroy {
    
    constructor(private messageService: MessageService) { }
}
```
<br/>

#### The use of type 

We can create types
```

type Post = { title: string, content: string };
```

We can create instances of the types using of()
```
of( {title: 'Simulating HTTP Requsts', content: 'This is off the hook!!'})
```
<br/>

#### How to define const values in a class

static readonly DOCUMENT_URL

```
class WriteDocumentFieldDefinitions {
  static readonly DOCUMENT_URL = 'document_url';
  static readonly DOCUMENT_BINARY_URL = 'document_binary_url';
  static readonly DOCUMENT_FILENAME = 'document_filename';
  static readonly UPLOAD_ERROR_FILE_REQUIRED = 'File required';
  static readonly UPLOAD_ERROR_NOT_AVAILABLE = 'Document upload facility is not available at the moment';
}
```


#### Functions parameters examples

* A question mark after an identifier means that the parameter is optional. For example:

```
function stringify123(callback?: (num: number) => string) {
  const num = 123;
  if (callback) {
    return callback(num); // (A)
  }
  return String(num);
}
```

```
function buildName(firstName = "Will", lastName: string) {
    return firstName + " " + lastName;
}
```

* ...restOfName: string[])
```
function buildName(firstName: string, ...restOfName: string[]) {
    return firstName + " " + restOfName.join(" ");
}

let buildNameFun: (fname: string, ...rest: string[]) => string = buildName;

// employeeName will be "Joseph Samuel Lucas MacKinzie"
let employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
```

* Anonymous function
```
let myAdd = function(x, y) { return x + y; };

const filterFx = function (el) { return el != null; }

let myAdd2 = function(x: number, y: number): number { return x + y; };
```

####	Scopes


*  This scope can change if it inside a function scope. Make sure `this` is unusable in this standalone function.  Make sure `this` is unusable in this standalone function

```
function f(this: void) {
    // make sure `this` is unusable in this standalone function
}

// Bad this !!!!!
class Handler {
    info: string;
    onClickBad(this: Handler, e: Event) {
        // oops, used `this` here. using this callback would crash at runtime
        this.info = e.message;  <--- NO !
    }
}
// Good this 

class Handler {
    info: string;
    onClickGood(this: void, e: Event) {
        // can't use `this` here because it's of type void!
        console.log('clicked!');
    }
}
let h = new Handler();
uiElement.addClickListener(h.onClickGood);

```
* We can define an scope and assing it to a variable. let deck: Deck = { .. } . Then access to functions declared inside the scope.

* This can also refer to the function internal scope.  let cardPicker = deck.createCardPicker();

```
interface Card {
    suit: string;
    card: number;
}
interface Deck {
    suits: string[];
    cards: number[];
    createCardPicker(this: Deck): () => Card;
}
let deck: Deck = {
    suits: ["hearts", "spades", "clubs", "diamonds"],
    cards: Array(52),
    // NOTE: The function now explicitly specifies that its callee must be of type Deck
    createCardPicker: function(this: Deck) {
        return () => {
            let pickedCard = Math.floor(Math.random() * 52);
            let pickedSuit = Math.floor(pickedCard / 13);

            return {suit: this.suits[pickedSuit], card: pickedCard % 13};
        }
    }
}

let cardPicker = deck.createCardPicker();
let pickedCard = cardPicker();

alert("card: " + pickedCard.card + " of " + pickedCard.suit);
```

####	Characters ||
```
var title = title || "Error";
```

Basically checks if title evaluates to false. If it does, it "returns" "Error", otherwise it returns title.
```
if (!title) {
  title = "Error";
}
```


#### Key values Pairs

```
let caseValueComponentId = 'pepe';

const keyValue = {
  document_url: 'value1',
  'document_binary_url': 'value2',
  [this.caseValueComponentId]: 'value3'
}
```
The result will be a key-value pair like this. [(document_url,value1),(document_binary_url,value2 ).(pepe,value3)]
<br/>

#### @ViewChild('fileInput')

@ViewChild is used to associate an dom element to angular ElementRef. with ElementRef we can do things at html dom level.

For instance capture click in and click out.

```  
@ViewChild('fileInput') fileInput: ElementRef;


@HostListener('document:click', ['$event'])
  clickout(event) {
    //Capturing the event of of the associated  ElementRef <input type="file" #fileInpu

    if(this.fileInput.nativeElement.contains(event.target)) {
      this.clickInsideTheDocument=true
      console.log("clicked inside");
    } else {
      console.log("clicked outside");  
      this.fileValidations ()   
    }
  }
```

In the template we use #fileInput to attach the DOM element to an angular @ViewChild('fileInput')
```
<input class="form-control bottom-30" [id]="id()" type="file" (keydown.Tab)="fileValidationsOnTab()" (change)="fileChangeEvent($event)"  #fileInput/>
```

<br/>


#### @Pipe functions with |

As the character mention a @pipe is a function that it can be put anywhere in the html and executed. 
This is the syntax function() | pipe_function() . Where the pipe function can receive as parameter the result of function() .

It will be called value inside the pipe function. 

```
<p>Super power boost: {{2 | exponentialStrength: 10}}</p> 

```
<br/>

The pipe declaration <br/>

```
import { Pipe, PipeTransform } from '@angular/core';
/*
 * Raise the value exponentially
 * Takes an exponent argument that defaults to 1.
 * Usage:
 *   value | exponentialStrength:exponent
 * Example:
 *   {{ 2 | exponentialStrength:10 }}
 *   formats to: 1024
*/
@Pipe({name: 'exponentialStrength'})
export class ExponentialStrengthPipe implements PipeTransform {
  transform(value: number, exponent?: number): number {
    return Math.pow(value, isNaN(exponent) ? 1 : exponent);
  }
}
```

<br/>

#### Characters [Form] validations

```
export class FormControlDemoComponent {
  name = new FormControl('', [Validators.required, Validators.maxLength(15)]);
  age = new FormControl(20, Validators.required);  
  city = new FormControl();
  country = new FormControl({value: 'India', disabled: true});
  married = new FormControl(true);
````  
<br/>
In the template you can match componets with the form validations

<br/>

```
<div>
   Name: <input [formControl]="name">
         <label *ngIf="name.invalid" [ngClass] = "'error'"> Name required with max 15 character. </label>
 </div>
 <div>
   <button (click)="setNameValue()">Set value</button>
   <button (click)="setResetName()">Reset</button>
 </div>
 <div>
   Age: <input [formControl]="age">
 </div>
 <div>
   City: <input [formControl]="city">
 </div>
 <div>
   Country: <input [formControl]="country">
 </div>
```
