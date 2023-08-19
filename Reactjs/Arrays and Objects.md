# Array
## Key Props
- JSX array need unique key for referencing items
- Add `key={i}`

## Create
### Arrays
```javascript
const colors = ['red', 'green', 'blue'];

colors.slice(0, 1); // ['red']
colors.slice(0, 2); // ['red', 'green']
colors.slice(0, 0); // []
colors.slice(1);    // ['green', 'blue']
colors.slice(2);    // ['blue']
colors.slice(-1);   // ['blue']
colors.slice(-2);   // ['green', 'blue']

const newColor = 'pink';
const index = 1;
const newColors = [
    ...colors.slice(0, index),
    newColor,
    ...colors.slice(index),
] // ['red', 'pink', 'green', 'blue']
```

## Update
### Object Props
```javascript
const fruit = {
    color: 'red',
    name: 'apple',
};

const newFruit = {
    ...fruit,       // {color:'red', name:'apple'}
    color: 'green', // found duplicate key, uses this
};                  // {color:'green', name:'apple'}
```

### Array of Objects
```javascript
const fruits = [
    {
        color: 'red',
        name: 'apple',
    },
];
const newName = 'strawberry';
const newFruits = fruits.map(fruit => {
    if (fruit.name === 'apple') {
        fruit.name = newName;
    }
    return fruit;
}) // {color:'red', name:'strawberry'}
```

## Delete
### Arrays
```javascript
// FKT - Filter Keeps True
// filter with a particular value
const colors = ['red', 'green', 'blue'];

colors.filter(v => v === 'red'); // ['green', 'blue']
```

### Objects
```javascript
const fruit = {
    color: 'red',
    name: 'apple',
};

const {name, ...fruitOnlyColor} = fruit;
console.log(fruitOnlyColor); // {color: 'red'}
console.log(name);           // 'apple'
```

# Reference
- https://react.dev/learn/rendering-lists#keeping-list-items-in-order-with-key
