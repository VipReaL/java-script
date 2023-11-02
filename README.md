# JavaScript

- **.write** - Команда write выводит на страницу текст, заданный в скобках:

```javascript
document.write('Семь раз отмерь - один отрежь.');
```

- **console.log()** - выводит сообщения в консоль:

```javascript
console.log('Семеро одного не ждут');
```

- **.length** - свойство length возвращает длину массива или строки:

```javascript
months.length; // 12

[].length; // 0 - пустой массив не содержит элементов, его длина 0
[1, 2, 3].length; // 3 — в массиве три элемента, его длина 3

console.log('АБВГДЕЁЖЗИЙКЛМНОПРСТУФХЦЧШЩЪЫЬЭЮЯ'.length);  // 33

const greekAlphabet = 'αβγδεζηθικλμνξοπρστυφχψω';
console.log(greekAlphabet.length); // 24
```

- **typeof** - Тип данных определяют оператором typeof:

```javascript
typeof 10; // "number"
typeof 'Hello World!'; // "string"
typeof true; // "boolean"
typeof undefined; // "undefined"
typeof 1234567890n // "bigint"
```

Работа typeof выглядит простой и понятной, но есть 3 случая, когда результат работы typeof неочевиден:

```javascript
typeof NaN; // "number". Да, "Not a Number" имеет тип данных "number".

typeof null; // "object". Это даже было признано официальным багом JavaScript. Его решили не исправлять, чтобы не сломать уже написанный код.

typeof function () {} // "function". Хоть такого типа и нет.
```

- **.isFinite** - В JavaScript две бесконечности — Infinity и -Infinity. Это самое большое и самое малое числовые значения в языке.  
Метод Number.isFinite проверяет код на «бесконечность». Если Number.isFinite передать на вход любую из бесконечностей, он вернёт false, конечное число — true:

```javascript
Number.isFinite(Infinity); // false
Number.isFinite(-Infinity); // false
Number.isFinite(1703); // true
```

- **.isNaN** - Забавное свойство NaN — оно не равно ничему, даже самому себе:

```javascript
console.log(NaN === NaN); // false
```

Из-за этого нельзя напрямую проверить, оказался ли результат вычисления не числом. Для решения этой проблемы создан метод Number.isNaN.  

Когда методу Number.isNaN передают как параметр какое-нибудь выражение, он отвечает true или false на вопрос: «Правда ли, что этот параметр — NaN?» 

```javascript
Number.isNaN(NaN); // true
Number.isNaN(0 / 0); // true
```

- **.querySelector** / **.querySelectorAll** - Оба метода принимают на вход строку — селектор нужного элемента.

```javascript
// Для выбора элемента по идентификатору
let container = document.querySelector('#container');

// По имени класса
let content = container.querySelector('.content');

/* Обратите внимание: мы ищем элементы не по всему
DOM-дереву, а внутри уже найденного элемента */
let contentItems = content.querySelectorAll('.content__item');
```

Главное преимущество этих методов — возможность искать элементы по сложным составным селекторам.

- **.getElementById** - получить элемент по идентификатору.

- **.getElementsByClassName** - получить элементы по имени класса.

- **.getElementsByTagName** - получить элементы по имени тега.

- **.getAttribute** - Метод getAttribute принимает на вход имя атрибута и возвращает его значение:

```javascript
/* получаем первый элемент в DOM, описанный тегом <img>,
т. е. первое изображение на странице */

let imageOnPage = document.querySelector('img');

imageOnPage.getAttribute('src'); // вернётся ссылка, записанная в атрибуте src первого изображения, которое вернул метод querySelector
```

Если у элемента нет атрибута, который мы запросили, или подобного атрибута не существует вовсе, вернётся специальное значение null. Если атрибут задан, но не подразумевает значения, например, disabled, мы получим пустую строку.

- **.hasAttribute** - убедиться в наличии атрибута удобно методом hasAttribute, который возвращает true, если атрибут задан, и false, если нет.

```javascript
bigAndRed.hasAttribute('onclick'); // true
bigAndRed.hasAttribute('несуществующий атрибут'); // false
bigAndRed.hasAttribute('disabled'); // true
```

- **.setAttribute** - метод setAttribute принимает на вход два аргумента: имя атрибута, значение которого мы хотим задать, и само значение:

```javascript
bigAndRed.setAttribute('lang', 'ru');
сonsole.log(bigAndRed.hasAttribute('lang')); //true
```

