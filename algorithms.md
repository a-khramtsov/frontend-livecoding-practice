# Задачи для практики к собеседованиям на frontend-разработчика - Алгоритмы

✅ - значит, что на задачу есть решение в коде  
📹 - значит, что на задачу есть видеообъяснение

## Алгоритмы

### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/U1q4WlXm_0E)

Отсортировать и что бы из двух массивов получился один со всеми данными - отсортированными

```ts
const a = [1, 3, 5];
const b = [2, 4, 6, 7];

const sortArrays = (a, b) => {}

console.log(sortArrays(a, b));
```


<details>
  <summary>Решение</summary>
  
```ts
const a = [1, 3, 5];
const b = [2, 4, 6, 7];

const sortArrays = (a, b) => {
  let aIndex = 0;
  let bIndex = 0;
  const result = [];

  while (aIndex < a.length && bIndex < b.length) {
    if (a[aIndex] < b[bIndex]) {
      result.push(a[aIndex]);
      aIndex++;
    } else {
      result.push(b[bIndex]);
      bIndex++;
    }
  }

  while (aIndex < a.length) {
    result.push(a[aIndex]);
    aIndex++;
  }

  while (bIndex < b.length) {
    result.push(b[bIndex]);
    bIndex++;
  }

  return result;
};

console.log(sortArrays(a, b));


```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/ic3xbHpH4ho)

Найти единственное уникальное значение в массиве

```ts
const findUnique = (array) => {}

console.log(findUnique([2,2,1,1,3,3,5]));
console.log(findUnique([5,5,5,5,1]));
console.log(findUnique([2,2,2,2]));
```


<details>
  <summary>Решение</summary>

```ts
// Объяснение в видео
// 0..9 - Десятичная система счисления
// 0..1 - Двоичная система счисления


// Любое число в десятичной системе можно представить в двоичном виде
// 0 = 00000000
// 1024 = 1111111111 = 2 в 10 степени
// 2 -> 4 -> 8 -> 16 -> 32 -> 64 -> 128 -> 256 -> 512 -> 1024 - степени 2
// 1000000 -> 256  -> 1 + 2 + 4 + 8 + 16 + 32 + 64 + 128 = 255

// Логическое ИЛИ -> 1 || 0 -> true || false -> true
// Логическое И -> 1 && 0 -> true && false -> false

// XOR - получаем 1, если получаем разные значения
// 1 ^ 1 -> 0
// 0 ^ 0 -> 0
// 0 ^ 1 -> 1
// 1 ^ 0 -> 0


const sum = array => {
  let result = 0;

  for (let i = 0; i < array.length; i++) {
    result ^= array[i];
  }

  return result;
};

console.log(sum([2, 2, 1]));

```
</details>


 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/PRvxs8rxC30)

Найти индексы элементов, которые в сумме дают target

```ts
function twoSum(nums, target) {
 
}

console.log(twoSum([2, 7, 11, 5, 9, 10, 15], 26)); // Output: [0, 1]
console.log(twoSum([2,7,11,15], 9)); // Output: [0, 1]
console.log(twoSum([3,2,4], 6)); // Output: [1, 2]
console.log(twoSum([3,3], 6)); // Output: [0, 1]
```

<details>
  <summary>Решение</summary>

```ts
function twoSum(nums, target) {
  const object = {};

  for (let i = 0; i < nums.length; i++) {
    const value = target - nums[i];

    if (object.hasOwnProperty(value)) {
      return [object[value], i];
    }

    object[nums[i]] = i;
  }
}
```

</details>


 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### 📹 Задача
[Видеообъяснение](https://youtu.be/VMY3ZuLGoEs)

```ts
// Реализовать функцию проверку на анаграммы
function isAnagram(first, second) {
}

isAnagram('finder', 'friend'); // true
isAnagram('test', 'sets'); // false
isAnagram('abc', 'aaa'); // false
isAnagram('abb', 'aab'); // false


```

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/pZYADXAm_fg)

Объединить анаграммы в группы 

```ts
function groupAnagrams(strs) {
  
}

console.log(groupAnagrams(['eat', 'tea', 'tan', 'ate', 'nat', 'bat'])); // [["bat"],["nat","tan"],["ate","eat","tea"]]
console.log(groupAnagrams([''])); // [[""]]
console.log(groupAnagrams(['a'])); // [["a"]]

```

<details>
  <summary>Решение</summary>

```ts
function groupAnagrams(strs) {
  const object = {};

  for (let str of strs) {
    const sorted = str
      .split('')
      .sort()
      .join('');

    if (!object[sorted]) {
      console.log(object);
      object[sorted] = [];
    }

    object[sorted].push(str);
  }

  return Object.values(object);
}

// [["bat"],["nat","tan"],["ate","eat","tea"]]
console.log(groupAnagrams(['eat', 'tea', 'tan', 'ate', 'nat', 'bat']));
console.log(groupAnagrams([''])); // [[""]]
console.log(groupAnagrams(['a'])); // [["a"]]


```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/ic3xbHpH4ho)

