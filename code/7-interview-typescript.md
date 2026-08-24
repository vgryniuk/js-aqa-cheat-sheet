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
