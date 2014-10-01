# Menu Slider

A menu slider that moves the main content to the side and reveals a menu behind it.

![alt tag](https://i.imgflip.com/ck1pq.gif)

[Demo at jsfiddle.net](http://jsfiddle.net/marcusmolchany/hjb5cwh1/1/)

##Hamburger Button How-To
###HTML
```
<div id="menu-slider-hamburger">
  <div id="top-bar" class="menu-slider-hamburger-bar"></div>
  <div id="middle-bar" class="menu-slider-hamburger-bar"></div>
  <div id="bottom-bar" class="menu-slider-hamburger-bar"></div>
</div>
```
###CSS
```
#menu-slider-hamburger {
  height: 15px;
  width: 20px;
}

#menu-slider-hamburger:hover {
  cursor: pointer;
}

#menu-slider-hamburger > .menu-slider-hamburger-bar {
  margin-bottom: 3px;
  height: 3px;
  width: 20px;
  background-color: gray;
  opacity: 0.5;

  -webkit-transition: all 0.6s ease;
     -moz-transition: all 0.6s ease;
      -ms-transition: all 0.6s ease;
       -o-transition: all 0.6s ease;
          transition: all 0.6s ease;
}

#menu-slider-hamburger.open > #top-bar {
  -webkit-transform: translateY(6px) rotate(45deg);
     -moz-transform: translateY(6px) rotate(45deg);
      -ms-transform: translateY(6px) rotate(45deg);
       -o-transform: translateY(6px) rotate(45deg);
          transform: translateY(6px) rotate(45deg);
}

#menu-slider-hamburger.open > #middle-bar {
  -webkit-transform: rotateY(90deg);
     -moz-transform: rotateY(90deg);
      -ms-transform: rotateY(90deg);
       -o-transform: rotateY(90deg);
          transform: rotateY(90deg);
}

#menu-slider-hamburger.open > #bottom-bar {
  -webkit-transform: translateY(-6px) rotate(-45deg);
     -moz-transform: translateY(-6px) rotate(-45deg);
      -ms-transform: translateY(-6px) rotate(-45deg);
       -o-transform: translateY(-6px) rotate(-45deg);
          transform: translateY(-6px) rotate(-45deg);
}
```
###Javascript
```
function animateHamburger() {
  var hamburgerButton = this;
  hamburgerButton.className = hamburgerButton.classList.contains('open') ? 'closed':'open';
}

var hamburgerButton = document.getElementById('menu-slider-hamburger');
hamburgerButton.addEventListener('click', animateHamburger, false);
```

##Menu Slider How-To
###HTML
```
<div id="menu-wrapper" class="closed">
  <ul id="menu">
    <li class="selected"><a href="#">First Item</a></li>
    <li><a href="#">Second Item</a></li>
    <li><a href="#">Third Item</a></li>
    <li><a href="#">Fourth Item</a></li>
    <li><a href="#">Fifth Item</a></li>
  </ul>
</div>
<div id="main-content" class="closed">
 <h1>Main Content</h1>
 <p>Content</p>
</div>
```
###CSS
```
#menu-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: auto;

  background: gray;
}

#menu-wrapper.closed {
}

#menu-wrapper.open {
  display: block;
}

ul#menu {
  list-style-type: none;
  padding: 0 30px 0 0;
}

ul#menu li {
  border-bottom: 1px solid darkgray;
}

ul#menu li.selected {
  background-color: rgb(171, 171, 171);
}

ul#menu > li > a {
  display: block;

  padding: 10px 60px 10px 10px;

  text-decoration: none;
}

ul#menu > li > a:link {
  color: white;
}

ul#menu > li > a:hover {
  color: white;
}

ul#menu > li > a:visited {
  color: white;
}

#main-content {
  position: absolute;
  top: 0;
  height: 100%;
  width: auto;

  padding: 10px 10px 0 10px;

  background-color: white;

  box-shadow: -6px 0px 10px 1px #646464;

  -webkit-transition: all 0.5s ease;
     -moz-transition: all 0.5s ease;
      -ms-transition: all 0.5s ease;
       -o-transition: all 0.5s ease;
          transition: all 0.5s ease;
}

#main-content.closed {
  left: 0;
}

#main-content.open {
  left: 150px
}

#menu-slider-hamburger {
  height: 15px;
  width: 20px;
}
```
###Javascript
```
function slideMenu() {
  var mainContent = document.getElementById('main-content');
  var menuWrapper = document.getElementById('menu-wrapper');

  menuWrapper.className = menuWrapper.classList.contains('open') ? 'closed':'open';
  mainContent.className = mainContent.classList.contains('open') ? 'closed':'open';
}

function selectMenuItem() {
  var selectedMenuItem = this;

  selectedMenuItem.className = 'selected';

  var menu = document.getElementById('menu');
  var menuItems = menu.children;
  for (var i = 0; i < menuItems.length; i++) {
    if (menuItems[i] != this) {
      menuItems[i].className = '';
    }
  }
}

var menu = document.getElementById('menu');
var menuItems = menu.children;

for (var i = 0; i < menuItems.length; i++) {
  menuItems[i].addEventListener('click', selectMenuItem, false);
}
```

##License
MIT take what you want and give some back if you feel like it

##Sources used during development
* CSS  
  * http://stackoverflow.com/questions/13968486/move-div-with-css-transition  
  * http://css-tricks.com/snippets/css/better-helvetica/  
  * http://stackoverflow.com/questions/10463208/box-shadow-on-the-left-side-of-the-element-only  
* Javascript  
  * http://stackoverflow.com/questions/2739667/add-another-class-to-a-div-with-javascript  
  * http://stackoverflow.com/questions/5898656/test-if-an-element-contains-a-class  

Hamburger button inspired by Tumblr, Facebook Paper, Apple and other websites with similar animations.