Написать функцию которая вернет те значения из первого массива, которых нету во втором массиве

```ts
const longArr1: number[] = [1,4,3,2];
const longArr2: number[] = [1,2];

func(longArr1: number[], longArr2: number[]): number[] // вернуть [4,3]
```

<details>
  <summary>Решение</summary>

```ts
const longArr1 = [1, 4, 3, 2, 1, 1];
const longArr2 = [1, 2];

const func = (a, b) => {
  const aObject = a.reduce((acc, current) => {
    if (acc[current]) {
      acc[current]++;
    } else {
      acc[current] = 1;
    }

    return acc;
  }, {});
  
  const result = b.reduce((acc, current) => {
    if (acc[current]) {
      acc[current]--;
    }
    
    return acc;
    
  }, aObject);
  
  
  return Object.keys(result).reduce((acc, current) => {
    const value = current;
    const repeats = result[current];
  
    
    for (let i = 0; i < repeats; i++) {
        acc.push(Number(value))
      }
    
    return acc;
  }, [])
};


console.log(func(longArr1, longArr2))
```
</details>


 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


### ✅ 📹 Задача
[Видеообъяснение]()

Условие:   
Даны два отсортированных по возрастанию массива целых чисел arr1 и arr2. Напишите функцию, которая возвращает массив элементов, присутствующих только в одном из массивов (симметрическую разность).

Требования:  
- Входные массивы уже отсортированы по возрастанию
- Результат должен быть отсортирован по возрастанию
- Дубликаты в пределах одного массива должны быть сохранены
- Не использовать дополнительные структуры данных (Set, Map и т.д.)


```ts

/*
Пример 1:
- Вход: nums1 = [1, 2, 3], nums2 = [2, 4, 6, 7, 8]
- Выход: [1, 3, 4, 6]

Пример 2:
- Вход: nums1 = [4, 5, 6], nums2 = [6, 7, 8]
- Выход: [4, 5, 7, 8]
* */

function getSymmetricDifference(arr1, arr2) {

}


console.log(getSymmetricDifference([1, 2, 3], [2, 4, 6, 7, 8]));  // [1, 3, 4, 6]

```

<details>
    <summary>Решение</summary>

```ts

function getSymmetricDifference(arr1, arr2) {
    const result = [];
    let i = 0;
    let j = 0;

    while (i < arr1.length && j < arr2.length) {
        if (arr1[i] === arr2[j]) {
            i++;
            j++;
        } else if (arr1[i] < arr2[j]) {
            result.push(arr1[i]);
            i++;
        } else {
            result.push(arr2[j]);
            j++;
        }
    }

    while (i < arr1.length) {
        result.push(arr1[i]);
        i++;
    }

    while (j < arr2.length) {
        result.push(arr2[j]);
        j++;
    }

    return result;
}
```

</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/ic3xbHpH4ho)

Проверить, что все скобкки в строке валидны

```ts
const checkBrackets = (str) => {}

console.log(checkBrackets('[[((]]))'));
console.log(checkBrackets('[)'));
console.log(checkBrackets('))[[(<>)()]]'));
console.log(checkBrackets('[[<<>>]](((([[]]))))'));
console.log(checkBrackets('([])'));

```

<details>
  <summary>Решение</summary>

```ts
const brackets = {
    '[': ']',
    '<': '>',
    '{': '}',
    '(': ')'
};

const checkBrackets = str => {
    const stack = [];

    const array = Array.from(str);

    const bracketKeys = Object.keys(brackets);
    const bracketValues = Object.values(brackets);
    console.log(array)

    for (let bracket of array) {
        if (bracketKeys.includes(bracket)) {
            stack.push(bracket);
        } else if (bracketValues.includes(bracket) && brackets[stack[stack.length - 1]] === bracket) {
            stack.pop()
        } else {
            return false
        }
    }


    return stack.length === 0;
}

console.log(checkBrackets('[[((]]))'));
console.log(checkBrackets('[)'));
console.log(checkBrackets('))[[(<>)()]]'));
console.log(checkBrackets('[[<<>>]](((([[]]))))'));
console.log(checkBrackets('([])'));

```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/PRvxs8rxC30)

Дан неотсортированный массив уникальных чисел и число.
Необходимо вернуть массив из кортежей пар чисел массива, если их сумма равна исходному числу и вернуть пустой массив, если таких пар нет.


```ts
function getRanges(arr) {
 
}

console.log(getRanges([1, 2, 5, 10, 9, 11, 6, 8, 0, 13, 16])); // 0-2,5-6,8-11,13
```


