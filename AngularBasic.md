# Angular 100 Interview Questions and Answers

## Beginner Level (1-30)

---

# 1. What is Angular?

## Answer

Angular is a TypeScript-based open-source front-end framework developed by Google for building Single Page Applications (SPA). It follows a component-based architecture that promotes code reusability and maintainability. Angular provides built-in features such as routing, dependency injection, forms, HTTP communication, and state management support.

In enterprise applications, Angular is preferred because it provides a structured development approach and supports large-scale application development.

### Example

```typescript
@Component({
  selector: 'app-root',
  template: `<h1>Welcome to Angular</h1>`
})
export class AppComponent {}
```

### Real-World Use Case

E-commerce applications such as Amazon-like platforms can use Angular to build product catalog, cart, order management, and payment modules.

---

# 2. What are the advantages of Angular?

## Answer

Angular provides several advantages for enterprise application development. It follows a modular architecture which improves maintainability and makes development easier. Angular includes built-in routing, dependency injection, form validation, and HTTP services, reducing the need for third-party libraries.

Because Angular uses TypeScript, developers benefit from static typing, better IDE support, compile-time error checking, and enhanced code readability.

### Advantages

- Component-Based Architecture
- Dependency Injection
- TypeScript Support
- Powerful CLI
- RxJS Integration
- Lazy Loading
- Built-in Testing Support

### Example

```bash
ng generate component employee
```

### Real-World Use Case

Banking and FinTech applications often prefer Angular due to its structure and scalability.

---

# 3. What is a Single Page Application (SPA)?

## Answer

A Single Page Application is a web application that loads a single HTML page and dynamically updates content without reloading the entire page. Angular applications are typically SPAs because navigation happens through routing instead of full page refreshes.

SPAs improve user experience by reducing server round-trips and providing faster navigation between views.

### Example

```typescript
{ path: 'dashboard', component: DashboardComponent }
```

### Advantages

- Faster Navigation
- Better User Experience
- Reduced Server Load
- Improved Performance

---

# 4. What is TypeScript?

## Answer

TypeScript is a superset of JavaScript developed by Microsoft. It introduces static typing, interfaces, classes, decorators, and modern object-oriented programming concepts.

Angular is built entirely on TypeScript because it improves maintainability, enables compile-time checks, and enhances productivity through better tooling.

### Example

```typescript
let username: string = "Geetha";
let experience: number = 8;
```

### Interface Example

```typescript
interface Employee {
  id:number;
  name:string;
}
```

### Interview Follow-Up

Difference between:

- JavaScript and TypeScript
- any vs unknown
- interface vs type

---

# 5. What is a Component in Angular?

## Answer

A Component is the fundamental building block of Angular applications. Components control a section of the user interface and consist of HTML, CSS, and TypeScript code.

Every Angular application contains at least one component called the root component. Components help divide applications into smaller reusable units.

### Example

```typescript
@Component({
 selector:'app-user',
 templateUrl:'./user.component.html',
 styleUrls:['./user.component.css']
})
export class UserComponent {
}
```

### Real-World Example

An online shopping site may have:

- Product Component
- Cart Component
- Login Component
- Header Component

---

# 6. What is a Module?

## Answer

A Module in Angular is used to organize the application into cohesive blocks of functionality. It defines which components, directives, and services belong together.

Angular applications contain a root module named AppModule. Feature modules can be created to separate functionality and enable lazy loading.

### Example

```typescript
@NgModule({
 declarations:[
  AppComponent,
  EmployeeComponent
 ],
 imports:[
  BrowserModule
 ]
})
export class AppModule {}
```

### Types of Modules

1. Root Module
2. Feature Module
3. Shared Module
4. Core Module

---

# 7. What is a Directive?

## Answer

Directives are instructions that extend or modify the behavior of DOM elements. They allow developers to manipulate elements without directly accessing the DOM.

Angular provides three types of directives: Component Directives, Structural Directives, and Attribute Directives.

### Example

```html
<div *ngIf="isLoggedIn">
 Welcome User
<*div>
```

### Common Directives

-**ngIf
- *ngFor
- ngClass
- ngStyle*
---

