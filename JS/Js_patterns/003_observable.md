```typescript
class Observable {
  constructor() {
    this.observers = []; // empty array
  }

  subscribe(func) {
    this.observers.push(func); // add new function to observe
  }

  unsubscribe(func) {
    this.observers = this.observers.filter((observer) => observer !== func);
  }

  notify(data) {
    this.observers.forEach((observer) => observer(data));
  }
}
```