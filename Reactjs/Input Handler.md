# Input Handler

## Shorthand validation
```javascript
function App() {
    return <div>{name.length < 3 && 'name must be longer than 3'}</div>
}
```

## Do
```javascript
import { useState } from 'react';

function App() {
    const [value, setValue] = useState('');
    const handleInputChange = (event) => {
        // TODO: add validation
        setValue(event.target.value);
    }
    return <input value={value} onChange={handleInputChange} />
}
```

## Don't
```javascript
function App() {
    const value = document.querySelector('input').value;
    return <input value={value} />
}
```
