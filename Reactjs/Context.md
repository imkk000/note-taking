# Context
- An alternative  to Props is **Context**
- Is not replacement for **Props and Redux**
- Store file in directory `src/context`
- Using Context
    - Create the context
    - Specify the data that will be shared
    - **Consume** the data in a component
- Properties
    - Provider: Component used to specify what data we want to share
    - Consumer: Component used to get access to data (Not often used)

```javascript
const Provider = 5;
export {Provider};
import { Provider } from './Provider';

// new context
import { createContext } from 'react';
const ComponentContext = createContext();

// apply context to component
return (
    <ComponentContext.Provider value={10}>
        <ChildComponent />
    </ComponentContext.Provider>
);

// read context value in child component
import { useContext } from 'react';
import ComponentContext from './ComponentContext';

const value = useContext(ComponentContext);
return <p>{value}</p>
```
