## How to do cleanup in useeffect?

**The **useEffect** hook accepts a callback function and an optional dependency array. The callback can return a cleanup function that React executes:**


```javascript
import { useEffect } from 'react';

function MyComponent() {
  useEffect(() => {
    // Effect code (e.g., setting up a subscription, timer, or event listener)
    console.log('Effect ran');

    // Cleanup function
    return () => {
      console.log('Cleanup ran');
      // Clean up resources (e.g., clear timers, remove listeners, cancel subscriptions)
    };
  }, [/* dependency array */]);

  return <div>My Component</div>;
}
```
