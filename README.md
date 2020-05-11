# WebHero JavaScript Style Guide

В данном руководстве описаны подходы по оформлению Java Script. Данное руководство не является железным правилом для всех проектов во frontend, а только рекомендации для разработки проектов в нашей школе :slightly_smiling_face: На вашей работе могут быть другие правила. Все правила обсуждаются и согласовываются участниками команды и придерживаются их на протяжении разработки всего проекта.

&nbsp;
## Содержание

1. [Соглашение об именовании](#соглашение-об-именовании)
2. [Переменные](#переменные)
3. [Запятые](#запятые)
4. [Точка с запятой](#точка-с-запятой)
5. [Блоки](#блоки)
6. [Объекты](#объекты)
7. [Массивы](#массивы)
9. [Деструктуризация](#деструктуризация)
10. [Строки](#строки)
11. [Функции](#функции)
12. [Стрелочные функции](#стрелочные-функции)
13. [Классы и конструкторы](#классы-и-конструкторы)
14. [Модули](#модули)
15. [Генераторы](#генераторы)
16. [Операторы сравнения](#операторы-сравнения)
17. [Комментарии](#комментарии)
18. [Пробелы](#пробелы)
19. [Преобразование и приведение типов](#преобразование-и-приведение-типов)
20. [Регулярные выражения](#регулярные-выражения)


&nbsp;

## Соглашение об именовании.

&nbsp;
#### 1. Избегайте однобуквенных названий.

> eslint: [`id-length`](https://eslint.org/docs/rules/id-length#top)

&nbsp;

❌  не надо так 👇
```javascript
function q() {
  // ...
}
```

&nbsp;

✅ надо так 👇
```javascript
function query() {
  // ...
}
```

&nbsp;
#### 2. Используйте camelCase для названий переменных, объектов и функций.

> eslint: [`camelcase`](https://eslint.org/docs/rules/camelcase#top)

&nbsp;

❌  не надо так 👇
```javascript
const OBJEcttsssss = {};
const this_is_my_object = {};
function c() {}
```

&nbsp;

✅ надо так 👇
```javascript
const thisIsMyObject = {};
function thisIsMyFunction() {}
```

&nbsp;
#### 3. Используйте PascalCase для именования конструкторов или классов.

> eslint:  [`new-cap`](https://eslint.org/docs/rules/new-cap#top)

&nbsp;

❌ не надо так 👇
```javascript
function user(options) {
  this.name = options.name;
}

const bad = new user({
  name: 'nope',
});
```

&nbsp;

✅ надо так 👇
```javascript
class User {
  constructor(options) {
    this.name = options.name;
  }
}

const good = new User({
  name: 'yup',
});
```

&nbsp;
#### 4. Не используйте нижнее подчеркивание в начале или конце названий.

> eslint: [`no-underscore-dangle`](https://eslint.org/docs/rules/no-underscore-dangle#top)

&nbsp;

❌ не надо так 👇
```javascript
this.__firstName__ = 'Panda';
this.firstName_ = 'Panda';
this._firstName = 'Panda';
```

&nbsp;

✅ надо так 👇
```javascript
this.firstName = 'Panda';
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Переменные.

&nbsp;
#### 1. Всегда используйте let или const для объявления переменных.

> eslint: [`no-undef`](https://eslint.org/docs/rules/no-undef-init#top), [`prefer-const`](https://eslint.org/docs/rules/prefer-const#top)

&nbsp;

❌ не надо так 👇
```javascript
uperPower = new SuperPower();
```

&nbsp;

✅ надо так 👇
```javascript
const superPower = new SuperPower();
```

&nbsp;
#### 2. Не нужно неинициализированной переменной задавать значение undefined, это значение присваивается автоматически.

> eslint: [`no-undef`](https://eslint.org/docs/rules/no-undef#top)

&nbsp;

❌ не надо так 👇
```javascript
let foo = undefined;
let bar = undefined;
```

&nbsp;

✅ надо так 👇
```javascript
let foo;
let bar;
```

&nbsp;
#### 3. Используйте let и const для объявления каждой переменной.

> eslint: [`one-var`](https://eslint.org/docs/rules/one-var#top)

&nbsp;

❌ не надо так 👇
```javascript
const items = getItems(),
    goSportsTeam = true,
    dragonball = 'z';
```
    
&nbsp;

✅ надо так 👇
```javascript
const items = getItems();
const goSportsTeam = true;
const dragonball = 'z';
```

&nbsp;
#### 4. Не используйте множественное присваивание. Такие конструкции создают неявные глобальные переменные.

> eslint: [`no-multi-assign`](https://eslint.org/docs/rules/no-multi-assign#top)

&nbsp;

❌ не надо так 👇
```javascript
(function example() {
  let a = b = c = 1;
}());

console.log(a); // ошибка ReferenceError
console.log(b); // 1
console.log(c); // 1
```

&nbsp;

✅ надо так 👇
```javascript
(function example() {
  let a = 1;
  let b = a;
  let c = a;
}());

console.log(a); // ошибка ReferenceError
console.log(b); // ошибка ReferenceError
console.log(c); // ошибка ReferenceError
```

&nbsp;
#### 5. Не переноси строку после оператора присваивания.

> eslint : [`operator-linebreak`](https://eslint.org/docs/rules/operator-linebreak#top)

&nbsp;
При нарушении правила [` max-len`](https://eslint.org/docs/rules/max-len#top) оборачивай присваивание в скобки.

&nbsp;

❌ не надо так 👇
```javascript
const foo =
  superLongLongLongLongLongLongLongLongFunctionName();


const foo
  = 'superLongLongLongLongLongLongLongLongString';
```

&nbsp;

✅ надо так 👇
```javascript
const foo = (
  superLongLongLongLongLongLongLongLongFunctionName()
);

const foo = 'superLongLongLongLongLongLongLongLongString';
```

&nbsp;
#### 6. Не объявляй неиспользуемые переменные.

> eslint: [`no-unused-vars`](https://eslint.org/docs/rules/no-unused-vars#top)

&nbsp;

❌ не надо так 👇
```javascript
let x = 0;
let y = 1; // Переменная не используется

function getX() {
    return x + 1;
}
```

&nbsp;

✅ надо так 👇
```javascript
let x = 0;

function getX() {
    return x + 1;
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Объявление переменных.

&nbsp;
#### 1. Если ты не переназначаешь переменную, то используй const для ее объявления. И наоборот.

> eslint: [`prefer-const`](https://eslint.org/docs/rules/prefer-const#top), [`no-const-assign`](https://eslint.org/docs/rules/no-const-assign#top)

&nbsp;

❌ не надо так 👇
```javascript
var a = 1;
var b = 2;

var count = 1;
if (true) {
  count += 1;
}
```

&nbsp;

✅ надо так 👇
```javascript
const a = 1;
const b = 2;

let count = 1;
if (true) {
  count += 1;
}
```

&nbsp;
#### 2. Не используй var. Используй let и const.

> eslint: [`no-var`](https://eslint.org/docs/rules/no-var#top)

&nbsp;

❌ не надо так 👇
```javascript
var x = "y";
var CONFIG = {};
```

&nbsp;

✅ надо так 👇
```javascript
let x = "y";
const CONFIG = {};
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Запятые.

&nbsp;
#### 1. Запятые не должны быть в начале строки.

> eslint: [`comma-style`](https://eslint.org/docs/rules/comma-style#top)

&nbsp;

❌ не надо так 👇
```javascript
const story = [
    once
  , upon
  , aTime
];
```

&nbsp;

✅ надо так 👇
```javascript
const story = [
  once,
  upon,
  aTime,
];
```

&nbsp;
#### 2. Ставь запятую после последнего свойства в объектах и массивах .Они делают git-diff более чистым.

> eslint: [`comma-dangle`](https://eslint.org/docs/rules/no-comma-dangle#top)

&nbsp;
git-diff без использования оконечной запятой
```javascript
onst hero = {
     firstName: 'Florence',
-    lastName: 'Nightingale'
+    lastName: 'Nightingale',
+    inventorOf: ['coxcomb chart', 'modern nursing']
};
```

git diff с использованием оконечной запятой
```javascript
const hero = {
     firstName: 'Florence',
     lastName: 'Nightingale',
+    inventorOf: ['coxcomb chart', 'modern nursing'],
};
```

&nbsp;

❌ не надо так 👇
```javascript
const hero = {
  firstName: 'Dana',
  lastName: 'Scully'
};
```

&nbsp;

✅ надо так 👇
```javascript
const hero = {
  firstName: 'Dana',
  lastName: 'Scully',
};

// Но учтите, что ставить запятую после “rest” элемента нельзя
function createHero(
  firstName,
  lastName,
  inventorOf,
  ...heroArgs
) {
  // does nothing
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Точка с запятой.

&nbsp;
#### 1. Всегда ставьте точку с запятой в конце выражения.

> eslint: [`semi`](https://eslint.org/docs/rules/semi#top)

&nbsp;

❌ не надо так 👇
```javascript
// Выбросит исключение
const luke = {}
const leia = {}
[luke, leia].forEach((jedi) => jedi.father = 'vader')

// Выбросит исключение
const reaction = "No! That’s impossible!"
(async function meanwhileOnTheFalcon() {
  // handle `leia`, `lando`, `chewie`, `r2`, `c3p0`
  // ...
}())

// Вернет `undefined` вместо корректной строки так return находится один в строке и ASI автоматически вставит точку с запятой именно туда!
function foo() {
  return
    'search your feelings, you know it to be foo'
}
```

&nbsp;

✅ надо так 👇
```javascript
const luke = {};
const leia = {};
[luke, leia].forEach((jedi) => {
  jedi.father = 'vader';
});

const reaction = "No! That’s impossible!";
(async function meanwhileOnTheFalcon() {
  // handle `leia`, `lando`, `chewie`, `r2`, `c3p0`
  // ...
}());

function foo() {
  return 'search your feelings, you know it to be foo';
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Блоки.

&nbsp;
#### 1. Используй фигурные скобки для всех многострочных блоков.

> eslint: [`nonblock-statement-body-position`](https://eslint.org/docs/rules/nonblock-statement-body-position#top)

&nbsp;

❌ не надо так 👇
```javascript
if (test)
  return false;

function foo() { return false; }
```

&nbsp;

✅ надо так 👇
```javascript
if (test) return false;

function bar() {
  return false;
}
```

&nbsp;
#### 2. При использовании конструкции if .. else располагайте else на одной строке со скобкой закрывающей блок if.

> eslint: [`brace-style`](https://eslint.org/docs/rules/brace-style#top)

&nbsp;

❌ не надо так 👇
```javascript
if (test) {
  thing1();
  thing2();
}
else {
  thing3();
}
```

&nbsp;

✅ надо так 👇
```javascript
if (test) {
  thing1();
  thing2();
} else {
  thing3();
}
```

&nbsp;
#### 3. Если в блоке if вы используете return, то последующее использование блока else не требуется. Условия, использующие return в обеих частях  if .. else if .. могут быть разбиты на два отдельных условия.

> eslint: [`no-else-return`](https://eslint.org/docs/rules/no-else-return#top)

&nbsp;

❌ не надо так 👇
```javascript
function foo() {
  if (x) {
    return x;
  } else {
    return y;
  }
}

function cats() {
  if (x) {
    return x;
  } else if (y) {
    return y;
  }
}

function dogs() {
  if (x) {
    return x;
  } else {
    if (y) {
      return y;
    }
  }
}
```

&nbsp;

✅ надо так 👇
```javascript
function foo() {
  if (x) {
    return x;
  }

  return y;
}

function cats() {
  if (x) {
    return x;
  }

  if (y) {
    return y;
  }
}

function dogs(x) {
  if (x) {
    if (z) {
      return y;
    }
  } else {
    return z;
  }
}
```

&nbsp;
#### 4. Не оставляй пустые блоки в рабочем коде .

> eslint: [`no-empty`](https://eslint.org/docs/rules/no-empty-label#top)

&nbsp;

❌ не надо так 👇
```javascript
if (foo) {
}

while (foo) {
}

switch(foo) {
}

try {
    doSomething();
} catch(ex) {

} finally {

}
```

&nbsp;

✅ надо так 👇
```javascript
if (foo) {
    // empty
}

while (foo) {
    /* empty */
}

try {
    doSomething();
} catch (ex) {
    // continue regardless of error
}

try {
    doSomething();
} finally {
    /* continue regardless of error */
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Объекты.

&nbsp;
#### 1. Для объявления объекта использую фигурные скобки.

> eslint: [`no-new-object`](https://eslint.org/docs/rules/no-new-object#top)

&nbsp;

❌ не надо так 👇
```javascript
const item = new Object();
```

&nbsp;

✅ надо так 👇
```javascript
const item = {};
```

&nbsp;
#### 2. Не дублируй названия ключей в объектах.

> eslint: [`no-dupe-keys`](https://eslint.org/docs/rules/no-dupe-keys#top)

&nbsp;

❌ не надо так 👇
```javascript
var foo = {
    bar: "baz",
    bar: "qux"
};

var foo = {
    "bar": "baz",
    bar: "qux"
};
```

&nbsp;

✅ надо так 👇
```javascript
var foo = {
    bar: "baz",
    quxx: "qux"
};
```

&nbsp;
#### 3. Не вызывай встроенные методы Object.prototype (такие как hasOwnProperty, propertyIsEnumerable, и isPrototypeOf) у самих объектов. Вместо этого вызывай их с помощью call передавая в него объект.

> eslint: [`no-prototype-builtins`](https://eslint.org/docs/rules/no-prototype-builtins#top)

&nbsp;

Такие встроенные методы могут быть переопределены в объекте и могут работать не так, как они описаны в Object.prototype

&nbsp;

❌ не надо так 👇
```javascript
object.hasOwnProperty(key);
```

&nbsp;

✅ надо так 👇
```javascript
Object.prototype.hasOwnProperty.call(object, key);

// еще лучше
const has = Object.prototype.hasOwnProperty;
console.log(has.call(object, key));
/* или*/
import has from 'has';
console.log(has(object, key));
```

&nbsp;
#### 4. Ставь один пробел после двоеточия в массиве, но не ставь пробел до двоеточия.

> eslint: [`key-spacing`](https://eslint.org/docs/rules/key-spacing#top)

&nbsp;

❌ не надо так 👇
```javascript
let obj = { "foo" : 42 };
```

&nbsp;

✅ надо так 👇
```javascript
let obj = { "foo": 42 };
```

&nbsp;
#### 5. Не форматируй свойства объектов так, чтобы они находились на одной линии.

> eslint: [`key-spacing`](https://eslint.org/docs/rules/key-spacing#top)

&nbsp;

❌ не надо так 👇
```javascript
let obj = {
  foobar: 42,
  bat:    2 * 2
};
```

&nbsp;

✅ надо так 👇
```javascript
let obj = {
  foobar: 42,
  bat: 2 * 2
};
```

&nbsp;
#### 6. В многострочных объектах после открывающей фигурной скобки свойства необходимо писать с новой строки. Закрывающую фигурную скобку следует также расположить на новой строке. Если объект однострочный, фигурные скобки должны находиться на одной строке.

> eslint: [`object-curly-newline`](https://eslint.org/docs/rules/object-curly-newline#top)

&nbsp;

❌ не надо так 👇
```javascript
let a = {foo: 1
};
let b = {
  foo: 1};
let c = {foo: 1, bar: 2
};
let d = {
  foo: 1, bar: 2};
let e = {foo: function() {
  dosomething();
}};

let {f
} = obj;
let {
  g} = obj;
let {h, i
} = obj;
let {
  j, k} = obj;
let {l = function() {
  dosomething();
}} = obj;
```

&nbsp;

✅ надо так 👇
```javascript
let a = {};
let b = {foo: 1};
let c = {
  foo: 1
};
let d = {
  foo: 1, bar: 2
};
let e = {
  foo: 1,
  bar: 2
};
let f = {foo: function() {dosomething();}};
let g = {
  foo: function() {
      dosomething();
  }
};

let {} = obj;
let {h} = obj;
let {i, j} = obj;
let {
  k, l
} = obj;
let {
  m,
  n
} = obj;
let {
  o,
  p
} = obj;
let {q = function() {dosomething();}} = obj;
let {
  r = function() {
      dosomething();
  }
} = obj;
```

&nbsp;
#### 7. В однострочных объектах не ставь пробел после открывающей фигурной скобки и перед закрывающей фигурной скобкой.

> eslint: [`object-curly-spacing`](https://eslint.org/docs/rules/object-curly-spacing#top)

&nbsp;

❌ не надо так 👇
```javascript
let obj = { 'foo': 'bar' };
let obj = {'foo': 'bar' };
let obj = { baz: {'foo': 'qux'}, bar};
let obj = {baz: { 'foo': 'qux'}, bar};
let {x } = y;
import { foo } from 'bar';
```

&nbsp;

✅ надо так 👇
```javascript
let obj = {'foo': 'bar'};
let obj = {'foo': {'bar': 'baz'}, 'qux': 'quxx'};
let obj = {
  'foo': 'bar'
};
let obj = {'foo': 'bar'
};
let obj = {
  'foo':'bar'};
let obj = {};
let {x} = y;
import {foo} from 'bar';
```

&nbsp;
#### 8. Пиши каждую пару ключ свойство с новой строки.

> eslint: [`object-property-newline`](https://eslint.org/docs/rules/object-property-newline#top)

&nbsp;

❌ не надо так 👇
```javascript
const obj0 = { foo: "foo", bar: "bar", baz: "baz" };

const obj1 = {
  foo: "foo", bar: "bar", baz: "baz"
};

const obj2 = {
  foo: "foo", bar: "bar",
  baz: "baz"
};

const obj3 = {
  [process.argv[3] ? "foo" : "bar"]: 0, baz: [
    1,
    2,
    4,
    8
  ]
};
```

&nbsp;

✅ надо так 👇
```javascript
const obj1 = {
  foo: "foo",
  bar: "bar",
  baz: "baz"
};


const user = process.argv[2];
const obj3 = {
  user,
  [process.argv[3] ? "foo" : "bar"]: 0,
  baz: [
    1,
    2,
    4,
    8
  ]
};
```

&nbsp;
#### 9. Для доступа к свойствам объекта используйте точечную запись.

> eslint: [`dot-notation`](https://eslint.org/docs/rules/dot-notation#top)

&nbsp;

❌ не надо так 👇 
```javascript
const luke = {
  jedi: true,
  age: 28,
};

const isJedi = luke['jedi'];
```

&nbsp;

✅ надо так 👇
```javascript
const isJedi = luke.jedi;
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Массивы.

&nbsp;
#### 1. Используй квадратные скобки [ ] для объявления массивов.

> eslint: [`no-array-constructor`](https://eslint.org/docs/rules/no-array-constructor#top)

&nbsp;

❌ не надо так 👇
```javascript
const items = new Array();
```

&nbsp;

✅ надо так 👇
```javascript
const items = [];
```

&nbsp;
#### 2. Не ставь пробел после открывающей квадратной скобки и перед закрывающей квадратной скобкой.

> eslint: [`array-bracket-spacing`](https://eslint.org/docs/rules/array-bracket-spacing#top)

&nbsp;

❌ не надо так 👇
```javascript
const arr = [ 'foo', 'bar' ];
const arr = ['foo', 'bar' ];
const arr = [ ['foo'], 'bar'];
const arr = [[ 'foo' ], 'bar'];
const arr = [ 'foo',
  'bar'
];
const [ x, y ] = z;
const [ x,y ] = z;
const [ x, ...y ] = z;
const [ ,,x, ] = z;
```

&nbsp;

✅ надо так 👇
```javascript
const arr = [];
const arr = ['foo', 'bar', 'baz'];
const arr = [['foo'], 'bar', 'baz'];
const arr = [
  'foo',
  'bar',
  'baz'
];
const arr = ['foo',
  'bar'
];
const arr = [
  'foo',
  'bar'];

const [x, y] = z;
const [x,y] = z;
const [x, ...y] = z;
const [,,x,] = z;
```

&nbsp;
#### 3. Не оставляй пусты места (“дыры”) в массивах.

> eslint: [`no-sparse-arrays`](https://eslint.org/docs/rules/no-sparse-arrays#top)

&nbsp;

❌ не надо так 👇
```javascript
let items = [,];
let colors = [ "red",, "blue" ];
```

&nbsp;

✅ надо так 👇
```javascript
let items = ["red", "blue"];

// можно ставить завершающую запятую после последнего элемента 
let colors = [ "red", "blue", ];
```

&nbsp;
#### 4. При использовании перебирающих методов массивов в коллбэке всегда используй return для возврата результата коллбэка. Если тебе не нужно использовать результат коллбэка, используй для перебора forEach.

> eslint: [`array-callback-return`](https://eslint.org/docs/rules/array-callback-return#top)

&nbsp;

❌ не надо так 👇
```javascript
inbox.filter((msg) => {
  const { subject, author } = msg;
  if (subject === 'Mockingbird') {
    return author === 'Harper Lee';
  } else {
    return false;
  }
});

[[0, 1], [2, 3], [4, 5]].reduce((acc, item, index) => {
  const flatten = acc.concat(item);
});
```


&nbsp;

✅ надо так 👇
```javascript
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});


[1, 2, 3].map((x) => x + 1);

[[0, 1], [2, 3], [4, 5]].reduce((acc, item, index) => {
  const flatten = acc.concat(item);
  return flatten;
});



inbox.filter((msg) => {
  const { subject, author } = msg;
  if (subject === 'Mockingbird') {
    return author === 'Harper Lee';
  }

  return false;
});
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Деструктуризация.

&nbsp;
#### 1. Используй деструктуризацию объектов и массивов при использовании нескольких свойств объекта или значений массива.

> eslint: [`prefer-destructuring`](https://eslint.org/docs/rules/prefer-destructuring#top)

&nbsp;

Это позволит сократить код.

&nbsp;

❌ не надо так 👇
```javascript
function getFullName(user) {
  const firstName = user.firstName;
  const lastName = user.lastName;

  return `${firstName} ${lastName}`;
}

const arr = [1, 2, 3, 4];
const first = arr[0];
const second = arr[1];
```

&nbsp;

✅ надо так 👇
```javascript
function getFullName(user) {
  const { firstName, lastName } = user;
  return `${firstName} ${lastName}`;
}

// еще лучше
function getFullName({ firstName, lastName }) {
  return `${firstName} ${lastName}`;
}

const arr = [1, 2, 3, 4];
const [first, second] = arr;
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Строки.

&nbsp;
#### 1. Используй одинарные кавычки ' '  для строк.

> eslint: [`quotes`](https://eslint.org/docs/rules/quotes#top)

&nbsp;

❌ не надо так 👇
```javascript
const name = "Capt. Janeway";
```

&nbsp;

✅ надо так 👇
```javascript
const name = 'Capt. Janeway';
```

&nbsp;
#### 2. Если в строке ты обращаешься к какой-либо переменной через ${variable} , то такая строка должна быть обернута в обратные кавычки ` ` .

> eslint: [`no-template-curly-in-string`](https://eslint.org/docs/rules/no-template-curly-in-string#top)

❌ не надо так 👇
```javascript
'Hello ${name}!';
'Time: ${12 * 60 * 60 * 1000}';
```

&nbsp;

✅ надо так 👇
```javascript
`Hello ${name}!`;
`Time: ${12 * 60 * 60 * 1000}`;

templateFunction`Hello ${name}`;
```

&nbsp;
#### 3. Используй шаблонные строки вместо конкатенации.

> eslint: [`prefer-template`](https://eslint.org/docs/rules/prefer-template#top), [`template-curly-spacing`](https://eslint.org/docs/rules/template-curly-spacing#top)

❌ не надо так 👇
```javascript
function sayHi(name) {
  return 'How are you, ' + name + '?';
}

function sayHi(name) {
  return ['How are you, ', name, '?'].join();
}

function sayHi(name) {
  return `How are you, ${ name }?`;
}
```

&nbsp;

✅ надо так 👇
```javascript
function sayHi(name) {
  return `How are you, ${name}?`;
}
```

&nbsp;
#### 4. Никогда не используй функцию eval().

> eslint: [`no-eval`](https://eslint.org/docs/rules/no-eval#top)

❌ не надо так 👇
```javascript
let obj = { x: "foo" },
  key = "x",
  value = eval("obj." + key);
```

&nbsp;

✅ надо так 👇
```javascript
let obj = { x: "foo" },
  key = "x",
  value = obj[key];
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Функции.

&nbsp;
#### 1. Используй function expressions (Функциональное Выражение) и присваивай ее переменной вместо function declarations (Объявление Функции).
Лучше: используй стрелочные функции.
> eslint: [`func-style`](https://eslint.org/docs/rules/func-style#top)

&nbsp;

Это позволит избежать ошибок, если функция будет вызвана до ее объявления.

&nbsp;

❌ не надо так 👇
```javascript
function foo() {
  // ...
}

const foo = function () {
  // ...
};
```

&nbsp;

✅ надо так 👇
```javascript
const short = function longUniqueMoreDescriptiveLexicalFoo() {
  // ...
};

//лучше
const foo = () => {};
```

&nbsp;
#### 2. Оборачивай в скобки немедленно вызывамые функции IIFE.

> eslint: [`wrap-iife`](https://eslint.org/docs/rules/wrap-iife#top)

&nbsp;

❌ не надо так 👇
```javascript
const x = function () { return { y: 1 };}(); 
const x = (function () { return { y: 1 };})(); 
```

&nbsp;

✅ надо так 👇
```javascript
const x = (function () { return { y: 1 };}())
```

&nbsp;
#### 3. Не объявляй функцию внутри цикла.

> eslint: [`no-loop-func`](https://eslint.org/docs/rules/no-loop-func#top)

&nbsp;

❌ не надо так 👇
```javascript
for (let i=10; i; i--) {
  (function() { return i; })();
}

while(i) {
  const a = function() { return i; };
  a();
}
```

&nbsp;

✅ надо так 👇
```javascript
const a = function() {};

for (let i=10; i; i--) {
  a();
}
```

&nbsp;
#### 4. Не используй argument для получения аргументов, вместо этого используй spread оператор.

> eslint: [`prefer-rest-params`](https://eslint.org/docs/rules/prefer-rest-params#top)

&nbsp;

❌ не надо так 👇
```javascript
function foo() {
  console.log(arguments);
}

function foo(action) {
  const args = Array.prototype.slice.call(arguments, 1);
  action.apply(null, args);
}

function foo(action) {
  const args = [].slice.call(arguments, 1);
  action.apply(null, args);
}
```


&nbsp;

✅ надо так 👇
```javascript
function foo(...args) {
    console.log(args);
}

function foo(action, ...args) {
    action.apply(null, args); 
}
```

&nbsp;
#### 5. Не используй new Function для создания функций.

> eslint: [`no-new-func`](https://eslint.org/docs/rules/no-new-func#top)

&nbsp;

❌ не надо так 👇
```javascript
const add = new Function('a', 'b', 'return a + b');
```

&nbsp;

✅ надо так 👇
```javascript
const subtract = Function('a', 'b', 'return a - b');
```

&nbsp;
#### 6. Всегда ставь один пробел перед () и перед {} в функциях.

> eslint: s[`pace-before-function-paren`](https://eslint.org/docs/rules/space-before-function-paren#top), [`space-before-blocks`](https://eslint.org/docs/rules/space-before-blocks#top)

&nbsp;

❌ не надо так 👇
```javascript
const f = function(){};
const g = function (){};
const h = function() {};
```

&nbsp;

✅ надо так 👇
```javascript
const x = function () {};
const y = function a() {};
```

&nbsp;
#### 7. Не переназначай аргументы функции.

> eslint: [`no-param-reassign`](https://eslint.org/docs/rules/no-param-reassign#top)

&nbsp;

❌ не надо так 👇
```javascript
function foo(bar) {
  bar = 13;
}

function foo(bar) {
  bar++;
}
```

&nbsp;

✅ надо так 👇
```javascript
function foo(bar) {
  let baz = bar;
}
```

&nbsp;
#### 8. Не дублируй названия аргументов в функциях.

> eslint: [`no-dupe-args`](https://eslint.org/docs/rules/no-dupe-args#top)

&nbsp;

❌ не надо так 👇
```javascript
function foo(a, b, a) {
  console.log("value of the second a:", a);
}

const bar = function (a, b, a) {
  console.log("value of the second a:", a);
};
```

&nbsp;

✅ надо так 👇
```javascript
function foo(a, b, c) {
  console.log(a, b, c);
}

const bar = function (a, b, c) {
  console.log(a, b, c);
};
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Стрелочные функции.

&nbsp;
#### 1. Используйте стрелочные функции для передачи коллбеков.
 
> eslint: [`prefer-arrow-callback`](https://eslint.org/docs/rules/prefer-arrow-callback#top), [`arrow-spacing`](https://eslint.org/docs/rules/arrow-spacing#top)

&nbsp;

❌ не надо так 👇
```javascript
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});
```

&nbsp;

✅ надо так 👇
```javascript
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```

&nbsp;
#### 2. Если тело функции состоит из одной операции, то можно опустить фигурные скобки и использовать неявный return.

> eslint: [`arrow-body-style`](https://eslint.org/docs/rules/arrow-body-style#top)

&nbsp;

❌ не надо так 👇
```javascript
[1, 2, 3].map((number) => {
  const nextNumber = number + 1;
  `A string containing the ${nextNumber}.`;
});
```

&nbsp;

✅ надо так 👇
```javascript
[1, 2, 3].map((number) => `A string containing the ${number + 1}.`);
```

&nbsp;
#### 3. При использовании стрелочной функции не оборачивай аргумент в скобки, если он один.

> eslint: [`arrow-parens`](https://eslint.org/docs/rules/arrow-parens#top)

&nbsp;

❌ не надо так 👇
```javascript
(a) => {}
```

&nbsp;

✅ надо так 👇
```javascript
a => {}
(a, b) => {}
```

&nbsp;
#### 4. Использование стрелочных функций совместно с операторами сравнения может запутать. Оборачивайте такие участки кода в скобки.

> eslint: [`no-confusing-arrow`](https://eslint.org/docs/rules/no-confusing-arrow#top)

&nbsp;

❌ не надо так 👇
```javascript
const itemHeight = (item) => item.height <= 256 ? item.largeSize : item.smallSize;
const itemHeight = (item) => item.height >= 256 ? item.largeSize : item.smallSize;
```

&nbsp;

✅ надо так 👇
```javascript
const itemHeight = (item) => (item.height <= 256 ? item.largeSize : item.smallSize);

const itemHeight = (item) => {
  const { height, largeSize, smallSize } = item;
  return height <= 256 ? largeSize : smallSize;
};
```

&nbsp;
#### 5. Не делай переносы строк сразу после стрелочной функции.

> eslint: [`implicit-arrow-linebreak`](https://eslint.org/docs/rules/implicit-arrow-linebreak#top)

&nbsp;

❌ не надо так 👇
```javascript
foo =>
  bar;

foo =>
  (bar);
```

&nbsp;

✅ надо так 👇
```javascript
foo => bar;
foo => (bar);
foo => (
   bar
)
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Классы и конструкторы.

&nbsp;
#### 1. Называй функции-конструкторы с большой буквы.

> eslint: [`new-cap`](https://eslint.org/docs/rules/new-cap#top)

&nbsp;

❌ не надо так 👇
```javascript
const colleague = new person();
const friend = new person.acquaintance();
```

&nbsp;

✅ надо так 👇
```javascript
const colleague = new Person();
const friend = new person.Acquaintance();
```

&nbsp;
#### 2. Не пиши пустой конструктор в классах. Классы имеют конструктор по умолчанию.

> eslint: [`no-useless-constructor`](https://eslint.org/docs/rules/no-useless-constructor)

&nbsp;

❌ не надо так 👇
```javascript
class Jedi {
  constructor() {}

  getName() {
    return this.name;
  }
}


class Rey extends Jedi {
  constructor(...args) {
    super(...args);
  }
}
```

&nbsp;

✅ надо так 👇
```javascript
class Rey extends Jedi {
  constructor(...args) {
    super(...args);
    this.name = 'Rey';
  }
}
```

&nbsp;
#### 3. Не дублируй методы в классах.

> eslint: [`no-dupe-class-members`](https://eslint.org/docs/rules/no-dupe-class-members#top)

&nbsp;

❌ не надо так 👇
```javascript
class Foo {
  bar() { return 1; }
  bar() { return 2; }
}
```

&nbsp;

✅ надо так 👇
```javascript
class Foo {
  bar() { return 1; }
}

class Foo {
  bar() { return 2; }
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Модули.

&nbsp;
#### 1. Используйте один импорт на модуль, не дублируй импорты.

> eslint: [`no-duplicate-imports`](https://eslint.org/docs/rules/no-duplicate-imports#top)

&nbsp;

❌ не надо так 👇
```javascript
import foo from 'foo';
// … другие import-ы … //
import { named1, named2 } from 'foo';
```

&nbsp;

✅ надо так 👇
```javascript
import foo, { named1, named2 } from 'foo';

// или так:
import foo, {
  named1,
  named2,
} from 'foo';
```

&nbsp;
#### 2. Не экспортируйте мутабельные переменные (которые могут измениться).

> eslint: [`import/no-mutable-exports`](https://github.com/benmosher/eslint-plugin-import/blob/master/docs/rules/no-mutable-exports.md)

&nbsp;

❌ не надо так 👇
```javascript
let foo = 3;
export { foo };
```

&nbsp;

✅ надо так 👇
```javascript
const foo = 3;
export { foo };
```

&nbsp;
#### 3. Все импорты должны объявляться в начале.

> eslint: [`import/first`](https://github.com/benmosher/eslint-plugin-import/blob/master/docs/rules/first.md)

&nbsp;

❌ не надо так 👇
```javascript
import foo from 'foo';
foo.init();

import bar from 'bar';
```

&nbsp;

✅ надо так 👇
```javascript
import foo from 'foo';
import bar from 'bar';

foo.init();
```

&nbsp;
#### 4. Многострочные импорты пиши в столбик.

> eslint: [`object-curly-newline`](https://eslint.org/docs/rules/object-curly-newline#top)

&nbsp;

❌ не надо так 👇
```javascript
import {longNameA, longNameB, longNameC, longNameD, longNameE} from 'path';
```

&nbsp;

✅ надо так 👇
```javascript
import {
  longNameA,
  longNameB,
  longNameC,
  longNameD,
  longNameE,
} from 'path';
```

&nbsp;
#### 5. Не указывайте расширения файлов при импорте.

> eslint [`import/extensions`](https://eslint.org/docs/rules/no-duplicate-imports#top)

&nbsp;

❌ не надо так 👇
```javascript
import foo from './foo.js';
import bar from './bar.jsx';
import baz from './baz/index.jsx';
```

&nbsp;

✅ надо так 👇
```javascript
import foo from './foo';
import bar from './bar';
import baz from './baz';
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Генераторы.

&nbsp;
#### 1. При использовании генераторов ставь один пробел перед * , но не ставь пробел после * .

> eslint: [`generator-star-spacing`](https://eslint.org/docs/rules/generator-star-spacing#top)

&nbsp;

❌ не надо так 👇
```javascript
function * generator() {}
let anonymous = function * () {};
let shorthand = {* generator() {} };
```

&nbsp;

✅ надо так 👇
```javascript
function *generator() {}
let anonymous = function *() {};
let shorthand = { *generator() {} };
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Операторы сравнения.

&nbsp;
#### 1. Используй === и !== (строгое сравнение ), вместо == и != (нестрогое сравнение).

> eslint: [`eqeqeq`](https://eslint.org/docs/rules/eqeqeq#top)

&nbsp;

Это считается хорошей практикой, т.к. ты избегаешь неявного преобразования типов данных.

&nbsp;

❌ не надо так 👇
```javascript
a == b 
foo == true
bananas != 1
value == undefined
```

&nbsp;

✅ надо так 👇
```javascript
typeof foo === 'undefined'
'hello' !== 'world'
0 === 0
true === true
foo === null
```

**Исключения:**
* сравнение двух литеральных значений:
* вызов typeof;
* сравнение с nullю

&nbsp;

❌ не надо так 👇
```javascript
a == b
foo == true
bananas != 1
value == undefined
```

&nbsp;

✅ надо так 👇
```javascript
typeof foo == 'undefined'
'hello' != 'world'
0 == 0
true == true
foo == null
```

&nbsp;
#### 2. Используйте фигурные скобки для создания блоков в case и default в конструкции switch...case , которые содержат лексические объявления (например, let, const, function и class).

> eslint: [`no-case-declarations`](https://eslint.org/docs/rules/no-case-declarations#top)

&nbsp;

Лексические объявления видны во всем блоке switch, но инициализируются только при срабатывании определенного case. Чтобы убедиться, что лексическое объявление применяется только к текущему case, необходимо использовать скобки.

&nbsp;

❌ не надо так 👇
```javascript
switch (foo) {
  case 1:
    let x = 1;
    break;
  case 2:
    const y = 2;
    break;
  case 3:
    function f() {
      // ...
    }
    break;
  default:
    class C {}
}
```

&nbsp;

✅ надо так 👇
```javascript
switch (foo) {
  case 1: {
    let x = 1;
    break;
  }
  case 2: {
    const y = 2;
    break;
  }
  case 3: {
    function f() {
      // ...
    }
    break;
  }
  case 4:
    bar();
    break;
  default: {
    class C {}
  }
}
```

&nbsp;
#### 3. Тернарные операторы не должны быть вложены.

> eslint: [`no-nested-ternary`](https://eslint.org/docs/rules/no-nested-ternary#top)

&nbsp;

❌ не надо так 👇
```javascript
const foo = maybe1 > maybe2
  ? "bar"
  : value1 > value2 ? "baz" : null;

const maybeNull = value1 > value2 ? 'baz' : null;
```

&nbsp;

✅ надо так 👇
```javascript
const foo = maybe1 > maybe2
  ? 'bar'
  : maybeNull;

//лучше так
const foo = maybe1 > maybe2 ? 'bar' : maybeNull;
```

&nbsp;
#### 4. Избегай ненужный тернарных операторов.

> eslint: [`no-unneeded-ternary`](https://eslint.org/docs/rules/no-unneeded-ternary#top)

&nbsp;

❌ не надо так 👇
```javascript
const foo = a ? a : b;
const bar = c ? true : false;
const baz = c ? false : true;
```

&nbsp;

✅ надо так 👇
```javascript
const foo = a || b;
const bar = !!c;
const baz = !c;
```

&nbsp;
#### 5. При смешивании операторов заключай их в скобки. Единственным исключением являются стандартные арифметические операторы: +, - и **, так как их приоритет широко понят. Рекомендуется  заключать в скобки / и *, потому что их приоритет может быть неоднозначным, когда они смешаны.

> eslint: [`no-mixed-operators`](https://eslint.org/docs/rules/no-mixed-operators#top)

&nbsp;

Это позволит избежать ошибок. Также код станет более читабельным

&nbsp;

❌ не надо так 👇
```javascript
const foo = a && b < 0 || c > 0 || d + 1 === 0;
const bar = a ** b - 5 % d;

if (a || b && c) {
  return d;
}

const bar = a + b / c * d;
```

&nbsp;

✅ надо так 👇
```javascript
const foo = (a && b < 0) || c > 0 || (d + 1 === 0);

const bar = a ** b - (5 % d);

if (a || (b && c)) {
  return d;
}

const bar = a + (b / c) * d;
```

&nbsp;
#### 6. Не повторяй условия в конструкции switch case.

> eslint: [`no-duplicate-case`](https://eslint.org/docs/rules/no-duplicate-case#top)

&nbsp;

❌ не надо так 👇
```javascript
let a = 1,
  one = 1;

switch (a) {
  case 1:
    break;
  case 2:
    break;
  case 1:         // дубликат
     break;
  default:
    break;
}
```

&nbsp;

✅ надо так 👇
```javascript
let a = 1,
  one = 1;
	
switch (a) {
  case 1:
    break;
  case 2:
    break;
  case 3:
    break;
  default:
    break;
}
```

&nbsp;
#### 7. Не используй в if, for, while, do...while или в тернарных выражениях в условиях постоянные выражения (литералы).

> eslint: [`no-constant-condition`](https://eslint.org/docs/rules/no-constant-condition#top)

&nbsp;

❌ не надо так 👇
```javascript
if (false) {
  doSomethingUnfinished();
}

do {
  doSomethingForever();
} while (x = -1);

let result = 0 ? a : b;
```

&nbsp;

✅ надо так 👇
```javascript
if (x === 0) {
  doSomething();
}

while (typeof x === "undefined") {
  doSomething();
}

do {
  doSomething();
} while (x);
	
let result = x !== 0 ? a : b;
```

&nbsp;
#### 8. В условных выражениях не используй оператор присваивания = в условии.

> eslint: [`no-cond-assign`](https://eslint.org/docs/rules/no-cond-assign#top)

&nbsp;

Если тебе все-таки необходимо сделать присваивание в условии, то оберни это присваивание в круглые скобки 

&nbsp;

❌ не надо так 👇
```javascript
let x;
if (x = 0) {
    var b = 1;
}
```

&nbsp;

✅ надо так 👇
```javascript
let x;
if (x === 0) {
 	   var b = 1;
}
```

&nbsp;
#### 9. В таких конструкция как if в условии, где результат выражения уже приведен к булевому типу (true/false) не приводи этот результат к булевому типу повторно с помощью двойного отрицания (!!) или Boolean().

> eslint: [`no-extra-boolean-cast`](https://eslint.org/docs/rules/no-extra-boolean-cast#top)

&nbsp;

❌ не надо так 👇
```javascript
let foo = !!!bar;

let foo = !!bar ? baz : bat;

let foo = Boolean(!!bar);

let foo = new Boolean(!!bar);

if (!!foo) {
    // ...
}

if (Boolean(foo)) {
    // ...
}

while (!!foo) {
    // ...
}

do {
    // ...
} while (Boolean(foo));

for (; !!foo; ) {
    // ...
}
```

&nbsp;

✅ надо так 👇
```javascript
let foo = !!bar;
let foo = Boolean(bar);

function foo() {
    return !!bar;
}

let foo = bar ? !!baz : !!bat;
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Комментарии.

&nbsp;
#### 1. В комментариях после // или /* должен быть пробел.

> eslint: [`spaced-comment`]()

&nbsp;

❌ не надо так 👇
```javascript
//is current tab
const active = true;

/**
 *make() returns a new element
 *based on the passed-in tag name
 */
function make(tag) {

  // ...

  return element;
}
```

&nbsp;

✅ надо так 👇
```javascript
// is current tab
const active = true;


/**
 * make() returns a new element
 * based on the passed-in tag name
 */
function make(tag) {

  // ...

  return element;
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Пробелы.

&nbsp;
#### 1. Используйте отступ в 2 пробела. Таб можно настроить на 2 пробела.

> eslint: [`indent`](https://eslint.org/docs/rules/indent#top)

&nbsp;

❌ не надо так 👇
```javascript
function foo() {
∙∙∙∙let name;
}


function bar() {
∙let name;
}
```

&nbsp;

✅ надо так 👇
```javascript
function baz() {
∙∙let name;
}
```

&nbsp;
#### 2. Ставь пробел перед и после ключевого слова. Если ключевое слово начинается с начала строки, пробел не нужен. Пробел не нужен после имени функции перед списком аргументов.

> eslint: [`keyword-spacing`](https://eslint.org/docs/rules/keyword-spacing#top)

&nbsp;

❌ не надо так 👇
```javascript
if(isJedi) {
  fight ();
}

function fight () {
  console.log ('Swooosh!');
}
```

&nbsp;

✅ надо так 👇
```javascript
if (isJedi) {
  fight();
}

function fight() {
  console.log('Swooosh!');
}
```

&nbsp;
#### 3. Ставь по одному пробелу вокруг операторов.

> eslint: [`space-infix-ops`](https://eslint.org/docs/rules/space-infix-ops#top)

&nbsp;

❌ не надо так 👇
```javascript
const x=y+5;
```

&nbsp;

✅ надо так 👇
```javascript
const x = y + 5;
```

&nbsp;
#### 4. Не оставляйте в блоках пустые строки.

> eslint: [`padded-blocks`](https://eslint.org/docs/rules/padded-blocks#top)

&nbsp;

❌ не надо так 👇
```javascript
function bar() {

  console.log(foo);

}


if (baz) {

  console.log(qux);
} else {
  console.log(foo);

}


class Foo {

  constructor(bar) {
    this.bar = bar;
  }
}
```

&nbsp;

✅ надо так 👇
```javascript
function bar() {
  console.log(foo);
}


if (baz) {
  console.log(qux);
} else {
  console.log(foo);
}
```

&nbsp;
#### 5. Не используйте несколько пустых строк для разделения кода.

> eslint: [`no-multiple-empty-lines`](https://eslint.org/docs/rules/no-multiple-empty-lines#top)

&nbsp;

❌ не надо так 👇
```javascript
class Person {
  constructor(fullName, email, birthday) {
    this.fullName = fullName;


    this.email = email;


    this.setAge(birthday);
  }


  setAge(birthday) {
    const today = new Date();


    const age = this.getAge(today, birthday);


    this.age = age;
  }
}
```

&nbsp;

✅ надо так 👇
```javascript
class Person {
  constructor(fullName, email, birthday) {
    this.fullName = fullName;
    this.email = email;
    this.setAge(birthday);
  }

  setAge(birthday) {
    const today = new Date();
    const age = getAge(today, birthday);
    this.age = age;
  }
}
```

&nbsp;
#### 6. Не ставь пробел после открывающей круглой скобки и перед закрывающей круглой скобкой.

> eslint: [`space-in-parens`](https://eslint.org/docs/rules/space-in-parens#top)

&nbsp;

❌ не надо так 👇
```javascript
function bar( foo ) {
  return foo;
}
```

&nbsp;

✅ надо так 👇
```javascript
function bar(foo) {
  return foo;
}
```

&nbsp;
#### 7. Избегайте использования строк кода длинной более 100 символов (включая пробелы).

> eslint: [`max-len`](https://eslint.org/docs/rules/max-len#top)

&nbsp;

❌ не надо так 👇
```javascript
const foo = jsonData && jsonData.foo && jsonData.foo.bar && jsonData.foo.bar.baz && jsonData.foo.bar.baz.quux && jsonData.foo.bar.baz.quux.xyzzy;

$.ajax({ method: 'POST', url: 'https://airbnb.com/', data: { name: 'John' } }).done(() => console.log('Congratulations!')).fail(() => console.log('You have failed this city.'));
```

&nbsp;

✅ надо так 👇
```javascript
const foo = jsonData
  && jsonData.foo
  && jsonData.foo.bar
  && jsonData.foo.bar.baz
  && jsonData.foo.bar.baz.quux
  && jsonData.foo.bar.baz.quux.xyzzy;

$.ajax({
  method: 'POST',
  url: 'https://airbnb.com/',
  data: { name: 'John' },
})
  .done(() => console.log('Congratulations!'))
  .fail(() => console.log('You have failed this city.'));
```

&nbsp;
#### 8. Ставь один пробел после открывающей фигурной скобки и перед закрывающей в теле функций, условий если они написаны в строку.

> eslint: [`block-spacing`](https://eslint.org/docs/rules/block-spacing#top)

&nbsp;

❌ не надо так 👇
```javascript
function foo() {return true;}
if (foo) { bar = 0;}
```

&nbsp;

✅ надо так 👇
```javascript
function foo() { return true; }
if (foo) { bar = 0; }
```

&nbsp;
#### 9. Не ставь пробел перед запятой, ставь пробел после запятой.

> eslint: [`comma-spacing`](https://eslint.org/docs/rules/comma-spacing#top)

&nbsp;

❌ не надо так 👇
```javascript
let foo = 1,bar = 2;
let arr = [1 , 2];
```

&nbsp;

✅ надо так 👇
```javascript
let foo = 1, bar = 2;
let arr = [1, 2];
```

&nbsp;
#### 10. При вызове функции не ставь пробел перед открывающей круглой скобкой.

> eslint: [`func-call-spacing`](https://eslint.org/docs/rules/func-call-spacing#top)

&nbsp;

❌ не надо так 👇
```javascript
func ();

func
();
```

&nbsp;

✅ надо так 👇
```javascript
func();
```

&nbsp;
#### 11. Не ставь пробелы, табы в конце строк.

> eslint: [`no-trailing-spaces`](https://eslint.org/docs/rules/no-trailing-spaces#top)

&nbsp;

❌ не надо так 👇
```javascript
let foo = 0;//•••••
let baz = 5;//••
//•••••
```

&nbsp;

✅ надо так 👇
```javascript
let foo = 0;
let baz = 5;
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Преобразование и приведение типов.

&nbsp;
#### 1. Не преобразовывай типы данных с помощью оператора new в String, Number и Boolean.

> eslint: [`no-new-wrappers`](https://eslint.org/docs/rules/no-new-wrappers#top)

&nbsp;

❌ не надо так 👇
```javascript
let stringObject = new String("Hello world");
let numberObject = new Number(33);
let booleanObject = new Boolean(false);
```

&nbsp;

✅ надо так 👇
```javascript
let text = String(someValue);
let num = Number(someValue);
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Методы отладки кода.

&nbsp;
#### 1. Не оставляй console.

> eslint: [`no-console`](https://eslint.org/docs/rules/no-console#top)

&nbsp;

Методы console хорошо подходят для отладки кода, однако их не должно быть в финальной версии кода.

&nbsp;

❌ не надо так 👇
```javascript
console.log("Log a debug level message.");
console.warn("Log a warn level message.");
console.error("Log an error level message.");
```

&nbsp;

✅ надо так 👇
```javascript
// Кастомный console
Console.log("Hello world!");
```

&nbsp;
#### 2. Рабочий код  не должен содержать debugger.

> eslint: [`no-debugger`](https://eslint.org/docs/rules/no-debugger#top)

❌ не надо так 👇
```javascript
function isTruthy(x) {
    debugger;
    return Boolean(x);
}
```

&nbsp;

✅ надо так 👇
```javascript
function isTruthy(x) {
    return Boolean(x); // set a breakpoint at this line
}
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

## Регулярные выражения.

&nbsp;
#### 1. Не используй управляющие символы(перенос строки, табуляция и другие) в регулярных выражениях.

> eslint: [`no-control-regex`](https://eslint.org/docs/rules/no-control-regex#top)

&nbsp;

❌ не надо так 👇
```javascript
let pattern1 = /\x1f/;
let pattern2 = new RegExp("\x1f");
```

&nbsp;

✅ надо так 👇
```javascript
let pattern1 = /\x20/;
let pattern2 = new RegExp("\x20");
```

&nbsp;
#### 2. При использовании квадратных скобок [ ] в регулярных выражениях, они не должны быть пустыми.

> eslint [`no-empty-character-class`](https://eslint.org/docs/rules/no-empty-character-class#top)

&nbsp;

❌ не надо так 👇
```javascript
/^abc[]/.test("abcdefg"); // false
"abcdefg".match(/^abc[]/); // null
```

&nbsp;

✅ надо так 👇
```javascript
/^abc/.test("abcdefg"); // true
"abcdefg".match(/^abc/); // ["abc"]

/^abc[a-z]/.test("abcdefg"); // true
"abcdefg".match(/^abc[a-z]/); // ["abcd"]
```

**[⬆ Вернуться к содержанию](#содержание)**

&nbsp;

&nbsp;

[![](https://webheroschool.ru/logo.png)](http://webheroschool.ru/)