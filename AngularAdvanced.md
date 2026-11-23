# Advanced Angular Interview Questions (51-60)

---

# 51. What are Decorators in Angular?

## Answer

Decorators are special functions in TypeScript that add metadata to classes, properties, methods, and parameters. Angular heavily relies on decorators to identify and configure various building blocks such as Components, Services, Directives, Pipes, and Modules.

Decorators tell Angular how a class should behave and how it should be processed during compilation. They simplify configuration and make Angular applications more declarative.

Common Angular decorators include @Component, @Injectable, @NgModule, @Input, @Output, and @ViewChild.

### Common Decorators

- @Component
- @Injectable
- @NgModule
- @Input
- @Output
- @ViewChild

### Example

```typescript
@Component({
 selector: 'app-home',
 template: '<h2>Welcome</h2>'
})
export class HomeComponent {}
```

### Real-Time Use Case

Angular uses decorators to identify which classes should participate in dependency injection and rendering.

---

# 52. What is @Component Decorator?

## Answer

@Component is one of the most important Angular decorators. It converts a TypeScript class into an Angular Component and provides metadata describing how Angular should create and use that component.

The metadata includes selector, template, style files, change detection strategy, and encapsulation settings.

Without the @Component decorator, Angular cannot recognize a class as a component.

### Example

```typescript
import { Component } from '@angular/core';

@Component({
 selector: 'app-employee',
 templateUrl: './employee.component.html',
 styleUrls: ['./employee.component.css']
})
export class EmployeeComponent {}
```

### Key Properties

- selector
- template
- templateUrl
- styles
- styleUrls
- providers

### Real-Time Use Case

Creating reusable UI components such as Header, Footer, Product Card, or Dashboard Widgets.

---

# 53. What is @Injectable Decorator?

## Answer

@Injectable marks a class as a service that can participate in Angular's Dependency Injection system.

It instructs Angular to create and manage instances of the service automatically. Services decorated with @Injectable can be injected into components, other services, directives, and guards.

The most common configuration is `providedIn: 'root'`, which creates a singleton service for the entire application.

### Example

```typescript
import { Injectable } from '@angular/core';

@Injectable({
 providedIn: 'root'
})
export class EmployeeService {

 getEmployees() {
   return [];
 }

}
```

### Benefits

- Singleton Service Creation
- Dependency Injection Support
- Improved Testability
- Better Code Reuse

### Real-Time Use Case

Managing API communication across the entire application.

---

# 54. What is @Input Decorator?

## Answer

The @Input decorator allows data to be passed from a parent component to a child component.

It enables component communication and promotes reusable component design. Whenever the parent updates the value, Angular automatically passes the latest value to the child component.

@Input is one of the most commonly used decorators in enterprise Angular applications.

### Parent Component

```html
<app-employee
 [employeeName]="name">
</app-employee>
```

### Child Component

```typescript
@Input()
employeeName!: string;
```

### Example

```typescript
export class EmployeeComponent {

 @Input()
 employeeName!: string;

}
```

### Real-Time Use Case

Passing customer details, order information, or configuration settings from parent to child components.

---

# 55. What is @Output Decorator?

## Answer

The @Output decorator is used to send data from a child component to a parent component.

It works together with EventEmitter to notify parent components when an event occurs in the child component.

@Output is frequently used in forms, reusable widgets, and component interactions.

### Child Component

```typescript
@Output()
employeeSelected =
new EventEmitter<number>();
```

### Parent Component

```html
<app-employee
 (employeeSelected)="selectEmployee($event)">
</app-employee>
```

### Benefits

- Parent-Child Communication
- Event Driven Architecture
- Reusable Components

### Real-Time Use Case

Notifying the parent component when a user selects an item from a list.

---

# 56. What is EventEmitter?

## Answer

EventEmitter is an Angular class used together with @Output to emit custom events from child components to parent components.

It allows child components to communicate user actions or state changes back to their parent components.

EventEmitter follows the publish-subscribe pattern and is a fundamental mechanism for component communication.

### Example

```typescript
@Output()
saveClicked =
new EventEmitter<string>();
```

### Emit Event

```typescript
save() {

 this.saveClicked.emit(
   'Employee Saved'
 );

}
```

### Parent Subscription

```html
<app-child
 (saveClicked)="handleSave($event)">
</app-child>
```

### Real-Time Use Case

Sending order confirmation details from child checkout components to parent order workflows.

---

# 57. What is AOT (Ahead-of-Time) Compilation?

## Answer

Ahead-of-Time Compilation converts Angular templates and TypeScript code into optimized JavaScript during the build process rather than at runtime.

AOT compilation improves application performance, decreases startup time, and detects template errors during compilation.

Production Angular applications typically use AOT compilation by default.

### Example

```bash
ng build --configuration production
```

### Advantages

- Faster Startup
- Smaller Bundle Size
- Better Security
- Early Error Detection

### Compilation Flow

```text
TypeScript
    ↓
Angular Compiler
    ↓
Optimized JavaScript
```

### Real-Time Use Case

