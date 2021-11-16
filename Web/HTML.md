# Basic HTML

## index.html

is the default main page

## HTML file structure

```html
<!DOCTYPE html>
<html>
    <head>
    </head>
    <body>
    </body>
</html>
```

## head tags

### title

the title of the page and the header that appear in the search engine

```html
<title>my website</title>
```

### meta tags

not shown in the browser used is search engine optimaziation

```html
<meta title="tag-type" content="tag content">
```

##### types

- **charset** the page encoding charcters

- **viewport**  scale the content to the width of the  device

- **description** the search engine decription

- **keyword** for search optimization

## body tages

### headings

```html
<h1>Title</h1>
<h2>Title</h2>
<h3>Title</h3>
<h4>Title</h4>
<h5>Title</h5>
<h6>Title</h6>
```

### paragraph

```html
<p>this a paragraph</p>
```

### text decoration

```html
<!--bold-->
<p> <strong> this</strong> a paragraph</p>
<!--italic-->
<p> <em> this</em> a paragraph</p>
<!--strike through-->
<p> <del> this</del> a paragraph</p>
```

### line break

```html
<br>
```

### line spirator

```html
<hr>
```

### links

```html
<a href="link">text</a>
```

##### attributes

- **target**: show how the link opens 

### image

```html
<img src="link-to-image" alt="text appear if image falid to load">
```

### list

```html
  <!-- Unordered lists -->
  <ul>
    <!-- list item -->
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
  </ul>

  <!-- Ordered Lists -->
  <ol>
  <!-- list item -->
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
  </ol>
```

### table

```html
<table>
<!-- table header -->
    <thead>
<!-- table row -->
      <tr>
<!-- header item -->
        <th>First Name</th>
        <th>Last Name</th>
        <th>Email</th>
      </tr>
    </thead>
<!-- table content -->
    <tbody>
<!-- table row -->
      <tr>
<!-- content item -->
        <td>John</td>
        <td>Doe</td>
        <td>jdoe@gmail.com</td>
      </tr>
      <tr>
        <td>Kate</td>
        <td>Smith</td>
        <td>kate@gmail.com</td>
      </tr>
    </tbody>
  </table>
```

### forms

```html
<!-- Text -->
    <div>
      <label for="name">Name</label><br>
      <input type="text" id="name" name="name" value="John Doe">
    </div>
    <!-- Email -->
    <div>
      <label for="email">Email</label><br>
      <input type="email" name="email" id="email" placeholder="Enter an email">
    </div>
    <!-- Textarea -->
    <div>
      <label for="message">Message</label><br>
      <textarea name="message" id="message" cols="50" rows="5"></textarea>
    </div>
    <!-- Select -->
    <div>
      <label for="sex">Sex</label>
      <select name="sex" id="sex">
        <option value="male">Male</option>
        <option value="female" selected>Female</option>
        <option value="other">Other</option>
      </select>
    </div>
    <!-- Number -->
    <div>
      <label for="age">Age</label><br>
      <input type="number" name="age" id="age">
    </div>
    <!-- Date -->
    <div>
      <label for="bithdate">Birthdate</label><br>
      <input type="date" name="birthdate" id="birthdate">
    </div>
    <!-- Radio -->
    <div>
      <label for="membership">Membership</label>
      <input type="radio" name="membership" value="simple" id="membership"> Simple
      <input type="radio" name="membership" value="standard" id="membership" checked> Standard
      <input type="radio" name="membership" value="super" id="membership"> Super
    </div>
    <!-- Checkbox -->
    <div>
      <label for="membership">I Like..</label>
      <input type="checkbox" name="likes" value="bike" id="likes"> Bike
      <input type="checkbox" name="likes" value="car" id="likes"> Car
      <input type="checkbox" name="likes" value="boat" id="likes"> Boat
    </div>
    <!-- Input submit -->
    <input type="submit" value="Submit">
    <!-- Button submit -->
    <!-- <button type="submit">Submit</button> -->
    <button type="reset">Reset</button>
```

### ids

```html
<div id="main-header">
    <h1>My Website</h1>
    <p>A site about me</p>
  </div>
```

### class

```html
<div class="card">
    <h1>My Website</h1>
    <p>A site about me</p>
  </div>
```

### html page sturcture

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>HTML5 Semantic Tags</title>
  </head>
  <body>
    <!-- Header -->
    <header id="header" class="card">
      <h1>My Website</h1>
      <p>Just Another Website</p>
    </header>

    <!-- Main Content (left) -->
    <main id="main">
      <!-- Section -->
      <section id="welcome" class="card">
        <h2>Welcome To Our Website</h2>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat
          cupiditate itaque possimus numquam corporis odit deserunt voluptas
          repellat ad ex earum magnam mollitia magni eaque nisi, excepturi nam
          temporibus! Sed. <br />
          <a href="#" class="text-center">Click For More</a>
        </p>
      </section>
      <!-- Section -->
      <section id="blog">
        <h2>From Our Blog</h2>
        <!-- Article One -->
        <article class="article">
          <h3>Article One</h3>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem
            veniam adipisci necessitatibus quia quisquam? Eligendi vitae quia
            totam accusantium officiis!
          </p>
        </article>
        <!-- Article Two -->
        <article class="article">
          <h3>Article Two</h3>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem
            veniam adipisci necessitatibus quia quisquam? Eligendi vitae quia
            totam accusantium officiis!
          </p>
        </article>
      </section>
    </main>

    <!-- Sidebar (right) -->
    <aside id="sidebar" class="card">
      <h3>Navigation</h3>
      <!-- Navigation -->
      <nav>
        <ul id="main-nav">
          <li><a href="index.html">Home</a></li>
          <li><a href="about.html">About</a></li>
          <li><a href="contact.html">Contact</a></li>
        </ul>
      </nav>
      <hr />
      <h3>Contact Us</h3>
      <ul>
        <li><strong>Address:</strong> 50 Main st, Boston MA</li>
        <li><strong>Phone:</strong> (555) 555-5555</li>
        <li><strong>Email:</strong> me@somethingcool.come</li>
      </ul>
    </aside>

    <div class="clr"></div>

    <!-- Footer -->
    <footer id="footer">
      <p class="text-center">Copyright © My Website 2019</p>
    </footer>
  </body>
</html>

```










