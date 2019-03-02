# Data binding

Databinding simply means getting data from and to component logic(that is, `component-name.component.ts`).

## Data from Logic to Template

### By String Interpolation

Say there is a variable named `data` in our logic file. To get this variable in it's template, we simpley use :
```typescript
{{data}}
```
*Inside the curly braces, we can write anything that resolves into a string. We can't use multiline expressions inside the curly braces.*

### By Property Binding

Property binding is used to pass data from one component to another(Parent Component to Child component). Another use is to dynamically modify DOM properties. 

#### For modifying DOM properties
In `component-name.component.html`
```html
    <button [disabled]="isDisabled">Some Button<button>
```
In the above example, `isDisabled` is a function defined in the logic(`component-name.component.ts`). The function in this case should return a boolean value. A full list of properties is available [here](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement).

#### For passing data

Here, `child-component-name` is the Child Component name.

In Parent Component :
```html
    <app-child-component-name [variableName]="someData"></app-child-component-name>
```
Here `someData` is a variable from parent component logic.

In Child Component:

This has to be added in Child Component logic: 

1. Import Input decorator :
```typescript
import { Input } from '@angular/core';
```
Then retrive the variable as follows :
```typescript
@Input() variableName;
```
After this, we can use `variableName` in the child component.
