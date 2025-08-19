## How DI works?

STEP 1:

```typescript
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root' // Registers the service as a singleton at the root level
})
export class MyService {
  getData(): string {
    return 'Hello from MyService!';
  }
}
```

* **The **@Injectable** decorator marks the class as injectable.**
* **providedIn: 'root'** ensures the service is available application-wide as a singleton.

**Angular’s DI system needs to know how to provide the service. The **providedIn: 'root'** metadata in the service handles this automatically. However, you can also register providers manually in a module or component.**1.

**Using **providedIn: 'root'** (Recommended)**:

* **As shown above, this is the modern way to register services, introduced in Angular 6+.**
* **It ensures a single instance of the service is created and tree-shaking optimizes unused services.**

1. **Alternative: Register in NgModule**:
   If you need to scope the service to a specific module, add it to the **providers** array in **app.module.ts**:

```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';
import { MyService } from './services/my.service';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule],
  providers: [MyService], // Register the service here
  bootstrap: [AppComponent]
})
export class AppModule {}
```

**Component-Level Provider (Optional)**:
If you want a new instance of the service for a specific component and its children, register it in the component’s metadata:

```typescript
@Component({
  selector: 'app-my-component',
  template: '...',
  providers: [MyService] // New instance for this component
})
export class MyComponent {}
```

Inject the service into the component:
Open src/app/my-component/my-component.component.ts and inject MyService via the constructor:

```typescript
import { Component, OnInit } from '@angular/core';
import { MyService } from '../services/my.service';

@Component({
  selector: 'app-my-component',
  template: `<p>{{ data }}</p>`
})
export class MyComponent implements OnInit {
  data: string;

  constructor(private myService: MyService) {} // Inject the service

  ngOnInit(): void {
    this.data = this.myService.getData(); // Use the service
  }
}
```

The private myService: MyService syntax tells Angular to inject an instance of MyService.

**Explore Advanced DI (Optional)**1. Using InjectionToken for Non-Class Dependencies:
   If you need to inject a configuration value (e.g., API URL), create an InjectionToken:

```typescript
import { InjectionToken } from '@angular/core';

export const API_URL = new InjectionToken<string>('API_URL');

// In app.module.ts
@NgModule({
  providers: [{ provide: API_URL, useValue: 'https://api.example.com' }]
})
export class AppModule {}
```

Types of Providers

Angular supports various provider types for flexibility:*

Class Provider: provide: MyService, useClass: MyService

* Value Provider: provide: 'API_URL', useValue: 'https://api.example.com'
* Factory Provider: provide: MyService, useFactory: () => new MyService(config)
* Alias Provider: provide: MyService, useExisting: OtherService
* Injection Tokens: Used for non-class dependencies (e.g., configuration objects)

Summary of Steps1. Create a service with @Injectable and define its logic.

1. Register the service (via providedIn: 'root' or in a module/component).
2. Create a component and inject the service via its constructor.
3. Use the service in the component to fetch or manipulate data.
4. Add the component to the app’s template.
5. Run and test the app.
6. (Optional) Explore advanced DI features like InjectionToken or factory providers.
7. Test the DI setup using Angular’s testing utilities.

## BehaviourSubject

A BehaviorSubject in Angular (part of the RxJS library) is a special type of Subject that holds a current value and emits it to new subscribers immediately upon subscription. Unlike a regular Subject, it always has a value, even if no events have been emitted yet, making it useful for representing state that components can rely on.Key Characteristics of BehaviorSubjectInitial Value: Requires an initial value when created.
Current Value Access: Subscribers get the most recent value (or initial value) immediately upon subscription.
Multiple Subscribers: Like other Subjects, it supports multiple subscribers, and all receive the same value when next() is called.
State Management: Often used to hold and share state (e.g., user data, form state) across components.
Common Methods

next(value): Emits a new value to all subscribers.
getValue(): Retrieves the current value of the BehaviorSubject.
subscribe(): Allows components to subscribe to value changes.
asObservable(): Converts the BehaviorSubject to an Observable to prevent external code from calling next().

Use Cases
State Management: Share application state (e.g., user authentication status, theme settings).
Form Data: Track form input changes across components.
Real-Time Updates: Reflect changes like notifications or live data feeds.

## Lifecycle Hooks

OnChanges
Fired when one or more of the component or directive properties have been changed.

