## Функции и типы

Помогая вам осознать
- роль функций в выражении зависимости одних значений от других
- синтаксис типов функций

мне можно становиться все менее многословным в объяснениях.

Достатачно видеть соответствие, одного под другим, чтобы осознать типы функций

```
foo      1     2       =>    3
foo : (number, number) => number
```

Это - функция, которая будучи примененной к двум значениям типа `number`, будет вычислена до значения типа `number`. И кстати имя у нее `foo`. Даже так и говорят: "foo is a function number, number to number"

```
foo : (number, number) => number
foo : (number, number) to number
```

`(number, number) => number` - это тип! А значит он определяет, какие там могут жить обитатели, а какие не могут

Например, функция `sum : (number, number) => number` может. А `меньше : (number, number) => boolean` не может.

