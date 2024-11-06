# Задачи для практики с собеседованиям на frontend-разработчика - Замыкание

✅ - значит, что на задачу есть решение в коде  
📹 - значит, что на задачу есть видеообъяснение

## Замыкание

### 📹 Задача
[Видеообъяснение](https://youtu.be/VMY3ZuLGoEs)

Что будет выведено в консоль?

```ts
let number = 0

const increment = () => {
  number += 1
  const message = `Incremented to ${number}`

  return () => {
    console.log(message)
    console.log(`Number: ${number}`)
  }
}

const log = increment()
increment()
increment()
log()
```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


 ### 📹 Задача
[Видеообъяснение похожей задачи](https://youtu.be/VMY3ZuLGoEs)

Что будет выведено в консоль?

```ts
function createIncrement(){
    let count = 0;
    function increment(){
        count++
    }
    let message = `Count is ${count}`
    function log(){
        console.log(message)
    }
    return [increment, log];
}

const [increment, log] = createIncrement();
increment();
increment();
increment();
log(); // что выведет и какая у нас проблема

```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


## 📹 Задача

 Что выведется в консоль и как это исправить?

```ts
const button = document.getElementById("button");
for (var i = 0; i < 3; i++) {
     button.addEventListener("click", function (e) {
         console.log(i);
     });
button.click();

```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


 ## 📹 Задача

 Что выведется в консоль?

```ts
for (var i = 0; i < 10; i++) {
  setTimeout(function() {
      console.log(i);
  })
}
```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
 
