## Angular notes

###### A question mark

A question mark after an identifier means that the parameter is optional. For example:

```
function stringify123(callback?: (num: number) => string) {
  const num = 123;
  if (callback) {
    return callback(num); // (A)
  }
  return String(num);
}
```
<br/>

######	 Characters ||
```
var title = title || "Error";
```

Basically checks if title evaluates to false. If it does, it "returns" "Error", otherwise it returns title.
```
if (!title) {
  title = "Error";
}
```

<br/>

###### @ViewChild('fileInput')

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

###### Characters [Form] validations

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