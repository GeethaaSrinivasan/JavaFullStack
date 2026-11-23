# Intermediate Level Angular Interview Questions (31-40)

---

# 31. What is RxJS in Angular?

## Answer

RxJS (Reactive Extensions for JavaScript) is a library used for reactive programming with asynchronous data streams. Angular heavily relies on RxJS for handling HTTP requests, user events, route parameters, and real-time data.

RxJS introduces the concept of Observables, Operators, and Subscriptions, which help developers process asynchronous data efficiently. It provides a cleaner and more maintainable alternative to callbacks and promises.

Understanding RxJS is essential for Angular developers because many Angular APIs return Observables.

### Example

```typescript
import { of } from 'rxjs';

of('Angular', 'RxJS')
  .subscribe(value => console.log(value));
```

### Output

```text
Angular
RxJS
```

### Real-Time Use Case

Handling real-time stock prices, chat messages, notifications, and API responses.

---

# 32. What is an Observable?

## Answer

An Observable is a data stream that emits values over time. Unlike a Promise, an Observable can emit multiple values and can be cancelled before completion.

Observables are lazy, meaning they do not execute until a subscriber listens to them. Angular uses Observables extensively for HTTP communication, event handling, and route navigation.

They help decouple producers and consumers of data.

### Example

```typescript
import { Observable } from 'rxjs';

const employeeObservable =
new Observable(observer => {

  observer.next('Employee 1');
  observer.next('Employee 2');

  observer.complete();

});
```

### Subscriber

```typescript
employeeObservable.subscribe(
 data => console.log(data)
);
```

### Real-Time Use Case

Receiving continuous updates from a WebSocket connection.

---

# 33. What is a Subscription?

## Answer

A Subscription is used to listen to values emitted by an Observable. Without subscription, an Observable will not execute.

Subscriptions allow Angular components to receive and process data from asynchronous streams. Proper subscription management is important to prevent memory leaks.

Angular developers should unsubscribe when a component is destroyed.

### Example

```typescript
subscription =
this.http.get('/api/employees')
.subscribe(data => {

   console.log(data);

});
```

### Cleanup

```typescript
ngOnDestroy() {

  this.subscription.unsubscribe();

}
```

### Real-Time Use Case

Listening to API responses or real-time dashboard updates.

---

# 34. What is the difference between Observable and Promise?

## Answer

Both Observables and Promises are used for handling asynchronous operations, but they have key differences.

Promises emit a single value and execute immediately. Observables can emit multiple values and execute only when subscribed.

Observables also provide powerful operators for transforming and combining streams.

### Comparison

| Feature | Observable | Promise |
|----------|------------|----------|
| Multiple Values | Yes | No |
| Lazy Execution | Yes | No |
| Cancellation | Yes | No |
| Operators | Yes | No |
| RxJS Support | Yes | No |

### Promise Example

```typescript
fetch('/users')
.then(data => console.log(data));
```

### Observable Example

```typescript
this.http.get('/users')
.subscribe(data => console.log(data));
```

### Interview Tip

Observables are preferred in Angular because they offer more flexibility and control.

---

# 35. What are RxJS Operators?

## Answer

Operators are functions that allow developers to transform, filter, combine, and manipulate data emitted by Observables.

Operators make it easier to process complex asynchronous workflows without nested subscriptions.

They improve readability and maintainability of reactive code.

### Common Operators

- map
- filter
- tap
- debounceTime
- switchMap
- mergeMap
- concatMap
- catchError

### Example

```typescript
of(1,2,3,4,5)
.pipe(
  filter(num => num > 3)
)
.subscribe(console.log);
```

### Output

```text
4
5
```

### Real-Time Use Case

Filtering employee records before displaying them.

---

# 36. What is switchMap?

## Answer

switchMap is a higher-order RxJS operator that switches to a new Observable whenever the source Observable emits a value.