Production deployments for banking, healthcare, and e-commerce applications.

---

# 58. What is JIT (Just-In-Time) Compilation?

## Answer

Just-In-Time Compilation compiles Angular templates directly in the browser during application runtime.

JIT is commonly used during development because it provides faster build cycles and enables immediate feedback after code changes.

Although easier for development, JIT is slower than AOT for production environments.

### Example

```bash
ng serve
```

### Characteristics

- Runtime Compilation
- Faster Development
- Slower Initial Loading
- Larger Bundle Size

### Compilation Flow

```text
TypeScript
   ↓
Browser
   ↓
Runtime Compilation
```

### Real-Time Use Case

Used during local development and debugging.

---

# 59. What is the Ivy Rendering Engine?

## Answer

Ivy is Angular's next-generation rendering and compilation engine introduced to improve build performance, bundle size, and debugging capabilities.

Ivy generates more efficient JavaScript code and enables advanced features such as improved tree-shaking and faster component rendering.

Since Angular 9, Ivy has been the default rendering engine.

### Benefits

- Smaller Bundles
- Faster Compilation
- Better Tree Shaking
- Easier Debugging
- Improved Runtime Performance

### Example

```typescript
@Component({
 selector: 'app-root',
 template: '<h1>Hello Ivy</h1>'
})
export class AppComponent {}
```

### Real-Time Use Case

Large enterprise applications with hundreds of components requiring optimal performance.

---

# 60. Explain Angular Compiler Architecture.

## Answer

Angular Compiler Architecture is responsible for transforming Angular application code into executable JavaScript that browsers can understand.

The architecture consists of TypeScript compilation, Angular template compilation, metadata analysis, dependency injection generation, and rendering instruction generation.

Modern Angular applications primarily use the Ivy compiler architecture for improved performance and maintainability.

### Compilation Process

```text
TypeScript Source
       ↓
Angular Compiler
       ↓
Template Compilation
       ↓
Dependency Analysis
       ↓
Ivy Instructions
       ↓
Optimized JavaScript
```

### Key Responsibilities

- Template Compilation
- Metadata Processing
- Dependency Injection Generation
- Error Validation
- Build Optimization

### Example

```typescript
@Component({
 selector:'app-user',
 template:'{{name}}'
})
export class UserComponent {

 name = 'Angular';

}
```

### Real-Time Use Case

Compiling large enterprise applications into highly optimized browser-ready code.

---

## Interview Summary (51-60)

### Most Frequently Asked Questions

1. Difference between @Input and @Output
2. Decorators in Angular
3. EventEmitter Working Mechanism
4. Dependency Injection and @Injectable
5. AOT vs JIT Compilation
6. Ivy Architecture
7. Angular Compilation Process
8. Component Metadata
9. Component Communication
10. Production Build Optimization


---
# Advanced Angular Interview Questions (61-70)

---

# 61. What is NgModule in Angular?

## Answer

NgModule is a decorator that defines an Angular module. It acts as a container that groups related components, directives, pipes, and services into a cohesive block of functionality.

Before Angular 14 standalone APIs, NgModule was the primary mechanism for organizing Angular applications. It helps manage dependencies, declarations, routing, and application bootstrapping.

Although Standalone Components are becoming popular, many enterprise applications still heavily use NgModules.

### Example

```typescript
@NgModule({
 declarations: [
   AppComponent,
   EmployeeComponent
 ],
 imports: [
   BrowserModule
 ],
 providers: [
   EmployeeService
 ],
 bootstrap: [
   AppComponent
 ]
})
export class AppModule {}
```

### Key Properties

- declarations
- imports
- exports
- providers
- bootstrap

### Real-Time Use Case

Managing modules such as CustomerModule, EmployeeModule, and OrdersModule in enterprise applications.

---

# 62. What is a Shared Module?

## Answer

A Shared Module contains reusable components, directives, and pipes that can be used across multiple feature modules.

Instead of duplicating common functionality in different modules, developers place them inside a Shared Module and export them for reuse.

Shared modules improve maintainability and reduce code duplication.

### Example

```typescript
@NgModule({
 declarations: [
   HeaderComponent,
   FooterComponent,
   HighlightDirective
 ],
 exports: [
   HeaderComponent,
   FooterComponent,
   HighlightDirective
 ]
})
export class SharedModule {}
```

### Usage

```typescript
imports: [
 SharedModule
]
```

### Common Contents

- Header Components
- Footer Components
- Custom Pipes
- Common Directives

### Real-Time Use Case

Sharing navigation bars and reusable UI widgets across multiple business modules.

---

# 63. What is a Core Module?

## Answer

A Core Module contains singleton services and application-wide functionality that should be loaded only once during application startup.

Unlike Shared Modules, Core Modules are generally imported only by the root AppModule.

Core modules often include authentication, logging, configuration, and global services.

### Example

```typescript
@NgModule({
 providers: [
   AuthService,
   LoggerService
 ]
})
export class CoreModule {}
```

### Typical Core Services

