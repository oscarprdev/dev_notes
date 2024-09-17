
```typescript
function reducer(state, action) {
  switch (action.type) {
    case "LOAD":
      return load(state, action.payload);
    case "SELECT":
      return select(state, action.payload);
    case "UPDATE":
      return update(state, action.payload);
    case "REMOVE":
      return remove(state, action.payload);
    default:
      return state;
  }
}
```