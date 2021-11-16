# JavaScript

## Console Logs

**logging number, string, array, object**

```js
console.log("Hello World");
console.log([1, 2, 3, 4]);
console.log({ a: 1, b: 2 });
```

### log levels

```js
console.log("Hello World");
console.warn("This is a warning");
console.error("This is some error");
```

### log table

**log in table form for objects and arrays**

```js
console.table({ a: 1, b: 2 });
```

### Log time

**calculate executing time between time and time-end logs**

```js
// tag must be one for time and timeEnd
console.time("Hello");
console.log("Hello");
console.log("World");
console.timeEnd("Hello");
```

## Variables and Contestants

## Let

**block scope variables**

```js
let x = 5;
let s = "String";
```

### var

**function scope variables**

```js
let x = 5;
let s = "String";
```

### const

```js
const x = 5;
const s = "String";
```

## Data Types

### Primitive

```js
// String
const name = 'John Doe';
// Number
const age = 45;
// Boolean
const hasKids = true;
// Null
const car = null;
// Undefined
let test;
// Symbol
const sym = Symbol();
```

### Reference

```js
// Array
const hobbies = ['movies', 'music'];
// Object literal
const address = {
  city: 'Boston',
  state: 'MA'
}
```

### String format

```javascript
`Name: ${name}`
```

### Date

```js
const today = new Date();
let birthday = new Date('9-10-1981 11:25:00');
birthday = new Date('September 10 1981');
birthday = new Date('9/10/1981');

val = today.getMonth();
val = today.getDate();
val = today.getDay();
val = today.getFullYear();
val = today.getHours();
val = today.getMinutes();
val = today.getSeconds();
val = today.getMilliseconds();
val = today.getTime();

birthday.setMonth(2);
birthday.setDate(12);
birthday.setFullYear(1985);
birthday.setHours(3);
birthday.setMinutes(30);
birthday.setSeconds(25);
```

## Control statement

| operator | value                  |
|:--------:|:----------------------:|
| ==       | compare value only     |
| ===      | compare value and type |

## Functions

### Deceleration

```js
function greet(firstName = 'John', lastName = 'Doe'){
  return 'Hello ' + firstName + ' ' + lastName;
}
```

### Expression

```js
const square = function(x = 3){
  return x*x;
};
```

## Windows Object

```js
// Alert
alert('Hello World');

// Prompt
const input = prompt();
// Confirm
if(confirm('Are you sure')){
   console.log('YES');
} else {
   console.log('NO');
}

let val;

// Outter height and width
val = window.outerHeight;
val = window.outerWidth;

// Inner height and width
val = window.innerHeight;
val = window.innerWidth;

// Scroll points
val = window.scrollY;
val = window.scrollX;

// Location Object
val = window.location;
val = window.location.hostname;
val = window.location.port;
val = window.location.href;
val = window.location.search;

// Redirect
window.location.href = 'http://google.com';
// Reload
window.location.reload();

// History Object

window.history.go(-2);
val = window.history.length;

// Navigator Object
val = window.navigator;
val = window.navigator.appName;
val = window.navigator.appVersion;
val = window.navigator.userAgent;
val = window.navigator.platform;
val = window.navigator.vendor;
val = window.navigator.language;
```

## DOM - Domain Object Model

### properties

```js
// list of all html nodes as html collection
val = document.all;
// head tag
val = document.head;
// body tag
val = document.body;
// document type
val = document.doctype;
val = document.domain;
val = document.URL;
val = document.characterSet;
val = document.contentType;
// html collection of all forms tags
val = document.forms;
// html collection of all links <a> tags
val = document.links;
// html collection of all images
val = document.images;
// html collection of all scripts
val = document.scripts;
```

### html collection

interface represents a generic collection (array-like object) can access properties of the element from

```js
val = document.forms;
val = document.forms[0];
val = document.forms[0].id;
val = document.forms[0].method;
val = document.forms[0].action;
```

### One Element Select

#### By id

```js
document.getElementById('task-title');
```

#### By query selector element

css like method to select elements in only select first element that match the query

```js
document.querySelector('li').style.color = 'red';
document.querySelector('ul li').style.color = 'blue';
document.querySelector('li:last-child').style.color = 'red';
document.querySelector('li:nth-child(3)').style.color = 'yellow';
document.querySelector('li:nth-child(4)').textContent = 'Hello World';
document.querySelector('li:nth-child(odd)').style.background = '#ccc';
document.querySelector('li:nth-child(even)').style.background = '#f4f4f4'
```

