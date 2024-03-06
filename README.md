# Сборник задач по алгоритмам

## Содержание

- [Задача 1](#задача-1)
- [Задача 2](#задача-2)

### Задача 1

**Условие:** Найти наиболее часто встречающийся символ в строке

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

**Условие:** Отсортировать массив квадратов чисел

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
