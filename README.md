# Сборник задач по алгоритмам

## Содержание

#### Уровень 1
- [Задача 1](#задача-1)
- [Задача 2](#задача-2)
- [Задача 3](#задача-3)
- [Задача 4](#задача-4)
- [Задача 5](#задача-5)
- [Задача 6](#задача-6)
- [Задача 7](#задача-7)
- [Задача 8](#задача-8)
- [Задача 9](#задача-9)
- [Задача 10](#задача-10)

#### Уровень 2
- [Задача 11](#задача-11)

## Уровень 1

### Задача 1

**Условие:** Найти наиболее часто встречающийся символ в строке.\
**Пример:** <code>getMaxCharConcurrency("absjklaaaa")</code> -> <code>a</code>\
**Решение:** Сложность по времени <code>O(n + k)</code>

```javascript
const getMaxCharConcurrency = (string) => {
  let concurrency = new Map();

  for (let i = 0; i < string.length; i++) {
    if (concurrency.has(string[i])) {
        concurrency.set(string[i], concurrency.get(string[i]) + 1);
    } else {
        concurrency.set(string[i], 1);
    }
  }

  const entries = concurrency.entries();

  let resultChar = "";
  let resultCount = 0;

  for (let [char, count] of entries) {
    if (count > resultCount) {
        resultChar = char;
        resultCount = count;
    }
  }
};
```
### Задача 2

**Условие:** Вернуть отсортированный массив квадратов чисел. На вход функция получает отсортированный по возрастанию массив чисел.  Числа могут быть отрицательными.\
**Пример:** <code>getSquareNumbers([-2, 1, 5, 9])</code> -> <code>[1, 4, 25, 81]</code>\
**Решение:** Сложность по времени <code>O(n)</code>

```javascript
const getSquareNumbers = (nums) => {
  const output = [];
  let left = 0;
  let right = nums.length - 1;

  for (let i = right; i >= 0; i--) {
    let currentLeft = Math.pow(nums[left], 2)
    let currentRight = Math.pow(nums[right], 2)

    if (currentLeft > currentRight) {
      output[i] = currentLeft;
      left++
    } else {
      output[i] = currentRight;
      right--;
    }
  }

  return output;
};
```
### Задача 3

**Условие:** Найти первое (левое) вхождение положительного числа X или вывести -1, если число не встречалось.\
**Пример:** <code>findX("abcb", "b")</code> -> <code>1</code>\
**Решение:** Сложность по времени <code>O(n)</code>

```javascript
const findX = (sequence, x) => {
	let result = -1;
  
  for (let i = 0; i < sequence.length; i++) {
  	if (result === -1 && sequence[i] === x) {
    	result = i;
    }
  }
  
  return result;
}
```
### Задача 4

**Условие:** Найти последнее (правое) вхождение положительного числа X или вывести -1, если число не встречалось.\
**Пример:** <code>findLastX("abcb", "b")</code> -> <code>3</code>\
**Решение:** Сложность по времени <code>O(n)</code>

```javascript
const findLastX = (sequence, x) => {
  let result = -1;

  for (let i = 0; i < sequence.length; i++) {
    if (sequence[i] === x) {
      result = i;
    }
  }

  return result;
}
```
### Задача 5

**Условие:** Дана последовательность чисел длиной N (N > 1). Найти максимальное число в последовательности и второе по величине число (такое, которое будет максимальным, если вычеркнуть из последовательности первое максимальное число).\
**Пример:** <code>getMaximums([-1, -10, -15, -1, -3])</code> -> <code>[-1, -1]</code>\
**Решение:** Сложность по времени <code>O(n)</code>

```javascript
const getMaximums = (nums) => {
  let max1 = Math.max(nums[0], nums[1]);
  let max2 = Math.min(nums[0], nums[1]);

  for (let i = 2; i < nums.length; i++) {
    if (nums[i] > max1) {
      max2 = max1;
      max1 = nums[i];
    } else if (nums[i] > max2) {
      max2 = nums[i];
    }
  }

  return [max1, max2];
}
```
### Задача 6

**Условие:** Дана последовательность чисел длиной N (N > 1). Найти минимальное четное число в последовательности или вывести -1, если такого числа нет.\
**Пример:** <code>getMinEven([-1, -10, -15, -1, -3])</code> -> <code>-10</code>\
**Решение:** Сложность по времени <code>O(n)</code>

```javascript
const getMinEven = (nums) => {
  let result = -1;

  for (let i = 0; i < nums.length; i++) {
    if (nums[i] % 2 === 0 && (result === -1 || nums[i] < result)) {
      result = nums[i];
    }
  }

  return result;
}
```
### Задача 7

**Условие:** Есть последовательность слов. Нужно вывести все самые короткие слова через пробел.\
**Пример:** <code>getShortestWords(["hi", "hello", "so", "wow"])</code> -> <code>"hi,so"</code>\
**Решение:** Сложность по времени <code>O(n)</code>

```javascript
const getShortestWords = (words) => {
  let shortestLength = words[0].length;
  let result = [];

  for (let word of words) {
    if (word.length < shortestLength) {
      shortestLength = word.length;
    }
  }

  for (let word of words) {
    if (word.length === shortestLength) {
      result.push(word);
    }
  }

  return result.join();
}
```
### Задача 8

**Условие:** Написать функцию сжатия строки. Если на вход пришла пустая строка, сгенерировать ошибку. \
Пояснения: Если символ встречается 1 раз, он остается без изменений. Если символ встречается более одного раза подряд - перед ним добавляется число с количеством повторений. \
**Пример:** <code>getCompressedStr('abbaajjjjl')</code> -> <code>ab2a2j4l</code>\
**Решение:** Сложность по времени <code>O(n)</code>

```javascript

const pack = (s, count) => {
  if (count > 1) {
    return `${s}${count}`
  }

  return s;
}

const getCompressedStr = (s) => {
  let lastSymbol = s[0];
  let lastPosition = 0;
  const result = [];

  for (let i = 0; i < s.length; i++) {
    if (s[i] !== lastSymbol) {
      result.push(pack(lastSymbol, i - lastPosition));
      lastPosition = i;
      lastSymbol = s[i];
    }
  }
  result.push(pack(lastSymbol, s.length - lastPosition));

  return result.join("");
}
```
### Задача 9

**Условие:** Дана последовательность положительных чисел, длиной N и число X. Нужно найти два различных числа, которые в сумме дадут X или вернуть [0, 0], если их нет. \
**Пример:** <code>getTerms([3, 4, 7, 9, 10], 7)</code> -> <code>[4, 3]</code>\
**Решение:** Сложность по времени <code>O(n)</code>

```javascript

const getTerms = (nums, x) => {
  const terms = new Set();
  
  for (let num of nums) {
    if (terms.has(x - num)) {
      return [num, x - num];
    }
    terms.add(num);
  }

  return [0, 0];
};
```

### Задача 10

**Условие:** \
**Пример:** \
**Решение:** 

```javascript
 
// in progress

```

## Уровень 2

### Задача 11

**Условие:** Подсчет дождевой воды. \
**Пример:** <code>bfRainTerraces([2, 4, 1, 4])</code> -> <code>3</code> \
**Решение:** Сложность по времени <code>O(n^2)</code>

```javascript
 
const bfRainTerraces(terraces) {
  let highestBar = 0;
  
  for (let i = 0; i < terraces.length; i++) {
    if (terraces[i] > terraces[highestBar]) {
	highestBar = i;
    }
  }
  
  let waterAmount = 0;
  let currentMax = 0;
  
  for (let k = 0; k < highestBar; k++) {
    if (terraces[k] > currentMax) {
	currentMax = terraces[k];
    }
    waterAmount += currentMax - terraces[k];
  }
  
  currentMax = 0;
  
  for (let j = terraces.length - 1; j > highestBar; j--) {
    if (terraces[j] > currentMax) {
	currentMax = terraces[j];
    }
    waterAmount += currentMax - terraces[j];
  }

  return waterAmount;
}
 
```

