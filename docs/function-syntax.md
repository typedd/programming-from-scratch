## Создаем новые функции!

Мы можем создавать новые функции!

JavaScript: Синтаксис "толстой стрелки" (fat arrow)

```ts
sum      1     2                        =>   3
sum : (number, number)                  => number
// javascript
sum = (x     ,      y)                  => (x + y)
// typescript / Flow.js
sum = (x : number, y : number) : number => (x + y)
```

JavaScript: Синтаксис классический

```ts
         sum 1     2                             =>   3
// javascript
function sum(x,    y) {                      return x + y; }
// typescript / Flow.js
function sum(x: number, y: number): number { return x + y; };
```