If a previous request is still running, switchMap automatically cancels it and subscribes to the latest request. This prevents unnecessary API calls.

switchMap is commonly used in search and autocomplete functionality.

### Example

```typescript
searchControl.valueChanges
.pipe(
  switchMap(keyword =>
    this.http.get('/api/search?q=' + keyword)
  )
)
.subscribe();
```

### Benefits

- Prevents unnecessary requests
- Improves performance
- Avoids race conditions

### Real-Time Use Case

Search suggestions while users type.

---

# 37. What is HttpClient in Angular?

## Answer

HttpClient is Angular's built-in service used for communication with backend REST APIs.

It supports GET, POST, PUT, PATCH, and DELETE requests. HttpClient automatically converts JSON responses into JavaScript objects and returns Observables.

HttpClientModule must be imported before using HttpClient.

### Example

```typescript
constructor(
 private http: HttpClient
){}
```

### GET Request

```typescript
this.http.get('/api/employees')
.subscribe(
 data => console.log(data)
);
```

### Real-Time Use Case

Retrieving employee, customer, or product information from backend services.

---

# 38. What is an HTTP Interceptor?

## Answer

An HTTP Interceptor is a middleware layer that intercepts outgoing HTTP requests and incoming responses globally.

Interceptors are useful for adding authentication tokens, implementing logging, modifying headers, handling errors, and monitoring API calls.

They eliminate repetitive code across services.

### Example

```typescript
@Injectable()
export class AuthInterceptor
implements HttpInterceptor {

 intercept(req: HttpRequest<any>,
           next: HttpHandler) {

   const clonedRequest =
   req.clone({
     setHeaders:{
       Authorization:
       'Bearer TOKEN'
     }
   });

   return next.handle(clonedRequest);
 }

}
```

### Real-Time Use Case

Automatically attaching JWT tokens to secured API requests.

---

# 39. What are Route Guards in Angular?

## Answer

Route Guards control navigation between routes based on predefined conditions. They help secure applications by restricting unauthorized access.

Angular executes guards before activating routes, loading modules, or leaving pages.

Guards play a critical role in authentication and authorization mechanisms.

### Types of Guards

- CanActivate
- CanDeactivate
- CanLoad
- Resolve

### Example

```typescript
{
 path:'admin',
 canActivate:[AuthGuard]
}
```

### Real-Time Use Case

Preventing users from accessing admin pages without proper permissions.

---

# 40. What is CanActivate Guard?

## Answer

CanActivate Guard determines whether a route can be activated before Angular navigates to it.

It is primarily used for authentication and authorization. If the guard returns true, navigation proceeds; otherwise Angular blocks access.

CanActivate is one of the most frequently used guards in enterprise applications.

### Example

```typescript
@Injectable()
export class AuthGuard
implements CanActivate {

 canActivate(): boolean {

   return !!localStorage
          .getItem('token');

 }

}
```

### Route Configuration

```typescript
{
 path:'dashboard',
 component:DashboardComponent,
 canActivate:[AuthGuard]
}
```

### Real-Time Use Case

Allowing access to dashboards only after successful login.

---

## Interview Follow-Up Questions

### What is CanDeactivate Guard?

Used to prevent users from accidentally leaving a page with unsaved changes.

### What is Resolve Guard?

Loads required data before the route is activated.

### What is CanLoad Guard?

Restricts lazy-loaded modules from being loaded by unauthorized users.

### What is Dependency Injection Hierarchy?

Angular provides dependencies through a hierarchical injector system where child injectors inherit services from parent injectors while allowing service overriding when needed.

---
# Intermediate Level Angular Interview Questions (41-50)

---

# Intermediate Level Angular Interview Questions (41-50)

---

# 41. What is CanDeactivate Guard?

## Answer

CanDeactivate Guard is used to determine whether a user can leave a route or component. It is commonly used to prevent accidental navigation when there are unsaved changes in a form.