<details>
  <summary>Решение</summary>

```ts
function getRanges(arr) {
  arr.sort((a, b) => a - b);

  const ranges = [];

  for (let i = 0; i < arr.length; i++) {
    const value = arr[i];
    const previousPossibleValue = arr[i] - 1;

    if (arr.indexOf(previousPossibleValue) === -1) {
      let end = value;

      while (arr.indexOf(end + 1) !== -1) {
        end++;
      }

      if (value === end) {
        ranges.push(value);
      } else {
        ranges.push(`${value}-${end}`);
      }
    }
  }

  return ranges.join(',');
}

console.log(getRanges([1, 2, 5, 10, 9, 11, 6, 8, 0, 13, 16]));
// 0-2,5-6,8-11,13

// За один проход цикла
function getRanges(arr) {
  arr.sort((a, b) => a - b); // Sort the array in ascending order

  let ranges = [];
  let start = arr[0]; // 8
  let end = arr[0];   // 8

  for (let i = 1; i < arr.length; i++) {
    if (arr[i] === end + 1) {
      end = arr[i];
    } else {
      ranges.push(start === end ? `${start}` : `${start}-${end}`);
      start = arr[i];
      end = arr[i];
    }
  }

  ranges.push(start === end ? `${start}` : `${start}-${end}`);

  return ranges.join(',');
}
```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/j1c5dqdZkoU)

Написать функцию для проверки идентичности деревьев

```ts
function isSameTree(p, q) {
  if (p === null && q === null) {
    return true;
  }

  if (p === null || q === null) {
    return false;
  }

  if (p.val !== q.val) {
    return false;
  }

  return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
}

const tree1 = {
  val: 1,
  left: {
    val: 2,
    left: {
      val: 5,
      left: {
        val: 5,
        left: null,
        right: null,
      },
      right: null,
    },
    right: {
      val: 2,
      left: null,
      right: null,
    },
  },
  right: {
    val: 8,
    left: {
      val: 9,
      left: null,
      right: null,
    },
    right: null,
  },
};

const tree2 = {
  val: 1,
  left: {
    val: 2,
    left: {
      val: 5,
      left: {
        val: 5,
        left: null,
        right: null,
      },
      right: null,
    },
    right: {
      val: 5,
      left: null,
      right: null,
    },
  },
  right: {
    val: 8,
    left: {
      val: 9,
      left: null,
      right: null,
    },
    right: null,
  },
};

const isSame = isSameTree(tree1, tree2);
console.log(isSame);

```


<details>
  <summary>Решение</summary>

```ts
function isSameTree(p, q) {
  if (p === null && q === null) {
    return true;
  }

  if (p === null || q === null) {
    return false;
  }

  if (p.val !== q.val) {
    return false;
  }

  return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
}

```
</details>


 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/pZYADXAm_fg)

 Реализовать и проитерироваться по односвязному списку

```ts
class ListNode {
  
}

let l1 = new ListNode(2);
l1.next = new ListNode(4);
l1.next.next = new ListNode(3);

let l2 = new ListNode(5);
l2.next = new ListNode(6);
l2.next.next = new ListNode(4);
```

 <details>
  <summary>Решение</summary>

![Объяснение](https://www.google.com/url?sa=i&url=https%3A%2F%2Fproproprogs.ru%2Fstructure_data%2Fstd-odnosvyaznyy-spisok-struktura-i-osnovnye-operacii&psig=AOvVaw268YdNDvuUzT_ynUDIVXDI&ust=1730919742767000&source=images&cd=vfe&opi=89978449&ved=0CBQQjRxqFwoTCJj0zdfwxYkDFQAAAAAdAAAAABAE)

```ts
class ListNode {
  constructor(val) {
    this.val = val === undefined ? 0 : val;
    this.next = null;
  }
}

let l1 = new ListNode(2);
l1.next = new ListNode(4);
l1.next.next = new ListNode(3);

let l2 = new ListNode(5);
l2.next = new ListNode(6);
l2.next.next = new ListNode(4);

function iterateList(node) {
  let current = node;
  while (current !== null) {
    console.log(current.val);
    current = current.next;
  }
}

iterateList(l1);

```
</details>


  ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/pZYADXAm_fg)

Объединить два отсортированных связанных списка

```ts
class ListNode {
  constructor(val) {
    this.val = val === undefined ? 0 : val;
    this.next = null;
  }
}

let l1 = new ListNode(2);
l1.next = new ListNode(4);
l1.next.next = new ListNode(3);

let l2 = new ListNode(5);
l2.next = new ListNode(6);
l2.next.next = new ListNode(4);

function merge(list1, list2) {
}

console.log(merge(l1, l2));


```

