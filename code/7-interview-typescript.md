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
**Type annotation vs Type inference:** `type annotation`, це коли тип вказаний явно, `type inference` це коли ts сам визначає тип на етапі статичної перевірки коду. Не потрібно явно вказувати тип там, де TypeScript легко визначає його сам. Хороший TypeScript-код не містить зайвих type annotations
```
\\ type annotation
let name: string = "John";

\\type inference
let name = "John";
```
---

### Type Inference
**Type inference** — це здатність TypeScript автоматично визначати тип змінної, параметра або виразу без явного зазначення типу.