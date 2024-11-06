# Задачи для практики с собеседованиям на frontend-разработчика - Рекурсия

✅ - значит, что на задачу есть решение в коде  
📹 - значит, что на задачу есть видеообъяснение

## Рекурсия

### ✅ 📹 Задача
[Видеобъяснение](https://t.me/c/2062644132/983/1202)

Преобразовать вложенный объект в flat-структуру

```ts
const tree = {
 a: {
    b: 'two',
    c: {
        d: 'one'
    }
 }
}

console.log(JSON.Parce(treeFn(tree)))
{
 'a.b': 'two',
 'a.c.d': 'one'
}
```


<details>
  <summary>Решение</summary>

```ts
const treeFn = (tree, parentKey = '') => {
  let result = {};

  for (let key in tree) {
    let newKey = parentKey ? `${parentKey}.${key}` : key;

    if (typeof tree[key] === 'object') {
      Object.assign(result, treeFn(tree[key], newKey));
    } else {
      result[newKey] = tree[key];
    }
  }

  return result;
};


```
</details>

  ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


### ✅ 📹 Задача
[Видеобъяснение](https://t.me/c/2062644132/983/1937)

Рекурсивно просуммировать все цифры

```ts
const obj = {
  a: 1,
  b: {
    c: 3,
    d: -10,
    e: {
      f: {
        g: 1,
      },
    },
  },
};
```

<details>
  <summary>Решение</summary>

Вариант с передачей аккамулятора

```ts
const sumRecursive = (node, sum = 0) => {
  for (let key in node) {
    console.log(key, node[key]);
    if (typeof node[key] === 'number') {
      sum += node[key];
    } else {
      sum = sumRecursive(node[key], sum);
    }
  }

  return sum;
};

```

Вариант без передачи параметра  

```ts
const sumRecursive = node => {
  if (typeof node === 'number') {
    return node;
  } else {
    let sum = 0;

    for (let key in node) {
      sum += sumRecursive(node[key]);
    }

    return sum;
  }
};
```

Вариант через this

```ts
function sumRecursive(value = 0) {
  console.log(this);
  for (let key in this) {
    if (typeof this[key] === 'number') {
      value += this[key];
    } else {
      value = sumRecursive.call(this[key], value);
    }
  }

  return value;
}
sum.call(obj);
```
</details>

  ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


### ✅ 📹 Задача
[Видеобъяснение](https://t.me/c/2062644132/983/1404)

Написать функцию, которая будет принимать объект с вложенными объектами type/value и возвращать объект понятной структуры без них. Понятней будет на примере:

```ts
// Входные параметры:
// Первый:
const inputTest = {
  key1: null,
  key2: [
    {
      type: "test1",
      value: {
        key3: "string",
        key4: 1
      }
    },
    {
      key5: "string",
      key6: 1
    }
  ],
  key7: {
    type: "test2",
    value: 100
  }
}


// должен стать таким объектом:
const resultTest = {
  key1: null,
  key2: [
    {
      key3: "string",
      key4: 1
    },
    {
      key5: "string",
      key6: 1
    },
  ],
  key7: 100
}

// Второй:
const inputObj2 = {
  type: "banner",
  value: {
    data: {
      type: "id",
      value: "14ac6615-5fb6-4232-881f-bb0a999c217d"
    }
  }
}

// должен стать таким объектом:
const resultObj2 = {
  data: "14ac6615-5fb6-4232-881f-bb0a999c217d"
}

/// Третий
const inputObj1 = {
  type: "layout",
  value: {
    config: {
      cols: 20
    },
    rows: [
      {
        type: "layout_row",
        value: {
          columns: [
            {
              config: {
                desktopWidth: 0,
                mobileWidth: 10
              },
              data: []
            },
            {
              config: {
                desktopWidth: null,
                mobileWidth: 20
              },
              data: null
            },
            {
              config: {
                desktopWidth: 10,
                mobileWidth: 10
              },
              data: "json string"
            }
          ]
        }
      },
      {
        type: "layout_row",
        value: {
          columns: [
            {
              config: {},
              data: {}
            },
          ]
        }
      },
    ]
  }
}

// должен стать таким объектом:
const resultObj1 = {
  config: {
    cols: 20
  },
  rows: [
    {
      columns: [
        {
          config: {
            desktopWidth: 0,
            mobileWidth: 10
          },
          data: []
        },
        {
          config: {
            desktopWidth: null,
            mobileWidth: 20
          },
          data: null
        },
        {
          config: {
            desktopWidth: 10,
            mobileWidth: 10
          },
          data: "json string"
        }
      ]
    },
    {
      columns: [
        {
          config: {},
          data: {}
        },
      ]
    }
  ]
}

```


<details>
  <summary>Решение</summary>

```ts
const convert = data => {
  return Object.keys(data).reduce((acc, current) => {
    const element = data[current];

    if (element === null) {
      acc[current] = element;
    } else if (typeof element === 'object' && element?.type && element?.value) {
      const { type, value } = element;

      acc[current] = value;
    } else if (typeof element === 'object') {
      acc[current] = convert(element);
    } else {
      acc[current] = element;
    }

    return acc;
  }, {});
};

console.log(convert(inputTest));
```
</details>


 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


### ✅ 📹 Задача
[Видеобъяснение](https://t.me/c/2062644132/983/1829)

Найти самый глубокий максимальный элемент

```ts
const array = 
[
	1, 
	[
		[
			20, 
			1, 
			[101]
		], 
	2
	], 
	[
		[-2], 
		[
			[102, 100]
		]
	]
];

const findDeepestMaxElement = (array) => {

}

console.log(findDeepestMaxElement(array) === 102) // true
```


<details>
  <summary>Решение</summary>

```ts
const array = [1, [[20, 1, [101]], 2], [[-2], [[102, 100]]]];

const deepthStorage = {};

const arrayRecursiveDeep = (_array, deepth = 0) => {
  for (let arr of _array) {
    if (typeof arr === 'object') {
      arrayRecursiveDeep(arr, deepth + 1);
    } else {
      if (!deepthStorage[deepth]) {
        deepthStorage[deepth] = [];
      }

      deepthStorage[deepth].push(arr);
    }
  }
};

arrayRecursiveDeep(array);

const keys = Object.keys(deepthStorage).map(Number);
const maxKey = Math.max(...keys);
const maxDeepValue = Math.max(...deepthStorage[maxKey]);

console.log(deepthStorage);
```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

 
### Задача
 <!-- [Видеобъяснение]() -->

Обойти объект с вложенностями и поменять все 1 на 0 и наоборот  
Возможные решения: 
1. цикл for of + рекурсия
2. конвертация в json
3. стек (самое оптимальное) 

```ts
const tree = {
   a: {
      b: {
         a: 1,
     },
   },
   b: 1,
};
```


<!--
<details>
  <summary>Решение</summary>

```ts

```
</details>
-->


  ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### Задача
<!-- [Видеобъяснение]() -->

Написать функцию глубокого копирования  
Исходный объект, который нужно скопировать. Значение "a" может быть массивом, объектом или примитивом, вложенность "а" может быть бесконечной

```ts
const a = [
  {
    name: '6x45',
    draw: {
      cost: 50,
      multiDraws: [1, 2, 3]
    },
    count: null
  },
  {
    name: '7x49',
    draw: {
      cost: 75,
      multiDraws: [{c: 13}, 5, 6]
    },
    count: 10
  }
];

const b = copy(a);
  
function copy() { //написать функцию copy
  
}

// ниже проверка, что объект "а" действительно был скопирован в новый объект 
if(b) b[1].draw.multiDraws[0].c = '369';
console.log(' ORIG: ', JSON.stringify(a), '\n\n', 'COPY: ', JSON.stringify(b));
```

<!--

<details>
  <summary>Решение</summary>

```ts

```
</details>

-->

  ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
