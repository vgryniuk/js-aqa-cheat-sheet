# Робота з даними у JavaScript і TypeScript
---
### Типи даних
JavaScript має 7 примітивних типів і 1 непримітивний (reference type): `string`, `number`, `boolean`, `undefined`, `null`, `symbol`, `bigint`, `object`.

У TypeScript є всі типи JavaScript, а також власні типи, які існують лише під час компіляції: `any`, `unknown`, `never`, `void`, `enum`, `tuples`, `union types`, `intersection types`, `literal types`, `type aliases`, ` interface`.

---
### Object 

**Об'єкт (Object)** — це колекція пар ключ → значення. Ключі — це властивості (properties), а значення можуть бути будь-якого типу: число, рядок, масив, функція або інший об'єкт.

JavaScript
```
const user = {
    id: 1,
    name: "John",
    active: true
};
```

TypeScript
```
type User = { //можна також визначати через interface
    id: number;
    name: string;
    active: boolean;
};
```
---

### Array
Масив (`Array`) — це впорядкована колекція елементів. Кожен елемент має індекс, який починається з 0. У JavaScript масив може містити значення різних типів, але в TypeScript зазвичай використовують масиви одного типу.

**Найпоширеніші методи масивів:**
* `push()` -	додати в кінець
* `pop()` -	видалити останній
* `shift()` -	видалити перший
* `unshift()` -	додати на початок
* `filter()` -	відфільтрувати
* `find()` -	знайти перший елемент
* `reduce()` -	звести масив до одного значення
* `some()` -	хоча б один підходить
* `every()` -	усі підходять
* `includes()` -	перевірити наявність
* `sort()` -	сортування
---


