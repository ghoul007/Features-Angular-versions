# Angular Version
## Angular 2

* Released in 2016
* Written entirely in TypeScript
* Component-based instead of Controller
* ES6 and typescript supported


## Angular 3
Why dont have a verion 3 ?
* The angular router was already in v3 and releasing angular 3 with router 4 will create confusion
* To avoid this confusion they decided to skip the version 3 and release with version 4.0.0

##  Angular 4
* Released in 2017
* Lot of performance improvement is made to reduce size of AOT compiler generated code
* Typescript 2.1 & 2.2 compatible — all feature of ts 2.1 & 2.2 are supported in Angular 4 application
* Animation features are separated from @angular/core to @angular/Animation
* Else block in *ngIf introduced

```Javascript
<*ngIf=”yourCondition; else myFalsyTemplate">
“<ng-template #myFalsyTemplate>Else Html</ng-template>”
```