# 8. What is a Structural Di*ective?

## Answer

Structural dir*ctives change the layout of the DO* by adding, removing, or manipulat*ng elements dynamically. They are *dentified by the * symbol.

These *irectives are commonly used for co*ditional rendering and iteration o*er collections.

### Example

```h*ml
<div *ngIf="showMessage">
 Welc*me
</div>
```

### ngFor Example

*``html
<li *ngFor="let emp of empl*yees">
 {{emp.name}}
</li>
```

##* Common Structural Directives

- **gIf
- *ngFor
- *ngSwitch

---

# 9* What is an Attribute Directive?

*# Answer

Attribute directives mod*fy the appearance or behavior of e*isting elements without changing t*e DOM structure.

Unlike structura* directives, attribute directives *o not add or remove elements; they*only alter styling or behavior.

#*# Example

```html
<p [ngClass]="'*ctive'">
 Angular Interview
</p>
`*`

### Example Using ngStyle

```h*ml
<p [ngStyle]="{'color':'blue'}"*
 Angular
</p>
```

### Common Att*ibute Directives

- ngClass
- ngSt*le
- Custom Attribute Directives

*--

# 10. What is Data Binding?

#* Answer

Data Binding is the mecha*ism used by Angular to synchronize*data between the component and the*view. It eliminates the need for m*nual DOM manipulation.

Angular su*ports four types of data binding:
*1. Interpolation
2. Property Bindi*g
3. Event Binding
4. Two-Way Bind*ng

### Interpolation

```html
<p>*{name}}</p>
```

### Property Bind*ng

```html
<img [src]="imageUrl">*```

### Event Binding

```html
<b*tton (click)="save()">
 Save
</but*on>
```

### Two-Way Binding

```h*ml
<input [(ngModel)]="username">
*``

### Real-World Example

A regi*tration form uses two-way binding *o instantly update form values bet*een the UI and component.

---

# 11. What is Interpolation in Angular?

## Answer

Interpolation is a one-way data binding mechanism used to display component data in the HTML template. It uses double curly braces `{{ }}` to bind component properties to the view.

Whenever the value of a component property changes, Angular automatically updates the UI through its change detection mechanism. Interpolation is commonly used to display text, numbers, dates, and other dynamic data.

Interpolation can only be used for displaying values and not for assigning values or handling events.

### Example

```typescript
export class EmployeeComponent {
  employeeName = 'Geetha';
  experience = 8;
}
```

```html
<h2>{{ employeeName }}</h2>
<p>Experience: {{ experience }} Years</p>
```

### Real-Time Use Case

Displaying logged-in user information in the application header.

---

# 12. What is Property Binding?

## Answer

Property Binding is used to bind component data to an HTML element property. It uses square brackets `[]` and enables dynamic updates to DOM properties.

Unlike interpolation, property binding works with element properties such as `src`, `disabled`, `hidden`, and `value`. Angular automatically updates the DOM whenever the bound property changes.

Property binding helps avoid direct DOM manipulation and keeps UI synchronized with component data.

### Example

```typescript
export class ProductComponent {
  imageUrl = 'assets/laptop.png';
}
```

```html
<img [src]="imageUrl">
```

### Disable Button Example

```typescript
isDisabled = true;
```

```html
<button [disabled]="isDisabled">
 Save
</button>
```

### Real-Time Use Case

Dynamically enabling or disabling buttons based on form validation status.

---

# 13. What is Event Binding?

## Answer

Event Binding allows communication from the view to the component by responding to user actions such as clicks, key presses, mouse movements, and form submissions.

Angular uses parentheses `()` to bind DOM events to component methods. When an event occurs, Angular executes the associated method.

Event binding helps developers create interactive applications without directly writing JavaScript event listeners.

### Example

```typescript
export class EmployeeComponent {

  saveEmployee() {
    console.log('Saved Successfully');
  }

}
```

```html
<button (click)="saveEmployee()">
 Save
