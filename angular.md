
# 🅰️ Angular

Angular components go through a lifecycle managed by Angular. You can tap into specific moments of that lifecycle using lifecycle hooks.

## 1. 📌 Lifecycle Hooks

`ngOnInit()`

- Called once after the first `ngOnChanges()`.
- Ideal for initialization logic (e.g. API calls, setting defaults).

`ngOnChanges(changes: SimpleChanges)`

- Called whenever an `@Input()` property changes.
- Receives a SimpleChanges object.

`ngDoCheck()`

- Called during every change detection run.
- Use for custom change detection (advanced use cases).

`ngAfterContentInit()`

- Called once after Angular projects external content into the component.

`ngAfterContentChecked()`

- Called after every check of projected content.

`ngAfterViewInit()`

- Called once after the component's view and child views have been initialized.

## 2. Components

Fundamental UI building blocks.

Each component has:

- A **TypeScript class**
- An **HTML template**
- A **CSS style**
- A **selector**

## 3. Structural Directives

Change the DOM layout.
Examples: `*ngIf`, `*ngFor`, `*ngSwitch`

#### Attribute Directives

Change the appearance or behavior of elements.

Example: `ngClass`, `ngStyle`, or `custom directives`.

## 3. Pipes

Transform data in templates.
Angular provides built-in pipes like `date`, `uppercase`, `async`.

You can also create custom pipes.

- **Pure**: efficient, only re-evaluates on input changes.
- **Impure**: always recalculates, watch for performance impact.

##  4. Forms

### Template-Driven
- Defined directly in the HTML using directives (`ngModel`, `#form="ngForm"`).
- **Two-way data binding** with `[(ngModel)]`.
- Suitable for **simple forms**.
- Logic is mostly in the **template**.
- Uses `FormsModule`.

### 📄 Example

```html
<form #form="ngForm" (ngSubmit)="onSubmit(form)">
  <input name="username" ngModel required />
  <button type="submit">Submit</button>
</form>
```

### Reactive Forms 

- Defined in the component class using FormControl, FormGroup, and FormBuilder.
- Uses explicit and immutable data structures.
- Ideal for complex, dynamic, or large-scale forms.
- Uses `ReactiveFormsModule`.

Defined in the component class using FormControl, FormGroup, and FormBuilder.

> Use **Template-driven** for simple forms like login, contact forms.

> Use **Reactive form** complex forms with dynamic validations, conditional fields, or large applications.



## 5. RxJS

- **Observables**: Lazy collections of multiple values over time.
- **Subjects**:
  - `Subject`: Multicast observable.
  - `BehaviorSubject`: Emits last value to new subscribers.
  - `ReplaySubject`: Replays past values.
  - `AsyncSubject`: Emits last value on complete.


### ❄️ Cold Observables
- Start when subscribed.
- Each subscriber gets a new execution.
- Example: `HttpClient.get()`, `of()`

### 🔥 Hot Observables
- Already producing values.
- All subscribers share the same execution.
- Example: `Subject`, `fromEvent()`

### 🧠 Quick Comparison

|              | Cold         | Hot           |
|--------------|--------------|---------------|
| Starts on sub| ✅ Yes       | ❌ No         |
| Shared data  | ❌ No        | ✅ Yes        |
| Examples     | `of()`, HTTP | `Subject`, DOM events |


### 🔧 Common Operators

- **Creation**: `of`, `from`, `interval`, `timer`.
- **Transformation**: `map`, `pluck`, `scan`.
- **Filtering**: `filter`, `debounceTime`, `distinctUntilChanged`.
- **Flattening**: `mergeMap`, `switchMap`, `concatMap`, `exhaustMap`.
- **Combining**: `combineLatest`, `withLatestFrom`, `forkJoin`, `zip`.
- **Error Handling**: `catchError`, `retry`, `retryWhen`, `throwError`.
- **Utility**: `tap`, `take`, `first`, `takeUntil`, `finalize`.

### 🔧 `mergeMap` vs `switchMap` vs `concatMap`

| Operator    | Cancels Previous? | Runs in Parallel? | Preserves Order? | Recommended Use Case                  |
|-------------|-------------------|-------------------|------------------|----------------------------------------|
| `mergeMap`  | ❌ No              | ✅ Yes            | ❌ No            | Parallel tasks, when order doesn't matter |
| `switchMap` | ✅ Yes             | ✅ Yes            | ❌ No            | Live search, cancel on new input         |
| `concatMap` | ❌ No              | ❌ No             | ✅ Yes           | Sequential tasks, order matters         |

