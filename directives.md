# Directives

Directives give instructions the transforms the DOM.

## Built In Directives

## Structural Directives
Directives that add/remove DOM elements.
### *ngIf

```html
<div *ngIf="checkCondition()"></div>
```
Here, the `div` element only renders if the function `checkCondition()` returns true. We can also use any expression which resolves to true or false.
#### With else
```html
<div *ngIf="checkCondition(); else ElseElementName">Some text</div>

<ng-template #ElseElementName>
<div>Some other text</div>
</ng-template>
```
### *ngFor
```html
<div *ngFor="let name of names">
    {{name}}
</div>
```
This recursively adds `div` element of all elements in `names` array defined in the logic.

#### With index
```html
<div *ngFor="let name of names; let i = index">
    {{i}}|{{name}}
</div>
```

## Attribute Directives

### ngStyle
`ngStyle` is used to give dynamic css styles to an element.

```html
<div [ngStyle]="{'backgroud-color': 'green'}"></div>
```
OR
```html
<div [ngStyle]="{backgroudColor: 'green'}"></div>
```
OR
```html
<div [ngStyle]="{backgroudColor: getElementColor()}"></div>
```