</button>
```

### Keyboard Event Example

```html
<input (keyup)="searchEmployee()">
```

### Real-Time Use Case

Executing API calls when users click a Search button.

---

# 14. What is Two-Way Data Binding?

## Answer

Two-Way Data Binding allows synchronization between the component and the view. Any change in the UI updates the component, and any change in the component updates the UI automatically.

Angular implements two-way binding using the `[(ngModel)]` directive provided by the FormsModule.

This approach reduces boilerplate code and is commonly used in forms and user input scenarios.

### Example

```typescript
export class UserComponent {
  username = '';
}
```

```html
<input [(ngModel)]="username">

<p>{{username}}</p>
```

### Benefits

- Less code
- Automatic synchronization
- Easy form handling
- Improved user experience

### Real-Time Use Case

Registration and profile update forms.

---

# 15. What is Dependency Injection (DI)?

## Answer

Dependency Injection is a design pattern used by Angular to provide required dependencies automatically to classes instead of creating them manually.

Angular maintains an injector container that creates and manages object lifecycles. This promotes loose coupling, better maintainability, easier testing, and higher reusability.

DI is one of the core concepts that makes Angular suitable for enterprise applications.

### Example

```typescript
@Injectable({
 providedIn: 'root'
})
export class EmployeeService {

}
```

```typescript
constructor(private employeeService: EmployeeService) {

}
```

### Advantages

- Loose Coupling
- Better Unit Testing
- Improved Reusability
- Easier Maintenance

### Real-Time Use Case

Injecting services for API communication throughout the application.

---

# 16. What is a Service in Angular?

## Answer

A Service is a TypeScript class used to encapsulate reusable business logic, API calls, validation logic, and shared functionality.

Services allow components to remain focused on UI responsibilities while business logic remains centralized and reusable.

Angular services are commonly injected into components using Dependency Injection.

### Example

```typescript
@Injectable({
 providedIn: 'root'
})
export class EmployeeService {

  getEmployees() {
    return [
      { id:1, name:'John' },
      { id:2, name:'David' }
    ];
  }

}
```

### Component Usage

```typescript
constructor(private empService: EmployeeService) {}
```

### Real-Time Use Case

Managing employee data retrieval across multiple screens.

---

# 17. What is Angular CLI?

## Answer

Angular CLI (Command Line Interface) is a powerful tool that automates Angular project creation, development, testing, building, and deployment activities.

CLI significantly improves developer productivity by generating boilerplate code and enforcing Angular best practices.

Most real-world Angular projects heavily rely on CLI commands throughout the development lifecycle.

### Create Project

```bash
ng new employee-app
```

### Create Component

```bash
ng generate component employee
```

### Run Application

```bash
ng serve
```

### Benefits

- Faster Development
- Consistent Project Structure
- Automatic Configuration
- Reduced Boilerplate Code

---

# 18. What is Routing in Angular?

## Answer

Routing enables navigation between different views or pages within an Angular application without reloading the browser page.

Angular Router maps URLs to components and loads the appropriate view dynamically. Routing helps build Single Page Applications with seamless navigation.

Applications such as e-commerce, banking, and LMS systems heavily depend on routing.

### Route Configuration

```typescript
const routes: Routes = [
 {
  path:'home',
  component:HomeComponent
 },
 {
  path:'employees',
  component:EmployeeComponent
 }
];
```

### Navigation

```html
<a routerLink="/employees">
 Employees