Оба аргумента — строки. Если передать значение другого типа, оно всё равно будет приведено к строке.

```javascript
disabledCheckbox.setAttribute('disabled', true); // Делаем чекбокс неактивным.
disabledCheckbox.setAttribute('disabled', 'Значение этого аргумента может быть любым');
disabledCheckbox.setAttribute('disabled', 'Мы передаём его, только чтобы метод отработал');
disabledCheckbox.setAttribute('disabled', false); // и даже этот вызов сработает
```

- **.removeAttribute** - метод removeAttribute удаляет атрибут у элемента:

```javascript
bigAndRed.hasAttribute('disabled'); // true
bigAndRed.removeAttribute('disabled'); // удаляем атрибут
bigAndRed.hasAttribute('disabled'); // false
```

- **.className** - у каждого элемента DOM есть свойство className. С его помощью можно прочитать или записать значение атрибута class:

```javascript
// выбираем элемент c классом 'princess'
let rank = document.querySelector('.princess');
console.log(rank.className); // princess

rank.className = 'queen'; // принцесса стала королевой, перезаписываем класс на 'queen'
console.log(rank.className); // queen
```

Если у элемента несколько классов, в свойстве className они будут разделены пробелами:

```html
<div class="her majesty queen">Елизавета</div>
```

```javascript
// выбираем элемент c классом 'queen'
let rank = document.querySelector('.queen');

console.log(rank.className); // her majesty queen
```

- **.classList** - Для управления атрибутом class удобнее пользоваться свойством classList. Оно содержит список всех классов элемента и обладает собственными методами, чтобы управлять этими классами.

```html
<!-- В именах классов записаны марки машин Её Величества -->
<div class="bentley rolls-royce">Королевский гараж</div>
```

```javascript
/* получаем список машин королевы в переменной,
обратившись к соответствующему элементу с селектором .bentley */

let garage = document.querySelector('.bentley');
console.log(`Гараж Её Величества: ${garage.classList}`); // Гараж Её Величества: bentley rolls-royce
```

- **.contains** - проверяет, есть ли у элемента класс, переданный как аргумент:

```javascript
let garage = document.querySelector('.bentley');

garage.classList.contains('bentley'); // true — bentley есть
garage.classList.contains('jaguar'); // false — а jaguar нет
```

- **.add** - добавляет элементу класс:

```javascript
// в королевский гараж поступил Ягуар
garage.classList.add('jaguar');

console.log(`Гараж Её Величества: ${garage.classList}`); // bentley rolls-royce jaguar
```

- **.remove** - удаляет у элемента класс, переданный как аргумент:

```javascript
garage.classList.remove('jaguar'); // Ягуар надоел

console.log(`Гараж Её Величества: ${garage.classList}`); // bentley rolls-royce
```

- **.toggle** - метод toggle работает как add, если у элемента класс отсутствует, и как remove — если присутствует. То есть метод переключает класс у элемента:

```html
<div class="bentley rolls-royce jaguar">Королевский гараж</div>
```

```javascript
// А если Ягуар есть, нужно от него избавиться  
garage.classList.toggle('jaguar');

console.log(`Гараж Её Величества: ${garage.classList}`); // bentley rolls-royce
```

- **.innerHTML** - Свойство innerHTML содержит в себе строку со всем наполнением элемента (в том числе и разметкой):

```javascript
document.body.innerHTML; // Если в документе нет разметки, вернёт пустую строку.
```

innerHTML позволяет не только получить значение свойства, но и перезаписать его:

```javascript
document.body.innerHTML = '<div>Добавим разметку</div>'; // Теперь на странице есть только один div. Если бы перед этим в документе была какая-либо разметка, она была бы заменена этим одним div.
```

Свойством innerHTML можно прочитать, изменить или удалить содержимое элемента:

```javascript
document.body.innerHTML = ''; // записав пустую строку, можно удалить всё содержимое элемента
```

- **.textContent** - позволяет получить или перезаписать текстовое содержимое элемента. Обратите внимание: вёрстка при этом не затрагивается.

```html
<p id="paragraph">Это текст внутри элемента.</p>
```

```javascript
let paragraph = document.getElementById('paragraph');
console.log(paragraph.textContent); // "Это текст внутри элемента."
paragraph.textContent = 'А это новый текст.'; // можно перезаписать содержимое
```

