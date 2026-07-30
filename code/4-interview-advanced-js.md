## Поглиблений JavaScript
### Closure (замикання)
**Closure (замикання)** — це механізм JavaScript, коли функція зберігає доступ до змінних із зовнішньої області видимості навіть після того, як зовнішня функція вже завершила виконання.

**`Closure = Function + Outer Scope`**

Для чого використовуються closure?
* приватні змінні;
* створення фабрик функцій;
* callback;
* збереження стану;
* модулі.

```
function outer() {
    let count = 0;
    function inner() {
        count++;
        console.log(count);
    }
    return inner;
}

const counter = outer();
counter();                \\1
counter();                \\2
counter();                \\3
```
---
### Prototype і Prototype Chain

**Prototype (прототип)** — це механізм JavaScript, який дозволяє об'єктам успадковувати властивості та методи від інших об'єктів. Кожен JavaScript-об'єкт має внутрішнє посилання на інший об'єкт — його прототип. Цей ланцюжок називається **Prototype Chain**.

```
const animal = {
    eat() {
        console.log("Eating");
    }
};

const dog = {
    bark() {
        console.log("Barking");
    }
};

Object.setPrototypeOf(dog, animal);

dog.bark();
dog.eat();
```

**Prototype у функцій** У JavaScript функції теж є об'єктами.
```
function User(name) {
    this.name = name;
}

User.prototype.sayHello = function() {
    console.log(
        "Hello " + this.name
    );
};

const user1 = new User("John");
user1.sayHello();
```

У сучасному JavaScript часто використовують **class**, але class всередині все одно використовує prototype.

---
### Class. Як працює наслідування через `extends` і `super`?
**`Class`** у JavaScript — це синтаксичний цукор над prototype-based inheritance. Тобто JavaScript не став об'єктно-орієнтованою мовою класичного типу Java/C#. Всередині class все одно використовує: `prototype`, `prototype chain`, `constructor functions`. Але class робить код більш зрозумілим і схожим на класичний ООП.
```
class User {
    constructor(name) {
        this.name = name;
    }
    sayHello() {
        console.log(`Hello ${this.name}`);
    }
}

const user = new User("John");
user.sayHello();
```
**Наслідування через `extends`** - `extends` дозволяє одному класу отримати властивості та методи іншого класу.

**`super`** використовується для звернення до батьківського класу. Є два основних випадки:
* виклик конструктора батьківського класу;
* виклик методів батьківського класу.

---
### Shallow Copy і Deep Copy
У JavaScript об'єкти та масиви зберігаються за посиланням, а не копіюються автоматично. Тому просте присвоєння: `const user2 = user1;` не створює новий об'єкт. Обидві змінні будуть посилатися на один і той самий об'єкт у пам'яті.

**Shallow Copy (поверхнева копія)** - створює новий об'єкт, але вкладені об'єкти копіює як посилання. Тобто, примітиви копіюються, об'єкти всередині залишаються спільними.

Способи зробити Shallow Copy:
* **Object spread** - `const copy = { ...original};`
* **Object.assign()** - `const copy = Object.assign({}, original);`
* **Масиви** - `const arr2 = [ ...arr1];`

**Deep Copy (глибока копія)** - створює повністю незалежну копію. Всі вкладені об'єкти також копіюються.

Способи зробити Deep Copy:
* **structuredClone() (сучасний варіант)** - `const copy = structuredClone(original);`
* **JSON.parse / JSON.stringify** - `const copy = JSON.parse(JSON.stringify(original));`
---
### Immutability
**Immutability (незмінність)** — це принцип, за яким після створення об'єкт або значення не змінюється напряму. Замість зміни існуючого об'єкта створюється новий об'єкт із потрібними змінами. У JavaScript це не є обов'язковим правилом мови, але це дуже поширений підхід у сучасному програмуванні.

---
### Garbage Collection і Memory Leaks
**Garbage Collection (GC)** — це автоматичний механізм JavaScript, який знаходить об'єкти, які більше не використовуються програмою, і звільняє пам'ять, яку вони займають.

**Memory Leak** — це ситуація, коли програма більше не використовує об'єкт, але він все ще залишається доступним для Garbage Collector.

Основні причини Memory Leak у JavaScript
* Глобальні змінні
* Залишені таймери
* Event listeners
* Closures
* Великі кеші
---
