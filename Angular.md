# What is Angular and why is it used?

- Angular is a platform and framework for building single-page client applications using HTML and TypeScript.
- Angular is written in TypeScript.
- It's scalable, maintainable, and testable.

# What are Angular Components?

- Components are the fundamental building blocks of Angular applications.
- Use CSS, TS and HTML File used in components.

# Angular Modules

- Angular applications are modular and Angular has its own modularity system called NgModules.
- An NgModule is a class marked by the @NgModule decorator.

# What is Data Binding in Angular?

- There are four forms of data binding in Angular:

  - Interpolation,
  - Property Binding,
  - Event Binding,
  - and Two-Way Data Binding.

    <!-- Interpolation -->
    <h1>{{title}}</h1>

    <!-- Property Binding -->

    <img [src]="imageUrl">

    <!-- Event Binding -->

    <button (click)="onClick()">Click me</button>

    <!-- Two-Way Data Binding -->

    <input [(ngModel)]="name">

# What is Dependency Injection in Angular?

- Dependency Injection (DI) is a design pattern used to implement IoC (Inversion of Control).
- It allows a class to request dependencies from external sources rather than creating them itself.
- Angular uses DI to provide components with services and other dependencies.

# What are Angular Directives?

- There are three types of directives:
  - Component Directives,
  - Structural Directives,
  - Attribute Directives.

# What is Angular Router?

-Angular Router is a powerful and flexible navigational service in Angular that enables navigation from one view to another as users perform application tasks
-Angular Router enables navigation by interpreting a browser URL as an instruction to change the view.

# What is Angular Forms?

- Two approaches to handling user input through forms:
  1.  reactive forms
  2.  template-driven forms.

# What are Angular Services?

- Create reusable business logic and data operations
- Services are singleton objects, instantiated only once during the lifetime of an application.
- Typically used to perform tasks such as fetching data from a server

  <!-- Example -->

  import { Injectable } from '@angular/core';
  import { HttpClient } from '@angular/common/http';
  import { Observable } from 'rxjs';

  @Injectable({
  providedIn: 'root'
  })
  export class ApiService {
  private apiUrl = 'https://api.example.com/data';

  constructor(private http: HttpClient) {}

  getData(): Observable<any> {
  return this.http.get(this.apiUrl);
  }
  }

<!-- End Example -->

# Angular Pipes

- Pipes are a way to transform data in an Angular template

<!-- custom pipe example -->

import { Pipe, PipeTransform } from '@angular/core';

@Pipe({name: 'exponentialStrength'})
export class ExponentialStrengthPipe implements PipeTransform {
transform(value: number, exponent: string): number {
let exp = parseFloat(exponent);
return Math.pow(value, isNaN(exp) ? 1 : exp);
}
}

<!-- End custom pipe example -->

# What are Angular lifecycle hooks?

- ngOnInit(): Called once, after the first ngOnChanges().
- ngOnChanges(): Called whenever one or more data-bound input properties change.
- ngOnDestroy(): Called just before the component is destroyed.
- ngAfterViewInit(): Called after Angular initializes the component's views and child views.

# async pipe

- Angular subscribes to an Observable or Promise and returns the latest value it has emitted.
- When a new value is emitted, the async pipe marks the component to be checked for changes
- The async pipe automatically unsubscribes when the component is destroyed.

Example:
{{ data$ | async }}

# Change Detection

- detects changes in the state of an application and updates the view accordingly.
- It uses a tree of views, where each view is a node.
- This process is triggered by user interactions, XHR events, timer events, or other asynchronous events.

Example:
@Component({
selector: 'app-change-detection',
template: '<p>{{ counter }}</p>',
changeDetection: ChangeDetectionStrategy.OnPush
})

export class ChangeDetectionComponent {
counter = 0;

increment() {
this.counter++;
}
}

# Angular signals

- Angular signals are used to manage and communicate state changes within an application.

# What is an HTTP interceptor in Angular

- An HTTP interceptor in Angular is a service that intercepts HTTP requests or responses.
- Interceptors can be used for tasks such as adding authentication tokens, logging requests, handling errors, etc.

<!-- Example -->

import { Injectable } from '@angular/core';
import { HttpInterceptor, HttpRequest, HttpHandler, HttpEvent } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
const clonedReq = req.clone({
headers: req.headers.set('Authorization', 'Bearer YOUR_TOKEN_HERE')
});
return next.handle(clonedReq);
}
}

import { HTTP_INTERCEPTORS } from '@angular/common/http';

@NgModule({
providers: [
{ provide: HTTP_INTERCEPTORS, useClass: AuthInterceptor, multi: true }
]
})
export class AppModule {}

<!-- End Example -->

# tree shaking

- Tree shaking is a term commonly used in the context of JavaScript and Angular applications to describe the process of removing dead code.
- Angular uses tree shaking to include only the necessary parts of the code in the final bundle, eliminating unused code during the build process.

Example:

- Tree shaking works automatically with Angular CLI projects when building for production (ng build --prod). It removes unused modules and components from the final bundle.

# RxJS (Reactive Extensions for JavaScript)

RxJS (Reactive Extensions for JavaScript) is a library for reactive programming using Observables

- Handling Asynchronous Operations
- Declarative Data Handling
- Event Handling:
- State Management:
- WebSocket Communication:
- Caching and Retry Logic:
- Animation and UI Updates:
- Functional Reactive Programming (FRP):

- Overall, RxJS is valuable in modern web development for its ability to handle asynchronous operations, manage complex data flows, and provide a reactive approach to application architecture and state management.