- Authentication Service
- Logging Service
- App Configuration Service
- User Session Service

### Best Practice

Import CoreModule only once inside AppModule.

### Real-Time Use Case

Managing authentication and application configuration globally.

---

# 64. What are Feature Modules?

## Answer

Feature Modules organize application functionality around a specific business domain. They help developers break large applications into smaller, manageable units.

Each feature module contains its own components, services, routing, and business logic.

Feature modules are commonly combined with lazy loading for improved application performance.

### Example

```typescript
@NgModule({
 declarations: [
   EmployeeListComponent,
   EmployeeDetailComponent
 ]
})
export class EmployeeModule {}
```

### Common Feature Modules

- EmployeeModule
- CustomerModule
- ProductModule
- OrderModule

### Benefits

- Better Maintainability
- Improved Scalability
- Easier Team Collaboration
- Supports Lazy Loading

### Real-Time Use Case

Banking applications with separate modules for loans, accounts, and payments.

---

# 65. What are Standalone Components?

## Answer

Standalone Components are Angular components that do not require NgModules. Introduced in Angular 14, they simplify application architecture by allowing components to manage their own dependencies.

Standalone components reduce boilerplate code and make Angular applications easier to understand and maintain.

Angular now recommends standalone APIs for modern application development.

### Example

```typescript
@Component({
 selector: 'app-employee',
 standalone: true,
 template: `<h2>Employee Component</h2>`
})
export class EmployeeComponent {}
```

### Importing Standalone Component

```typescript
imports: [
 EmployeeComponent
]
```

### Benefits

- Less Boilerplate
- Faster Development
- Simpler Structure
- Better Tree Shaking

### Real-Time Use Case

Modern Angular microfrontend and enterprise applications.

---

# 66. What are Standalone APIs?

## Answer

Standalone APIs allow Angular applications to be built without NgModules. Developers can bootstrap components directly and configure routing, HTTP services, and dependency injection using providers.

They simplify Angular architecture and improve maintainability.

Standalone APIs are part of Angular's push toward a more lightweight development experience.

### Bootstrap Example

```typescript
bootstrapApplication(AppComponent);
```

### Routing Example

```typescript
provideRouter(routes)
```

### HttpClient Example

```typescript
provideHttpClient()
```

### Benefits

- Reduced Complexity
- Faster Startup
- Smaller Bundle Size
- Easier Learning Curve

### Real-Time Use Case

Developing modern Angular 17+ enterprise applications.

---

# 67. What are Signals in Angular?

## Answer

Signals are Angular's reactive state management primitives introduced to simplify reactivity and improve performance.

A Signal stores a value and automatically notifies Angular whenever the value changes. Signals reduce dependency on manual change detection and improve application responsiveness.

Signals are expected to become a core part of Angular's future reactive architecture.

### Example

```typescript
import { signal } from '@angular/core';

count = signal(0);
```

### Updating Signal

```typescript
this.count.set(10);
```

### Reading Signal

```typescript
{{ count() }}
```

### Benefits

- Fine-grained Reactivity
- Better Performance
- Simplified State Management

### Real-Time Use Case

Managing shopping cart counters, dashboard widgets, and notification updates.

---

# 68. What are Computed Signals?

## Answer

Computed Signals are derived values that automatically recalculate when dependent signals change.

They help eliminate manual calculations and ensure derived state always stays synchronized with source state.

Computed signals are read-only and update automatically whenever dependencies change.

### Example

```typescript
import {
 signal,
 computed
} from '@angular/core';

price = signal(100);

quantity = signal(2);

totalAmount = computed(
 () => this.price() * this.quantity()
);
```

### Usage

```typescript
totalAmount()
```

### Output

```text
200
```

### Real-Time Use Case

Calculating shopping cart totals and order summaries.

---

# 69. What are Effects in Angular Signals?

## Answer

Effects allow developers to execute side effects whenever Signal values change.

Unlike Computed Signals, which derive values, Effects perform operations such as logging, API calls, analytics tracking, or updating external resources.

Effects automatically re-execute whenever one of their dependent signals changes.

### Example

```typescript
import {
 signal,
 effect
} from '@angular/core';

count = signal(0);

effect(() => {

 console.log(
   'Count Changed:',
   this.count()
 );

});
```

### Trigger

```typescript
this.count.set(5);
```

### Output

```text
Count Changed: 5
```

### Real-Time Use Case

Tracking user activities and updating analytics dashboards.

---

# 70. What is InjectionToken in Angular?

## Answer

InjectionToken is used when Angular needs to inject values that are not classes, such as configuration objects, constants, API URLs, or interfaces.

Since interfaces do not exist at runtime, Angular cannot inject them directly. InjectionToken provides a unique identifier for dependency injection.

InjectionToken improves type safety and supports configurable dependencies.

### Example

```typescript
import {
 InjectionToken
} from '@angular/core';

export const API_URL =
new InjectionToken<string>(
 'API_URL'
);
```

### Provider Registration

```typescript
providers: [
 {
   provide: API_URL,
   useValue:
   'https://api.company.com'
 }
]
```

