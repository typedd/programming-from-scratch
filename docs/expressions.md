## Выражения (expressions) как форма зависимости

Выражения - это когда значения (буквальные или именованные) стоят вперемешку с функциями.

Например, в математике `1 + 2` это выражение. Тут `1` и `2` - это значения (буквальные), а `+` - это функция (функция сложения).

`x^2 + y^2 + z^2 <= R^2` - математика шара. То есть такое описание (выражение) зависимости точек в трехмерном пространстве друг от друга, с целью определения составляет ли любая данная точка (выраженная тремя координами) пространство шара заданного радиуса (в системе координат с центром в центре шара) или находится за его пределами.

`2`ки (двойки) - буквальные/статичные/константные/литеральные значения

`x`, `y`, `z` и `R` - именованные значения (динамичные)

`^`, `+`, `<=` - функции (соответственно:
- `^` - возведение числа стоящего слева в степень, выраженную числом, стоящим справа
- `+` - сложение числа слева с число справа
- `<=` - функция, отвечающая ДА, в случае если число слева меньше числа слрава или равно числу справа, иначе, отвечающая НЕТ )

Все эти функции математические, предопределенные и известные если не тысячи, то сотни лет. И имеют знакомый нам синтаксис: если две короткие черточки, одна горизонтальная, а другая перпендикулярна ей, то это знак "плюс" и семантика у него - это функция сложения (того, что слева, с тем, что справа)!

Выражения могут включать в себя другие выражения, или построены на основе вложенных выражений:

`x^2 + y^2 + z^2 <= R^2` - выражение, будучи вычисленным, дающее в результате значение логического типа (boolean), то есть либо ДА, либо НЕТ (true / false).

`x^2 + y^2 + z^2` - выражение, будучи вычисленным, дающее в результате значение типа число

`x^2`, `R^2` - выраженияб будучи вычисленными, дающие в результате значения типа число

`x` - уже не выражение, тут "перемешки" с функциями нету, это просто именованное значение

`+ y^2` - не является выражением, и вообще ничем не является, кроме набора символовом, синтаксически неполным, для преобретения любой семантики. Синтаксис не соблюден - нету числа слева от +, чтобы сложить его с тем, что справа.

### О скобках в выражениях

Круглые скобки: синтаксис `(` и `)` имеют такую семантику, как и в математике: для явного определения порядка действий.

`1 + 2 * 3` - здесь порядок действий неявный, но оговоренный правилами математики: у функции умножения приоритет выше, чем у сложения.

`1 + (2 * 3)` - здесь порядок действий настойчиво явный, хоть и нет необходимости его обозначать скобками

`(1 + 2) * 3` - а здесь явный порядок действий просто необходим
