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


## Data from Template to Logic

Data from template, like user input and interactions, are passed to the logic by using *Event Binding*.

### Event Binding

Code for binding `click` on a button element is given below. We can also bind `click` event to div, span, anchor etc.

```html
    <button (click)="buttonClicked()"> Some Button</button>
```

Here `buttonClicked()` is the name of the function defined in the logic. So, when the button is clicked, the function `buttonClicked()` in the logic is called. 

A full list of supported events can be found [here](https://developer.mozilla.org/en-US/docs/Web/Events). Any of those events can be put inside the parantheses. 

To pass details of the event, we can use `$event` parameter. For example, 

```html
    <input (keyup)="log($event)">
```
Where `log()` is  a function defined on the logic like :
```typescript
log(event: any){
    console.log(event);
}
```

## Two way Data Binding

```typescript
<input [(ngModel)]="variableName">
```
In this case, whatever the user inputs is stored to `variableName` and if `variableName` is changed by some other means in the logic, it is reflected in the input field.

For using `ngModel`, FormsModule should be added to the imports array in `app.module.ts`