OnInit
Fired when component or directive properties have been initialized.

OnDestroy
Fired when the component or directive instance is destroyed

AfterContentInit
Fire after the initialization of the content of the component or directive has finished.

AfterContentChecked
Fire after the view has been fully initialized.

AfterViewInit
Fires after initializing both the component view and any of its child views. This is a useful lifecycle hook for plugins
outside of the Angular 2 ecosystem. For example, you could use this method to initialize a jQuery date picker based on the markup that Angular 2 has rendered.

## Data Binding

Data binding in Angular is a mechanism that synchronizes the data between the component (TypeScript) and the template (HTML). It enables dynamic updates to the UI when the underlying data changes and vice versa. Angular supports several types of data binding, which I’ll outline below with concise explanations and examples.Types of Data BindingInterpolation (One-Way Binding: Component to View)  Uses double curly braces {{ }} to display component data in the template.
Data flows from the component to the view.

```typescript
// Component
export class AppComponent {
  title = 'Hello, Angular!';
}
```

```html
<!-- Template -->
<h1>{{ title }}</h1>
```

Output: Displays "Hello, Angular!" in the UI.

Property Binding (One-Way Binding: Component to View)  Binds a component property to an HTML element property using square brackets [ ].

```typescript

// Component
export class AppComponent {
  isDisabled = true;
}
```

```html
<!-- Template -->
<button [disabled]="isDisabled">Click me</button>
```

Output: The button is disabled based on the isDisabled property.

Event Binding (One-Way Binding: View to Component)  Binds DOM events to component methods using parentheses ( ).

```typescript
// Component
export class AppComponent {
  handleClick() {
    console.log('Button clicked!');
  }
}
```

```html
<!-- Template -->
<button (click)="handleClick()">Click me</button>
```

Output: Logs "Button clicked!" to the console when the button is clicked.

**Two-Way Binding**  Combines property and event binding to synchronize data between component and view.
Uses [(ngModel)] directive (requires FormsModule to be imported).

```typescript
// Component
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';

@Component({
  selector: 'app-root',
  template: `<input [(ngModel)]="name" placeholder="Enter name">
             <p>You entered: {{ name }}</p>`,
  standalone: true,
  imports: [FormsModule]
})
export class AppComponent {
  name = '';
}
```

Output: The input field and the paragraph update simultaneously as the user types.

Attribute Binding  Binds component data to HTML attributes (not properties) using [attr.].

```typescript

// Component
export class AppComponent {
  colSpanValue = 2;
}
```

```html
<!-- Template -->
<td [attr.colspan]="colSpanValue">Spanning columns</td>
```

Output: The `<td>` element spans 2 columns.

Class and Style Binding  Dynamically apply CSS classes or styles based on component logic.
Class Binding

```typescript

// Component
export class AppComponent {
  isActive = true;
}
```

```html
<!-- Template -->
<div [class.active]="isActive">Conditional Class</div>
```

```css
.active { background-color: lightblue; }
```

Output: The div has a light blue background if isActive is true.
Style Binding

```html

<div [style.backgroundColor]="isActive ? 'lightblue' : 'white'">Conditional Style</div>
```

Key PointsOne-Way Binding: Data flows either from component to view (interpolation, property binding) or view to component (event binding).
Two-Way Binding: Requires FormsModule for ngModel and is useful for form inputs.
Performance: Angular’s change detection automatically updates the UI when bound data changes, but overuse of two-way binding can impact performance in large applications.
Directives: Structural directives like *ngIf and *ngFor often work with data binding to conditionally render or iterate over elements.

## Angular Directives

Angular directives are special markers (attributes or elements) in the DOM that extend HTML functionality or manipulate the DOM in Angular applications. They allow you to attach behavior to elements, modify their structure, or create reusable components. Angular has three main types of directives: Component Directives, Structural Directives, and Attribute Directives.

Defined using the @Component decorator, they encapsulate HTML, CSS, and TypeScript logic.
Identified by a leading asterisk (*) in templates. *ngif
Modify the behavior or appearance of an element without altering the DOM structure. ngClass

# What is Angular Services?

what is http interceptor

what is observable

Difference between Constructor and ngOnint?

What is AuthGuard or RouteGuard

Difference between ViewChild and ViewChildren

Difference between ContentChild and ContentChildren

what is ng-content

what is queryList

Template diven and reactive form

how angular handle change detection
