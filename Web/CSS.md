# CSS



[link](##selctors)

## Basic Structure

```css
selector {
    attribute: value
}
```

## Link CSS

1. **inline css**
   
   ```html
     <h1 style="color:red">Heading One</h1>
   ```

2. **internal css**
   
   ```html
   <!-- in header tag -->
   <style>
       /* Internal CSS */
       h2 {
         color: green;
       }
     </style>
   ```

3. **external css**
   
   ```html
   <!-- in header tag -->
   <link rel="stylesheet" href="css/style.css">
   <!-- only load this if max-width -->
   <link rel="stylesheet" media="screen and (max-width: 768px)" href="mobile.css">
   ```

### Selectors

### Elements

```css
body {
 background-color: #333;
}
```

### Class selectors

```css
.class-name {
    color: blue;
}
```

### ID

```css
#id {
   background-color: #f4f4f4;
}
```

### Multi-Selectors

```css
/* uses any number and type of selector */
#id1, #id2 {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 5px;
}
```

### Nested Selectors

```css
/* select every p tag inside id */
/* can be as deep as you want */
#id p {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 5px;
}
```

### State Selectors

```css
a:hover {
  color: coral;
}

a:visited {
  color: red;
}

a:active {
  color: red;
}
```

### Direct parent

```css
div > p {
    background-color: #ddd;
}
```

### Right after

```css
div + p {
    background-color: #ddd;
}
```

### Followed by in the same parent

```css
u ~ p {
    background-color: #ddd;
}
```

### Have attribute

```css
a[target] {
   background: #ddd;
}
```

### Attribute value

```css
input[type='email'] {
    width: 100%;
}
```

## nth Child

```css
li:first-child {
   background: red !important;
}

/* last-child */
li:last-child {
   background: blue;
}

/* Position 3 */
li:nth-child(3) {
   background: purple;
}

/* Every 3rd */
li:nth-child(3n + 0) {
   background: orange;
}

/* Every 3rd after 7 */
li:nth-child(3n + 7) {
   background: yellow;
}

/* odd */
li:nth-child(odd) {
   background: #ccc;
}

/* even */
li:nth-child(even) {
   background: #ddd;
}
```

### Before/After

```css
header::before {
}
header::after {
}
```

## Attributes

### Fonts

```css
font-family: Arial, Helvetica, sans-serif;
font-size: 18px;
line-height: 1.6em;    
font-weight:bold;    
font-style: italic;   
```

```html
<!-- to add external fonts add the following to the head tag-->
<link href="https://fonts.googleapis.com/css?family=Roboto" rel="stylesheet">
```

### Colors

```css
/* Color Name */
color:red;
/* RGB */
color: rgb(255,255,255);
/* Hex */
color: #f4f4f4;
```

### Background

```css
background-color:red;
background: #333;
background: url('./img/stars.jpg') no-repeat center center;
/* keep the backgroud as scroll */
background-attachment: fixed;
```

### Border

```css
border-width: 3px;
border-color: red;
border-style: solid;
/* shorthand for the above */
border: 3px solid red;
border-radius: 10px;
border-top: blue solid 3px;
border-down: blue solid 3px;
border-left: blue solid 3px;
border-right: blue solid 3px;
border-top-left-radius: 10px;
border-top-right-radius: 10px;
border-bottom-left-radius: 10px;
border-bottom-right-radius: 10px;
```

### Padding

```css
/* Padding on all sides */
padding: 20px;
/* Padding per side */
padding-top: 10px;
padding-right: 20px;
padding-bottom: 10px;
padding-left: 20px;
/* Padding shorthand = top, right, bottom, left */
padding: 10px 20px 10px 20px;
/* Padding shorthand = top/bottom left/right */
padding: 10px 20px;
```

### Margin

```css
/* Margin on all sides */
margin: 20px;
/* Margin per side */
margin-top: 10px;
margin-right: 20px;
margin-bottom: 10px;
margin-left: 20px;
/* Margin shorthand = top, right, bottom, left */
margin: 10px 20px 10px 20px;
/* Margin shorthand = top/bottom left/right */
margin: 10px 20px;
/* equal margin on left and right */
margin: auto;
```

### Float

```css
float: left;
float: right;
```

### Text

```css
text-align: left;
text-align: right;
text-align: center;
/* Text  spaced to line up its left and right edges */
text-align: justify;
text-decoration: none;
text-decoration-color: red;
text-decoration-line: underline;
text-decoration-style: solid;
text-decoration-thickness: 5px
```

### Display

```css
display: inline;
display: block;
display: inline-block
display: none
```

### Position

```css
position: relative;
/*postion in side the parent*/
position: absolute;
position: fixed;
position: sticky;
/* used in relative & absolute*/
top: 50px;
left: 50px;
bottom: 100px;
right: 100px;
```

### Media Query

```css
/* applied to min-width */
@media(min-width: 500){

}
/* applied between min-width and max-width */
@media(min-width: 501px) and (max-width: 768px) {
}
```

### Units

```css
/* size of 2 * parent element */
/* not recommended */
font-size: 2em;
/* size of 2 * root element */
font-size: 2rem;
```

### View Port

split width and height to 100 lines instead of resolution

```css
/* take halt of the height */
height: 50vh;
/* take halt of the width */
width: 50vw;
```

### Flex

```css
/* applied to the parent element that hold the flex items */
display: flex;
flex-direction: row;
 /* Cross axis align */
align-items: center;
/* Main axis align */
justify-content: center;
/* applied to item */
/* similar to layout_weight */
flex-grow: 1;
align-self: flex-start;
align-self: flex-end;
/* limit to shrink */
flex-shrink: 0;
```

### Grid

```css
/* applied to parent element */
/* enable grid */
display: grid;
/* grid columns */
grid-template-columns: 300px 300px 300px 300px; */
grid-template-columns: auto 300px 300px 300px; */
grid-template-columns: 1fr 3fr;
grid-template-columns: repeat(2, auto);
grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
/* grid row */
grid-template-rows: 1fr 3fr 1fr;
/* Set implicit rows */
grid-auto-rows: 3fr;
grid-gap: 1rem;
/* applied with grid-area*/
grid-template-areas:
          'header header header header'
          'content content content sidebar'
          'box-1 box-2 box-3 box-4'
          'footer footer footer footer';
/* on child element */
grid-column-start: 1;
grid-column-end: 4;
grid-row-start: 1;
grid-row-end: 3;
grid-column: 1 / span 3;
grid-area: content;
```

### Box Shadow

```css
/* offset-x | offset-y | color */
box-shadow: 10px 10px teal;
/* offset-x | offset-y | blur-radius | color */
box-shadow: 5px 5px 20px teal;
/* Negative values */
box-shadow: -5px -5px 20px teal;
/* offset-x | offset-y | blur-radius | spread-radius | color */
box-shadow: 3px 3px 10px 1px rgba(0, 0, 0, 0.3);
/* inset | offset-x | offset-y | color */
box-shadow: inset -3px -3px teal;
/* Multiple shadows */
box-shadow: 3px 3px teal, -3px -3px olive;
```

### Text Shadow

```css
/* h-shadow | v-shadow | color */
text-shadow: 0.2rem 0.2rem steelblue;
/* h-shadow | v-shadow | blur */
text-shadow: 0.4rem 0.3rem 0.7rem steelblue;
/* Negetive Values */
text-shadow: -0.4rem -0.3rem 0.7rem steelblue;
```

## Variables

### Definition

```css
:root {
    --container-max: 960px;
}
```

### Usage

```css
max-width: var(--container-max);
```

## Animation

### Key-frames

#### element attributes

```css
animation-name: animate2;
animation-duration: 2s;
animation-iteration-count: 1;
animation-fill-mode: forwards;
animation-delay: 2s;
animation-direction: alternate;
animation-timing-function: ease-in-out;
```

#### key-frames definition

```css
@keyframes animate1 {
   from {
      top: 0;
   }

   to {
      width: 600px;
      background-color: red;
      top: 200px;
   }
}
```

```css
@keyframes animate2 {
   0% {
      left: 0px;
      top: 0px;
      background-color: white;
      border-radius: 0 0 0 0;
   }
   25% {
      left: 300px;
      top: 0px;
      background-color: red;
      border-radius: 50% 0 0 0;
   }
   50% {
      left: 300px;
      top: 300px;
      background-color: green;
      border-radius: 50% 50% 0 0;
   }
   75% {
      left: 0px;
      top: 300px;
      background-color: blue;
      border-radius: 50% 50% 50% 0;
   }
   100% {
      left: 0px;
      top: 0px;
      background-color: white;
      border-radius: 50% 50% 50% 50%;
   }
}
```

### Transition

### element attributes

```css
transition-property: background, border-radius height width
transition-property: all;
transition-duration: 1s;
transition-timing-function: ease-in;
transition-delay: 2s, 4s;

/* Shorthand - property/duration/timing-function/delay */
transition: all 1s ease-in-out 1s;
```

#### transition attributes

- background-color
- background-position
- border-color
- border-width
- border-spacing
- bottom
- color
- font-size
- font-weight
- height left
- letter-spacing
- line-height
- margin
- max-height
- max-width
- min-height
- min-width
- opacity
- outline-color
- outline-offset
- outline-width
- padding right
- text-indent
- text-shadow
- top
- vertical-align
- visibility
- width
- word-spacing
- z-index

#### Transform

```css
/* Transform - rotate, scale, skew */
transform: rotate(25deg);
transform: skew(25deg);
transform: scale(2); 
```

### SASS

#### setup

* install node js

* npm install node-sass

* 

* add to scripts in package.json
  
  ```json
   "sass": "node-sass -w scss/ -o dist/css/ --recursive"
  ```

* npm run sass

#### variable

```scss
$secondary-color: skyblue;
/* usage */
background: $secondary-color;
```

#### partial

file that intended to be used as partial should start with _  to prevent sass from compiling it

```scss
@import 'variables';
```

#### Nesting

```scss
header {
  background: $dark-color;
  color: set-text-color($dark-color);
  padding: 1rem;

  h1 {
    text-align: center;
  }
}
.section {
  padding: 3rem;
 // instead of using .section-a 
  &-a {
    background: $primary-color;
    color: set-text-color($primary-color);
  }

  &-b {
    background: $secondary-color;
    color: set-text-color($secondary-color);
  }
}
```

#### inheritance

```scss
%btn-shared {
  display: inline-block;
  padding: 0.7rem 2rem;
  border: none;
  cursor: pointer;
  text-decoration: none;
  margin-top: 1rem;
}
// usage 
btn-light {
    @extend %btn-shared;
    background-color: $light-color;
    color: set-text-color($light-color);

    &:hover {
      @include transform(rotate(20deg));
      background-color: darken($light-color, 10%);
    }
}
```

#### Function

```scss
@function set-text-color($color) {
  @if (lightness($color) > 50) {
    @return #000;
  } @else {
    @return #fff;
  }
}
// usage
color: set-text-color($primary-color);
```

#### Mixin

```scss
@mixin transform($property) {
  --webkit-transform: $property;
  -ms-transform: $property;
  transform: $property;
}
// usage
@include transform(rotate(-20deg));
```