Before Angular destroys the current component and navigates away, it invokes the CanDeactivate guard. The guard can return true, false, Promise, or Observable.

This helps improve user experience and prevents data loss.

### Example

```typescript
export interface CanComponentDeactivate {
  canDeactivate(): boolean;
}
```

```typescript
@Injectable()
export class UnsavedChangesGuard
implements CanDeactivate<CanComponentDeactivate> {

  canDeactivate(
    component: CanComponentDeactivate
  ): boolean {

    return component.canDeactivate();

  }

}
```

### Route Configuration

```typescript
{
 path:'employee-edit',
 component: EmployeeEditComponent,
 canDeactivate:[UnsavedChangesGuard]
}
```

### Real-Time Use Case

Preventing users from leaving an employee registration form without saving changes.

---

# 42. What is Resolve Guard?

## Answer

Resolve Guard is used to fetch required data before a route is activated. This ensures that all necessary data is available before a component is displayed.

Instead of showing a loading indicator after navigation, Angular waits until the resolver completes its task.

Resolve guards improve user experience and reduce unnecessary loading states.

### Example

```typescript
@Injectable()
export class EmployeeResolver
implements Resolve<any> {

  constructor(
    private empService: EmployeeService
  ) {}

  resolve() {
    return this.empService.getEmployees();
  }

}
```

### Route Configuration

```typescript
{
 path:'employees',
 component: EmployeeComponent,
 resolve:{
   employees: EmployeeResolver
 }
}
```

### Accessing Data

```typescript
this.route.data.subscribe(data => {
  this.employees = data['employees'];
});
```

### Real-Time Use Case

Loading customer profiles before navigating to the profile page.

---

# 43. What is CanLoad Guard?

## Answer

CanLoad Guard prevents Angular from loading lazy-loaded modules until specific conditions are satisfied.

Unlike CanActivate, CanLoad stops the module itself from being downloaded by unauthorized users.

This enhances security and improves application performance by avoiding unnecessary module downloads.

### Example

```typescript
@Injectable()
export class AdminGuard
implements CanLoad {

 canLoad(): boolean {

   return localStorage
         .getItem('role') === 'ADMIN';

 }

}
```

### Route Configuration

```typescript
{
 path:'admin',
 loadChildren: () =>
 import('./admin/admin.module')
 .then(m => m.AdminModule),
 canLoad:[AdminGuard]
}
```

### Real-Time Use Case

Preventing non-admin users from downloading admin-related modules.

---

# 44. What is Dependency Injection Hierarchy?

## Answer

Angular uses a hierarchical dependency injection system where services can be provided at different levels such as root, module, component, or directive.

Child injectors inherit services from parent injectors unless they provide their own implementation. This mechanism provides flexibility and helps optimize memory usage.

Understanding injector hierarchy is important when debugging service instances.

### Example

```typescript
@Injectable({
  providedIn:'root'
})
export class EmployeeService {}
```

### Component-Level Service

```typescript
@Component({
 selector:'app-employee',
 providers:[EmployeeService]
})
```

### Benefits

- Better Memory Management
- Scoped Services
- Improved Performance
- Flexible Dependency Resolution

### Real-Time Use Case

Sharing a service globally while allowing specific components to override functionality.

---

# 45. What is ViewChild?

## Answer

ViewChild is a decorator that allows a component to access a child component, directive, or DOM element after the view has been initialized.

It is commonly used when direct interaction with child elements is required.

ViewChild becomes available after the ngAfterViewInit lifecycle hook executes.

### Example

```typescript
@ViewChild('username')
username!: ElementRef;
```

### HTML

```html
<input #username>
```

### Accessing Element

```typescript
ngAfterViewInit() {
  this.username.nativeElement.focus();
}
```

### Real-Time Use Case

Automatically focusing a login textbox when a page loads.

---

# 46. What is Content Projection?

## Answer

