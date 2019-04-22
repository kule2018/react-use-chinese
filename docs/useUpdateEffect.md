# `useUpdateEffect`

React effect hook that ignores the first invocation (e.g. on mount). The signature is exactly the same as the `useEffect` hook.

 忽略第一次调用的 react 副作用钩子（例如在 mount 上）。 标记与`useEffect`钩子完全相同。

## Usage

```jsx
import React from 'react'
import {useUpdateEffect} from 'react-use';

const Demo = () => {
  const [count, setCount] = React.useState(0);
  
  React.useEffect(() => {
    const interval = setInterval(() => {
      setCount(count => count + 1)
    }, 1000)
    
    return () => {
      clearInterval(interval)
    }
  }, [])
  
  useUpdateEffect(() => {
    console.log('count', count) // will only show 1 and beyond
    
    return () => { // *OPTIONAL*
      // do something on unmount
    }
  }) // you can include deps array if necessary

  return <div>Count: {count}</div>
};
```