<details>
  <summary>Решение</summary>

```ts
class ListNode {
  constructor(val) {
    this.val = val === undefined ? 0 : val;
    this.next = null;
  }
}

let l1 = new ListNode(1);
l1.next = new ListNode(3);
l1.next.next = new ListNode(5);

let l2 = new ListNode(4);
l2.next = new ListNode(6);
l2.next.next = new ListNode(7);


/*
{
    "val": 1,
    "next": {
        "val": 3,
        "next": {
            "val": 5,
            "next": null
        }
    }
}
*/

/*
{
    "val": 4,
    "next": {
        "val": 6,
        "next": {
            "val": 7,
            "next": null
        }
    }
}
*/

function merge(list1, list2) {
  let list = new ListNode();
  let current = list;

  while (list1 && list2) {
    if (list1.val < list2.val) {
      current.next = list1;
      list1 = list1.next;
    } else {
      current.next = list2;
      list2 = list2.next;
    }
    current = current.next;
  }
  
  current.next = list1 || list2;

  return list.next;
}

console.log(merge(l1, l2));

```
</details>

 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### ✅ 📹 Задача
[Видеообъяснение](https://youtu.be/pZYADXAm_fg)

Сложить два отсортированных связанных списка

 ```ts
class ListNode {
  constructor(val) {
    this.val = val === undefined ? 0 : val;
    this.next = null;
  }
}

let l1 = new ListNode(1);
l1.next = new ListNode(5);
l1.next.next = new ListNode(3);

let l2 = new ListNode(1);
l2.next = new ListNode(6);
l2.next.next = new ListNode(4);

function sum(list1, list2) {
 
}

console.log(sum(l1, l2));
```


<details>
  <summary>Решение</summary>

```ts
/*
{
    "val": 1,
    "next": {
        "val": 4,
        "next": {
            "val": 3,
            "next": null
        }
    }
}
*/

/*
{
    "val": 1,
    "next": {
        "val": 6,
        "next": {
            "val": 4,
            "next": null
        }
    }
}
*/

function sum(list1, list2) {
  let list = new ListNode();
  let current = list;

  let total = 0;
  let value = 0;

  while (list1 || list2 || value) {
    total = value;
    if (list1) {
      total += list1.val;
      list1 = list1.next;
    }
    if (list2) {
      total += list2.val;
      list2 = list2.next;
    }

    value = Math.floor(total / 10);
    total %= 10;
    current.next = new ListNode(total);
    current = current.next;
  }

  return list.next;
}

console.log(sum(l1, l2));

```
  
</details>


 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->


### Задача

[//]: # ([Видеообъяснение]&#40;ССЫЛКА&#41;)

Написать функцию getNumberCombinations, которая бы находила все возможные комбинации чисел из numbers, сумма которых равна number. При этом:
1) numbers содержит, только уникальные положительные числа (> 0)
2) в комбинации не должно быть повторений чисел
3) все комбинации должны быть уникальными

```ts
const getNumberCombinations = (numbers, target) => {
    const results = [];

    return results;
};
```

<details>
    <summary>Решение</summary>

```ts

```
</details>


 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

### Задача

Т-Банк, неадекватная задача

Условие: Дано изображение в виде двумерного массива символов picture, где каждый символ представляет цвет пикселя. Необходимо определить минимальное количество мазков кисти, требуемое для раскрашивания всего изображения.
Правила:
- Один мазок может закрашивать только соседние (по вертикали или горизонтали) пиксели одного цвета
- Пиксели считаются соседними, если они граничат по вертикали или горизонтали
- Каждый пиксель должен быть закрашен ровно один раз
```
Вход: [
["a","a","a","a"],
["a","b","b","a"],
["a","a","a","a"]
]
Выход: 2
```

```ts
function strokesRequired(picture) {
   
}
```


<details>

<summary>Решение</summary>

```ts
function strokesRequired(picture) {
    if (!picture.length || !picture[0].length) return 0;

    const rows = picture.length;
    const cols = picture[0].length;
    const visited = Array.from({ length: rows }, () => new Array(cols).fill(false));
    let strokes = 0;

    for (let i = 0; i < rows; i++) {
        for (let j = 0; j < cols; j++) {
            if (!visited[i][j]) {
                const color = picture[i][j];
                dfs(i, j, color);
                strokes++;
            }
        }
    }

    function dfs(i, j, color) {
        if (i < 0 || i >= rows || j < 0 || j >= cols ||
            visited[i][j] || picture[i][j] !== color) {
            return;
        }
        visited[i][j] = true;
        dfs(i + 1, j, color);
        dfs(i - 1, j, color);
        dfs(i, j + 1, color);
        dfs(i, j - 1, color);
    }

    return strokes;
}
```

</details>


 ---
 <!--  ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
