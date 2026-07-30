## Асинхронність
---
### Callback 
**Callback Function** — це функція, яка передається як аргумент в іншу функцію і викликається пізніше.
```
const numbers = [1,2,3];
const doubled = numbers.map(number => number * 2);    \\ callback: number => number * 2
```

Таку вкладеність називають **Callback Hell** або **Pyramid of Doom**. Саме для вирішення цієї проблеми з'явилися `promise` і `async/await`.
```
doSomething(function () {
    doSomethingElse(function () {
        doAnotherThing(function () {
            finish(function () {
            });
        });
    });
});
```
---

### Promise
**Promise** — це об'єкт, який представляє результат асинхронної операції, що стане доступним зараз або в майбутньому. Іншими словами, Promise — це "обіцянка", що операція завершиться успішно (fulfilled), або з помилкою (rejected).

Promise має три стани: Pending, Fulfilled, Rejected.

**Promise у Playwright** - Практично всі методи Playwright повертають Promise.
```
await page.goto("/");   \\повертає Promise<void>
const text =  await page.textContent("h1");  \\повертає Promise<string | null>
```

Promise можна чекати лише через `await`, `await` "розгортає" Promise.
```
const response = fetch("/users");         \\ Promise<Response>
const response = await fetch("/users");   \\ Response
```

---

### async/await
**`async/await`** — це сучасний синтаксис для роботи з Promise, який дозволяє писати асинхронний код так, ніби він є синхронним.

**`async`** ставиться перед функцією. Після цього функція завжди повертає Promise.
**`await`** чекає завершення Promise і повертає його результат

Приклад у Playwright. Без `await`: `page.click("button");` Клік буде лише запланований, але виконання коду продовжиться далі.

---
### Event Loop
**Event Loop** — це механізм JavaScript, який дозволяє виконувати асинхронний код, незважаючи на те, що JavaScript працює в одному потоці (single-threaded). Його задача — контролювати виконання синхронного коду, callback-функцій, Promise і додавати готові задачі в Call Stack у правильному порядку.

**Чому потрібен Event Loop?** JavaScript має один основний потік виконання. Тобто одночасно може виконувати тільки одну операцію. Але в реальному застосунку є операції, які займають час. Якби JavaScript чекав їх завершення, браузер зависав би. Тому асинхронні операції виконуються окремими механізмами, а Event Loop керує поверненням результатів.

```
          Web APIs
             ↓
Call Stack ← Event Loop ← Queues
                         |
              ┌──────────┴──────────┐
              ↓                     ↓
        Microtask Queue        Callback Queue
        (Promise)              (setTimeout)
```

* **Call Stack** - Це місце, де виконується JavaScript-код.
* **Web APIs** - Браузер або Node.js мають власні механізми для асинхронних операцій.
* **Callback Queue (Task Queue)** - Сюди потрапляють callback-и.
* **Microtask Queue** - Це черга з вищим пріоритетом. Тут знаходяться: Promise callbacks, await.

**Головне правило Event Loop**
Порядок:
1. Виконати весь синхронний код
2. Виконати всі Microtasks
3. Виконати одну Task
4. Повторити цикл

Приклад: Що буде в консолі?
```
console.log("1");

setTimeout(() => {
    console.log("2");
}, 0);

Promise.resolve()
    .then(() => {
        console.log("3");
    });

console.log("4");
```

```
console.log("1"); \\ Синхронний код.
console.log("4"); \\ Наступний синхронний код

Promise.resolve()
    .then(() => {
        console.log("3"); \\ Спочатку виконується Microtask (Promise)
    });

setTimeout(() => {
    console.log("2"); \\ Потім Task (Callback)
}, 0);

```
---

### Promise.all() і Promise.race()

**`Promise.all()`** і **`Promise.race()`** — це статичні методи об'єкта Promise, які дозволяють працювати з декількома асинхронними операціями одночасно.

`Promise.all()` запускає декілька Promise паралельно і чекає завершення всіх.
`Promise.race()` повертає результат першого Promise, який завершився.

---