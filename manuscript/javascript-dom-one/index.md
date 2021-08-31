# JavaScript and the DOM: Part I

TODO summary

## Modern JavaScript Project

TODO VIDEO

what is Vite
why Vite

{title="Command Line",lang="text"}
~~~~~~~
npm init vite@latest javascript-modern -- --template vanilla
~~~~~~~

- after project setup

{title="Command Line",lang="text"}
~~~~~~~
cd javascript-modern
npm install
npm run dev
~~~~~~~

- open http://localhost:3000
- you see something in the browser which comes as default from Vite

### Exercises:

* Read more about [how we used to set up JavaScript manually in the old days](https://www.robinwieruch.de/javascript-project-setup).

## DOM API: JavaScript meets HTML

The DOM (Document Object Model) API is an interface to talk with JavaScript to HTML. In this section, we will explore this particular API for the browser step by step while we will continue using it throughout the rest of this book. Now, after you created your modern JavaScript project, open the *index.html* file in your editor. The content may be the same or similar depending on your current Vite version:

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="favicon.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite App</title>
  </head>
  <body>
    <div id="app"></div>
    <script type="module" src="/main.js"></script>
  </body>
</html>
~~~~~~~

The HTML file does not display much inside its `<body>` tag except for two crucial pieces which power your JavaScript application. First, there is a `<div>` tag which has an `id` attribut. The `id` attribute can be later used in JavaScript to reference this particular HTML element. And second, there is a `<script>` tag which loads a JavaScript file. Leads head over to this JavaScript file called *main.js* and check what it does:

{title="main.js",lang="javascript"}
~~~~~~~
import './style.css'

document.querySelector('#app').innerHTML = `
  <h1>Hello Vite!</h1>
  <a href="https://vitejs.dev/guide/features.html" target="_blank">Documentation</a>
`
~~~~~~~

The JavaScript file imports a *style.css* file. We will revisit the file and the `import` (and `export`) statement later. Furthermore, the JavaScript file uses the DOM API to manipulate the HTML. We will use the DOM API throughout the following sections to read from and write to the HTML. For now, let's examine the JavaScript code in our file.

The `document` object is a globally available built-in object for client-side JavaScript in the browser. This object represents your access point to the HTML of your website. In this case, it gives you access to the *index.html* file. By using methods on the `document` object, we can read information from the HTML or write information to the HTML. In this example, the code performs the latter by writing new inner HTML to the selected HTML element.

The `querySelector()` method is one modern DOM API method to select a specific HTML element (programmatically also referred to as **HTML node**). Because we are using `#app` with a `#`, we select a HTML element by its `id` attribute whereas the identifier on the HTML element is `app`. When you look back at yout *index.html* file, you can see that we have such HTML element. Selecting a HTML element by its `class` attribute, for example `querySelector('.app')` with a leading `.` is another common scenario.

Now, by having access to a HTML element after selecting it, we can read or write to it. As said, in this example, the code is writing to the HTML element by mutating its `innerHTML` property and assigning a JavaScript string to it. The string is not a mere string, but uses HTML tags such as `<h1>` and `<a>` to be used as structural elements. Change the HTML modification to the following and verify it in the browser after saving the file (and running the application with `npm run dev`):

{title="main.js",lang="javascript"}
~~~~~~~
document.querySelector("#app").innerHTML = `
# leanpub-start-insert
  <h1>Hello JavaScript!</h1>
# leanpub-end-insert
  <a href="https://vitejs.dev/guide/features.html" target="_blank">Documentation</a>
`;
~~~~~~~

In conclusion, the DOM API allows you to access HTML with JavaScript. While the Document Object Model (DOM) is a logical tree of nodes in memory, its API is the interface which allows us to interact with it (e.g. `querySelector()`). In a nutshell, the DOM API is the bridge between HTML and JavaScript. Where we can display static content by only using HTML, we can display dynamic content by leveraging the DOM API and JavaScript.

### Exercises:

* Read more about [the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction).

## HTML Crash Course (Optional)

HTML (HyperText Markup Language) is used to display structured content on a website. While **HTML tags** are used to give a website structure, the space within these HTML tags can be filled with information (e.g. `Hello JavaScript!`). HTML tags in combination with their content are called **HTML elements** (e.g. `<h1>Hello JavaScript!</h1>`). However, don't try to be too dogmatic about HTML element and HTML tag, because many developers use them interchangeably.

Now, as an exercise for this HTML crash course, let's recap the *index.html* file from our modern JavaScript project and extend it step by step:

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="favicon.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite App</title>
  </head>
  <body>
    <div id="app"></div>
    <script type="module" src="/main.js"></script>
  </body>
</html>
~~~~~~~

In this example, you see HTML in its natural existence as a tree of tags. The tree always starts with a `<html>` tag, followed by the nested `<head>` and `<body>`. While the `<head>` tag acts mostly as parent tag for website settings, for example the `<title>` tag which changes the browser tab's title of the website, the `<body>` tag acts as parent tag for all your content. If we would ignore JavaScript for a moment, we could use the `<body>` tag to display just structured yet static content in the browser:

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  ...
  <body>
# leanpub-start-insert
    <h1>Hello JavaScript</h1>
    <p>I like JS, but also HTML and CSS.</p>
    <p>
      This is a website written with
      <a href="https://developer.mozilla.org/en-US/docs/Web/HTML">HTML</a> ...
    </p>
# leanpub-end-insert
  </body>
</html>
~~~~~~~

Here we are using a `<h1>` tag for a primary headline, a `<p>` tag for a paragraph, and a `<a>` tag for an anchor (read: link) to another URL. HTML tags inside tags (e.g. using `<a>` inside `<p>`) are called **nested tags** (or **nested elements** when including to the paragraph's content). Not every HTML tag can be nested in another one (e.g. `<p>` should not be nested in another `<p>`, because it does not make sense semantically).

You can also see that HTML elements behave differently in there structural context: While each paragraph element (read: `<p>` tag) takes up horizontally more space, the anchor element (read: `<a>` tag) displays inline within its parent paragraph element. Hence the different naming: **inline element** (e.g. anchor element) and *block element* (e.g. paragraph element).

All tags we have used so far have a semantic meaning. The headline element (read: `<h1>` tag) is used for headlines, the paragraph element for text, and the anchor element for links navigating a user to another page of the website or to another website. Other HTML tags such as `<div>` (block element) and `<span>` (inline element) are used for layouting the elements without using any style (read: CSS) yet.

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  ...
  <body>
    ...
# leanpub-start-insert
    <div>
      <span>1</span>
      <span>2</span>
    </div>
    <div>
      <span>3</span>
      <span>4</span>
    </div>
# leanpub-end-insert
  </body>
</html>
~~~~~~~

What's goes beyond tags/elements here is the `<a>` tag's `href` attribute. In this case, the `href` attribute takes as value a relative or absolute URL, in this case an absolute URL, to navigate the user to a different website. **HTML attributes** can be used on HTML tags and there is a wide variety of them. Whereas some HTML attributes are semantically reserved for specific HTML tags (e.g. `href` for `<a>`), other HTML attributes are not tied to specific HTML elements (e.g. `class`, `id`).

Sometimes you will also encounter **self-closing tags**. For example, the `<input>` tag is used whenever you want to capture input from a user. If the input is text, then it should be specified with the input element's `type` attribute by using `text` as value. You may also want to have a button to perform an action with the content of your input elements (e.g. register a user, log in a user, send a contact form):

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  ...
  <body>
    ...
# leanpub-start-insert
    <div>
      <label>Username:</label>
      <input type="text" />
    </div>
    <div>
      <label>Password:</label>
      <input type="password" />
    </div>
    <button>Save</button>
# leanpub-end-insert
  </body>
</html>
~~~~~~~

HTML offers you all the elements that you need for giving a modern website its structure and native behavior. While most HTML elements have their semantically use cases (e.g. headlines, paragraphs, labels, inputs, buttons), other HTML elements are used for their layouting properties (e.g. div, span). In order to give HTML elements specific characteristics, you can use their wide variety of attributes.

### Exercise:

* Change the `<title>` tag's content and see it reflected in the browser.
* Use the `for` attribute on the `<label>` tag and a matching `id` attribute for the `<input>` tag for each pair of label/input elements. Afterward, by clicking ob a label element the input element will be focused. When using `id` attributes (or other attributes like `class`), always use kebab-case as best practice naming convention.
* Use the `<img>` tag with a `src` attribute to display an image in the browser.
* Question: What's the difference between HTML tag and HTML element?
  * Answer: While a HTML tag refers to the opening and closing entity (e.g. `<h1>` and `</h1>`) in angle brackets, a HTML element encompasses the opening tag, the closing tag, and the content in between (e.g. `<h1>Hello JavaScript</h1>`).
* Question: What other values for the `type` attribute does the `<input>` tag offer?
  * Answer: Other popular values are `number` and `tel`.

## CSS Crash Course (Optional)

## JavaScript's Import/Export Statements

- CSS
- JavaScript file

## Third-Party Dependencies

A programming language thrives with its ecosystem. In JavaScript land, the ecosystem with libraries and frameworks is mainly driven through Node.js and its packages (also called node packages, libraries, frameworks, third-party, dependencies, or as long term: third-party dependencies). Now even though Node.js is used for JavaScript in the backend, like we use it right now by just executing JavaScript on the command line and not inside a browser, the node package manager (npm) is available for JavaScript in the frontend (read: browser) too.

In this section, we will explore how to use the ecosystem to our benefit in our current setup. We will install one library via npm as third-party dependency to our project. Then we will import code (e.g. functions) from the library and use this code. Before we can install a library though, we have to initialize a project first. Go on the command line, stop your running project if neccessary, and initialize the project properly by typing:

{title="Command Line",lang="text"}
~~~~~~~
npm init -y
~~~~~~~

This setup has to be done only once per project and allows you to install packages afterward. Once the command went through successfully, you should see a *package.json* file in the same folder where all your libraries (here called dependencies) will get allocated:



https://lodash.com/docs/4.17.15

### Exercises: