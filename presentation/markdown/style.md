<!-- .slide: data-background="#330033" -->
# style  <!-- .element: class="r-fit-text" -->


<!-- .slide: data-background="#330033" data-transition="fade-in fade-out" -->
![style](./assets/style-style.gif)


<!-- .slide: data-background="#330033" -->
## react .module.scss

Embeded in `CRA` and `Vite` out of the box.

The only thing you need to do is to name your style file with _.module_ like _button.module.scss_ and use it in component


<!-- .slide: data-background="#330033" -->
## advantages

- classes are scoped to component <!--  .element: class="fragment" data-fragment-index="1" -->
- easier maintenance (topic for discussion) <!--  .element: class="fragment" data-fragment-index="2" -->
- possibility to send classes to multiple components <!--  .element: class="fragment" data-fragment-index="3" -->


<!-- .slide: data-background="#330033" -->
## disadvantages

- modules do not accept props <!--  .element: class="fragment" data-fragment-index="5" -->
- used as objects - not so clear for the first time <!--  .element: class="fragment" data-fragment-index="6" -->


<!-- .slide: data-background="#330033" -->
## button.module.scss

```css[1,2,7|4-6]
.theClass {
  background-color: blue;

  &:hover {
    background-color: red;
  }
}
```


<!-- .slide: data-background="#330033" -->
## Button.ts

```js[1|4]
import btn from './button.module.scss'; 

const Button = () => (
  <button className={btn.theClass}>button</button>
)
```


<!-- .slide: data-background="#330033" -->
## output

```html
<button class="theClass__1a2b3">button</button>
```


<!-- .slide: data-background="#330033" -->
## more classes in one component

```js[4-6]
import btn from './button.module.scss'; 

const Button = () => (
  <button className={`${btn.theClass} ${btn.primary}`}>
    button
  </button>
)
```


<!-- .slide: data-background="#330033" -->
## more and more classes with some conditions

it starts to be messy - with help comes _clsx_ library. Every argument in a method if it is a string, it will be shown. We can also use an object to make it even more clearer.


<!-- .slide: data-background="#330033" data-transition="fade-in fade-out" -->
![style](./assets/style-messy.gif)


<!-- .slide: data-background="#330033" -->
```js[5-7|2|8|9|10|11]
import btn from './button.module.scss'; 
import clsx from 'clsx';

const Button = () => (
  <button className={`${btn.theClass} ${btn.primary}`}>
    button
  </button>
  // simplified for easier reading
  {clsx(btn.theClass, btn.primary, "big")}
  {clsx(true && btn.theClass, false && btn.primary)}
  {clsx({[btn.theClass]: true, [btn.primary]: false}, "big")}
)
```


<!-- .slide: data-background="#330033" -->
## questions

?