### Multi element select

#### By query selector all

work like query selector but return all elements as node list

```js
 document.querySelectorAll('li.collection-item');
```

#### By Element class

return html collection of all element has a this class

```js
document.getElementsByClassName('collection-item');
```

#### By Tag name

return html collection of matched tag

```js
 document.getElementsByTagName('li');
```

### Element Tree traverse

### children

```js
const list = document.querySelector('ul.collection');
val = list.childNodes; // all nodes including text, comment, ..
val = list.children; // only elments
// First child
val = list.firstChild;
val = list.firstElementChild;
// Last child
val = list.lastChild;
val = list.lastElementChild;
// Count child elements
val = list.childElementCount;
```

### Parent

```js
val = list.parentNode;
val = list.parentElement;
```

### Sibling

```js
// Get next sibling
val = listItem.nextSibling;
val = listItem.nextElementSibling
// Get prev sibling
val = listItem.previousSibling;
val = listItem.previousElementSibling;
```

### HTML Collection vs Node List

### Node vs Element

**Node**: is any dom object 

| type | node                   |
|:----:|:----------------------:|
| 1    | Element                |
| 2    | Attribute (deprecated) |
| 3    | Text node              |
| 8    | Comment                |
| 9    | Document itself        |
| 10   | Doctype                |

**Element** : is one type on node that represent a html tag

### Create Element

#### using create element

```js
// Create element
const li  = document.createElement('li');
// Add class
li.className = 'collection-item';
// Add id
li.id = 'new-item';
// Append li as child to ul
document.querySelector('ul.collection').appendChild(li);
```

#### using inner html

```js
document.querySelector("ul.collection").innerHTML +=
  '<li class="collection-item"> Hello World <a href="#" class="delete-item secondary-content"> <i class="fa fa-remove"></i> </a> </li>';
```

### Remove Element

```js
cardAction.replaceChild(newHeading, oldHeading);
const list = document.querySelector('ul');
// Remove list item
lis[0].remove();
// Remove child element
list.removeChild(lis[3]);
```

### Element attributes

```js
val = link.getAttribute('href');
val = link.setAttribute('href', 'http://google.com');
link.setAttribute('title', 'Google');
val = link.hasAttribute('title');
link.removeAttribute('title');
```

### Element class

```js
val = link.className; // as one Strng 
val = link.classList; // as a list
link.classList.add('test');
link.classList.remove('test');
```

### Event

#### event attributes

```js
// Event target element
  val = e.target;
  // Event type
  val = e.type;
  // Timestamp
  val = e.timeStamp;
  // Coords event relative to the window
  val = e.clientY;
  val = e.clientX;
  // Coords event relative to the element
  val = e.offsetY;
  val = e.offsetX;
```

#### event add handler

```js
document.querySelector('.clear-tasks').addEventListener('click', onClick);
```

### Event types

- click event
- copy event
- cut event
- dblclick event
- DOMActivate event
- DOMMouseScroll event
- focus event
- fullscreenchange event
- keydown event
- keypress event
- keyup event
- mousedown event
- mouseenter event
- mouseleave event
- mousemove event
- mouseout event
- mouseover event
- mouseup event
- mousewheel event
- overflow event
- paste event
- scroll event
- select event
- show event
- touchcancel event
- touchend event
- touchmove event
- touchstart event
- wheel event

## Local Storage

Save key value pairs in the browser cache

```js
localStorage.setItem('name', 'John');
localStorage.removeItem('name');
```

### Session storage

as local storage but for only this session

```js
sessionStorage.setItem('name', 'John');
```

## OOP

### old way

##### Define Class

```js
function Person(name, dob) {
  this.name = name;
  this.age = age;
  this.birthday = new Date(dob);
  this.calculateAge = function(){
    const diff =  Date.now() - this.birthday.getTime();
    const ageDate = new Date(diff);
    return Math.abs(ageDate.getUTCFullYear() - 1970);
  }
}
```

##### create object

```js
const brad = new Person('Brad', '9-10-1981');
```

##### Define a method into prototype

```js
Person.prototype.calculateAge = function(){
  const diff =  Date.now() - this.birthday.getTime();
  const ageDate = new Date(diff);
  return Math.abs(ageDate.getUTCFullYear() - 1970);
}
```

##### inheritance

