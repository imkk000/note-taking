# Stale Variable References
- Happens when `useEffect` read the old memory variable after re-render a component

```javascript
const [counter, setCounter] = useState(0);

// Issue
useEffect(() => {
    // counter read the old variable and print to log
    // because of running first time only
    document.body.click = () => {
        console.log(counter);
    }
}, []);

// Fixed
useEffect(() => {
    // after counter changed, it will run this effect
    document.body.click = () => {
        console.log(counter);
    }
}, [counter]);
```
