# JavaScript vs TypeScript — порівняння синтаксису



| Концепт | JavaScript | TypeScript |
|---|---|---|
| Змінна | let name = "John" | let name: string = "John" |
| Константа | const age = 30 | const age: number = 30 |
| Типізація | Dynamic typing | Static typing |
| Перевірка типів | Runtime | Compile time |
| Компіляція | Виконується напряму | TS → JS → Runtime |
| Рядок | let text = "hello" | let text: string = "hello" |
| Число | let count = 10 | let count: number = 10 |
| Boolean | let active = true | let active: boolean = true |
| Масив | const nums = [1,2,3] | const nums: number[] = [1,2,3] |
| Об'єкт | const user = {name:"Bob"} | const user: User = {name:"Bob"} |
| Функція | function add(a,b) | function add(a:number,b:number):number |
| Arrow function | (a,b)=>a+b | (a:number,b:number):number=>a+b |
| Параметр функції | function test(name) | function test(name:string) |
| Return type | Не вказується | function test(): string |
| Optional параметр | function test(name) | function test(name?: string) |
| Interface | Немає | interface User {name:string} |
| Type | Немає | type User = {name:string} |
| Union type | Немає | string \| number |
| Literal type | Немає | "success" \| "error" |
| Tuple | Звичайний array | [string, number] |
| Enum | Немає | enum Role {Admin, User} |
| Generic | Немає | function identity<T>(x:T):T |
| Any | Немає | let value:any |
| Unknown | Немає | let value:unknown |
| Never | Немає | function error():never |
| Void | Немає | function log():void |
| Class property | Створюється в runtime | name:string |
| Private | Немає стандартно | private id:number |
| Public | Немає | public name:string |
| Protected | Немає | protected role:string |
| Readonly | Немає | readonly id:number |