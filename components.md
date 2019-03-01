# Components in Angular

## Manually creating a component

Manually creating a component involves creating some files, naming them in a certain way, and placing them in correct folder and adding them to our declaratives list. 

Let's say we need to create a component called `component-name`.

### Creating necessary files and folders

1. Create a folder called `component-name` in `src/app` folder
2. Inside `component-name` folder, add 2 files with names `component-name.component.html` and `component-name.component.ts`
3. Paste this to `component-name.component.html`

```typescript
import { Component } from '@angular/core';

@Component({
    selector: 'app-component-name',
    templateUrl: './app.component.html'
})

export class ComponentName {
    some_variable = "Hello World!";
}
```

Paste this to `component-name.component.html`

```html
    <h1>{{some_variable}}</h1>
```

### Register the component in main module file

Open the file `src/app.module.ts` and add `ComponentName` to declarations. 
1. Add this line to the top:

```typescript
import {ComponentName} from './component-name/component-name.component'
```

2. Add `ComponentName` to declarations array:

```typescript
    declarations: [AppComponent,
                    ComponentName]
```

### Using the component

Add the components selector, in this case `app-component-name`, as tags to the root componet's template to use our custom component. 

Open `src/app.component.html` and add this line:
`<app-component-name></app-component-name>`

## Adding Component using Angular CLI

Inside the app folder, run this command to geneate a component with name `component-name`:

`ng generate component component-name`