## ES6 and ES5
**ES** stands for **ECMASript** which kind of is a language in the end. We say **Javascript** all the time but theoretically **ECMAScript** 
is the language and **Javascript** is more like a dialect which follows **ES**.

* ES5 is supported by all browsers but for ES6, you will need some **polyfills** or **transpilers** which basically takes your ES6 code
and rewrites in ES5 styled way
* [ES6 Compatibility Table](https://kangax.github.io/compat-table/es6/) | It will give you an idea on whether you need or not a compiler
(like **BabelJS**) to convert your ES6 Code to ES5.

## Syntax change and Extensions
* ```let``` and ```const``` are two new keywords added by ES6 to add block level scope.
* Hoisting with ```let``` and ```const``` does not work unlike the ```var```.

## Fat arrow functions
```javascript
function fn()
{
  console.log("hello!");
}
```
can be written in ES6 as
```javascript
var fn = () => {
  console.log("hello!");
 };
```