</a>
```

### Real-Time Use Case

Navigating between Dashboard, Orders, Products, and Profile pages.

---

# 19. What is Router Outlet?

## Answer

Router Outlet is a directive that acts as a placeholder where Angular dynamically loads routed components.

Whenever a user navigates to a different route, Angular displays the corresponding component inside the router outlet.

Without Router Outlet, Angular routing would not know where to display the selected component.

### Example

```html
<router-outlet></router-outlet>
```

### Route Example

```typescript
{
 path:'dashboard',
 component:DashboardComponent
}
```

When users open `/dashboard`, Angular loads DashboardComponent inside the router outlet.

### Real-Time Use Case

Displaying different pages inside a common application layout.

---

# 20. What is a Pipe in Angular?

## Answer

A Pipe is a feature that transforms data before displaying it in the view. Pipes improve readability by formatting values without modifying the original data.

Angular provides several built-in pipes such as DatePipe, CurrencyPipe, PercentPipe, UpperCasePipe, and LowerCasePipe. Developers can also create custom pipes.

Pipes help keep templates clean and maintain a clear separation between presentation and business logic.

### Date Pipe Example

```html
{{ today | date }}
```

### Currency Pipe Example

```html
{{ salary | currency:'INR' }}
```

### UpperCase Pipe Example

```html
{{ employeeName | uppercase }}
```

### Real-Time Use Case

Displaying salary, currency values, dates, and formatted user information across enterprise applications.

---
---

# 21. What are Built-in Pipes in Angular?

## Answer

Built-in Pipes are predefined pipes provided by Angular to transform and format data before displaying it in the view. They help developers present data in a user-friendly format without writing additional logic.

Angular includes several commonly used pipes such as DatePipe, CurrencyPipe, PercentPipe, UpperCasePipe, LowerCasePipe, JsonPipe, and SlicePipe.

Using built-in pipes keeps templates clean and improves code readability.

### Common Built-in Pipes

- DatePipe
- CurrencyPipe
- PercentPipe
- UpperCasePipe
- LowerCasePipe
- SlicePipe
- JsonPipe

### Example

```html
<p>{{ today | date:'dd/MM/yyyy' }}</p>

<p>{{ salary | currency:'INR' }}</p>

<p>{{ employeeName | uppercase }}</p>
```

### Real-Time Use Case

Formatting salaries, account balances, dates, and percentages in banking applications.

---

# 22. What is a Custom Pipe?

## Answer

A Custom Pipe is a user-defined pipe that transforms data according to business requirements. When built-in pipes cannot satisfy a specific need, developers create custom pipes.

Custom pipes improve code reusability and keep transformation logic separate from components.

Angular custom pipes implement the PipeTransform interface.

### Example

```typescript
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'reverse'
})
export class ReversePipe implements PipeTransform {

  transform(value: string): string {
    return value.split('').reverse().join('');
  }

}
```

### Usage

```html
<p>{{ 'Angular' | reverse }}</p>
```

### Output

```text
ralugnA
```

### Real-Time Use Case

Masking customer details, formatting account numbers, or displaying custom business data formats.

---

# 23. What is View Encapsulation?

## Answer

View Encapsulation controls how component styles are applied within Angular applications. It determines whether styles should affect only a specific component or the entire application.

Angular provides style isolation to prevent CSS conflicts between components.

There are three types of View Encapsulation available in Angular.

### Types

#### 1. Emulated (Default)

Angular simulates Shadow DOM behavior by adding unique attributes.

```typescript
encapsulation: ViewEncapsulation.Emulated
```

#### 2. None

Styles become global and affect all components.

```typescript
encapsulation: ViewEncapsulation.None
```

#### 3. ShadowDom

Uses native browser Shadow DOM implementation.

```typescript
encapsulation: ViewEncapsulation.ShadowDom
```

### Real-Time Use Case

Preventing CSS conflicts in large enterprise applications with hundreds of components.

---

# 24. What is ngOnInit Lifecycle Hook?

## Answer

ngOnInit is one of the most commonly used Angular lifecycle hooks. It is executed once after Angular initializes the component and its input properties.

Developers often use ngOnInit to load initial data, call APIs, initialize variables, and configure component settings.

The hook is part of Angular's OnInit interface.

### Example

```typescript
import { OnInit } from '@angular/core';

export class EmployeeComponent implements OnInit {

