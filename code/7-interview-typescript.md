# TypeScript

**TypeScript (TS)** — це надмножина JavaScript, яка додає до нього статичну типізацію та додаткові можливості для роботи з типами. TypeScript не виконується безпосередньо. Код TS спочатку компілюється в JavaScript, після чого виконується як звичайний JS.

**Основні особливості:**
* **Static typing** — можна явно вказувати типи змінних, параметрів і результатів функцій.
* **Type inference** — TypeScript часто сам визначає тип без явного зазначення.
* **Type safety** — багато помилок виявляються ще до запуску програми.
* **Union / Literal** types — можна задавати складніші обмеження типів.
* **interface і type** — опис структури об'єктів і власних типів.
* **Generic** — створення універсального коду, який зберігає типізацію.
* **Додаткові** типи — any, unknown, never, void, tuple тощо.
* **Краща підтримка IDE** — autocomplete, navigation, refactoring, підказки типів.
* **Повна сумісність з JavaScript** — практично будь-який валідний JS є валідним TS.
* **Компіляція в JavaScript** — типи існують переважно на етапі розробки й не є runtime-механізмом.
```
JavaScript
    ↓
динамічна типізація
    ↓
помилки часто виявляються під час виконання


TypeScript
    ↓
JavaScript + система типів
    ↓
перевірка типів
    ↓
JavaScript
    ↓
виконання
```
---

### Type Annotation
**Type annotation** — це явне вказування типу змінної, параметра функції, return value, property об'єкта тощо.
```
let name: string = "John";
let age: number = 30;
```
```
function add(a: number, b: number): number {
    return a + b;
}
```
---

### Type annotation vs Type inference:
* **`type annotation`** - тип вказаний явно
* **`type inference`**  — це здатність TypeScript автоматично визначати тип змінної, параметра або виразу без явного зазначення типу. 

Не потрібно явно вказувати тип там, де TypeScript легко визначає його сам. Хороший TypeScript-код не містить зайвих type annotations
```
\\ type annotation
let name: string = "John";

\\type inference
let name = "John";
```
---

### Union Types
**Union type** дозволяє змінній мати один із кількох можливих типів.
```
let id: string | number;
```
**Type Narrowing.** Щоб працювати з конкретним типом, потрібно спочатку його визначити. Найпростіший спосіб — `typeof`.
```
function printId(
    id: string | number
) {
    if (typeof id === "string") {
        console.log(
            id.toUpperCase()
        );
    } else {
        console.log(
            id.toFixed(2)
        );
    }
}
```
---

### Literal Types
**Literal type** — це тип, який дозволяє вказати конкретне значення, а не просто загальний тип. Наприклад, `string` означає: будь-який рядок. А `"success"` означає:тільки конкретний рядок `"success"`.
```
let status: "success";
status = "failed"; \\ помилка
```
**Literal Type + Union**
```
let status: "pending" | "success" | "failed";
```
---

### type
**type** — це конструкція TypeScript, яка дозволяє створювати власні іменовані типи. 
```
type UserId = string;
const id: UserId = "user-123";
```
Тобто замість того, щоб щоразу писати складний тип, ми можемо дати йому ім'я.

**Найпростіший Type Alias**
```
type UserId = string;
```
Тепер:
```
const id: UserId = "123";
```
Це еквівалентно:
```
const id: string = "123";
```
Але UserId **дає коду семантичний сенс**.
---

### interface
**interface** — це конструкція TypeScript для опису структури об'єкта. Вона визначає, які властивості та методи повинен мати об'єкт і яких вони типів. Одна з ключових можливостей interface — наслідування іншого interface. Interface може розширювати (`extends`) кілька interfaces. Клас може реалізувати interface через `implements`.
```
interface User {
    id: number;
    name: string;
    email: string;
}
```
**Interface для функцій.** Інтерфейс може описувати callable signature:
```
interface Calculator {
    (a: number, b: number): number;
}
```
---
### type vs interface

І `type`, і `interface` можуть описувати структуру об'єктів. Однак `type` є більш гнучким, оскільки може представляти об'єднання (`union`), перетини (`intersection`), примітивні типи, кортежі (`tuples`) та типи функцій. `interface` переважно призначений для опису структури об'єктів і підтримує такі можливості, як `extend`s та `declaration merging` (об'єднання оголошень). Для опису контрактів об'єктів зазвичай віддають перевагу `interface`, а для `union`-типів та складніших композицій типів використовують `type`.

Головна перевага `type` — `Union`.

Що використовувати в реальному проєкті?
Немає універсального правила: *"interface завжди для об'єктів, type завжди для всього іншого."* Обидва підходи нормальні. Можна використовувати таку практичну стратегію:

* **`interface`** - Коли описуємо об'єктний контракт. Особливо якщо: структура розширюватиметься, використовуються extends, працюємо з класами, потрібне declaration merging.
* **`type`** - Коли створюємо Union, Intersection, Primitive alias, , Function type.

```
                 type          interface
                  │                │
        ┌─────────┼───────┐        │
        │         │       │        │
      union    tuple   primitive   object
        │                         contract
        │                            │
        └──── composition           │
              через &               │
                                    │
                               extends
                                    │
                              declaration
                                merging
```
---
### any, unknown, never, void
**`any`** — це спеціальний тип TypeScript, який фактично говорить компілятору: "Не перевіряй тип цього значення." Змінна з типом any може містити практично будь-яке значення, і TypeScript дозволяє виконувати над нею операції без звичайної перевірки типів.

**`unknown`** — це тип TypeScript, який означає: "Я не знаю, який тут тип, тому спочатку перевір його." Це головна відмінність від `any`. `unknown` дозволяє зберігати будь-яке значення, але не дозволяє без перевірки виконувати над ним операції.

**`never`** — це спеціальний тип TypeScript, який означає: значення, якого ніколи не буде.

Найтиповіші випадки:
* функція завжди кидає exception;
* функція ніколи не завершується;
* TypeScript визначає, що певна ситуація неможлива.

```
function throwError(message: string): never {
    throw new Error(message);
}
```
**`void`** — це тип, який зазвичай використовується як тип результату функції, яка не повертає жодного значення.

* **`any`** - Не перевіряй тип
* **`unknown`** - Тип невідомий, перевір спочатку
* **`never`** - Такого значення не може бути
* **`void`** - Функція не повертає meaningful value
---

