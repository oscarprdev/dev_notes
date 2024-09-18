```typescript
1. Create context
const FlyOutContext = React.createContext();

2. Create a parent component
function FlyOut(props) {
  const [open, toggle] = React.useState(false);

  return (
    <FlyOutContext.Provider value={{ open, toggle }}>
      {props.children}
    </FlyOutContext.Provider>
  );
}

3. Create children component using the context
function Toggle() {
  const { open, toggle } = React.useContext(FlyOutContext);

  return (
    <div onClick={() => toggle(!open)}>
      <Icon />
    </div>
  );
}

4. Asign children to parent component
FlyOut.Toggle = Toggle;
```