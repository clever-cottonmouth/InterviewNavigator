## Passing data from child to parent
```javascript
// App.js
import React from 'react';
import './style.css';
import ParentComponent from './Parent.js';
export default function App() {
  return (
    <div>
      <ParentComponent />
    </div>
  );
}
  ```

```javascript
// Parent.js
import React, { useState } from 'react';
import ChildComponent from './Child';

function ParentComponent() {
  const [childData, setChildData] = useState('');

  // Callback function to receive data from child
  const handleChildData = (data) => {
    setChildData(data);
  };

  return (
    <div>
      <h1>Parent Component</h1>
      <p>Data from child: {childData}</p>
      <ChildComponent onData={handleChildData} />
    </div>
  );
}

export default ParentComponent;
```

```javascript
// Child.js
import React, { useState } from 'react';

function ChildComponent({ onData }) {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (e) => {
    setInputValue(e.target.value);
  };

  const sendDataToParent = () => {
    // Invoke the callback function passed from the parent
    onData(inputValue);
  };

  return (
    <div>
      <h2>Child Component</h2>
      <input type="text" value={inputValue} onChange={handleChange} />
      <button onClick={sendDataToParent}>Send Data to Parent</button>
    </div>
  );
}

export default ChildComponent;
```
