```javascript
// Option 1
function App(props) {
  const name = props.name;
  return name;
}

// Option 2
function App(props) {
  const {name} = props;
  return name;
}

// Option 3
function App({name}) {
  return name;
}

// With Alias
function App({name: newName}) {
  return newName;
}

// With default value
function App({name = 'this is my name'}) {
  // return 'this is my name' if it is undefined
  return name;
}

// With nested object
function App({name: {firstName, lastName}}) {
  return firstName + " " + lastName;
}
```

# Reference
- https://dmitripavlutin.com/javascript-object-destructuring/
