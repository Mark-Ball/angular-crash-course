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