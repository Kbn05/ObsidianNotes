To install framework:

npm install -g @angular/cli

To initialize projects:

ng new <nameProject>

To run project:

ng serve

To choose one component in the HTML file, you must write like a tag the component selector name.

To generate components manually:

ng generate component <name>

You should define if your component is or not standalone component in the component section.

To nest components:
 
 Import the class into the .ts file and then write the selector tag into the .html file.

String interpolation: bring a variable from .ts to .html like this (in String format):
{{var}}

Property binding: Associate a variable with a property tag(whatever format):
<img [src]=(TS var)>

Class binding: Define a class into css file, then define a condition that changes according to a variable.

Style binding: Same as class binding, but this works with css tags.

Event binding: Define events inside of brackets, the you define the action to perform after the event occurs. ex: <button (click)="(methodOrAction)">

Event filtering: Each key in the keyboard has his own value, ex: a = 65, enter = 13, etc...
According to the input value, you can filter the action performed by the program

Template filtering: Assign a #id to a HTML tag, ex:
<input type="text"  #name (keyup.enter)="method(name.value)">

twoWayDataBinding: Allows to send data from component to HTML file and vice versa through the directive NgModel(It's necessary to import inside the component.ts), ex:
<input type="text" [(ngModel)]="varName">

oneWayDataBinding: allows to share data from the component to the view, not backwards.

Angular Directives 

This allows to add a behavior or modify DOM elements 

Types of Directives

Component Directives: Is an element with his own behavior and view.

Structural Directives: Modify the DOM, adding or removing elements(ngFor, ngSwitch).

Attribute Directive: Change the behavior or appearance of an element(ngClass, ngStyle).

Custom Directive: Allows to create our own directive from scratch.

To work with Selenium: npm i selenium-webdriver