```js
function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

// Greeting
Person.prototype.greeting = function(){
  return `Hello there ${this.firstName} ${this.lastName}`;
}

const person1 = new Person('John', 'Doe');

// Customer constructor
function Customer(firstName, lastName, phone, membership) {
  Person.call(this, firstName, lastName);

  this.phone = phone;
  this.membership = membership;
}

// Inherit the Person prototype methods
Customer.prototype = Object.create(Person.prototype);
```

### ES6 Style

```js
class Person {
  constructor(firstName, lastName, dob) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.birthday = new Date(dob);
  }

  greeting() {
    return `Hello there ${this.firstName} ${this.lastName}`;
  }

  calculateAge() {
    const diff = Date.now() - this.birthday.getTime();
    const ageDate = new Date(diff);
    return Math.abs(ageDate.getUTCFullYear() - 1970);
  }

  getsMarried(newLastName) {
    this.lastName = newLastName;
  }

  static addNumbers(x, y) {
    return x + y;
  }
}
```

##### inheritance

```js
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  greeting() {
    return `Hello there ${this.firstName} ${this.lastName}`;
  }
}

class Customer extends Person {
  constructor(firstName, lastName, phone, membership) {
    super(firstName, lastName);

    this.phone = phone;
    this.membership = membership;
  }

  static getMembershipCost() {
    return 500;
  }
}
```

### object destruction

used to extract properties from an object without using dot notation

```js
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  greeting() {
    return `Hello there ${this.firstName} ${this.lastName}`;
  }
}
const person = new Person("hello", "world");
const {firstname, lastname} = person
```

## Asynchronous

### Ajax

```js
  // Create an XHR Object
  const xhr = new XMLHttpRequest();

  // OPEN
  xhr.open('GET', 'data.txt', true);

  // console.log('READYSTATE', xhr.readyState);

  // Optional - Used for spinners/loaders
  xhr.onprogress = function(){
    console.log('READYSTATE', xhr.readyState);
  }

  xhr.onload = function(){
    console.log('READYSTATE', xhr.readyState);
    if(this.status === 200) {
      // console.log(this.responseText);
      document.getElementById('output').innerHTML = `<h1>${this.responseText}</h1>`;
    }
  }

  xhr.onreadystatechange = function() {
    console.log('READYSTATE', xhr.readyState);
    if(this.status === 200 && this.readyState === 4){
      console.log(this.responseText);
    }
  }

  xhr.onerror = function() {
    console.log('Request error...');
  }

  xhr.send();
```

#### readyState Values

- 0: request not initialized 

- 1: server connection established

- 2: request received 

- 3: processing request 

- 4: request finished and response is ready

#### HTTP Statuses

- 200: "OK"

- 403: "Forbidden"

- 404: "Not Found"

### easy http Ajax Callback

```js
function easyHTTP() {
  this.http = new XMLHttpRequest();
}

// Make an HTTP GET Request
easyHTTP.prototype.get = function(url, callback) {
  this.http.open('GET', url, true);

  let self = this;
  this.http.onload = function() {
    if(self.http.status === 200) {
      callback(null, self.http.responseText);
    } else {
      callback('Error: ' + self.http.status);
    }
  }

  this.http.send();
}

// Make an HTTP POST Request
easyHTTP.prototype.post = function(url, data, callback) {
  this.http.open('POST', url, true);
  this.http.setRequestHeader('Content-type', 'application/json');

  let self = this;
  this.http.onload = function() {
    callback(null, self.http.responseText);
  }

  this.http.send(JSON.stringify(data));
}


// Make an HTTP PUT Request
easyHTTP.prototype.put = function(url, data, callback) {
  this.http.open('PUT', url, true);
  this.http.setRequestHeader('Content-type', 'application/json');

  let self = this;
  this.http.onload = function() {
    callback(null, self.http.responseText);
  }

  this.http.send(JSON.stringify(data));
}

// Make an HTTP DELETE Request
easyHTTP.prototype.delete = function(url, callback) {
  this.http.open('DELETE', url, true);

  let self = this;
  this.http.onload = function() {
    if(self.http.status === 200) {
      callback(null, 'Post Deleted');
    } else {
      callback('Error: '
 + self.http.status);
    }
  }

  this.http.send();
}
```

### Fetch API

