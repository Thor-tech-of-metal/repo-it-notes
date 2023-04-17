###### Binding

In Angular, it can be called the automatic synchronization of the data and the view.

For instance we have the following component:
```
export class PropertybindingComponent implements OnInit {

  title:string="Hello from component.";
}
```
<br/>

###### 1) {{ expression }}  or property interpolation

These are the interpolation brackets which can be used to directly evaluate the expression and insert them into the HTML.
**This is  used to display content from the model only.**

<br/>

```
<test src=" {{imagepath}} " width="300px" height="150px" alt="image not found">
```

<br/>

###### 2) () (parenthesis)

These are used for the events which are raised from the elements. Like DoubleClick. The () is then followed by =  method in the component.

```
<element (event)="method()"></element>
```
<br/>

###### 3)  [] (Square bracket)   

The square brackets set the value from the component to the HTML element/DOM properties. So the html will have this new property.
In Angular, there are 3 types of bindings:


*  **Property Binding:** Property binding means we pass the data from the component class and set the value to the given element in the view.

```
<img [src]="imagepath" width="300px" height="150px" alt="image not found">
```

<br/>
we have assigned the imagepath from the component directly to the src property. For this ,we used the [], which assigns the value from the component to the HTML element.

Using "bind-" Prefix Before Element Property
<br/>
```
<img bind-src="imagepath" width="100px" height="100px" alt="image not found">
```
<br/>

**We can use interpolation when value we are using from the component is a string.
Otherwise, we must use the other two methods in order to do the property binding.**

<br/>

* **Event Binding:**

These are the two ways to handle event binding.

  1)  (): Wrap the event in parentheses and assign the method from the component.

  2)  on-: Append on- before the event and assign the method from the component which will be called.


Component:   
```
SendData(Username: string, password: string, emailID: string): void {

    alert("user name " + Username);

    alert("password " + password);

    alert("email " + emailID);

}
```
Template:

```
User name  <input type="text" #txtUserName><br>

password <input type="password" #txtpassword><br>

Email  <input type="Email" #txtEmail><br>

1) (): Wrap

<button(click)="SendData(txtUserName.value,txtpassword.value,txtEmail.value)">  </button>

2)  on-: Append on- before the event

<button on-click="SendData(txtUserName.value,txtpassword.value,txtEmail.value)">Click to send Data</button>

```

#txtUsername, #txtpassword are the template reference variables which can be used with Angular to take in values.


* **Ng Binding:**

Use the ng-bind directive, which will bind the innerHTML of the element to the specified model property:
Data binding in AngularJS is the synchronization between the model and the view.

```
<p ng-bind="firstname"></p>
```

Use the ng-model directive to bind data from the model to the view on HTML controls.

```
 <input ng-model="firstname">
```

* **Two-Way Binding:**

```
 ([……])
 The html element with the [(ngModel)]="componentAttribute"  will constantly update the model.

```

 This allows for a continuous sync between the presentation and the View layer of the application.
 ```
<input type="text"  [(ngModel)]="showoutput">

<br/>

This constantly change: {{showoutput}}

</p>

 ```
