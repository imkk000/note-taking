# Component

- Filename start with Capitalization

## Data Flow

### Send result to parent component

- Pass the handle function through props
- Call inside child component

## Build a custom component

```jvascript
function Button({...events}) {
    // <button onClick={handleClick}></button>
    return <button {...events}></button>;
}

<Button onClick={handleClick} />
```
