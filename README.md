# Сборник задач по алгоритмам

## Содержание

- [Задача 1](#задача-1)
- [Задача 2](#задача-2)
- [Задача 3](#задача-3)
- [Задача 4](#задача-4)
- [Задача 5](#задача-5)
- [Задача 6](#задача-6)
- [Задача 7](#задача-7)

### Задача 1

**Условие:** Найти наиболее часто встречающийся символ в строке.

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

**Условие:** Отсортировать массив квадратов чисел. На вход функция получает массив чисел. Числа могут быть отрицательными.

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

**Условие:** Найти первое (левое) вхождение положительного числа X или вывести -1, если число не встречалось.

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

**Условие:** Найти последнее (правое) вхождение положительного числа X или вывести -1, если число не встречалось.

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

**Условие:** Дана последовательность чисел длиной N (N > 1). Найти максимальное число в последовательности и второе по величине число (такое, которое будет максимальным, если вычеркнуть из последовательности первое максимальное число).

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

**Условие:** Дана последовательность чисел длиной N (N > 1). Найти минимальное четное число в последовательности или вывести -1, если такого числа нет.

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

**Условие:** Есть последовательность слов. Нужно вывести все самые короткие слова через пробел.

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