## 🚀 Performance 

### 🧠 Change Detection Strategy

- **Default:** Checks all bindings of the component and its children.
- **OnPush:** Component updates only when:
  - An `@Input()` reference changes
  - `ChangeDetectorRef` is manually triggered
  - An internal event (like `EventEmitter`) fires


>- Use `OnPush` to improve performance in large applications.
>- Combine with `async` pipe or **Signals** to reduce re-rendering.

### 🔁 TrackBy in *ngFor

When using `*ngFor`, Angular re-renders the entire list if the array reference changes — even if only one item was updated.

### 🛠 Problem:
Without `trackBy`, Angular can't efficiently track which items changed, causing performance issues in large lists.

### ✅ Solution: Use `trackBy` to uniquely identify each item.

```ts
<div *ngFor="let item of items; trackBy: trackById">
  {{ item.name }}
</div>

trackById(index: number, item: any): number {
  return item.id;
}
```

## 🧠 6.Core Concepts

### ✅ JIT (Just-In-Time) vs AOT (Ahead-Of-Time)

| Feature              | JIT (Development)                     | AOT (Production)                         |
|----------------------|----------------------------------------|------------------------------------------|
| Compilation time     | In the browser (runtime)               | During the build                         |
| Load time            | Slower                                | Faster                                   |
| Bundle size          | Larger                                | Smaller                                  |
| Debug experience     | Easier for development                | Optimized for production                 |
| Security             | Risk of malicious templates            | Templates validated during build         |

**Conclusion:** AOT is preferred in production for performance, smaller bundles, and template safety.

---
### 📈 Best Practices

- **Unsubscribe** properly using `takeUntil`, `async` pipe, or `untilDestroyed`.
- Prefer **`async` pipe** in templates to avoid manual subscriptions.
- Use **`switchMap`** for HTTP calls to cancel previous requests.
- Leverage **RxJS Marble Testing** for observables.
- Create custom observable services for shared streams.


### 🔁 Common Angular Patterns

#### 🔹 Smart vs Dumb Components
- **Smart**: Handle data, logic, services, API calls.
- **Dumb**: Presentational only, use `@Input()` and `@Output()`.

#### 🔹 Facade Pattern
- Encapsulates complex logic (e.g., state, services) behind a clean API.
- Promotes separation of concerns in components.

#### 🔹 Singleton Services
- Angular services provided in `root` are singletons by default.
- Useful for shared state and logic.

#### 🔹 Dependency Injection (DI)
- Core pattern in Angular to manage service lifecycles and testing.

#### 🔹 ControlValueAccessor
- Bridge between Angular forms and custom components.


#### 🔹 Observer Pattern
- Core of RxJS: Observables + Subscribers.




## 🚀 Angular 14 → 17: Key Improvements Summary

###  Angular 14 (Jun 2022)
- **Standalone Components (Preview)**  
  → Components can be declared without `NgModule`.

- **Typed Reactive Forms**  
  → Form values now have proper TypeScript types.

- **Improved Template Diagnostics**  
  → Better error messages and autocompletion in templates.

- **Extended Developer CLI**  
  → Easier scaffolding and stricter defaults.

---

###  Angular 15 (Nov 2022)
- **Standalone APIs Officially Stable**  
  → Full support for `standalone: true` in components, pipes, and directives.

- **Directive Composition API (Experimental)**  
  → Reuse directive logic across components.

- **Simplified Lazy Loading**  
  → `loadComponent` for standalone components.

- **Improved Server-Side Rendering**  
  → Enhanced hydration and performance.

- **Optimized Builds**  
  → Smaller output bundles and improved tree-shaking.

---

###  Angular 16 (May 2023)
- **Signals (Developer Preview)**  
  → Fine-grained reactivity model (like Reactivity in SolidJS).

- **DestroyRef & `takeUntilDestroyed()`**  
  → Simplifies lifecycle-aware subscriptions.

- **Required Inputs**  
  → Mark `@Input()` as required at compile time.

- **Zone-less Change Detection (Experimental)**  
  → Use Angular without relying on Zone.js.

- **esbuild Support (experimental)**  
  → Faster builds with modern tooling.

---

###  Angular 17 (Nov 2023)
- **Signals (Stable)**  
  → Full support for Signals as a reactive state mechanism.

- **New Control Flow Syntax (Stable)**  
  → Template-level `@if`, `@for`, `@switch`, replacing `*ngIf` and `*ngFor`.



