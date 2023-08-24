# UseCallback
- `useCallback` is a React Hook that lets you cache a function definition between re-renders
- https://react.dev/reference/react/useCallback

```javascript
const FetchData = () => { };
// if it is empty array, it would be same reference variable from the first component rendering
const stableFetchData = useCallback(
    FetchData,
    [],
);
```
