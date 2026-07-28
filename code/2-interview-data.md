# Робота з даними
---
### Типи даних
JavaScript має 7 примітивних типів і 1 непримітивний (reference type): `string`, `number`, `boolean`, `undefined`, `null`, `symbol`, `bigint`, `object`.

У TypeScript є всі типи JavaScript, а також власні типи, які існують лише під час компіляції: `any`, `unknown`, `never`, `void`, `enum`, `tuples`, `union types`, `intersection types`, `literal types`, `type aliases`, ` interface`.

---
### Object у JavaScript і TypeScript

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