### Injection

```typescript
constructor(
 @Inject(API_URL)
 private apiUrl:string
){}
```

### Real-Time Use Case

Injecting environment configurations, API endpoints, and application settings.

---

# Interview Summary (61-70)

## Most Frequently Asked Questions

1. Standalone Components vs NgModules
2. Shared Module vs Core Module
3. Feature Modules Architecture
4. Signals vs RxJS
5. Computed Signals
6. Effects
7. Standalone APIs
8. InjectionToken Usage
9. Angular State Management
10. Angular 17 Reactive Features

---
# Advanced Angular Interview Questions (71-80)

---

# 71. What is Zone.js in Angular?

## Answer

Zone.js is a library used by Angular to detect asynchronous operations and automatically trigger Change Detection. It patches browser APIs such as setTimeout, setInterval, Promises, DOM events, and HTTP requests.

Whenever an asynchronous operation completes, Zone.js notifies Angular, which then updates the UI automatically. This allows developers to focus on business logic instead of manually updating the view.

Starting with Angular Signals and newer Angular versions, Angular is moving toward reducing dependency on Zone.js for better performance.

### Example

```typescript
setTimeout(() => {

  this.message = "Data Loaded";

}, 2000);
```

Angular automatically updates the UI when the timer completes because Zone.js detects the asynchronous operation.

### Benefits

- Automatic Change Detection
- Easier Development
- Reduced Boilerplate Code
- Better User Experience

### Real-Time Use Case

Updating dashboards automatically after API responses arrive.

---

# 72. What is ChangeDetectorRef?

## Answer

ChangeDetectorRef is a service that gives developers manual control over Angular's Change Detection process.

Although Angular automatically updates the UI in most cases, there are scenarios where developers need to manually trigger or optimize change detection.

This service becomes especially important when working with OnPush strategy and performance-critical applications.

### Example

```typescript
constructor(
 private cdr: ChangeDetectorRef
){}
```

### Trigger Change Detection

```typescript
this.employeeName = 'John';

this.cdr.detectChanges();
```

### Common Methods

- detectChanges()
- markForCheck()
- detach()
- reattach()

### Real-Time Use Case

Updating UI when data changes outside Angular's detection cycle.

---

# 73. What is a Custom Directive in Angular?

## Answer

A Custom Directive allows developers to create reusable behaviors that can be applied to HTML elements.

Directives help extend HTML functionality without modifying the DOM manually. Custom directives are commonly used for styling, validation, permissions, and dynamic UI behavior.

Angular supports both Attribute Directives and Structural Directives.

### Example

```typescript
@Directive({
 selector: '[appHighlight]'
})
export class HighlightDirective {

 constructor(
   private el: ElementRef
 ) {

   el.nativeElement.style
     .backgroundColor = 'yellow';

 }

}
```

### Usage

```html
<p appHighlight>
 Angular Interview
</p>
```

### Real-Time Use Case

Highlighting required fields across multiple forms.

---

# 74. What is an Attribute Directive?

## Answer

Attribute Directives modify the appearance or behavior of existing DOM elements without changing the DOM structure itself.

They are applied as element attributes and are useful for dynamically modifying styles, classes, and user interactions.

Angular provides ngClass and ngStyle as built-in attribute directives.

### Example

```html
<p
 [ngStyle]="{
   color:'blue'
 }">
 Angular
</p>
```

### ngClass Example

```html
<div
 [ngClass]="{
   active:isSelected
 }">
</div>
```

### Common Attribute Directives

- ngClass
- ngStyle
- Custom Directives

### Real-Time Use Case

Applying role-based styling across enterprise applications.

---

# 75. What is a Structural Directive?

## Answer

Structural Directives add, remove, or manipulate DOM elements dynamically.

Unlike Attribute Directives, Structural Directives change the actual DOM layout and are prefixed with an asterisk (*).

Angular provides several built-in structural directives for conditional rendering and looping.

### Example

```html
<div *ngIf="isLoggedIn">

 Welcome User
*</div>
```

### ngFor Example

```*tml
<li *ngFor="let emp of employe*s">

 {{emp.name}}

</li>
```

###*Common Structural Directives

- *n*If
- *ngFor
- *ngSwitch

### Real-*ime Use Case

Displaying dynamic m*nus based on user permissions.

--*

# 76. What is Renderer2?

## Ans*er

Renderer2 is Angular's abstrac*ion layer for safely interacting w*th DOM elements.

Instead of direc*ly accessing the DOM through nativ*Element, Angular recommends Render*r2 because it improves security, t*stability, and platform independen*e.

Renderer2 is particularly usef*l when applications need to suppor* Server-Side Rendering (SSR).

###*Example

```typescript
constructor*
 private renderer: Renderer2,
 pr*vate el: ElementRef
){}
```

### S*tting Style

```typescript
this.re*derer.setStyle(
 this.el.nativeEle*ent,
 'color',
 'red'
);
```

### *ommon Methods

- setStyle()
- addC*ass()
- removeClass()
- setAttribu*e()
- listen()

