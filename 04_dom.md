<a name="dom"></a>
# **The DOM**
---

Javascript can be run in many types of environment, can be run in the browser, in the server, in robots, the most popular is way to introduce is through the web browser.  
The browser turns your html into something that is called __DOM__ (_Document Object Model_)

  - **The Window:**  
  is the global scope in the browser, _the window_ is everything about the current open window, including the browser bar, the tabs, scrollbars.

    ```js
    window.location
    window.innerWidth
    ```

  - **The Document:**  
  Is responsible for everything from the opening ```<html>``` to the closing ```</html>``` including the ```<!DOCTYPE html>```

  - **The Navigator:**  
  Is in a higher level than the window.
  it gives you information about the device itself, like battery, webcam, audio access, gps coordinates, etc.  

<a name="selectElements"></a> 
## **Selecting elements**
When you need to be able to access the specific elemts on the page, like H2 tag (```<h2>```), a div tag (```<div>```), a buttton (```<button>```) or an image (```<img>```) you need to select hem first, and then you can add content, change content, listen for cliecks, you can do anything you want with it.
There are two main ways to select elements _QuerySelector_ and _QuerySelectorAll_ both take one argument and that is the CSS selector.

  - ### QuerySelector
    gives you the first matching element

    ```js
    const p = document.QuerySelect('p');
    ```

    QuerySelector will return the first ```<p>``` element on the page

  - ### QuerySelectorAll
    gives you a multiple elements

    ```js
    const p = document.QuerySelectAll('p');
    ```
    QuerySelectorALL will return all the ```<p>``` elements on the page

According to the following HTML we can grab divs, clases, or do parent-child selectors (like select an images that lives inside a class)
```html
<div class="items">
	<div class="item item1">
		<img src="http://img1.com" >
	</div>
	<div class="item">
		<img src="http://img2.link" >
	</div>
</div>
```
selecting a div with class of item:

```js
const item = document.QuerySelector('.item');
```
Look inside of an element that you already have selected (you can use QuerySelector on any other element):

```js
const item1 = document.QuerySelector('.item1');

const item1Image = item1.QeurySelector('img');
```

Looking for all the images that lives inside an element with class of item (parent-child select)


```js
const imgs = document.querySelectorAll('.item img');
```
Or we can select a div with the class of item

```js
const divItem = document.QuerySelector('div.item');
```
We can also have old to select elements from the DOM like:

- getElementById  
- getElementsByClassName  
- getElementsByTagName


<a name="elementPropertiesAndMethods"></a> 
## **Element properties and methods**

```html
<h2>I am a header</h2>
```

If we grab whatever element on the page like an ```<h2>``` we can see that this element is actually an object that has a lot of properties and methods, and we can see the properties by using ```console.dir```  

```js
const heading = document.QuerySelect('h2');
console.dir(heading)
```
one of these properties is _textContent_ and we can use them as _setters_ or _getters_

  - **getter:** is when you get the actual content of the element

    ```js
    console.log(heading.textContent);

    // the output is:  i am a header
    ```
  - **setter:** will update the content

    ```js
    heading.textContent = 'I am a new and updated header';
    ```
Similar to _textContent_ we have _innerText_ and some of the differences between both are that _textContent_ returns every element in the node, _innerText_ only shows human-readable elements, and also doest return hidden elements meaning that is aware of CSS styling:

let's pretend we have this HTML:

```html
  <h2>
    I am a heading.
    <style>
      h2 {
        color: red;			
      }
    </style>
  </h2>
```

so the different outputs from using textContent or innerText:

  - textConent:

    ```js
      const heading = document.querySelector('h2');
      console.log(heading.textContent);

      // the outout should be:
      I am a heading. 
      h2 {
          color: red; 
        }
    ```

  - innerText:
  
    ```js
      const heading = document.querySelector('h2');
      console.log(heading.innerText); 

      // the outout should be:
      I am a heading
    ```

We also have properties to work with like _insertAdjacentText_ it takes two arguments, the first one is the position, and second one is the element:

  - position:  
    - beforebegin: before the element itself
    - afterbegin: inside the element, before its first child
    - beforeend: inside the element, after its first chld
    - afterend: after the element itself  

Example:
we have the following HTML:

```html
<p class="pizza"> this is how many pizzas i ate! 🍕 </p>
```
and we want to put antoher pizza emoji at the end

```js
const pizzaList = document.QuerySelector('.pizza');

pizzaList.insertAdjacentText('beforeend', 🍕)
```
the result will be:

```html
<p class="pizza"> 
this is how many pizzas i ate! 🍕 
🍕
</p>
```

Differences between nodes and elements:

```html
<p class="pizza"> -----------------------> element and node
this is how many pizzas i ate! 🍕 -------> node
🍕 --------------------------------------> node
</p> ------------------------------------> element and node
```
  - Elements: are inside a tag  
    [Element methods and properties](https://developer.mozilla.org/en-US/docs/Web/API/Element)
  - Nodes: can be anything  
  [Nodes methods and properties](https://developer.mozilla.org/en-US/docs/Web/API/Node)



<br>

---
back to [Table of Content](tableOfContent.md)  
previous [The Tricky Bits](03_bits.md)  
next []()