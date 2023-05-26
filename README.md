# Color Palette For Users

## Описание
  Color Palette For Users - позволяет добавить в ваш проект пользовательский
интерфейс для управления палитрой цветов (кастомизация темы сайта пользователем).
Главным образом библиотека работает с css переменными и классами Bootstrap,
но изменив настройки по умолчанию, вы можете работать со своими css переменными и классами.
### Демонстрация [перейти](https://alexnilovwork.github.io/WebpackAndBootstrap/)
### Инсталляция
Install with [npm](https://www.npmjs.com/package/color-palette-for-users): `npm install color-palette-for-users`
### Примеры
DOM
```html
<h4 id="changed1">Example #1 <h4>
<div id="example1"><div>
```
CSS
```css
@import "bootstrap/scss/bootstrap";
```
JS
```javascript
import BootstrapColorPalette from 'color-palette-for-users';
const myPalette = new BootstrapColorPalette({
	"selector" : "#example1"
});
```
### Настройки
```javascript
const myPalette = new BootstrapColorPalette({
  "selector" : string,
	"dev": boolean,
	"auto": boolean,
	"type": string || object,
	"func": function,
	"palette": array,
	"size": number
});
```
#### selector - Селектор DOM элемента для отображения палитры цветов (обязательный)

#### dev - в значение true отображает сообщения в консоли (по умолчанию true)
#### auto (по умолчанию true)
        *true добавляет палитру цветов сразу после объявления new BootstrapColorPalette
        *false добавляет палитру цветов c помощью метода init() тогда когда вам это нужно
#### type (по умолчанию var)
        *string: var | rgb | bg | text | btn | border | rgba | main
        *object:
Вариант 1:
```javascript
"type" : {
  "type" : "rgba",
  "title": "Opacity",
  "min": 0,
  "max": 1,
  value": "1"
}
```
Вариант 2
```javascript
"type": {
  "type": "main", //Обязательный
  "itemSize": {
    "min": 80, //px
    "max": 120 //px
   },
   "font": 14, //px
   "vars": [
    {
      "name" : "Body background",
      "color" : "--bs-body-bg-rgb",
      "value" : "255, 255, 255", // Если используете css переменные bootstrap то этот параметр не обязательный
      "type" : "rgb" // Не обязательный, может принимать два значения rgb | hex
     },
   ]
 }  
```
#### func
  Функция которая будет выполняться после выбора/изменения цвета пользователем.
В зависимости от type в функцию передаются разные аргументы:
var - строка вида --bs-body-bg (имя css переменной или как определено в palette),
rgb - строка вида --bs-body-bg-rgb (имя css переменной или как определено в palette),
bg - строка вида bg-dark (имя class или как определено в palette),
text - строка вида text-dark (имя class или как определено в palette),
btn - строка вида btn-dark (имя class или как определено в palette),
border - строка вида border-dark (имя class или как определено в palette),
rgba - объект вида
```javascript
{
  "color": "--bs-info-rgb",
  "opacity": 1
}
```
main - массив вида
```javascript
[
  {
    "name" : "Body background",
    "color" : "--bs-body-bg-rgb",
    "value" : "255, 255, 255",
    "type" : "rgb"
  }
]
```
#### palette (по умолчанию зависит от type)
Массив вида :
```javascript
[
  "--bs-blue",
  "--my-css-var"
]
```
или
```javascript
[
  "bg-blue",
  "my-class"
]
```
#### size (по умолчанию 24)
  Размер одной ячейки цвета в px

## Метод
Если вы не хотите чтобы палитра цветов отрисовывалась сразу после объявления new BootstrapColorPalette,
установите опцию "auto" : "false" и используйте метод init(), когда вам это будет нужно
## Лицензия MIT
