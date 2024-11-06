# Задачи для практики с собеседованиям на frontend-разработчика - Контекст

✅ - значит, что на задачу есть решение в коде  
📹 - значит, что на задачу есть видеообъяснение

## Контекст

### ✅ 📹 Задача
[Видеобъяснение](https://t.me/c/2062644132/983/1081)

Меняем прототип. Что будет выведено в консоль?

```ts
function Person(name) {
    this.name = name;
}

const juan = new Person("Juan");

Person.prototype = {
  getName: function () {
		return this.name;
	},
};

const pedro = new Person("Pedro");

console.log(pedro.getName());
console.log(juan.getName());
```

<details>
  <summary>Решение</summary>

Происходит полная перезапись прототипа класса, но контруктор this.name остается на месте.
Надо поминть, что class это синатксический сахар над функциями и эти записи идентичны 


```ts
function Person(name) {
    this.name = name;
}
// РАВНО
class Person {
	construstor(name) {
		this.name = name;
	}
}

console.log(pedro.getName()); // pedro создан с помощью класса Person, но у него в этот момент нет метода getName. Будет ош
console.log(juan.getName()); // будет вызван метод getName и выведено поле name

```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


 ### ✅ 📹 Задача
[Видеъяснение](https://t.me/c/2062644132/983/1081)

Что будет выведено и как это исправить?

```ts

let obj = {
    name: 'David',
    getName() {
        console.log(`name is: ${this.name}`);
    },
};

let fn = obj.getName;

fn();
```

<details>
  <summary>Решение</summary>


```ts
let obj = {
    name: 'David',
    getName() {
        console.log(`name is: ${this.name}`);
    },
};

let fn = obj.getName.bind(obj);

fn();
```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


 
 ### ✅ 📹 Задача
[Видеъяснение](https://t.me/c/2062644132/983/1081)

Что будет выведено в консоль?

```ts
let obj1 = {
    name: 'User 1',
    getName() {
        console.log(`name is: ${this.name}`);
    },
};

let obj2 = {
    name: 'User 2',
    getName() {
        console.log(`name is: ${this.name}`);
    },
};

let fn = obj.getName.bind(obj2).bind(obj1);

fn();
```

<details>
  <summary>Решение</summary>

  Функцию bind можно выполнить только 1 раз. Это нужно запомнить как факт. [Объяснение](https://dev.to/akashkava/functionbindbind-does-not-work-in-javascript-59am)
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


 
### Задача

 Что будет выведено в консоль?

```ts
const person = { name: "Vasya", age: 22 };
const position = { title: "Software Engineer" };

person.position = position;
person.postion.salary = 120;

console.log(person.position);
console.log(position);
```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


 
### Задача
Что будет выведено в консоль?

```ts
function foo() {
  const x = 10;
  return {
    x: 20,
    bar: function () {
      console.log(this.x);
    },
    baz: () => {
      console.log(this.x);
    },
  };
}

const obj = foo();
obj.bar(); // ? 
obj.baz(); // ? 

const obj2 = foo.call({ x: 30 });
let y = obj2.bar;
let x = obj2.baz;

y(); // ? 
x(); // ? 

obj2.bar(); // ? 
obj2.baz(); // ?
```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


 ### ✅ Задача

Что будет выведено в консоль?

В чем разница hasOwnProperty и in?  
Что будет выведено в консоль? 

```ts
class Animal {
  constructor(name) {
    this.name = name;
  }
  
  sound() {
    console.log("Some sound");
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name);
    this.breed = breed;
  }
  
  bark() {
    console.log("Woof woof!");
  }
}

let myDog = new Dog("Buddy", "Labrador");

console.log(myDog.hasOwnProperty('name')); // ?
console.log(myDog.hasOwnProperty('sound')); // ?

console.log('name' in myDog); // ?
console.log('sound' in myDog); // ?
```

<details>
  <summary>Решение</summary>

```ts
console.log(myDog.hasOwnProperty('name')); // true
console.log(myDog.hasOwnProperty('sound')); // false

console.log('name' in myDog); // true
console.log('sound' in myDog); // true
```
  
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

