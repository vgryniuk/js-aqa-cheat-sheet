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