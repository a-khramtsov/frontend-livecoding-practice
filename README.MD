# Задачи для практики с собеседованиям на frontend-разработчика

## React

### Задача
[Видеобъяснение](https://t.me/c/2062644132/983/1081)
```js
// В App есть инпут, счетчик и дочерний компонент, 
// который выполняет лишние ререндеры, при обновлении счетчика и изменении инпута
// как избежать лишних ререндеров дочернего

import React,{ useState } from 'react';

export default function App() {
    const [input, setInput] = useState('');
    const [count, setCount] = useState(0);

    const increment = () => setCount(count + 1);

    return (
        <div>
            <input value={input} onChange={(e) => setInput (e.target.value)} /> 
            <p>Input text: {input}</p>
            
            <button onClick={increment}>Increment</button>
            <p>Count: {count}</p>

            <ChildComponent count={count} />
        </div>
    );
}

const ChildComponent = ({ count, increment }: any) => {
  console.log(":: render");
  return (
    <>
      <div>Child component {count}</div>
    </>
  );
};
```


<details>
  <summary>Решение</summary>

 
  ```js
const ChildComponent = memo(({ count }: any) => {
console.log(":: render");
return (
    <>
      <div>Child component {count}</div>
    </>
  );
});
  ```
</details>
