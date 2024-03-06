# Сборник задач по алгоритмам

## Содержание

- [Задача 1](#задача_1)

### задача_1

**Условие:** Найти наиболее часто встречающийся символ в строке

**Решение:** 

```javascript
const getMaxCharConcurrency2 = (string) => {
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
