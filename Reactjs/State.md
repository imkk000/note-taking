# Purpose
- store and modify data into a component
# Example
```javascript
const [name, setName] = useState(initial_state);

setCount(next_state);
```

# Arrays and Objects
```javascript
const [numbers, setNumbers] = useState([]);

// React will be rendered when memory address changes
// Using Variadic for extracting previous array
// then push new values back
setNumbers([...numbers, 1]);
```

## Do not directly mutate/change/modify arrays and objects
- *Push* modifies an array
```javascript
const [colors, setColors] = useState(['red', 'green']);

colors.push('blue');
```

- Modifying an element
```javascript
const [colors, setColors] = useState(['red', 'green']);

colors[0] = 'blue';
```

- Modifying a property
```javascript
const [fruit, setFruit] = useState({
    color: 'red',
    name: 'watermelon',
});

fruit.color = 'green';
```

# Reference
- https://react.dev/reference/react/useState
- [Update State Cheatsheet](https://state-updates.vercel.app/)