  ngOnInit(): void {
    console.log("Component Initialized");
  }

}
```

### Common Uses

- API Calls
- Initial Data Loading
- Variable Initialization
- Form Setup

### Real-Time Use Case

Loading employee records when the component opens.

---

# 25. What are Angular Lifecycle Hooks?

## Answer

Lifecycle Hooks are special methods provided by Angular that allow developers to execute code during different stages of a component's lifecycle.

These hooks help manage component creation, updates, rendering, and destruction.

Understanding lifecycle hooks is important for handling initialization, change detection, performance tuning, and cleanup activities.

### Common Lifecycle Hooks

| Hook | Purpose |
|--------|---------|
| ngOnInit | Initialization |
| ngOnChanges | Input Changes |
| ngDoCheck | Custom Change Detection |
| ngAfterViewInit | View Initialization |
| ngAfterContentInit | Content Initialization |
| ngOnDestroy | Cleanup |

### Example

```typescript
ngOnDestroy() {
  this.subscription.unsubscribe();
}
```

### Real-Time Use Case

Cleaning up subscriptions when a component is destroyed.

---

# 26. What is ngOnChanges?

## Answer

ngOnChanges is called whenever the value of an @Input property changes. It allows components to react to changes received from parent components.

The hook receives a SimpleChanges object containing current and previous values.

It is useful when component behavior depends on incoming data.

### Example

```typescript
@Input()
employeeName!: string;

ngOnChanges(changes: SimpleChanges) {

  console.log(changes['employeeName']);

}
```

### Real-Time Use Case

Refreshing employee details whenever a new employee is selected from a list.

---

# 27. What is Lazy Loading?

## Answer

Lazy Loading is a performance optimization technique where Angular loads feature modules only when users navigate to them.

Instead of loading the entire application at startup, Angular loads modules on demand. This significantly reduces the initial bundle size and improves application startup time.

Lazy loading is recommended for large-scale enterprise applications.

### Example

```typescript
{
 path:'admin',
 loadChildren: () =>
   import('./admin/admin.module')
   .then(m => m.AdminModule)
}
```

### Benefits

- Faster Application Startup
- Reduced Bundle Size
- Better User Experience
- Improved Scalability

### Real-Time Use Case

Loading Admin Module only when administrators access it.

---

# 28. What is Eager Loading?

## Answer

Eager Loading is the default module loading strategy in Angular. All modules are loaded when the application starts regardless of whether users access them.

While eager loading simplifies development, it can increase application startup time.

Eager loading is generally suitable for small applications with limited functionality.

### Example

```typescript
imports: [
  BrowserModule,
  EmployeeModule,
  ProductModule
]
```

### Advantages

- Simpler Configuration
- Faster Navigation After Load
- Suitable for Small Applications

### Real-Time Use Case

Internal tools where all modules are frequently accessed by users.

---

# 29. What are Reactive Forms?

## Answer

Reactive Forms are Model-Driven Forms introduced by Angular to build scalable, maintainable, and testable forms.

The form structure is created within the component class using FormGroup and FormControl. Reactive forms provide better validation, dynamic form creation, and unit testing support.

They are the preferred choice for enterprise applications.

### Example

```typescript
import { FormGroup, FormControl } from '@angular/forms';

employeeForm = new FormGroup({

  employeeName:
    new FormControl(''),

  email:
    new FormControl('')

});
```

### HTML

```html
<form [formGroup]="employeeForm">

  <input formControlName="employeeName">

</form>
```

### Real-Time Use Case

Complex registration forms, employee onboarding forms, and online banking applications.

---

# 30. What are Template-Driven Forms?

## Answer

Template-Driven Forms create and manage forms primarily in the HTML template using Angular directives such as ngModel.

These forms are easier to learn and suitable for small applications with simple validation requirements.

Angular automatically creates the internal form model based on template directives.

### Example

```typescript
export class UserComponent {

  username = '';

}
```

### HTML

```html
<form>

  <input
      name="username"
      [(ngModel)]="username">

</form>
```

### Advantages

- Easy to Implement
- Less TypeScript Code
- Suitable for Small Forms

### Real-Time Use Case

Feedback forms, contact forms, and simple user profile pages.

---

# Interview Follow-Up Question

### Reactive Forms vs Template-Driven Forms

| Feature | Reactive Forms | Template-Driven Forms |
|----------|----------------|----------------------|
| Approach | Model Driven | Template Driven |
| Scalability | High | Medium |
| Testing | Easy | Moderate |
| Dynamic Forms | Excellent | Limited |
| Validation | Advanced | Basic |
| Enterprise Usage | Recommended | Less Preferred |

---