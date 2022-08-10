## Заканчиваем (или заначинаем? в общем закругляемся!) с зодиаком

Формализмы (математика) в программировании говорит лучше любого человеческого языка (иначе мы бы программы на них писали). И в этой части, я надеюсь, можно объяснять все меньше и меньше. Код говорит сам за себя!

```ts
// zodiak.ts
type Zodiak = 'Aries' | "Taurus" | "???";

function between(date : Date, dateA : Date, dateB : Date) : boolean {
    return date > dateA && date < dateB;
}

function foo(date : Date) : Zodiak {
    if (between(date, new Date('1970-03-21'), new Date('1970-04-20'))) {
        return 'Aries';
    } else if (between(date, new Date('1970-04-21'), new Date('1970-05-21'))) {
        return 'Taurus';
    } else {
        return '???';
    }
}
console.log(
    '25.03 ->',
    foo(new Date('1970-03-35'))
);
console.log(
    '01.05 ->',
    foo(new Date('1970-05-01'))
);
```

```bash
$> tsc zodiak.ts
$> node zodiak.js
25.03 -> ???
01.05 -> Taurus
```

Во-первых, ха?! Как так? А во-вторых, Вы же говорили тот `else` с `???` никогда не случится!

Дебажим

```ts
// zodiak.ts
type Zodiak = 'Aries' | "Taurus" | "???";

function between(date : Date, dateA : Date, dateB : Date) : boolean {
    return date > dateA && date < dateB;
}

function foo(date : Date) : Zodiak {
    console.log('date:', date);
    if (between(date, new Date('1970-03-21'), new Date('1970-04-20'))) {
        return 'Aries';
    } else if (between(date, new Date('1970-04-21'), new Date('1970-05-21'))) {
        return 'Taurus';
    } else {
        return '???';
    }
}
console.log(
    '25.03 ->',
    foo(new Date('1970-03-35'))
);
console.log(
    '01.05 ->',
    foo(new Date('1970-05-01'))
);
```

```bash
...
$> node zodiak.js
date: Invalid Date
25.03 -> ???
date: 1970-05-01T00:00:00.000Z
01.05 -> Taurus
```

Хм, в первом случае `Invalid Date`. Ну правильно! `new Date('1970-03-35')` ;-) => `new Date('1970-03-25')`

```ts
// zodiak.ts
type Zodiak = 'Aries' | "Taurus" | "???";

function between(date : Date, dateA : Date, dateB : Date) : boolean {
    return date > dateA && date < dateB;
}

function foo(date : Date) : Zodiak {
    console.log('date:', date);
    if (between(date, new Date('1970-03-21'), new Date('1970-04-20'))) {
        return 'Aries';
    } else if (between(date, new Date('1970-04-21'), new Date('1970-05-21'))) {
        return 'Taurus';
    } else {
        return '???';
    }
}
console.log(
    '25.03 ->',
    foo(new Date('1970-03-25'))
);
console.log(
    '01.05 ->',
    foo(new Date('1970-05-01'))
);
```

```bash
...
$> node zodiak.js
date: 1970-03-25T00:00:00.000Z
25.03 -> Aries
date: 1970-05-01T00:00:00.000Z
01.05 -> Taurus
```

Теперь все в норме! Получается в прошлый раз мы серотонин незаслуженно получили?.. Хотя какая разница :-)

Задержимся на одном моменте: А что бы было, если бы мы наивно не сделали `else` с `???` ? Давайте проверим

```ts
// zodiak.ts
type Zodiak = 'Aries' | "Taurus";

function between(date : Date, dateA : Date, dateB : Date) : boolean {
    return date > dateA && date < dateB;
}

function foo(date : Date) : Zodiak {
    if (between(date, new Date('1970-03-21'), new Date('1970-04-20'))) {
        return 'Aries';
    } else if (between(date, new Date('1970-04-21'), new Date('1970-05-21'))) {
        return 'Taurus';
    }
}
console.log(
    '25.03 ->',
    foo(new Date('1970-03-35'))
);
console.log(
    '01.05 ->',
    foo(new Date('1970-05-01'))
);
```

```bash
...
node zodiak.js
25.03 -> undefined
01.05 -> Taurus
```

`undefined` какой-то... Откуда он взялся? Согласитесь, совершенно ведь непонятно. В предыдущем случае хотя бы было понятно, что оно уходит в тот самый `else` и было понятно почему: потому что среди всех сравнений не нашлось подходящего. Это мы сейчас уже знаем, что дата неправильная, а если бы не знали, то совершенно невозможно "ткнуть в код пальцем" и сказать "это упало вот тут!". И это у нас код 22 строки, а если 22457 строк в 34 файлах?

Если не раньше, то теперь то уж точно Вы завершите задачу до конца! Даже у Вас таких сомнений не осталось, правда ведь? Совершенная уверенность, что остальное - дело техники.

Конечно, еще остается этап "причесывания" кода (где-то покороче можно, где-то поэлегантнее), но если сейчас 3 часа ночи и сил на это нет, то по крайней мере сложно поспорить с фактом, что оно работает! Этап "причесывания" (refactoring) я оставляю читателю, ибо в этом уже мало интересного для меня самого, 22 строки или 3, уже не столь важно, как факт того, что программа работает и работает верно!

### Заключение

Порефлексируйте теперь: вспомните все ощущения, которые Вы испытали за время этого короткого путешествия. Больше было негатива или позитива? И запомните как должно ощущаться программирование как шаблон. В следующих задачах, если шаблон ваших эмоций другой, значит Вы не следуете этому методу! Это не обязательно говорит, что Вы делаете неправильно, но Вы точно не следуете этому методу.

Этот метод не единственно верный и его надо практиковать достаточное количество раз, но он работающий! Хороших Вам эмоций в обучении и труде!

Happy coding! :-)
