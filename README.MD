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

```js
<*ngIf=”yourCondition; else myFalsyTemplate">
“<ng-template #myFalsyTemplate>Else Html</ng-template>”
```

## Angular 5
* Released November 2017
* Build optimizer
* Angular Universal
* Decrease bundle size
* Increased the standardization across all browsers: For internationalization we were depending on 'i18n'
* HttpClient: until Angualar 4.3 @angular/HTTP was been used which is now depreciated and in Angular 5 a new module called HttpClientModule is introduced which comes under @angular/common/http package.
* Few new Router Life-cycle Events being added in Angular 5
```
ActivationStart, ActivationEnd, ChildActivationStart, ChildActivationEnd, GuardsCheckStart, GuardsCheckEnd, ResolveStart and ResolveEnd.
```
* Angular 5 supports TypeScript 2.3 version.
* compile Aot

## Angular6
* Released on April 2018
* Dependency on RxJS 6
* Remove support for  `template` tag and `ng-template` should be used.
* Angular Material + CDK
* Add providedIn property in injectable decorator. e.g:

```Angular
@Injectable({ providedIn: 'root'})
export class MyService{}
```
* CLI Changes:
  * ng update
  * ng add ( e.g ng add @angular/material)

* CLI + Material
  * Material Sidenav

  ```
  ng generate @angular/material:material-nav — name=my-nav
  ```
  * Dashboard

  ```
  ng generate @angular/material:material-dashboard — name=my-dashboard
  ```

  * Datatable

  ```
  ng generate @angular/material:material-table — name=my-table
  ```

* It uses angular.json instead of .angular-cli.json
* initial release of Angular Elements which gives us ability to use our angular components in other environments like a Vue.js application

## Angular 7

* Released on October 2018
* CLI Prompts: The CLI will now prompt users as when running common commands likeng new or ng add @angular/material with the intend of getting aid for building a new project using SCSS.
* Introduce a new Pipe called — KeyValuePipe
```js
@Component({
  selector: 'keyvalue-pipe',
  template: `<span>
    <p>Object</p>
    <div *ngFor="let item of object | keyvalue">
      {{item.key}}:{{item.value}}
    </div>
    <p>Map</p>
    <div *ngFor="let item of map | keyvalue">
      {{item.key}}:{{item.value}}
    </div>
  </span>`
})
export class KeyValuePipeComponent {
  object: {[key: number]: string} = {2: 'foo', 1: 'bar'};
  map = new Map([[2, 'foo'], [1, 'bar']]);
}
```
* Angular 7 now supporting to TypeScript 2.9.
* Angular 7 added a new compiler — Compatibility Compiler (ngcc)
* Added a new interface — DoBootstrap interface

```js
class AppModule implements DoBootstrap {
    ngDoBootstrap(appRef: ApplicationRef) {
        appRef.bootstrap(AppComponent);
    }
}
```

* Added a new interface — UrlSegment[] to CanLoad interface

```js
 constructor(router: Router) {
      const tree: UrlTree =
        router.parseUrl('/team/33/(user/victor//support:help)?debug=true#fragment');
      const f = tree.fragment; // return 'fragment'
      const q = tree.queryParams; // returns {debug: 'true'}
      const g: UrlSegmentGroup = tree.root.children[PRIMARY_OUTLET];
      const s: UrlSegment[] = g.segments; // returns 2 segments 'team' and '33'
      console.log(g.children[PRIMARY_OUTLET].segments); // returns 2 segments 'user' and 'victor'
      console.log(g.children['support'].segments); // return 1 segment 'help'
      console.log(g.segments) // return 2 segments team and
 }
```


## Angular 8
* Releasing March/April 2019
* Being smaller, faster and easier to use
* Added Support for TypeScript 3.2
* Added pathParamsOrQueryParamsChange mode for runGuardsAndResolvers in the Router:

This is a new option is basically the same as the pathParamsChange, but it also takes ***the query params*** into consideration.
[See more](https://juristr.com/blog/2019/01/Explore-Angular-Routers-runGuardsAndResolvers/)
```js
RouterModule.forRoot([
  ...
  {
    path: 'home/:id',
    component: HomeComponent,
    ...
    runGuardsAndResolvers: 'pathParamsOrQueryParamsChange'
  }
])
```


* Allow passing state to routerLink Directives in the Router ([Send data through routing paths in Angular
](https://stackoverflow.com/a/44865817/11270840))
    - Imperative navigation using the router.navigateByUrl()
    ```js
    this.router.navigateByUrl('/123', { state: { hello: 'world' } });
    ```
    - Declarative navigation using the routerLink directive, passing a state input
    ```html
    <a routerLink="/details" [state]="{ hello: 'world' }">Go</a>`,
    ```
    -Read it from the window.history.state property after the navigation has finished. You can use it to read the state from inside the component that you are navigating to
    ```js
      ngOnInit() {
    this.state$ = this.activatedRoute.paramMap
      .pipe(map(() => window.history.state))
  }
  ```

    - Read it from the NavigationExtras property of the NavigationStart event. This one is useful in top level components, because you cannot listen to the NavigationStart event from inside the component that you are navigating to
    ```js
      this.state$ =  this.router.events.pipe(
      filter(e => e instanceof NavigationStart),
      map(() => this.router.getCurrentNavigation().extras.state)
    )
    ```
    [See more]( https://netbasal.com/set-state-object-when-navigating-in-angular-7-2-b87c5b977bb)
* Allow passing state to NavigationExtras in the Router
```js
  this.state$ =  this.router.events.pipe(
      filter(e => e instanceof NavigationStart),
      map(() => this.router.getCurrentNavigation().extras.state)
```

* Added support for SASS
* Now compiler-cli resolve generated Sass/Less files to .css inputs that is a good feature if users might have run the CSS Preprocessor tool before the Angular compiler.
* Added an ng-new command that builds the project with Bazel [See more](https://blog.ninja-squad.com/2019/05/14/build-your-angular-application-with-bazel/)
* Export NumberValueAccessor & RangeValueAccessor directives