### Real-Time Use *ase

Creating reusable directives *hat manipulate element appearance *ynamically.

---

# 77. What is El*mentRef?

## Answer

ElementRef is*a wrapper around a native DOM elem*nt. It allows Angular components a*d directives to access underlying *TML elements directly.

While powe*ful, ElementRef should be used cau*iously because direct DOM manipula*ion may introduce security risks.
*Angular generally recommends using*Renderer2 whenever possible.

### *xample

```typescript
@ViewChild('*sername')
username!: ElementRef;
`*`

### HTML

```html
<input #usern*me>
```

### Accessing DOM

```typ*script
ngAfterViewInit() {

 this.*sername
     .nativeElement.focus(*;

}
```

### Real-Time Use Case

*utomatically focusing form control* after page initialization.

---

* 78. What is Angular Universal (SS*)?

## Answer

Angular Universal e*ables Server-Side Rendering (SSR) *n Angular applications.

Instead o* generating HTML in the browser, A*gular renders pages on the server *nd sends fully rendered HTML to us*rs. This improves SEO, performance* and initial page loading times.

*SR is especially beneficial for co*tent-heavy websites and public-fac*ng applications.

### Benefits

- *etter SEO
- Faster First Contentfu* Paint
- Faster Initial Loading
- *mproved Accessibility

### Example*
```bash
ng add @angular/ssr
```

*## Rendering Flow

```text
Browser*Request
       ↓
Node Server
     * ↓
Angular Rendering
       ↓
HTML*Response
```

### Real-Time Use Ca*e

News portals, e-commerce platfo*ms, and marketing websites.

---

* 79. What is Hydration in Angular?*
## Answer

Hydration is the proce*s where Angular reuses server-rend*red HTML instead of completely reb*ilding the DOM on the client side.*
When SSR renders content on the s*rver, hydration connects Angular c*mponents to the existing HTML duri*g browser startup.

Hydration sign*ficantly improves performance and *educes visual flickering.

### Exa*ple

```typescript
provideClientHy*ration()
```

### Benefits

- Fast*r Startup
- Reduced DOM Recreation*- Better User Experience
- Improve* Core Web Vitals

### Rendering Fl*w

```text
SSR HTML
    ↓
Browser *oads HTML
    ↓
Angular Hydrates E*isting DOM
```

### Real-Time Use *ase

High-traffic e-commerce websi*es where performance is critical.
*---

# 80. What are Deferrable Vie*s (@defer)?

## Answer

Deferrable*Views, introduced in Angular 17, a*low developers to defer loading of*specific components, templates, or*content until they are actually ne*ded.

This feature helps reduce in*tial bundle size and improves appl*cation performance by loading non-*ritical content later.

Angular su*ports multiple triggers such as id*e time, viewport entry, timer, and*user interaction.

### Example

``*html
@defer {

  <app-dashboard-ch*rt />

}
```

### Viewport Example*
```html
@defer (on viewport) {

  <app-heavy-report />

}
```

### Benefits

- Faster Initial Load
- Reduced Bundle Size
- Better Performance
- Improved User Experience

### Real-Time Use Case

Loading analytics dashboards, reports, charts, and large widgets only when users access them.

---

# Interview Summary (71-80)

## Frequently Asked Questions

1. Zone.js Working Mechanism
2. ChangeDetectorRef Methods
3. Renderer2 vs ElementRef
4. Custom Directives
5. Structural vs Attribute Directives
6. Angular Universal SSR
7. SSR vs CSR
8. Hydration Benefits
9. Angular 17 @defer
10. Modern Angular Performance Optimization

---

# Advanced Angular Interview Questions (81-90)

---

# 81. What is State Management in Angular?

## Answer

State Management is a technique used to manage and maintain application data consistently across components. As Angular applications grow, sharing data between multiple components becomes challenging.

State Management provides a centralized mechanism for storing, updating, and retrieving application state. Popular state management solutions in Angular include NgRx, Component Store, NGXS, Akita, and Signals.

Proper state management improves maintainability, scalability, debugging, and application performance.

### Example

```typescript
state = {
  employees: [],
  selectedEmployee: null
};
```

### Common State Types

- Application State
- UI State
- Router State
- User State
- API State

### Real-Time Use Case

Managing shopping carts, user sessions, and dashboard data across multiple screens.

---

# 82. What is NgRx?

## Answer

NgRx is a Redux-inspired state management library for Angular applications. It provides predictable state management using Actions, Reducers, Selectors, and Effects.

NgRx follows a unidirectional data flow, making applications easier to debug and maintain. It is commonly used in large enterprise applications where multiple components share complex data.

NgRx integrates seamlessly with Angular and RxJS.

### Core Components

- Store
- Actions
- Reducers
- Selectors
- Effects

### Example

```typescript
Store
  → Action
  → Reducer
  → New State
  → UI Update
```

### Real-Time Use Case

Managing thousands of products, orders, and customer details in an e-commerce application.

---

# 83. What is Store in NgRx?

## Answer

Store is the central repository that holds the application state in NgRx. Components do not modify state directly. Instead, they dispatch Actions which are processed by Reducers.

The Store acts as a single source of truth for the application and helps maintain consistency.

Components retrieve data from the Store using Selectors.

### Example

```typescript
constructor(
 private store: Store
){}
```

### Dispatch Action

```typescript
this.store.dispatch(
 loadEmployees()
);
```

### Select State

```typescript
this.store.select(
 selectEmployees
);
```

### Real-Time Use Case

Maintaining user profile information throughout an enterprise application.

---

# 84. What are Actions in NgRx?

## Answer

Actions are events that describe what happened in the application. They are dispatched by components, services, or effects and trigger state changes.

Actions are plain objects containing a type and optional payload.

By clearly defining every state change through actions, applications become more predictable and easier to debug.

### Example

```typescript
import {
 createAction,
 props
} from '@ngrx/store';
```

### Action Definition

```typescript
export const loadEmployees =
createAction(
 '[Employee] Load Employees'
);
```

### Action with Payload

```typescript
export const addEmployee =
createAction(
 '[Employee] Add Employee',
 props<{ employee:any }>()
);
```

### Real-Time Use Case

Triggering employee creation, deletion, or updates from UI screens.

---

# 85. What are Reducers in NgRx?

## Answer

Reducers are pure functions responsible for updating state based on incoming actions.

Reducers receive the current state and an action, then return a new state without modifying the existing state. This immutability makes debugging easier and helps maintain predictable application behavior.

Reducers should never perform API calls or side effects.

### Example

```typescript
export const employeeReducer =
createReducer(

 initialState,

 on(addEmployee,
 (state, {employee}) => ({

   ...state,

   employees:[
     ...state.employees,
     employee
   ]

 }))

);
```

### Responsibilities

- Update State
- Maintain Immutability
- Handle Actions
- Return New State

### Real-Time Use Case

Adding a new employee to the employee state store.

---

# 86. What are Selectors in NgRx?

## Answer

Selectors are pure functions used to retrieve specific data from the NgRx Store.

Instead of allowing components to access the entire state, selectors provide filtered and optimized access to required data.

Selectors improve performance because Angular only updates components when selected data changes.

### Example

```typescript
export const selectEmployees =
createSelector(

 selectEmployeeState,

 state => state.employees

);
```

### Usage

```typescript
employees$ =
this.store.select(
 selectEmployees
);
```

### Benefits

- Reusable
- Optimized
- Type Safe
- Easy Testing

### Real-Time Use Case

Displaying only active employees from a large employee collection.

---

# 87. What are Effects in NgRx?

## Answer

Effects handle side effects such as API calls, navigation, logging, or interaction with external services.

Reducers should remain pure functions and should not communicate with external systems. Effects listen for actions, perform external operations, and dispatch new actions.

Effects are built on top of RxJS Observables.

### Example

```typescript
@Injectable()
export class EmployeeEffects {

 loadEmployees$ =
 createEffect(() =>

   this.actions$.pipe(

     ofType(loadEmployees),

     switchMap(() =>
       this.employeeService
       .getEmployees()
       .pipe(
         map(data =>
          loadEmployeesSuccess({
            employees:data
          })
         )
       )
     )
   )
 );
}
```

### Real-Time Use Case

Calling REST APIs whenever users request employee information.

---

# 88. What is NgRx Entity Adapter?

## Answer

NgRx Entity Adapter simplifies managing collections of data within the Store. It reduces boilerplate code required for CRUD operations.

The Entity Adapter organizes data into an optimized structure using ids and entities, improving lookup performance and maintainability.

It is highly recommended when storing large collections.

### Example

```typescript
export interface Employee {

 id:number;
 name:string;

}
```

### Entity State

```typescript
{
 ids:[1,2,3],
 entities:{
   1:{id:1,name:'John'},
   2:{id:2,name:'David'}
 }
}
```

### Benefits

- Faster Lookup
- Less Boilerplate
- Built-in CRUD Operations
- Better Performance

### Real-Time Use Case

Managing thousands of employees or products efficiently.

---

# 89. What is Component Store?

## Answer

Component Store is a lightweight state management solution provided by NgRx for managing local component state.

Unlike the global Store, Component Store focuses on the state of a specific component or feature.

It reduces complexity when full NgRx Store implementation is unnecessary.

### Example

```typescript
@Injectable()
export class EmployeeStore
extends ComponentStore<any> {

 constructor() {

   super({
     employees:[]
   });

 }

}
```

### Benefits

- Local State Management
- Less Boilerplate
- Better Performance
- Easier Learning Curve

### Real-Time Use Case

Managing state within a dashboard widget or report screen.

---

# 90. Signals vs NgRx: Which One Should Be Used?

## Answer

Signals and NgRx both manage state, but they solve different problems.

Signals provide a lightweight reactive state mechanism built directly into Angular. NgRx provides enterprise-grade state management with actions, reducers, selectors, and effects.

For simple and medium-sized applications, Signals are often sufficient. For large applications requiring centralized state, auditing, undo/redo capabilities, and complex workflows, NgRx remains a strong choice.

### Signals Example

```typescript
count = signal(0);

count.set(10);
```

### NgRx Example

```typescript
this.store.dispatch(
 updateCount({value:10})
);
```

### Comparison

| Feature | Signals | NgRx |
|----------|----------|-------|
| Complexity | Low | High |
| Learning Curve | Easy | Moderate |
| Built Into Angular | Yes | No |
| Global State | Limited | Excellent |
| Enterprise Support | Good | Excellent |
| Boilerplate | Minimal | More |

### Real-Time Use Case

- Signals → Dashboard counters, UI state, forms
- NgRx → Banking systems, ERP solutions, large e-commerce platforms

---

# Interview Summary (81-90)

## Most Frequently Asked Questions

1. What is State Management?
2. Explain NgRx Architecture.
3. Store vs Component Store.
4. Actions vs Reducers.
5. Selectors vs Effects.
6. Why Reducers Must Be Pure Functions?
7. NgRx Entity Adapter.
8. State Normalization.
9. Signals vs NgRx.
10. When to Use NgRx in Enterprise Applications?

---

## NgRx Architecture Flow

```text
Component
    ↓
Dispatch Action
    ↓
Reducer
    ↓
Store Updated
    ↓
Selector
    ↓
Component Updates
```

---

# Advanced Angular Interview Questions (91-100)

---

# 91. What are Micro Frontends in Angular?

## Answer

Micro Frontends is an architectural approach where a frontend application is divided into smaller, independently deployable applications. Similar to microservices on the backend, each team can own, develop, test, and deploy its frontend independently.

This approach improves scalability, team productivity, and maintainability in large enterprise applications.

Angular applications commonly implement Micro Frontends using Webpack Module Federation.

### Architecture

```text
Shell Application
       |
-----------------------
|          |          |
HR App   Admin App  Sales App
```

### Benefits

- Independent Deployment
- Team Autonomy
- Better Scalability
- Technology Flexibility

### Real-Time Use Case

Large banking applications where different teams manage Loans, Payments, and Customer modules separately.

---

# 92. What is Module Federation?

## Answer

Module Federation is a Webpack 5 feature that enables multiple independent applications to share modules at runtime.

Instead of bundling everything into a single application, Angular applications can dynamically load components and modules from remote applications.

Module Federation is one of the most popular implementations for Angular Micro Frontends.

### Remote Module Example

```javascript
remotes: {
  employeeApp:
  'employeeApp@http://localhost:4201/remoteEntry.js'
}
```

### Loading Remote Module

```typescript
loadRemoteModule({
  remoteName: 'employeeApp',
  exposedModule: './EmployeeModule'
});
```

### Benefits

- Runtime Integration
- Shared Dependencies
- Smaller Deployments
- Team Independence

### Real-Time Use Case

Enterprise portals integrating applications from different teams.

---

# 93. How can Angular Application Performance be Optimized?

## Answer

Angular applications can be optimized using multiple strategies that reduce bundle size, minimize change detection, and improve loading speed.

Performance optimization becomes critical when applications contain thousands of components, large datasets, and frequent API interactions.

Optimized applications provide better user experience and lower infrastructure costs.

### Optimization Techniques

- Lazy Loading
- Standalone Components
- OnPush Change Detection
- TrackBy
- AOT Compilation
- SSR
- Hydration
- Deferrable Views (@defer)

### Example

```typescript
changeDetection:
ChangeDetectionStrategy.OnPush
```

### Real-Time Use Case

Large e-commerce websites handling millions of users.

---

# 94. What are Memory Leaks in Angular?

## Answer

A Memory Leak occurs when objects remain in memory even after they are no longer needed. Over time, memory leaks can degrade application performance and increase browser memory consumption.

The most common causes of memory leaks in Angular are unsubscribed Observables, event listeners, timers, and retained component references.

Developers should always clean up resources when components are destroyed.

### Problem Example

```typescript
this.httpService
.subscribe(data => {

});
```

### Proper Cleanup

```typescript
ngOnDestroy() {

 this.subscription.unsubscribe();

}
```

### Prevention Techniques

- Unsubscribe Observables
- Remove Event Listeners
- Clear Timers
- Use Async Pipe

### Real-Time Use Case

Dashboard applications running continuously for several hours.

---

# 95. What is Tree Shaking in Angular?

## Answer

Tree Shaking is a build optimization technique that removes unused code from the final application bundle.

Angular uses modern build tools to analyze imports and eliminate code that is never referenced by the application.

Tree Shaking significantly reduces bundle size and improves application loading speed.

### Example

```typescript
import {
 HttpClient
} from '@angular/common/http';
```

Only the imported functionality is included in the final build.

### Benefits

- Smaller Bundle Size
- Faster Downloads
- Better Startup Performance
- Reduced Network Usage

### Real-Time Use Case

Mobile users accessing applications on slower network connections.

---

# 96. What are Web Workers in Angular?

## Answer

Web Workers allow Angular applications to execute CPU-intensive tasks in a background thread without blocking the main UI thread.

Normally JavaScript runs on a single thread. Heavy calculations can freeze the UI. Web Workers solve this problem by offloading expensive operations.

This improves responsiveness and overall user experience.

### Generate Worker

```bash
ng generate web-worker app
```

### Worker Example

```typescript
addEventListener(
 'message',
 ({ data }) => {

  const result =
  performCalculation(data);

  postMessage(result);

});
```

### Real-Time Use Case

Data analytics, report generation, and large file processing.

---

# 97. What is a Progressive Web Application (PWA) in Angular?

## Answer

A Progressive Web Application (PWA) combines the capabilities of web applications and native mobile applications.

Angular supports PWAs through Service Workers, enabling offline functionality, caching, background synchronization, and push notifications.

PWAs improve reliability and user engagement.

### Enable PWA

```bash
ng add @angular/pwa
```

### Features

- Offline Access
- Push Notifications
- App Installation
- Background Sync

### Real-Time Use Case

E-commerce applications and food delivery platforms.

---

# 98. What are Angular Security Best Practices?

## Answer

Security is a critical concern in Angular applications. Angular provides several built-in security mechanisms, but developers must still follow secure coding practices.

Applications should validate input, sanitize content, protect APIs, and implement strong authentication mechanisms.

Security vulnerabilities can lead to data breaches and unauthorized access.

### Best Practices

- Use HTTPS
- Implement JWT Authentication
- Validate User Input
- Avoid Direct DOM Manipulation
- Use Angular Sanitization
- Protect Sensitive Data
- Implement Route Guards

### Example

```typescript
canActivate:[AuthGuard]
```

### Real-Time Use Case

Securing banking, healthcare, and financial applications.

---

# 99. Explain XSS and CSRF Protection in Angular.

## Answer

### XSS (Cross-Site Scripting)

XSS attacks occur when malicious scripts are injected into web pages and executed in users' browsers.

Angular automatically escapes interpolated values and sanitizes HTML content to reduce XSS risks.

### Example

```html
<p>{{userInput}}</p>
```

Angular safely escapes the content.

---

### CSRF (Cross-Site Request Forgery)

CSRF attacks trick authenticated users into executing unintended actions.

Protection mechanisms include:

- CSRF Tokens
- SameSite Cookies
- Authentication Validation

### Security Recommendations

- Never trust user input
- Use Angular sanitization
- Validate requests on backend
- Implement secure authentication

### Real-Time Use Case

Protecting online banking transactions.

---

# 100. What are Enterprise Angular Architecture and Best Practices?

## Answer

Enterprise Angular applications require a scalable and maintainable architecture that supports large teams, multiple modules, and long-term development.

A well-structured architecture reduces technical debt and makes applications easier to maintain and extend.

Organizations often define coding standards and architectural guidelines to ensure consistency.

### Recommended Project Structure

```text
src/
 ├── core/
 ├── shared/
 ├── features/
 ├── services/
 ├── models/
 ├── guards/
 ├── interceptors/
 ├── store/
 ├── assets/
 └── environments/
```

### Best Practices

- Use Lazy Loading
- Follow SOLID Principles
- Create Reusable Components
- Use Shared and Core Modules
- Implement State Management
- Secure APIs
- Optimize Performance
- Write Unit Tests

### Real-Time Use Case

Large-scale enterprise systems such as ERP, CRM, Banking, Insurance, and Healthcare platforms.

---

# Final Angular Interview Cheat Sheet (3–8 Years Experience)

## Frequently Asked Advanced Topics

### Angular Architecture
1. NgModule
2. Feature Modules
3. Standalone Components
4. Dependency Injection
5. Lazy Loading

### Performance Optimization
1. OnPush
2. TrackBy
3. SSR
4. Hydration
5. Deferrable Views

### RxJS
1. Observable
2. Subject
3. BehaviorSubject
4. switchMap
5. mergeMap

### State Management
1. NgRx
2. Store
3. Actions
4. Reducers
5. Selectors

### Angular 17+ Features
1. Signals
2. Computed Signals
3. Effects
4. Standalone APIs
5. @if
6. @for
7. @switch
8. @defer

### Enterprise Questions
1. Micro Frontends
2. Module Federation
3. Memory Leaks
4. Web Workers
5. Angular Security
6. XSS Protection
7. CSRF Protection
8. Enterprise Architecture

---

## Top 20 Must-Prepare Questions for 3–8 Years Angular Interviews

1. Dependency Injection
2. RxJS and Observables
3. switchMap vs mergeMap
4. Reactive Forms
5. Interceptors
6. Route Guards
7. Lazy Loading
8. Change Detection
9. OnPush Strategy
10. ViewChild
11. Content Projection
12. NgRx Architecture
13. Store & Reducers
14. Selectors & Effects
15. Signals
16. Standalone Components
17. SSR & Hydration
18. Angular Security
19. Performance Optimization
20. Micro Frontends

---