- **.innerText** - innerText отличается от textContent тем, что innerText возвращает только видимое текстовое содержимое. То есть innerText проигнорирует всё, что скрыто свойством display: none, а textContent — нет:

```html
<p id="paragraph">
  Это текст внутри элемента.
  <span style="display: none;">Невидимый текст.</span>
</p>
```

```javascript
let paragraph = document.getElementById('paragraph');

console.log(paragraph.innerText); // Это текст внутри элемента.
console.log(paragraph.textContent);
/* Это текст внутри элемента.
Невидимый текст. */
```

- **.addEventListener()** - Добавляет элементу действие, которое будет выполнено после срабатывания события. Например, на клик мышки или нажатие клавиши.

```javascript
const element = document.querySelector('button');

element.addEventListener('click', function (event) {
  console.log('Произошло событие', event.type);
});
```
ссылки: [DOKA](https://doka.guide/js/element-addeventlistener/ '.addEventListener()')

- Объект **event** - Методу addEventListener передают функцию-обработчик.  
У неё есть параметр — объект **event**. Он содержит информацию и о произошедшем событии, и о «кликнутом» элементе.  
Параметр event можно называть как угодно, но обычно используют evt или e.

```javascript
const button = document.querySelector('button');

button.addEventListener('click', function (event) { // event доступен как параметр
    console.log(event); // его можно использовать в теле обработчика
});
```

- **.target** - У объекта event есть свойство target. В нём хранится элемент, на котором сработало событие.  
Например, при клике на кнопку в свойство target попадает элемент этой кнопки:

```javascript
const button = document.querySelector('.button');

button.addEventListener('click', function (evt) {
  // в переменной eventTarget окажется элемент
  // button, на который мы кликнули

    const eventTarget = evt.target;
    eventTarget.setAttribute('disabled', true);
});
```

- **'submit'** - Слушатель который добавляется на элемент формы:

```html
<form class='form'>
    <input class='form__input' type='text'>
    <button class='form__button' type='submit'>
        Сохранить
    </button>
</form>
```
```javascript
let formElement = document.querySelector('.form');

formElement.addEventListener('submit', function () {
    console.log('Форма отправлена');
});
```
ссылки: [DOKA](https://doka.guide/js/event-submit/ 'submit')

- **.insertAdjacentHTML** - это способ добавлять элементы в родительский элемент не задевая других его потомков,и не перезагружая страницу в отличии от **.innerHTML**.

```javascript
element.insertAdjacentHTML('beforeend', '<div class="tiger"></div>');
```

Значение 'beforeend' указывает, что мы вставили HTML-код перед закрывающим тегом элемента. Возможны также значения:
* 'beforebegin' — вставка до открывающего тега;
* 'afterbegin' — вставка после открывающего тега;
* 'afterend' — вставка после закрывающего тега.

ссылки: [Яндекс.Практикум](https://practicum.yandex.ru/trainer/frontend-developer/lesson/f6e65260-1dd0-4c45-97a2-84441f8c5228/task/c75310ee-5e6b-410b-954f-85ad85cb3de6/ '.insertAdjacentHTML'), [learn.javascript](https://learn.javascript.ru/modifying-document), [Хабр](https://habr.com/ru/articles/235333/)

- **.insertAdjacentText** - свойство работает аналогичным образом, только вставляет текст, как и свойство textContent.

- **console.dir()** - отобразит список свойств и методов переданного объекта. Используйте его, если не знаете или не помните свойства элемента.

- **.value** - свойство оно есть у всех элементов input. Это свойство содержит значение поля ввода.

```javascript
let inputs = document.querySelectorAll('input');

console.log(inputs[0].value); // "Ты опоздала"
console.log(inputs[1].value); // "Игорь Тальков"
```

- **.checked** - Это свойство есть только у чекбоксов и радиокнопок. Оно содержит true, если чекбокс отмечен, и false — если нет.

- **.createElement** / **.createTextNode** - Перед тем как добавить элемент на страницу, его нужно создать. Это можно сделать с помощью методов  
document.createElement (принимает на вход имя тега, который нужно создать) и  
createTextNode (принимает на вход текст узла):

```javascript
// метод createElement принимает на вход имя тега в виде строки
const listItem = document.createElement('li');
const divElement = document.createElement('div');
const imageElement = document.createElement('img');

// метод createTextNode принимает строку — текст узла
const textItem = document.createTextNode('Hello, world');
```

## Добавление элементов на страницу

- **node.append(...nodes or strings)** — добавляет узлы или строки в конец node;
- **node.prepend(...nodes or strings)** — в начало node;
- **node.before(...nodes or strings)** — до node;
- **node.after(...nodes or strings)** — после node;
- **node.replaceWith(...nodes or strings)** — заменяет node заданными узлами или строками.

Все эти методы принимают на вход несколько параметров — элементов или текстовых блоков. Параметры перечисляются через запятую.

Чтобы *добавить элемент*, нужна ссылка на узел, относительно которого вставляется элемент. Для этого создайте элемент через createElement или используйте метод querySelector:

```javascript
// получаем элемент списка
const list = document.querySelector('.todo-list');
```

Кроме элемента, в который будем добавлять, нужно создать и элемент, который добавляем:

```javascript
const list = document.querySelector('.todo-list');

// создаём элемент списка
const listItem = document.createElement('li');
// добавляем в него текстовое содержимое
listItem.textContent = 'Полить цветы';
```

Методом append добавьте listItem в конец list:

```javascript
const list = document.querySelector('.todo-list');

const listItem = document.createElement('li');
listItem.textContent = 'Полить цветы';

// добавляем элемент списка в конец списка
list.append(listItem);
```

Метод append устроен так, что принимает на вход неограниченное количество аргументов. Если нужно добавить несколько элементов сразу, append это позволяет:

```javascript
const list = document.querySelector('.todo-list');

const listItem1 = document.createElement('li');
const listItem2 = document.createElement('li');
const listItem3 = document.createElement('li');

list.append(listItem1, listItem2, listItem3);
```

ссылки: [ЯндексПрактикум](https://practicum.yandex.ru/trainer/frontend-developer/lesson/10905c64-fb54-4219-9ae7-a79042adf3e0/task/30b27043-44cd-47d1-8fdb-94c074cb62bb/)

- **.remove()** - чтобы удалить элемент, нужно получить на него ссылку и вызвать метод remove:

```javascript
// выбрали элемент
const listItem = document.querySelector('li');

// удалили
listItem.remove();
```

- **.closest()** - возвращает ближайший родительский элемент с переданным селектором.

```html
<!-- Разметка элемента списка -->

<li class="todo__item">
  <span>Полить цветы</span>
  <button class="todo__item-button">Удалить</button>
<li>
```

```javascript
// выберите кнопку удаления
const deleteButton = document.querySelector('.todo__item-button');

// добавьте обработчик
deleteButton.addEventListener('click', function () {
  // ???
});
```

Когда мы вызываем **.closest()** на элементе кнопки удаления, то получаем искомый элемент списка, просто передав его класс:

```javascript
// выберем кнопку удаления
const deleteButton = document.querySelector('.todo__item-button');

// добавим обработчик
deleteButton.addEventListener('click', function () {
  const listItem = deleteButton.closest('.todo__item');
  listItem.remove();
});
```

- **.cloneNode()** - метод клоникования элемента. У метода один аргумент — true или false. Если хотите скопировать элемент вместе с содержимым, передайте true, без — false.  
Важно: обработчики событий элемента не скопируются. Их придётся добавить заново.

```javascript
// клонировать элемент вместе со всем его содержимым
const deepCopy = elem.cloneNode(true);

// клонирование без дочерних элементов
const shallowCopy = elem.cloneNode(false);
```

- тег **&lt;template&gt;** - заготовка вёрстки. Её используют для создания элементов. Если добавить template в HTML, содержимое тега не отобразится на сайте:

```html
<template id="user">
  <div class="user">
    <img class="user__avatar" alt="avatar">
    <p class="user__name"></p>
  </div>
</template>
```

Зато в JavaScript мы можем получить этот элемент методом querySelector:

```javascript
const userTemplate = document.querySelector('#user');
```

Чтобы получить содержимое template, нужно обратиться к его свойству content:

```javascript
const userTemplate = document.querySelector('#user').content;
```

Теперь этот элемент можно клонировать, наполнить содержимым и вставить в DOM.

```javascript
const userTemplate = document.querySelector('#user').content;
const usersOnline = document.querySelector('.users-online');

// клонируем содержимое тега template
const userElement = userTemplate.querySelector('.user').cloneNode(true);

// наполняем содержимым
userElement.querySelector('.user__avatar').src = 'tinyurl.com/v4pfzwy';
userElement.querySelector('.user__name').textContent = 'Дюк Корморант';

// отображаем на странице
usersOnline.append(userElement);
```