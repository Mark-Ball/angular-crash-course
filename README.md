# Crash Course

https://coursetro.com/posts/code/174/Angular-8-Tutorial-&-Crash-Course

## Creating components

Components are created using the angular CLI. To create a HomeComponent class: 
```
ng g c home
```

This creates a folder called home within app with 4 files inside it: html, scss, spec.ts (for testing), and ts.

## Routing

Routing takes place in the ```app-routing.module.ts``` file location in ```/src/app```.

Firstly we import the class from the ts file created above.

```
import { HomeComponent } from './home/home.component';
```

Then we add an object to the routes array.
```

const routes: Routes = [
  { path: '', component: HomeComponent }
];
```

## Event binding and one-way data binding

Our goal is to set up a simple button, which when clicked increments a counter which is displayed on the page.

Firstly we set up the variable and method in ```home.component.ts```.

```
clickCounter: number = 0;

countClick() {
  this.clickCounter += 1;
}
```

Then we set up the event binding and interpolation in ```home.component.html```.

```
<p>You've clicked <span (click)="countClick()">this</span> {{ clickCounter }} times.</p>
```

## Two-way data binding

This can be achieved using ```[(ngModel)]```. Firstly, we must set up ```FormsModule``` in ```app.module.ts```.

```javascript
// other imports
import { FormsModule } from '@angular/forms';

@NgModule({
  // other objects
  imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule // add this
  ]
  // other objects
```

We use ngModel in a tag in the html file and provide a place where the variable is output.

```html
<input type='text' [(ngModel)]="name">
  <br>
<strong>You said: </strong> {{ name }}
```

In the ts file we simply initialise the variable.

```javascript
name: string = '';
```

Now when we update the input field in the form, it updates ```name``` in the typescript, which updates the display on the page. We can also change the value of ```name``` in the ts (without using the input field) and it will update the page.

## Templating

This is acheved by the use of the ```ngIf``` and ```ngClass``` property bindings.

```ngIf``` is used for conditional rendering.

```html
<ng-template [ngIf]="clickCounter > 4" [ngIfElse]="none">
  <p>The click counter <strong>IS GREATER</strong> than 4.</p>
</ng-template>
```

```ngClass``` is used to put classes onto html elements. This can be done in combination with a method in the ts file.

home.component.html
```html
<div [ngClass]="setClasses()">
```

home.component.ts
```javascript
setClasses() {
  let myClasses = {
    active: this.clickCounter > 4,
    notActive: this.clickCounter <= 4,
  };
  return myClasses;
}
```