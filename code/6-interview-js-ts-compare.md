# JavaScript vs TypeScript — порівняння синтаксису

| Концепт | JavaScript (JS) | TypeScript (TS) |
|---|---|---|
| **Змінні** | ```js
let name = "John";
const age = 30;
``` | ```ts
let name: string = "John";
const age: number = 30;
``` |
| **Типи даних** | Типи визначаються під час виконання (runtime) | Типи перевіряються під час компіляції (compile time) |
| **Примітиви** | ```js
string
number
boolean
null
undefined
symbol
bigint
``` | ```ts
string
number
boolean
null
undefined
symbol
bigint
any
unknown
never
void
``` |
| **Функція** | ```js
function add(a, b) {
  return a + b;
}
``` | ```ts
function add(
  a: number,
  b: number
): number {
  return a + b;
}
``` |
| **Arrow function** | ```js
const add = (a, b) => {
  return a + b;
};
``` | ```ts
const add = (
  a: number,
  b: number
): number => {
  return a + b;
};
``` |
| **Тип повернення функції** | Не вказується | Вказується явно |
| | ```js
function getName() {
  return "John";
}
``` | ```ts
function getName(): string {
  return "John";
}
``` |
| **Object** | ```js
const user = {
  name: "John",
  age: 30
};
``` | ```ts
const user: {
  name: string;
  age: number;
} = {
  name: "John",
  age: 30
};
``` |
| **Interface** | Немає | ```ts
interface User {
  name: string;
  age: number;
}

const user: User = {
  name: "John",
  age: 30
};
``` |
| **Type alias** | Немає | ```ts
type User = {
  name: string;
  age: number;
};
``` |
| **Array** | ```js
const numbers = [1,2,3];
``` | ```ts
const numbers: number[] = [1,2,3];
``` |
| **Array через Generic** | Немає | ```ts
const numbers: Array<number> = [1,2,3];
``` |
| **Tuple** | Немає контролю структури | ```ts
const user: [string, number] = [
  "John",
  30
];
``` |
| **Union type** | Немає | ```ts
let id: string | number;

id = "abc";
id = 123;
``` |
| **Literal type** | Немає | ```ts
let status: "success" | "error";

status = "success";
``` |
| **Optional property** | ```js
const user = {
  name: "John"
};
``` | ```ts
interface User {
  name: string;
  age?: number;
}
``` |
| **Optional parameter** | ```js
function greet(name) {
}
``` | ```ts
function greet(
  name?: string
) {
}
``` |
| **Default parameter** | ```js
function greet(
  name = "Guest"
) {}
``` | ```ts
function greet(
  name: string = "Guest"
) {}
``` |
| **Class** | ```js
class User {
  constructor(name) {
    this.name = name;
  }
}
``` | ```ts
class User {
  name: string;

  constructor(name: string) {
    this.name = name;
  }
}
``` |
| **Access modifiers** | Немає | ```ts
class User {
  private id: number;
  public name: string;
  protected role: string;
}
``` |
| **Readonly** | Немає | ```ts
class User {
  readonly id: number;
}
``` |
| **Enum** | Немає (звичайно object) | ```ts
enum Role {
  Admin,
  User
}
``` |
| **Generics** | Немає | ```ts
function identity<T>(
  value: T
): T {
  return value;
}
``` |
| **Any** | Все дозволено | ```ts
let value: any;

value.foo();
value = 123;
``` |
| **Unknown** | Немає | ```ts
let value: unknown;

if(typeof value === "string"){
  value.toUpperCase();
}
``` |
| **Never** | Немає | ```ts
function error(): never {
  throw new Error();
}
``` |
| **Type assertion** | Немає | ```ts
const input =
value as string;
``` |
| **Modules** | ```js
export default user;
import user from "./user";
``` | ```ts
export default user;
import user from "./user";
``` |
| **Compilation** | Виконується напряму браузером / Node.js | TS → JS → виконання |
| **Перевірка помилок** | Runtime | Compile time |
| **Типізація** | Dynamic typing | Static typing |
| **IDE підтримка** | Базова | Значно краща (autocomplete, refactoring) |