```js
// Get Users
http.get('https://jsonplaceholder.typicode.com/users')
  .then(data => console.log(data))
  .catch(err => console.log(err));

// User Data
const data = {
  name: 'John Doe',
  username: 'johndoe',
  email: 'jdoe@gmail.com'
}

// Create User
http.post('https://jsonplaceholder.typicode.com/users', data)
  .then(data => console.log(data))
  .catch(err => console.log(err));

// Update Post
http.put('https://jsonplaceholder.typicode.com/users/2', data)
  .then(data => console.log(data))
  .catch(err => console.log(err));

// Delete User
http.delete('https://jsonplaceholder.typicode.com/users/2')
.then(data => console.log(data))
.catch(err => console.log(err));
```

### Easy HTTP with fetch

```js
/**
 * EasyHTTP Library
 * Library for making HTTP requests
 *
 * @version 2.0.0
 * @author  Brad Traversy
 * @license MIT
 *
 **/

 class EasyHTTP {

  // Make an HTTP GET Request 
  get(url) {
    return new Promise((resolve, reject) => {
      fetch(url)
      .then(res => res.json())
      .then(data => resolve(data))
      .catch(err => reject(err));
    });
  }

  // Make an HTTP POST Request
  post(url, data) {
    return new Promise((resolve, reject) => {
      fetch(url, {
        method: 'POST',
        headers: {
          'Content-type': 'application/json'
        },
        body: JSON.stringify(data)
      })
      .then(res => res.json())
      .then(data => resolve(data))
      .catch(err => reject(err));
    });
  }

   // Make an HTTP PUT Request
   put(url, data) {
    return new Promise((resolve, reject) => {
      fetch(url, {
        method: 'PUT',
        headers: {
          'Content-type': 'application/json'
        },
        body: JSON.stringify(data)
      })
      .then(res => res.json())
      .then(data => resolve(data))
      .catch(err => reject(err));
    });
  }

  // Make an HTTP DELETE Request
  delete(url) {
    return new Promise((resolve, reject) => {
      fetch(url, {
        method: 'DELETE',
        headers: {
          'Content-type': 'application/json'
        }
      })
      .then(res => res.json())
      .then(() => resolve('Resource Deleted...'))
      .catch(err => reject(err));
    });
  }

 }
```

### Async / Await

```js
async function myFunc() {
  const promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve('Hello'), 1000);
  });

  const error = false;

  if(!error){
    const res = await promise; // Wait until promise is resolved
    return res;
  } else {
    await Promise.reject(new Error('Something went wrong'));
  }
}

myFunc()
  .then(res => console.log(res))
  .catch(err => console.log(err));

async function getUsers() {
  // await response of the fetch call
  const response = await fetch('https://jsonplaceholder.typicode.com/users');

  // Only proceed once its resolved
  const data = await response.json();

  // only proceed once second promise is resolved
  return data;
}

getUsers().then(users => console.log(users));
```

### easy http with async / await

```js
/**
 * EasyHTTP Library
 * Library for making HTTP requests
 *
 * @version 3.0.0
 * @author  Brad Traversy
 * @license MIT
 *
 **/

 class EasyHTTP {
  // Make an HTTP GET Request 
  async get(url) {
    const response = await fetch(url);
    const resData = await response.json();
    return resData;
  }

  // Make an HTTP POST Request
  async post(url, data) {
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        'Content-type': 'application/json'
      },
      body: JSON.stringify(data)
    });

    const resData = await response.json();
    return resData;

  }

   // Make an HTTP PUT Request
   async put(url, data) {
    const response = await fetch(url, {
      method: 'PUT',
      headers: {
        'Content-type': 'application/json'
      },
      body: JSON.stringify(data)
    });

    const resData = await response.json();
    return resData;
  }

  // Make an HTTP DELETE Request
  async delete(url) {
    const response = await fetch(url, {
      method: 'DELETE',
      headers: {
        'Content-type': 'application/json'
      }
    });

    const resData = await 'Resource Deleted...';
    return resData;
  }

 }
```

## Error Handling

```js
try {
  // Produce a ReferenceError
  // myFunction();

  // Produce a TypeError
  // null.myFunction();

  // Will produce SyntaxError
  // eval('Hello World');

  // Will produce a URIError
  // decodeURIComponent('%');

  if(!user.name) {
    //throw 'User has no name';
    throw new SyntaxError('User has no name');
  }

} catch(e) {
  console.log(`User Error: ${e.message}`);
} finally {
  console.log('Finally runs reguardless of result...');
}
```

### error types

- ReferenceError
  - myFunction();
- TypeError
  - null.myFunction();
- SyntaxError
  - eval('Hello World');
