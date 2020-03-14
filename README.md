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
