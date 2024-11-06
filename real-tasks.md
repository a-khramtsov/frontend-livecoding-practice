# Задачи для практики с собеседованиям на frontend-разработчика - задачи, приближенные к реальной жизни

✅ - значит, что на задачу есть решение в коде  
📹 - значит, что на задачу есть видеообъяснение

## Задачи из реальной жизни

### ✅ 📹 Задача
[Видеобъяснение](https://t.me/c/2062644132/983/1404)

Нужно написать чистый читаемый код
Рассчитать оплату за проживание в отеле с учетом рабочих и праздничных дней
 
Функция может принимать 2 аргумента  
1. Количество ночей проживания в отеле (обязательный параметр)  
2. Дата заселения (необязательный параметр). Если значение не указано, то отсчет ведется от текущего дня  
- Стоимость проживания в будние дни (с понедельника по пятницу) стоит 1500 руб  
- Стоимость проживания в выходные дни (суббота, воскресенье) стоит 2200 руб  

```ts
const prices = {
  weekday: 1500,
  holiday: 2200,
};

function bookingCalculate() {
  
}

console.log(bookingCalculate(7)); // 11900
console.log(bookingCalculate(3, new Date('2023-11-10'))); // 5900
```

<details>
  <summary>Решение</summary>

```ts
const prices = {
  weekday: 1500,
  holiday: 2200,
};

const addDays = (date, days) => {
  const result = new Date(date);
  result.setDate(result.getDate() + days);
  return result;
};

const checkIsHoliday = day => {
  return !checkIsWeekdaty(day);
};

const checkIsWeekdaty = date => {
  const day = new Date(date).getDay();
  return day > 0 && day < 6;
};

function bookingCalculate(nights, startDate = new Date()) {
  const endDate = addDays(startDate, nights);

  let tempStartDate = startDate;
  let weekDays = 0;
  let hoilDays = 0;

  while (tempStartDate < endDate) {
    if (checkIsWeekdaty(tempStartDate)) {
      weekDays += 1;
    }
    if (checkIsHoliday(tempStartDate)) {
      hoilDays += 1;
    }
    tempStartDate = addDays(tempStartDate, 1);
  }
  return weekDays * prices.weekday + hoilDays * prices.holiday;
}

console.log(bookingCalculate(7)); // 11900
console.log(bookingCalculate(3, new Date('2023-11-10'))); // 5900

```
</details>


 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

 
### ✅ 📹 Задача
[Видеобъяснение](https://t.me/c/2062644132/983/1202)

1. Вернуть объект с ключами type из масива, значение - массив элементов с таким type  
2. Вернуть объект с ключами type, а значение - объект вида {count: количество, weight: суммарный вес}  

```ts
const arr = [
  { type: "banana", weight: 32 },
  { type: "apple", weight: 24 },
  { type: "kiwi", weight: 55 },
  { type: "banana", weight: 44 },
  { type: "orange", weight: 5 },
];

const groupByType = (arr) => {
  
};

console.log(groupByType(arr))
```

<details>
  <summary>Решение</summary>

1. Вернуть объект с ключами type из масива, значение - массив элементов с таким type  

```ts
const groupByType = (arr) => {
  const result = {};

  arr.forEach((item) => {
    const { type, ...rest } = item;

    if (result[type]) {
      result[type].push(rest);
    } else {
      result[type] = [rest];
    }
  });

  return result;
};

```

2. Вернуть объект с ключами type, а значение - объект вида {count: количество, weight: суммарный вес}  

```ts
const groupByType = (arr) => {
  const result = {};

  arr.forEach((item) => {
    const { type, weight } = item;

    if (result[type]) {
      result[type].count++;
      result[type].weight += weight;
    } else {
      result[type] = { count: 1, weight };
    }
  });

  return result;
};
```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


 
### ✅ 📹 Задача
[Видеобъяснение](https://t.me/c/2062644132/983/1574)

Имеется исходный массив плоских данных
  - Необходимо преобразовать его в структуру, где данные будут сгруппированы по одному из полей (кроме id)
  - Внутри сформированной группы должен лежать объект, ключами в которого должно стать поле (к примеру id)
  - Значением должен быть объект из исходного массива с соответствующем полем id, не включая само поле id
```ts
  const data = [
    { id: 1, age: 20, name: 'Иван', country: 'Russia' },
    { id: 2, age: 20, name: 'Дмитрий', country: 'USA' },
    { id: 3, age: 20, name: 'Алексей', country: 'Russia' },
    { id: 4, age: 20, name: 'Александр', country: 'USA' },
    { id: 5, age: 20, name: 'Иван', country: 'Russia' },
  ];

const groupBy = () => {

}

console.log(groupBy(data, 'country', 'id'));

  
// Должно получиться
  const result = {
    Russia: {
      1: { age: 20, name: 'Иван', country: 'Russia' },
      3: { age: 20, name: 'Алексей', country: 'Russia' },
      5: { age: 20, name: 'Иван', country: 'Russia' },
    },
    USA: {
      2: {age: 20, name: 'Дмитрий', country: 'USA' },
      4: { age: 20, name: 'Александр', country: 'USA' },
    }
  }
```

<details>
  <summary>Решение</summary>

```ts
  
const groupBy = (data, key, innerKey) => {
  return data.reduce((acc, current) => {
    const fieldByKey = current[key];
    console.log(current);

    if (!acc[fieldByKey]) {
      acc[fieldByKey] = {};
    }

    const innerKeyValue = current[innerKey];

    const rest = omit(current, 'id', 'age');

    acc[fieldByKey][innerKeyValue] = rest;

    return acc;
  }, {});
};

const omit = (obj, ...keys) => {
  const objectOfKeys = keys.reduce((acc, current) => {
    acc[current] = true;
    return acc;
  }, {});

  return Object.keys(obj).reduce((acc, key) => {
    if (objectOfKeys[key]) {
      acc[key] = obj[key];
    }

    return acc;
  }, {});
};

console.log(groupBy(data, 'country', 'id'));

```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


 
### ✅ 📹 Задача
[Видеобъяснение](https://t.me/c/2062644132/983/1404)

Написать класс EventEmmiter, аналог addeventlistener. 
- Метод метод on, который вызывается в именем события и функцией
- Метод off, который вызывается также с названием события и функцией
- Метод emit, который триггерит все функции

```ts

class EventEmitter {
  
}

// Пример использования
const myEventEmitter = new EventEmitter();

const greetListener = (name: string) => {
  console.log(`Hello, ${name}!`);
};

myEventEmitter.on('greet', greetListener);
myEventEmitter.emit('greet', 'Alice'); // Output: Hello, Alice!

myEventEmitter.off('greet', greetListener);
myEventEmitter.emit('greet', 'Bob'); // No output
```

<details>
  <summary>Решение</summary>

- Создаем поле класса, где будем хранить функции по каждому названию собития - это будет объект, типа `Record<string, Function[]>`
- В on, если по такому типа нет событий создается пустой массив и пушим в него функцию
- В off делаем фильтр и удаляем найденную функцию
- В emit проходим через forEach по функциям и вызываем их

```ts
class EventEmitter {
  private events: Record<string, Function[]> = {};

  on(eventName: string, listener: Function) {
      if (!this.events[eventName]) {
          this.events[eventName] = [];
      }
      this.events[eventName].push(listener);
  }

  off(eventName: string, listener: Function) {
      if (this.events[eventName]) {
          this.events[eventName] = this.events[eventName].filter((eventListener) => eventListener !== listener);
      }
  }

  emit(eventName: string, ...args: any[]) {
      if (this.events[eventName]) {
          this.events[eventName].forEach((listener) => {
              listener(...args);
          });
      }
  }
}

// Пример использования
const myEventEmitter = new EventEmitter();

const greetListener = (name: string) => {
  console.log(`Hello, ${name}!`);
};

myEventEmitter.on('greet', greetListener);
myEventEmitter.emit('greet', 'Alice'); // Output: Hello, Alice!

myEventEmitter.off('greet', greetListener);
myEventEmitter.emit('greet', 'Bob'); // No output
```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


 
### ✅ 📹 Задача
[Видеобъяснение](https://t.me/c/2062644132/983/2791)

Задача: Создайте игру "Память", в которой пользователи должны находить пары совпадающих карточек.

Правила:
1. Пользователям представляют 10 пар совпадающих карточек (всего 20 карточек) в случайном порядке.
2. Карточки отображаются в течение 3 секунд, затем все они переворачиваются, скрывая значения.
3. Пользователи могут переворачивать по 2 карточки за раз:
   - Если карточки совпадают, они должны показывать совпадение и остаться перевёрнутыми.
   - Если карточки не совпадают, они должны быть перевернуты обратно.
4. Пользователь продолжает этот процесс, пока все пары карточек не будут отгаданы.

Задачи для выполнения:
1. Отобразите на экране 10 пар совпадающих карточек в случайном порядке.
2. Реализуйте "переворачивание" карточек.
3. Отобразите карточки (лицом вверх) в течение 3 секунд в начале и затем переверните их все лицом вниз.
4. Разрешите переворачивать не более двух карточек за раз и:
   - если они совпадают, показывайте совпадение и оставляйте их перевёрнутыми.
   - если они не совпадают, переверните их обратно.
5. Кнопка перезапуска должна перезапустить игру.

[Архив](resourses/memory-game/Task.zip)

<details>
  <summary>Решение</summary>

  [Итоговый архив](resourses/memory-game/Result.zip)
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
 
### Задача

Такую задачу невозможно решить самому. Тут используется [Польская нотация](https://ru.wikipedia.org/wiki/%D0%9E%D0%B1%D1%80%D0%B0%D1%82%D0%BD%D0%B0%D1%8F_%D0%BF%D0%BE%D0%BB%D1%8C%D1%81%D0%BA%D0%B0%D1%8F_%D0%B7%D0%B0%D0%BF%D0%B8%D1%81%D1%8C). ГПТ генерирует решение на 100+ строк.    
Только на одном собеседовании давали такую задачу, ее можно посмотреть для общего развития, но серьезно готовиться к ней не стоит

```ts
// Your job is to create a calculator which evaluates expressions in Reverse Polish notation.
// For example expression 5 1 2 + 4 * + 3 - (which is equivalent to 5 + ((1 + 2) * 4) - 3 in normal notation) should evaluate to 14.
// For your convenience, the input is formatted such that a space is provided between every token.
// Empty expression should evaluate to 0.
// Valid operations are +, -, *, /.
// You may assume that there won't be exceptional situations (like stack underflow or division by zero).

const calcPN = (str) => {
  // TODO: Your awesome code here
};

calcPN("2 3 *"); // 6
calcPN("5 1 2 + 4 * + 3 -"); // 14
// STEPS:
// 5 1 2 + 4 * + 3 - || 1 + 2 => 3
// 5 3 4 * + 3 - || 3 * 4 => 12
// 5 12 + 3 - || 5 + 12 => 17
// 17 3 - || 17 - 3 => 14
// 14
```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
 