- URIError
  - decodeURIComponent('%');

## Reguex

```js
let re;
// Literal Characters
re = /hello/;
re = /hello/i;  // i =  case insensitive

// Metacharacter Symbols
re = /^h/i;           // Must start with
re = / world$/i;     // Must ends with
re = /^hello$/i;     // Must begin and end with
re = /h.llo/i;      // Matches any ONE character
re = /h*llo/i;      // Matches any character 0 or more times
re = /gre?a?y/i;    // Optional character
re = /gre?a?y\?/i;    // Escape character 


// Brackets [] - Character Sets
re = /gr[ae]y/i;      // Must be an a or e
re = /[GF]ray/i;      // Must be a G or F
re = /[^GF]ray/i;      // Match anything except a G or F
re = /[A-Z]ray/;      // Match any uppercase letter
re = /[a-z]ray/;      // Match any lowercase letter
re = /[A-Za-z]ray/;   // Match any  letter
re = /[0-9][0-9]ray/;      // Match any digit

// Braces {} - Quantifiers
re = /Hel{2}o/i;      // Must occur exactly {m} amount of times
re = /Hel{2,4}o/i;      // Must occur exactly {m} amount of times
re = /Hel{2,}o/i;      // Must occur at least {m} times

// Paretheses () - Grouping
re = /^([0-9]x){3}$/

// Shorthand Character Classes
re = /\w/;    // Word character - alphanumeric or _
re = /\w+/;    // + = one or more
re = /\W/;    // Non-Word character
re = /\d/;    // Match any digit
re = /\d+/;    // Match any digit 0 or more times
re = /\D/;      // Match any Non-digit
re = /\s/;      // Match whitespace char
re = /\S/;      // Match non-whitespace char
re = /Hell\b/i; // Word boundary

// Assertions
re = /x(?=y)/;  // Match x only if followed by y
re = /x(?!y)/;  // Match x only if NOT followed by y
```

## Iterator

```js
function nameIterator(names) {
  let nextIndex = 0;

  return {
    next: function() {
      return nextIndex < names.length ?
      { value: names[nextIndex++], done: false } :
      { done: true }
    }
  }
}
```

### Access Iterator

```js
// Create an array of names
const namesArr = ['Jack', 'Jill', 'John'];
// Init iterator and pass in the names array
const names = nameIterator(namesArr);
```

## Generator

```js
function* createIds() {
  let index = 1;

  while(true) {
    yield index++;
  }
}

const gen = createIds();

console.log(gen.next().value);
console.log(gen.next().value);
```

## Patterns

### Module Pattern

```js
const UICtrl = (function() {
// private
  let text = 'Hello World';

  const changeText = function() {
    const element = document.querySelector('h1');
    element.textContent = text;
  }

  return {
// public
    callChangeText: function() {
      changeText();
      // console.log(text);
    }
  }
})();
```

### Singleton

```js
const Singleton = (function() {
  let instance;

  function createInstance() {
    const object = new Object({name:'Brad'});
    return object;
  }

  return {
    getInstance: function() {
      if(!instance){
        instance = createInstance();
      }
      return instance;
    }
  }
})();
```

### Factory

```js
function MemberFactory() {
  this.createMember = function(name, type) {
    let member;

    if(type === 'simple') {
      member = new SimpleMembership(name);
    } else if (type === 'standard') {
      member = new StandardMembership(name);
    } else if (type === 'super') {
      member = new SuperMembership(name);
    }

    member.type = type;

    member.define =  function() {
      console.log(`${this.name} (${this.type}): ${this.cost}`);
    }

    return member;
  }
}
```

### Observer

```js
class EventObserver {
  constructor() {
    this.observers = [];
  }

  subscribe(fn) {
    this.observers.push(fn);
    console.log(`You are now subscribed to ${fn.name}`);
  }

  unsubscribe(fn) {
     // Filter out from the list whatever matches the callback function. If there is no match, the callback gets to stay on the list. The filter returns a new list and reassigns the list of observers.
     this.observers = this.observers.filter(function(item){
      if(item !== fn) {
        return item;
      }
    });
    console.log(`You are now unsubscribed from ${fn.name}`);
  }

  fire() {
    this.observers.forEach(function(item) {
      item.call();
    });
  }
}
```

### State

```js
const PageState = function() {
  let currentState = new homeState(this);

  this.init = function() {
    this.change(new homeState);
  }

  this.change = function(state) {
    currentState = state
;
  }
};
```
