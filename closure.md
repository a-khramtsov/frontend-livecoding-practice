# Задачи для практики к собеседованиям на frontend-разработчика - Замыкание

✅ - значит, что на задачу есть решение в коде  
📹 - значит, что на задачу есть видеообъяснение

## Замыкание

### [ОБЯЗАТЕЛЬНО К ОЗНАКОМЛЕНИЮ](https://learn.javascript.ru/closure)

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


### 📹 Задача

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


### ✅ 📹 Задача 

[Видеообъяснение](https://www.youtube.com/watch?v=9_QYthJvZrw)

 Что выведется в консоль?

```ts
for (var i = 0; i < 10; i++) {
  setTimeout(function() {
      console.log(i);
  })
}
```

<details>
    <summary>Решение</summary>

У var блочная область видимости, поэтому каждой итерации цикла `for` каждый раз переобъявляется переменная `i`
Также, нужно помнить про синхронных операции и макротаски в eventloop. 

Поэтому начала выполняются все синхронные операции (i++), а потом выполнися 10 раз setTimtout с последним значением `i`.

</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


### ✅ Задача

Задача "Калькулятор"  
Реализовать функции `one`, `plus`, `two`, чтобы результат ниже вывел 3

```ts
console.log(one(plus(two()))); // 3
console.log(two(plus(one()))); // 3
```

<details>
<summary>Решение</summary>

```ts
function one(func) {
    return func ? func(1) : 1;
}

function plus(x) {
    return function(y){ 
        return x + y;
    } 
}

function two(func) {
    return func ? func(2) : 2;
}

```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->



### Задача

```ts
const person = {
    name: 'Vasya'
};

(function() {
    person = {
        name: 'Petya'
    }
})(person);

console.log(person.name);

```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### ✅ 📹 Задача

[Видеообъяснение](https://www.youtube.com/watch?v=9_QYthJvZrw)

```ts


try {
    let x = 4;
    if (true) {
        console.log('x: ', x);
        let x = 5;
    }
} catch (error) {
    console.log('x error: ', error)
}

try {
    const y = 4;
    if (true) {
        const y = 5;
        console.log('y1: ', y);
    }
    console.log('y2: ', y)
} catch (error) {
    console.log('y error: ', error)
}

```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### ✅ 📹 Задача

[Видеообъяснение](https://www.youtube.com/watch?v=9_QYthJvZrw)

Объяснить, почему будет ошибка

```ts
function go(n) {
  console.log(n);

  for (let n of n.a) {
    console.log(n);
  }
}

go({ a: [1, 2, 3] });
```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
