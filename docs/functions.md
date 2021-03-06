## Функции (functions) как форма выражения (expression)

Итак, `+` - это функция сложения числа слева, назовем его `a`, с числом справа, назовем его `b`, и результат назовем `c`.

Можно визуализировать схему работы этой функции:

`a + b => c`

И некоторые примеры ее работы:

```
1 + 2 => 3
1 + 1 => 2
0 + 0 => 0
```

Значение, которые мы вычисляем, зависит от двух других значений, или другими словами: для его получения, нужны два числа. Схематично и с типами:

### (Ин)фиксный, (пре)фиксный и (постфиксный) синтаксис применения функции

- `1 + 2` - инфиксный, имя функции стоит посреди (`in-`) значений, которые необходимы для выполнения функции
- `+ 1 2` - префиксный, иия функции стоит перед (`pre-`) списком значений, которые необходимы для выполнения функции
- `1 2 +` - постфиксный, имя функции стоит после (`post-`) списка значений, которые необходимы для выполнения функции

Зачем нужен какой-то еще префиксный синтаксис вообще? Ну не все же функции выражают зависимость конкретно от двух значений, правда? Ведь, если задуматься с инфиксным синтаксисом имя функции можно поставить только между двумя значениями. А между тремя, например, куда его ставить? Префиксный и постфиксный синтаксис применения функции к значениям - более общий.

В общем виде функция сложения чисел, через префиксный синтаксис

```
+ 1 2 3 4 5 => 15
```

В разных ЯП по разному, но например, в JavaScript, присутствует и инфиксный (для математических функций) и префиксный синтаксис (для всех остальных). Постфиксный отсутсвует.

В некоторых ЯП синтаксис сложения прямо так и выглядит

```
+ 1 2 3 4 5
```

Ну правда, а зачем лишние символы, типа запятых или скобок? Неужели итак непонятно, что + - это имя функции и дальше "до конца", через пробел, значения, к которым эта функция применяется.

В некоторых ЯП, необходимы запятые и/или скобки

```
+(1, 2, 3, 4, 5)
```

Или в JavaScript (учитывая, что `+` - это спец символ для строго-бинарной, зависящей строго от двух значений, функции сложения)
```javascript
// javascript
sum(1, 2, 3, 4, 5)
```

Очень важно в тексте программы на любом ЯП видеть значения, выражения, имена функций и к чему они применяются. Синтаксис может сильно разниться, но суть остается неизменной.

### Практикум

На псевдо-ЯП, в качестве закрепления, перепишем инфиксный синтаксис (привычный нам из математики) на префиксный и постфиксный.

```
1 + 2 * 3 // infix
+ 1 (* 2 3) // prefix
1 (2 3 *) + // postfix

(1 + 2) * 3 // infix
* (+ 1 2) 3 // prefix
 // postfix
```

### Экзотика

В некоторых ЯП присутсвует спец инфиксный синтаксис для произвольно названных бинарных функций. Например, в PureScript

```
sum 1 2
1 `sum` 2
```

Видите те спец кавычки? Это функция (с именем sum), применяется к двум значениям (бинарная), стоящим по обе стороны от нее.

### Функции унарные, бинарные, тернарные, ...

- `Унарные` (uno) - те, которые зависят от одного значения.
- `Бинарные` (bi) - те, которые зависят от двух значений.
- `Тернарные` (ter, tre) - те, которые зависят от трех значений.
и т.д.

Функции, которые могут быть применены к любому кол-ву значений, называются `вариативными`. Например, функция сложения, особенно в ее инфиксном синтаксисе, в общем виде, вариативна

```
// pseudo PL
+ 1 2
=> 3
+ 1 2 3
=> 6
+ 1 2 3 4
=> 10
```

Не во всех ЯП есть вариативные функции. В JavaScript есть!

### Вызов функции? Или применение функции?

Говорят и так, и так. Это философский вопрос.

Но "вызвать функцию" ставит во главу угла саму функцию, как "вызывать джина из бутылки" и сделает какую-то магию.

А когда говоришь "применить функцию", фраза звучит незаконченной и неминуемо напрашивается " ... к чему", как бы в напоминание, что функция - это всего лишь форма выражения зависимости одних значений от других.

В случае функции сложения: значения результата сложения от двух исходных чисел.

"Вызовем функцию сложения" на языке JavaScript "звучит" так:
```javascript
// javascript
sum();
```

Ну вызвали, а дальше что? А! Забыли, ей же еще значения нужны!

"Применим функцию сложения к ..." на языке JavaScript "звучит" так:
```javascript
// javascript
sum(?
```

Тут уже не забудем...

Дело исключительно вкуса!