Content Projection allows a parent component to pass content into a child component using the `<ng-content>` directive.

This feature makes components more reusable and flexible because the projected content can vary depending on usage.

Content projection is similar to slots in Web Components.

### Child Component

```html
<div class="card">
  <ng-content></ng-content>
</div>
```

### Parent Component

```html
<app-card>
  <h3>Employee Details</h3>
</app-card>
```

### Benefits

- Better Reusability
- Cleaner Components
- Flexible UI Design

### Real-Time Use Case

Creating reusable card, modal, and dialog components.

---

# 47. What is Change Detection in Angular?

## Answer

Change Detection is the mechanism Angular uses to detect changes in application data and automatically update the DOM.

Whenever a component's data changes due to user interaction, API response, or asynchronous events, Angular checks the affected components and updates the view.

By default, Angular uses Zone.js to trigger change detection automatically.

### Example

```typescript
export class EmployeeComponent {

 employeeName = 'John';

 updateName() {
   this.employeeName = 'David';
 }

}
```

```html
<p>{{employeeName}}</p>
```

### Real-Time Use Case

Updating dashboards when new API data arrives.

---

# 48. What is OnPush Change Detection Strategy?

## Answer

OnPush is an optimized change detection strategy that reduces the number of checks Angular performs.

With OnPush, Angular only checks a component when an Input reference changes, an event occurs inside the component, or change detection is manually triggered.

This strategy significantly improves performance in large applications.

### Example

```typescript
@Component({
 selector:'app-employee',
 templateUrl:'./employee.component.html',
 changeDetection:
 ChangeDetectionStrategy.OnPush
})
```

### Advantages

- Better Performance
- Reduced CPU Usage
- Faster Rendering
- Optimized UI Updates

### Real-Time Use Case

Applications displaying thousands of records in tables and dashboards.

---

# 49. What is TrackBy in ngFor?

## Answer

TrackBy is used with the *ngFor directive to uniquely identify items in a collection.

Without TrackBy, Angular re-renders the entire list whenever data changes. With TrackBy, Angular updates only modified elements, improving performance.

TrackBy is highly recommended for large data sets.

### Example

```typescript
trackByEmployeeId(
 index:number,
 employee:any
){
 return employee.id;
}
```

### HTML

```html
<tr *ngFor="
 let emp of employees;
 trackBy: trackByEmployeeId">
</tr>
```

### Real-Time Use Case

Displaying thousands of employees in a data grid efficiently.

---

# 50. What are Dynamic Components in Angular?

## Answer

Dynamic Components are components that are created and inserted into the view at runtime instead of being declared directly in templates.

Angular provides ViewContainerRef and ComponentFactory mechanisms for dynamically loading components.

Dynamic components increase flexibility and support advanced UI requirements.

### Example

```typescript
constructor(
 private viewContainerRef:
 ViewContainerRef
){}
```

### Dynamic Creation

```typescript
this.viewContainerRef
.createComponent(
 EmployeeComponent
);
```

### Benefits

- Runtime Component Loading
- Reusable UI Elements
- Better Flexibility
- Configurable Interfaces

### Real-Time Use Case

Loading dynamic dashboard widgets, plugin modules, or popup components.

---

## Frequently Asked Interview Follow-Up Questions

### Difference Between ViewChild and Content Projection

| ViewChild | Content Projection |
|------------|--------------------|
| Access Child Elements | Insert External Content |
| Code Interaction | UI Reusability |
| Component Control | Flexible Layout |

### Difference Between Default and OnPush Change Detection

| Default | OnPush |
|----------|---------|
| Checks Entire Component Tree | Checks Selected Components |
| More CPU Usage | Better Performance |
| Suitable for Small Apps | Suitable for Large Apps |

### When Should TrackBy Be Used?

TrackBy should be used whenever large collections are rendered using ngFor to improve performance and reduce unnecessary DOM updates.

---