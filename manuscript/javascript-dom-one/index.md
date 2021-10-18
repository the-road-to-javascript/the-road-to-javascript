# JavaScript and the DOM: Part I

Your JavaScript fundamentals knowledge has grown to a substantial level. However, all this time you have only seen the output on your command line -- which isn't bad per se, because as a developer you should feel comfortable with the command line -- however, seeing something in a browser is for many developers in their early stages a more rewarding feeling. Therefore, these next sections of the book will show you how to translate your JavaScript into the browser by using it in a HTML website. You will learn about HTML, CSS, and how to use JavaScript with its DOM API to manipulate anything you want in the browser.

## HTML Crash Course (Optional)

HTML (HyperText Markup Language) is a **markup language**, a fundamental building block of the web, which is used to display structured content on a website. While HTML just structures and displays content, other web technologies such as CSS or JavaScript are there to add style or to add behavior to your website.

Let's create an *index.html* file and fill it with the following content. After you created this file, you can open it in a browser to see its content displayed like a website:

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>HTML</title>
  </head>
  <body>
    <h1>Hello HTML</h1>
  </body>
</html>
~~~~~~~

Whereas **HTML tags** (e.g. `<h1>`) are used to give a website structure, the space within these HTML tags can be filled with information (e.g. `Hello HTML`). HTML tags in combination with their content are called **HTML elements** (e.g. `<h1>Hello HTML</h1>`). However, don't get too dogmatic about the naming (HTML element vs HTML tag), because many developers use these terms interchangeably and most of them will refer to it as HTML element if they are not adressing specifically the HTML tag's representation with angle brackets.

In the last example, you have seen HTML in its natural existence as a tree of tags. The tree always starts with a `<html>` tag, followed by the nested `<head>` and `<body>`. While the `<head>` tag acts mostly as parent tag for website settings, for example the `<title>` tag which changes the browser tab's title of the website, the `<body>` tag acts as parent tag for all your content displayed in the browser. We can use the `<body>` tag to display just structured yet static content in the browser:

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  ...
  <body>
    <h1>Hello HTML</h1>
# leanpub-start-insert
    <p>I like JS, but also HTML and CSS.</p>
    <p>
      This is a website written with
      <a href="https://developer.mozilla.org/en-US/docs/Web/HTML">HTML</a> ...
    </p>
# leanpub-end-insert
  </body>
</html>
~~~~~~~

Here we are using a `<h1>` tag for a primary headline, a `<p>` tag for a paragraph, and a `<a>` tag for an anchor (read: link) to another URL. HTML tags inside tags (e.g. using `<a>` inside `<p>`) are called **nested tags** (or **nested elements** when including the paragraph's content). Not every HTML tag can be nested in another one (e.g. `<p>` should not be nested in another `<p>`, because it does not make sense semantically to nest a paragraph into a paragraph).

You can also see that HTML elements behave differently in there structural context: While each paragraph element (read: `<p>` tag) is displayed one below the other, the anchor element (read: `<a>` tag) displays inline within its parent paragraph element. Hence the different types of HTML elements: **inline element** (e.g. anchor element) and *block element* (e.g. paragraph element).

All tags we have used so far have a semantic meaning. The headline element (read: `<h1>` tag) is used for headlines, the paragraph element for text, and the anchor element for links -- navigating a user to another page of the same website or to another website. Other HTML tags such as `<div>` (block element) and `<span>` (inline element) are used for layouting the elements without using any style (read: CSS) yet.

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

![](images/html-anatomy.png)

Sometimes you will also encounter **self-closing tags**. For example, the `<input>` tag is used whenever you want to capture input from a user. If the input is text, then it should be specified with the input element's `type` attribute by using `text` as value. You may also want to have a button to perform an action (e.g. register a user, log in a user, send a contact form):

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
    <button>Sign In</button>
# leanpub-end-insert
  </body>
</html>
~~~~~~~

HTML offers you all the elements that you need for giving a modern website its structure and native behavior. While most HTML elements have their semantically use cases (e.g. headlines, paragraphs, labels, inputs, buttons), other HTML elements are used for their layouting properties (e.g. div, span). In order to give HTML elements specific characteristics, you can use their wide variety of attributes.

### Exercise:

* Read more about [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML).
* Change the `<title>` tag's content and see it reflected in the browser.
* Use the `for` attribute on the `<label>` tag and a matching `id` attribute for the `<input>` tag with the same value for each pair of label/input elements. Afterward, by clicking ob a label element the input element will be focused. When using `id` attributes (or other attributes like `class`), always use kebab-case as best practice naming convention.
* Use the `<img>` tag with a `src` attribute to display an image in the browser.
* Question: What's the difference between HTML tag and HTML element?
  * Answer: While a HTML tag refers to the opening and closing entity (e.g. `<h1>` and `</h1>`) in angle brackets, a HTML element encompasses the opening tag, the closing tag, and the content in between (e.g. `<h1>Hello JavaScript</h1>`).
* Question: What other values for the `type` attribute does the `<input>` tag offer?
  * Answer: Other popular values are `number` and `tel`.

## CSS Crash Course (Optional)

While HTML is used to display structured content, Cascading Style Sheets (CSS) are used to style this content on a website. CSS is not a programming language (like JavaScript) nor a markup language (like HTML). Instead, CSS is a **style sheet language** which enables one to selectively style HTML elements.

We will start off with the following *index.html* with structured but not yet styled HTML elements. Same as before, you can open this HTML file in a browser to display it as a website:

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>CSS</title>
  </head>
  <body>
    <h1>Hello CSS</h1>
    <p class="look-at-me">I like JS, but also HTML and CSS.</p>
    <p>
      This is my first website written with
      <a href="https://developer.mozilla.org/en-US/docs/Web/HTML">HTML</a> and
      styled with
      <a href="https://developer.mozilla.org/en-US/docs/Web/CSS">CSS</a> ...
    </p>
    <a href="https://www.robinwieruch.de">Visit my Website</a>
  </body>
</html>
~~~~~~~

In order to include another file in a HTML file, we can use the `<link>` tag. For example, if we would want to load a CSS file which styles our HTML file, we can include it by referencing it:

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  <head>
# leanpub-start-insert
    <link href="/style.css" rel="stylesheet" />
# leanpub-end-insert
    <title>CSS</title>
  </head>
  <body>
    ...
  </body>
</html>
~~~~~~~

Now, create a CSS file with the name *style.css* next to your *index.html* file and give it the following content. The CSS styling should be picked up by the HTML file which is displayed in the browser:

{title="style.css",lang="css"}
~~~~~~~
h1 {
  color: red;
  font-weight: 100;
}
~~~~~~~

Here we are using CSS to colorize all headlines with the `<h1>` tag of our HTML in red and reduce the general font weight. All information that we have used to style the headlines is called **ruleset** (short: **rule**). However, we can dissect each individual part. The `h1` in the ruleset is called **selector**. In this case, the selector selects all `<h1>` tags in our HTML and applies the styling to them. It's possible to select more than one HTML tag with a comma separated list:

{title="style.css",lang="css"}
~~~~~~~
# leanpub-start-insert
h1, p {
# leanpub-end-insert
  color: red;
  font-weight: 100;
}
~~~~~~~

The last example shows how to select all `<h1>` and all `<p>` tags with an **element selector**. If we want to select a specific element though, we would use a **class selector** instead. In the HTML file we already specified a `class` attribute on a `<p>` tag with the attribute value `look-at-me`. In CSS, we can reference this specific class with a class selector by prefixing the selector with a `.`:

{title="style.css",lang="css"}
~~~~~~~
.look-at-me {
  color: red;
}
~~~~~~~

Alternatives to element selectors and class selectors are **id selectors** (prefixing the selector with a `#`) and **attribute selectors** which are rarely used though. Typically you would use `class` attributes on your HTML to style various parts of your application. Another more popular selector is the **pseudo-class selector** which selects an element in a specific state. In the following example, we change the color of the anchor elements whenever a user hovers over one:

{title="style.css",lang="css"}
~~~~~~~
a:hover {
  color: red;
}
~~~~~~~

Last but not least, it's also possible to use a combination of selectors for nested elements. In the following example, we select only all anchor elements within paragraph elements. All the other anchor tags should not be styled this way:

{title="style.css",lang="css"}
~~~~~~~
p a {
  color: red;
}
~~~~~~~

Let's finish up with the terminology after we went through the different kinds of selectors in CSS. A **declaration** in CSS consists of property and property value. In our example, the property is `color`, the property value is `red` (which comes with many other options), and the declaration is `color: red;`. Every declaration has a mandatory `:` which separates the property from the property value and a `;` to end a declaration.

![](images/css-anatomy.png)

In the end, you will likely encounter many different property and property value pairs, complex pseudo-selectors, and combinations of CSS classes. However, all the CSS basics illustrated in this section should give you a good start into this topic.

### Exercises:

* Read more about [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS).
* Create a `<div>` tag as parent element for some other elements (e.g. a combination of headline, paragraph, image) and style this block element with `margin: 10px;`, `border: 1px solid red;`, and `padding: 20px;`. Afterward, read more about [the box model in CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model).

## Linking Files in HTML

If you went through the previous crash courses for HTML and CSS, or if you were already quite familiar with HTML, you may already know how to link files (e.g. CSS files, JavaScript files, etc.) to a HTML file. In the previous section, we already linked a CSS file to our HTML file, so that we were able to style the HTML with CSS. In this section, let's go through an example for linking a JavaScript file to our HTML file, so that it gets executed once the HTML is displayed in a browser.

First, we will create a *index.html* file and fill it with the following content. After you have created this file, you can open it in a browser to see its content displayed like a website:

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript</title>
  </head>
  <body>
    <h1>Hello JavaScript</h1>
  </body>
</html>
~~~~~~~

Second, create a *index.js* file next to your HTML file and give it the following content:

{title="index.js",lang="javascript"}
~~~~~~~
console.log('Hello JavaScript');
~~~~~~~

And third, in contrast to linking a CSS file with a `<link>` tag and its `href` attribute, link the JavaScript file in the *index.html* file with a `<script>` tag and its `src` attribute. We are using the `async` attribute here to load the JavaScript file in paralell to the HTML file and to execute the JavaScript file as soon as possible (read: non-blocking):

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript</title>
# leanpub-start-insert
    <script src="./index.js" async></script>
# leanpub-end-insert
  </head>
  <body>
    <h1>Hello JavaScript</h1>
  </body>
</html>
~~~~~~~

We are using a relative path *./index.js* which always takes the current file as origin and looks for another file from there in relative perspective. In this case, it indicates that the file must be in the same folder (see exercises for more information about this topic). Since all files are top-level files in our project, we could also use an absolute path by just using *index.js*.

Finally, refresh (or open if you didn't open it already) the HTML file in your browser, see how the HTML markup shows up, and open up the browser's developer tools and its console to verify the logging of your JavaScript code. You made it! You linked successfully a JavaScript file in a HTML file and made it execute upon opening the HTML file in a browser.

### Exercises:

* The developer tools of your browser should stay open when developing websites, so try to get comfortable with them over time. Especially useful for beginners are the "Console" (where you see JavaScript loggings) and "Elements" (where you see all your HTML) tabs.
* Question: If the JavaScript file would not be at the top-level of the folder but moved into a dedicated folder *javascript/index.js*, how would we have to link the JavaScript file in our HTML file?
  * Answer: Either with *./javascript/index.js* as relative path or with *javascript/index.js* as absolute path.
* Question: If HTML and JavaScript files were in two dedicated folders, in this case *html/index.html* and *javascript/index.js*, how would we have to link the JavaScript file in our HTML file?
  * Answer: Either with *../javascript/index.js* as relative path or with *javascript/index.js* as absolute path.
* Read more [in-depth about the script element in HTML](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script).

## Modern JavaScript Project

TODO VIDEO

After we recaped how to write HTML/CSS and how to link files to each other, you may be wondering whether there is some kind of tool which helps us with the latter in a more sophisticated way. And indeed, in the modern JavaScript world you will rarely see developers linking files manually to each other. Therefore, we will use a [bleeding edge](https://dictionary.cambridge.org/dictionary/english/bleeding-edge) JavaScript tool called Vite which includes a frontend development server and a file bundler.

*Note: At the time of writing this book, Vite is becoming one of the status quo frontend build tools. However, JavaScript is a fast moving ecosystem, so Vite will not be the last frontend build tool that you will be using as professional JavaScript developer eventually.*

Somewhen at the beginning of this book, you have installed Node.js which allowed you to learn JavaScript in a Node.js environment by executing JavaScript files with just one command (here: `node index.js`) on the terminal without worrying about HTML and CSS. If you haven't set up Node.js yet, now is the time to do it. Now we will use the Node Package Manager (npm) which comes with our Node installation to set up our modern JavaScript project with Vite from the command line or integrated terminal of our IDE (e.g. VSCode) by executing the following command:

{title="Command Line",lang="text"}
~~~~~~~
npm init vite@latest javascript-modern -- --template vanilla
~~~~~~~

You see that we used a template called vanilla (meaning: vanilla JavaScript) here. Vite comes with many more templates for modern libraries and frameworks like React.js. Now, after a successful setup, use the following commands to navigate into the project, to install all of its dependencies (we will talk about dependencies later), and to run the development server:

{title="Command Line",lang="text"}
~~~~~~~
cd javascript-modern
npm install
npm run dev
~~~~~~~

Finally, open up the browser on the printed URL (usually `http://localhost:3000`) and see what a default Vite project displays there. Congratulations, you created a modern JavaScript project with Vite which bundles all the files for you and has a development server which you can just run from the command line.

### Exercises:

* Explore the *main.js* file of your project. It is responsible for displaying the content in the browser with the help of the *index.html* file. Try to understand what's happening here. We will explain everything in more detail later.
* Read more about [how we used to set up JavaScript manually in the old days](https://www.robinwieruch.de/javascript-project-setup).
* Read more about [Vite and how it's used to set up modern JavaScript projects](https://vitejs.dev/).

## DOM API: JavaScript meets HTML

The DOM (Document Object Model) API enables developers to talk with JavaScript to HTML. In this section, we will explore this particular API for the browser step by step while we will continue using it throughout the rest of this book. Coming back to our freshly created modern JavaScript project, open the *index.html* file in your editor/IDE. The content may be the same or similar (depending on your current build tool and its version):

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

The HTML file does not display much inside its `<body>` tag except for two crucial pieces which power your JavaScript application. First, there is a `<div>` tag which has an `id` attribut. The `id` attribute can be later used in JavaScript to reference this particular HTML element (see *main.js*). And second, there is a `<script>` tag which loads a JavaScript file called *main.js*. Head over to this JavaScript file and check its content:

{title="main.js",lang="javascript"}
~~~~~~~
import './style.css'

document.querySelector('#app').innerHTML = `
  <h1>Hello Vite!</h1>
  <a href="https://vitejs.dev/guide/features.html" target="_blank">Documentation</a>
`
~~~~~~~

The JavaScript file imports a *style.css* file which applies all its CSS to the HTML. Furthermore, the JavaScript file uses the DOM API to manipulate the HTML. We will use the DOM API throughout the following sections to read from and write to the HTML. For now, let's examine the JavaScript code in this file.

The `document` object is a globally available built-in object for client-side JavaScript in the browser. This object represents your programmatic access point to the HTML of your website. In this case, it gives you access to the *index.html* file, because the JavaScript file is loaded in this file. By using methods on the `document` object, we can read information from the HTML or write information to the HTML. In this example, the code performs the latter by writing new inner HTML to the selected HTML element.

The `querySelector()` method is a modern DOM API method to select a specific HTML element (programmatically also referred to as **HTML node**). Because we are using `#app` with a `#`, we select a HTML element by its `id` attribute whereas the attribute's value on the HTML element is `app`. When you look back at yout *index.html* file, where the JavaScript file is loaded, you can see that we have such HTML element. Selecting a HTML element by its `class` attribute, for example `querySelector('.app')` with a leading `.` is another common scenario.

Now, by having access to a HTML element after selecting it, we can read or write to it. As said, in this example, the code is writing to the HTML element by mutating its `innerHTML` property and assigning a JavaScript string to it. The string is not a mere string, but uses HTML tags such as `<h1>` and `<a>` to be used as structural elements. Change the HTML modification to the following and verify it in the browser after saving the file (and running the application with `npm run dev`):

{title="main.js",lang="javascript"}
~~~~~~~
document.querySelector("#app").innerHTML = `
# leanpub-start-insert
  <h1>Hello JavaScript!</h1>
  <p>I like JS, but also HTML and CSS.</p>
# leanpub-end-insert
`;
~~~~~~~

In conclusion, the DOM API allows you to access HTML with JavaScript. While the Document Object Model (DOM) is a logical tree of nodes in memory, its API is the interface which allows us to interact with it (e.g. `querySelector()`). In a nutshell, the DOM API is the bridge between HTML and JavaScript. While we can display *static content* by only using HTML, we can display *dynamic content* by leveraging the DOM API and JavaScript. We will use the DOM API to create dynamic HTML by leveraging our JavaScript knowledge throughout the rest of the book.

### Exercises:

* Read more about [the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction).
* Read more about [the built-in document object](https://developer.mozilla.org/en-US/docs/Web/API/Document).
* Read more about [the querySelector() method](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector).
* Read more about [the innerHTML property](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML).
* Question: When to use the `innerHTML` and `innerText` properties to change an HTML element's content?
  * Answer: While `innerHTML` allows a developer to mix text with HTML with formatting, `innerText` is used for only text without formatting. Another popular alternative to `innerText` is `textContent` which have only subtle differences.

## Import/Export Statements

When we worked with JavaScript, we used so far only one file to perform all of our work. However, this does not scale well for larger applications where you want to organise JavaScript code in multiple folders and files. In our new project, you may already have seen the following line which imports a CSS file in our JavaScript file:

{title="main.js",lang="javascript"}
~~~~~~~
import './style.css'

document.querySelector('#app').innerHTML = `
  <h1>Hello JavaScript!</h1>
  <p>I like JS, but also HTML and CSS.</p>
`
~~~~~~~

Instead of linking a file manually in our HTML file, like we have learned before, with a modern build tool it's possible to just import files (e.g. JavaScript, CSS, SVG) in JavaScript. So importing this CSS file will automatically apply the styles to all HTML elements.

But let's take a step back to our initial use case: Splitting up a JavaScript application into multiple files. Change the code in the *main.js* to the following content where we retrieve a headline by returning it from a arrow function expression:

{title="main.js",lang="javascript"}
~~~~~~~
const getHeadline = () => 'Hello JavaScript!';

document.querySelector('#app').innerHTML = `
  <h1>${getHeadline()}</h1>
`;
~~~~~~~

Now you might want to split up the code that interacts with the DOM from the JavaScript functions. Therefore, create a new file next to your *main.js* file called *utility.js*. In there, put the following code:

{title="utility.js",lang="javascript"}
~~~~~~~
const getHeadline = () => 'Hello JavaScript!';
~~~~~~~

In order to make this code available to other files, we need to export it:

{title="utility.js",lang="javascript"}
~~~~~~~
const getHeadline = () => 'Hello JavaScript!';

# leanpub-start-insert
export { getHeadline };
# leanpub-end-insert
~~~~~~~

If you want to have a shorter and more inline export, the following works too:

{title="utility.js",lang="javascript"}
~~~~~~~
export const getHeadline = () => 'Hello JavaScript!';
~~~~~~~

Between both exports there is a tradeoff: While the former export can be used to group all the exports at the bottom of a file, which makes it clearer for every developer who works on the code to see what gets exported by just scrolling to this place, the latter export makes the export more concise with the cavaet that a developer has to scan the file for export statements:

{title="utility.js",lang="javascript"}
~~~~~~~
// inline exports in a file

export const getHeadline = () => 'Hello JavaScript!';

export const getText = () => 'I like JS, but also HTML and CSS.';

// vs export at the end of a file

const getHeadline = () => 'Hello JavaScript!';

const getText = () => 'I like JS, but also HTML and CSS.';

export {
  getHeadline,
  getText,
};
~~~~~~~

Personally I like to group the exports at the end of the file whenever a file grows too much in size. However, when there are only a few things exported from a file, I like to keep them inline. Next, after we have talked about exports, let's discuss how to import a variable in the *main.js* file:

{title="main.js",lang="javascript"}
~~~~~~~
import { getHeadline } from './utility.js';

document.querySelector('#app').innerHTML = `
  <h1>${getHeadline()}</h1>
`;
~~~~~~~

If we want to import more than one variable, we can just add them in a comma separated list:

{title="main.js",lang="javascript"}
~~~~~~~
import { getHeadline, getText } from './utility.js';

document.querySelector('#app').innerHTML = `
  <h1>${getHeadline()}</h1>
  <p>${getText()}</p>
`;
~~~~~~~

It's important to note that we are using a relative path here. In the case of having folders and files nested in these folders, you would have to include the folder path when importing from a folder (e.g. *./folder/utility.js*) and you would have to include `../` instead of `./` when importing from a file that's up the folder hierarchy.

The imports and exports that we have used here are called **named imports and exports** which are the best practice when developing applications with JavaScript. However, you should also learn about the **default export and import** in the exercises. Anyway, import and export statements not only help us to split up our JavaScript code and organise it in folders and files, but also to import CSS and other assets (e.g. SVG) when using a modern build tool.

### Exercises:

* Read more about [import and export statements in JavaScript](https://www.robinwieruch.de/javascript-import-export).
* At the moment the `getHeadline()` function returns a static string where a function is not very much needed in the first place. Add an argument for the `getHeadline()` function, so that you can dynamically display whether you like JavaScript, HTML, or CSS.
* Add an argument for the `getText()` function which allows you to pass in an array of strings containing subjects you like (e.g. CSS, HTML like `['CSS', 'HTML']`). Then use the built-in array's `join()` method to concatenate the lists item to a text which gets returned eventually.

## Third-Party Dependencies

A programming language thrives with its ecosystem. In JavaScript land, the ecosystem with libraries and frameworks is mainly driven through Node.js and its **packages** (also called node packages, libraries, frameworks, third-parties, dependencies, or as long term: third-party dependencies). Even though Node.js is used for JavaScript in the backend, the Node Package Manager (npm) is available for JavaScript in the frontend (read: browser) too.

In this section, we will explore how to use the ecosystem to our benefit in our current setup. We will install one library via npm as a **third-party dependency** to our project. Then we will import utilities (mostly functions) from the library them.

First of all, we can install a new package via npm to our project. Since we created the project with a modern build tool, it knows about npm and knows where to put the installed package. So on the command line, type the following command to install a popular library called Lodash:

{title="Command Line",lang="text"}
~~~~~~~
npm install lodash
~~~~~~~

Afterward, start the application again with `npm run dev`. After the successful installation of Lodash, let's use one of Lodash's functions to explore this library and to learn how to use a library. We will start with the following code in the *main.js* file:

{title="main.js",lang="javascript"}
~~~~~~~
const headline = 'Hello JavaScript!';
const text = 'I like JS, but also HTML and CSS.';

document.querySelector('#app').innerHTML = `
  <h1>${headline}</h1>
  <p>${text}</p>
`;
~~~~~~~

Now, since we have installed Lodash, we can import code from Lodash. It works the same way as importing code from another file from within our project. This time do not point to another file though, but to Lodash as installed package:

{title="main.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
import { kebabCase, camelCase } from 'lodash';
# leanpub-end-insert

const headline = 'Hello JavaScript!';
const text = 'I like JS, but also HTML and CSS.';

document.querySelector('#app').innerHTML = `
# leanpub-start-insert
  <h1>${kebabCase(headline)}</h1>
  <p>${camelCase(text)}</p>
# leanpub-end-insert
`;
~~~~~~~

Once you display the website in a browser, you should see how Lodash's `kebabCase()` and `camelCase()` alter both strings. These functions are not available in native JavaScript, so libraries like Lodash give us these functionalities without implementing them ourselves.

After you have learned how to import code from file and from packages, we will continue with learning JavaScript in combination with HTML by using the DOM API. Throughout the rest of the book, we will apply all of our fundamental JavaScript learnings in a web application which is displayed on a browser with the help of HTML.

### Exercises:

* Read more about [Lodash's functions](https://lodash.com/).
  * Try other functions from Lodash that work on strings, numbers, and arrays.
* Explore the *package.json* file which lists all the dependencies of your JavaScript project.
* Question: Earlier when you set up the project, you used `npm install` before running the project with the development server. What happens when entering `npm install`?
  * Answer: When running `npm install` on the command line, all `dependencies` and `devDependencies` from the *package.json* get installed. The installation of all the packages ends up in the *node_modules* folder from where it can be later imported in your JavaScript project.

## Selecting HTML Elements

We have learned how JavaScript and HTML play together by using the DOM API. We will explore this API more in this and the coming sections by applying our fundamental JavaScript learnings. In the previous sections, we have only selected one HTML element by its identifier. When we look again at our *index.html* file, we see a `<div>` with an `id` attribute. This `id` attribute is used in the *main.js* file to reference this HTML element. Now we will exchange the *index.html* file content with the following two elements:

{title="index.html",lang="html"}
~~~~~~~
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="favicon.svg" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0"
    />
    <title>JavaScript App</title>
  </head>
  <body>
# leanpub-start-insert
    <h1 id="headline"></h1>
    <p class="text"></p>
# leanpub-start-insert

    <script type="module" src="/main.js"></script>
  </body>
</html>
~~~~~~~

In the following, I will just focus on the content of the `<body>` tag without including every time the `<script>` tag anymore, because this and the rest will stay the same over the next sections of the book:

{title="index.html",lang="html"}
~~~~~~~
<h1 id="headline"></h1>
<p class="text"></p>
~~~~~~~

At the moment, both tags do not have any content. We could add static content between the tags, however, we could also move over to our *main.js* file where we can change the content dynamically with JavaScript and the DOM API:

{title="main.js",lang="javascript"}
~~~~~~~
const headline = 'Hello JavaScript!';
const text = 'I like JS, but also HTML and CSS.';

document.querySelector('#headline').textContent = headline;
document.querySelector('.text').textContent = text;
~~~~~~~

Keep in mind that the code could have been written the following way as well. In our case, we just used the return value of `querySelector()` right away to access the `textContent`.

{title="main.js",lang="javascript"}
~~~~~~~
const headline = 'Hello JavaScript!';
const text = 'I like JS, but also HTML and CSS.';

# leanpub-start-insert
const headlineNode = document.querySelector('#headline');
headlineNode.textContent = headline;

const textNode = document.querySelector('.text');
textNode.textContent = text;
# leanpub-end-insert
~~~~~~~

In this JavaScript file, we created two string variables and assigned them to both HTML elements. Whereas we selected one HTML element by using its `id` attribute (CSS `id` selector), we selected the other HTML element by using its `class` attribute (CSS `class` selector). Semantically in HTML, a value for an `id` attribute should be unique. In contrast, `class` attributes are often used with the same values in order to style all of them with CSS the same way. For example, we could have two paragraph elements with the same `class` attribute, because later they get styled the same way with CSS:

{title="index.html",lang="html"}
~~~~~~~
<h1 id="headline"></h1>
# leanpub-start-insert
<p class="text">I like Apples</p>
<p class="text">I like Bananas</p>
<p class="text">I like Cashews</p>
# leanpub-end-insert
~~~~~~~

Now, after we have inserted three paragraph tags in our HTML, and we keep our JavaScript file as before, we can see how only the first paragraph changes its content while the other paragraphs stay intact. That's because the `querySelector()` method from our JavaScript file only selects the first paragraph occurence from the HTML file. If we would want to change this, we would have to use the `querySelectorAll()` method instead which returns us all occurences:

{title="main.js",lang="javascript"}
~~~~~~~
const headline = 'Hello JavaScript!';
document.querySelector('#headline').textContent = headline;

# leanpub-start-insert
const textElements = document.querySelectorAll('.text');
textElements[0].textContent = 'I like JS';
textElements[1].textContent = 'I like HTML';
textElements[2].textContent = 'I like CSS';
# leanpub-end-insert
~~~~~~~

Whenever you have to select multiple elements, use `querySelectorAll()`, which returns you multiple HTML nodes, instead of `querySelector()`, which returns only the first occurence of a HTML node. Since all paragraphs share the same class and there are no other paragraphs in our HTML, we could also use a more unspecific element selector instead to just select all paragraphs:

{title="main.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
const textElements = document.querySelectorAll('p');
# leanpub-end-insert

textElements[0].textContent = 'I like JS';
textElements[1].textContent = 'I like HTML';
textElements[2].textContent = 'I like CSS';
~~~~~~~

However, recommended would always be using a more specific selector (e.g. `.text`), because it's more robust in the case of more paragraphs being added to the HTML file. Next, we can read from HTML elements with the DOM API as well. In the following, we are reading their contents and modify them with JavaScript. Since `textContent` is nothing more than a JavaScript string data type, we can use its built-in `toUpperCase()` method:

{title="main.js",lang="javascript"}
~~~~~~~
const textElements = document.querySelectorAll('.text');

textElements[0].textContent =
  textElements[0].textContent.toUpperCase();

textElements[1].textContent =
  textElements[1].textContent.toUpperCase();

textElements[2].textContent =
  textElements[2].textContent.toUpperCase();
~~~~~~~

This should display "I LIKE APPLES", "I LIKE BANANAS", and "I LIKE CASHEWS" in the browser. When you learned about arrays in JavaScript, you got introduced to array methods, such as the built-in `map()` method, as well. This method could be used here instead of assigning the modification to all HTML elements one by one. When using the `map()` method, we iterate over every element in the array and get access to each element in the `map()` method's callback function. In this callback function, we can then modify each element:

{title="main.js",lang="javascript"}
~~~~~~~
const textElements = document.querySelectorAll('p');

const toUpperCaseTransformation = (element) => {
  element.textContent = element.textContent.toUpperCase();

  return element;
};

textElements.map(toUpperCaseTransformation);
~~~~~~~

This example is not working though and you should see the error: `Uncaught TypeError: textElements.map is not a function` in your developer's tools logging in the browser. Essentially the error says that `map()` is not available of our `textElements` variable. Once we read up about the return value from the `querySelectorAll()` method, we learn that the method does not return a JavaScript array but a [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList) (which is a DOM specific data type). We can circumvent this by using a helper method called `Array.from()` which transforms iterative data structures (e.g. NodeList) into an array:

{title="main.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
const nodeElements = document.querySelectorAll('p');
const elements = Array.from(nodeElements);
# leanpub-end-insert

const toUpperCaseTransformation = (element) => {
  element.textContent = element.textContent.toUpperCase();

  return element;
};

# leanpub-start-insert
elements.map(toUpperCaseTransformation);
# leanpub-end-insert
~~~~~~~

Let's take one step back and look at our selectors. Change the body's elements content in the *index.html* file to the following content:

{title="index.html",lang="html"}
~~~~~~~
<h1 id="headline"></h1>
# leanpub-start-insert
<div class="food">
# leanpub-end-insert
  <p>I like Apples</p>
  <p>I like Bananas</p>
  <p>I like Cashews</p>
</div>
# leanpub-start-insert
<div class="animal">
  <p>I like Squirrels</p>
</div>
# leanpub-end-insert
~~~~~~~

When running the file in the browser, the JavaScript code still upper cases all the texts. What if you would want to change only the food paragraphs and not the animal paragraphs via JavaScript? We could use a more specific selector which entails the surrounding `<div>` element's `class` attribute. In this case, we want to select all paragraphs which are located in an element with the class `food`:

{title="main.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
const nodeElements = document.querySelectorAll('.food p');
# leanpub-end-insert
~~~~~~~

If we would want to be more specific, we could also address the container element (read: `<div> tag`) too. This way, paragraph elements that are child of `<div>` tags that have a `class` attribute with `food` get selected. If another element which is not a `<div>` tag with the `class` attribute `food` would be present, it wouldn't be selected by this selector:

{title="main.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
const nodeElements = document.querySelectorAll('div.food p');
# leanpub-end-insert
~~~~~~~

What's interesting is that a selection doesn't stop after one selector. Essentially when selecting one HTML element, we have this element at our hands and can from there select other child elements of this element:

{title="main.js",lang="javascript"}
~~~~~~~
const animalParagraphNode = document
  .querySelector('div.animal')
  .querySelector('p');

animalParagraphNode.textContent = 'I like Elephants';
~~~~~~~

Since every selection returns an element, you could also store the intermediate element as a variable for later usage:

{title="main.js",lang="javascript"}
~~~~~~~
const animalNode = document.querySelector('div.animal');
const animalParagraphNode = animalNode.querySelector('p');
~~~~~~~

So far, we have only used the `textContent` property of an element to change it. However, the [Element API](https://developer.mozilla.org/en-US/docs/Web/API/Element) has many different properties and even methods which are available. You should take some time to scan through the API documentation. The exercises offer some tasks of this kind for you.

After all, knowing about selecting one (here: `querySelector()`) or multiple (here: `querySelectorAll()`) elements, navigating from one parent element to its child element, reading and assigning values, becomes the access point for a JavaScript developer to interact with HTML.

### Exercises:

* Read more about [the querySelectorAll() method](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll).
* Read more about [the built-in Array.from() method and how it helps us to transform an iterable NodeList to an array data type](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from).
* Read more about [CSS selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) that are used for selecting elements via the DOM API.
* Print an element's height with the property `clientHeight` to your browser's console.
* Select `div.animal` with `querySelector()` and print its `children` property to your browser's console.
* Use a second `class` for the container element with the "animal" `class` (e.g. `class="animal forest-animal"`), select this element with the DOM API, and print both properties called `className` and `classList`. What's the difference between both properties?

## Creating HTML Elements

The last sections have shown you how to select and update HTML elements in a HTML file from a JavaScript file via the DOM API. In these cases, the data was already there in the HTML and we only wanted to read from it (e.g. read text from a HTML element) or write to it (e.g. write text to a HTML element). Mostly this happens whenever there is a finished HTML website where you want to use JavaScript for flexible adjustments.

However, in modern web applications, most often the data origins in JavaScript and as a developer we want to display it for an audience in HTML. Take for example the following JavaScript string that we will be using in a clean slate **main.js** file for our application:

{title="main.js",lang="javascript"}
~~~~~~~
const title = 'Hello JavaScript';
~~~~~~~

For this purpose, the content of the **index.html** HTML file's body tag is the following:

{title="index.html",lang="html"}
~~~~~~~
<div id="app" />

<script type="module" src="/main.js"></script>
~~~~~~~

From here, we want to display the data (here: `title`) as headline element (read: `<h1>` tag) within the `<div>` tag without touching the HTML file, because the data (read: string) comes from our JavaScript file. Fortunatly the DOM API gives us a method to create an HTML element, to set its content, and append this new HTML element as child to an existing parent element:

{title="main.js",lang="javascript"}
~~~~~~~
const title = 'Hello JavaScript';

# leanpub-start-insert
// create an HTML element
const titleNode = document.createElement('h1');

// set its content
titleNode.textContent = title;

// append it as element
document.querySelector('#app').appendChild(titleNode);
# leanpub-end-insert
~~~~~~~

By using the DOM API's `createElement()` method, we can create HTML elements out of thin air. After this element has been created, it lives in JavaScript's memory as variable (here: `titleNode`), because it isn't visible in the browser yet. Before making it visible, usually a developer sets properties (here: `textContent`). Then, the created element gets appended as a child element to a potential parent element which ultimatively makes it visible in the browser.

After all, JavaScript and its DOM API can not only be used to read and write data from and to HTML elements, but also to create new elements, to set their properties, and to append them as child element to a parent element. We will fortify this learning experience by going one step further with more complex data structures than a string. In the following, we want to display the following JavaScript array data structure from our clean slate *main.js* file on our website:

{title="main.js",lang="javascript"}
~~~~~~~
const list = [
  {
    title: 'React',
    url: 'https://reactjs.org/',
    author: 'Jordan Walke',
  },
  {
    title: 'Redux',
    url: 'https://redux.js.org/',
    author: 'Dan Abramov & Andrew Clark',
  },
];
~~~~~~~

The content of the **index.html** HTML file's body tag will be the following:

{title="index.html",lang="html"}
~~~~~~~
<div>
  <ul id="list" />
</div>

<script type="module" src="/main.js"></script>
~~~~~~~

Similar to the previous task, we want to display the data (here: `list`) as HTML element to make it visible in the browser. To be more specific, in this case we want to display each item of the list as `<li>` tag as a child of the `<ul>` tag. When we head over to our *main.js* file, we could accomplish this task the following way when considering what we have learned in the last task:

{title="main.js",lang="javascript"}
~~~~~~~
const list = [ ... ];

# leanpub-start-insert
const firstNode = document.createElement('li');
firstNode.textContent = list[0].title;
document.querySelector('#list').appendChild(firstNode);

const secondNode = document.createElement('li');
secondNode.textContent = list[1].title;
document.querySelector('#list').appendChild(secondNode);
# leanpub-end-insert
~~~~~~~

For each item in the list we repeat the procedure of creating a list item element, setting its content based on the JavaScript item's `title` property, and appending it to the parent list element which is already in the HTML. However, doing it this way is not only repetetive but also does not scale very well for a large list of items. Earlier we learned about for loop statements in JavaScript which help us in these situations:

{title="main.js",lang="javascript"}
~~~~~~~
const list = [ ... ];

# leanpub-start-insert
for (let i = 0; i < list.length; i++) {
  const itemNode = document.createElement('li');
  itemNode.textContent = list[i].title;
  document.querySelector('#list').appendChild(itemNode);
}
# leanpub-end-insert
~~~~~~~

Now it does not matter how many items there are in the list, because the loop takes care of displaying all of them. In modern JavaScript though, you will often see a built-in array method being used over a for loop statement. In this case, a `forEach()` method may be appropriate to use as well:

{title="main.js",lang="javascript"}
~~~~~~~
const list = [ ... ];

# leanpub-start-insert
list.forEach((item) => {
  const itemNode = document.createElement('li');
  itemNode.textContent = item.title;
  document.querySelector('#list').appendChild(itemNode);
});
# leanpub-end-insert
~~~~~~~

You may be wondering why we display the list programmatically via JavaScript in HTML. Wouldn't it be simpler to just use `<li>` tags in the HTML? And indeed it would be simpler, however, in modern JavaScript applications most data origins in JavaScript, so we need to have a way when having this data in JavaScript to display it in HTML. Using the DOM API is the status quo when not using a framework like React to perform such tasks.

### Exercises:

* Open the browser's developer tool's "Elements" tab and verify that all displayed elements of your website are there.
* Read more about [the DOM API's createElement() method](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement).
* Read more about [the DOM API's appendChild() method](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild).
* Question: If one would change the order of setting the `textContent` and appending the element with `appendChild()`, it would still work. Why does order not matter here?
  * Answer: Since we have a reference to the element, we can update it whenever we want. Meaning: whether the element is already in the DOM or not appended yet, we can always set its properties.
* Recap the following topics from earlier sections: for loop statements, callback functions, and built-in array methods such as `forEach()`.

## HTML Events in JavaScript

We will continue with our little application from the previous section in this section by enriching it with a user interaction. In order enable a user to interact with the website, we would need to provide an HTML element such as an input element where a user can type into the field. Let's add one of these to our *index.html* file:

{title="index.html",lang="html"}
~~~~~~~
<div>
# leanpub-start-insert
  <input />
# leanpub-end-insert

  <ul id="list" />
</div>
~~~~~~~

When displaying the HTML file in a browser, you should see the input field popping up above of the displayed list. To make this input field more accessible, we will provide a label HTML element too:

{title="index.html",lang="html"}
~~~~~~~
<div>
# leanpub-start-insert
  <label for="search">Search: </label>
  <input id="search" />
# leanpub-end-insert

  <ul id="list" />
</div>
~~~~~~~

By using the `for` attribute for the label element and the `id` attribute for the input field, we connect both elements so that when a user clicks the label the input field gets focused. What's missing is capturing the value that a user types into the input field. Therefore, we will head over to our *main.js* file and add a so called **event listener** to the HTML element:

{title="main.js",lang="javascript"}
~~~~~~~
const list = [ ... ];

list.forEach((item) => {
  ...
});

# leanpub-start-insert
document
  .querySelector('#search')
  .addEventListener('input', (event) => {
    console.log(event.target.value);
  });
# leanpub-end-insert
~~~~~~~

With the DOM API, we are selecting the element where the `id` equals `search` by using an id selector. Once we have this element, we add an event listener to it with the `addEventListener()` method which takes two arguments: While the first argument is the event type (others are `change`, `click`), the second argument is a callback function which runs every time a user triggers the event -- which in this case is typing into the input field.

The callback function gives us access to the `event` parameter which holds all the information about the current input field. Accessing `event.target` returns us the input field itself. Going one step further and accessing `event.target.value` returns us the current value of the input field. Verify it yourself by going back to your browser, open the developer tool's "Console" tab, and start typing into the input field.

Event listeners can be added to various HTML elements by using different event types. For example, a button can receive an event listener of type `click`. Whenever a user clicks on the button, the callback function will run. Another example: The `blur` event type on an input field runs every time an input field switches its internal state from focused to unfocused.

Now we have learned how to display elements via JavaScript and the DOM API on a website and how to listen to element interactions. With both these building blocks, we are going to create a search functionality for our little application. What we have done so far is displaying the list of items and hooking up an event listener on an input field element. What's missing is the implementation details within the callback function of the event listener which takes the current string from the input field, filters the list based on this string, and only displays the items from the list that match the search criteria. We could start this off by naivly just displaying all the items again when a user types into the input field:

{title="main.js",lang="javascript"}
~~~~~~~
const list = [ ... ];

list.forEach((item) => {
  ...
});

document
  .querySelector('#search')
  .addEventListener('input', (event) => {
# leanpub-start-insert
    // append list items
    list.forEach((item) => {
      const itemNode = document.createElement('li');
      itemNode.textContent = item.title;
      document.querySelector('#list').appendChild(itemNode);
    });
# leanpub-end-insert
  });
~~~~~~~

When trying the application in the browser, you will see that for every time a user types into the input field, the whole list of items from our array gets appended to the list element in HTML. That's actually what the code implements. So what we are looking for is removing the previous list item elements before we append the new list item elements. By setting the `textContent` of an element to an empty string, we remove all of its content:

{title="main.js",lang="javascript"}
~~~~~~~
const list = [ ... ];

list.forEach((item) => {
  ...
});

document
  .querySelector('#search')
  .addEventListener('input', (event) => {
# leanpub-start-insert
    // remove list elements
    document.querySelector('#list').textContent = '';
# leanpub-end-insert

    // append list items
    list.forEach((item) => {
      const itemNode = document.createElement('li');
      itemNode.textContent = item.title;
      document.querySelector('#list').appendChild(itemNode);
    });
  });
~~~~~~~

The previous implementation details made sure that we are always refreshing the displayed items when a user types into the input field. First we remove all item elements, then we add them again. That's the foundation for a so called re-rendering mechanism (read more about this in the next section). Next, we are going to implement the actual search functionality itself:

{title="main.js",lang="javascript"}
~~~~~~~
...

document
  .querySelector('#search')
  .addEventListener('input', (event) => {
    // remove list elements
    document.querySelector('#list').textContent = '';

# leanpub-start-insert
    const searchTerm = event.target.value;

    // append list items
    // but only the ones which meet the search criteria
    list
      .filter((item) => item.title.includes(searchTerm))
# leanpub-end-insert
      .forEach((item) => {
        const itemNode = document.createElement('li');
        itemNode.textContent = item.title;
        document.querySelector('#list').appendChild(itemNode);
      });
  });
~~~~~~~

As learned before, we can receive the current value from the input field element by using the listener's event. From there, we use this value as search criteria to filter our list. An array's built-in `filter()` method iterates over every item and returns each item to the new list when the conditional equals `true`. For example, when the `searchTerm` is "Rea", one of the items title's includes this partial string and therefore stays in the list while the other one gets removed. Afterward, we continue with the built-in `forEach()` method which displays all the remaining items.

The search functionality works, but it's not robust yet. Try to search for "react" instead of "React". The former will not work, because the search functionality is case sensitive. Before we change this implementation detail, let's extract the filter's callback function as standalone function:

{title="main.js",lang="javascript"}
~~~~~~~
...

document
  .querySelector('#search')
  .addEventListener('input', (event) => {
    // remove list elements
    document.querySelector('#list').textContent = '';

    const searchTerm = event.target.value;

# leanpub-start-insert
    const searchByTitle = (item) => item.title.includes(searchTerm);
# leanpub-end-insert

    // append list items
    // but only the ones which meet the search criteria
# leanpub-start-insert
    list.filter(searchByTitle).forEach((item) => {
# leanpub-end-insert
      const itemNode = document.createElement('li');
      itemNode.textContent = item.title;
      document.querySelector('#list').appendChild(itemNode);
    });
  });
~~~~~~~

Now the logic needs to implement a case insensitive searching. So we can extend the callback function's logic by lower casing each item's title and the search term before checking whether one includes the other:

{title="main.js",lang="javascript"}
~~~~~~~
...

document
  .querySelector('#search')
  .addEventListener('input', (event) => {
    // remove list elements
    document.querySelector('#list').textContent = '';

    const searchTerm = event.target.value;

# leanpub-start-insert
    const searchByTitle = (item) =>
      item.title.toLowerCase().includes(searchTerm.toLowerCase());
# leanpub-end-insert

    // append list items
    // but only the ones which meet the search criteria
    list.filter(searchByTitle).forEach((item) => {
      const itemNode = document.createElement('li');
      itemNode.textContent = item.title;
      document.querySelector('#list').appendChild(itemNode);
    });
  });
~~~~~~~

That's it. You have used JavaScript to display a filtered list to your user. Whenever the user types into the input field, the displayed list gets updated by first removing the previous list elements and then adding the filtered list elements based on the data and the search criteria. Since we are working with the DOM API here, we make everything visible to the end user in HTML here, while implementing all the logic in JavaScript.

### Exercises:

* Read more [about the DOM API's addEventListener method](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener).
* Recap the following topic from earlier sections: built-in array methods such as `filter()`.
* Question: Exchange the `addEventListener()` method's first argument from `input` to `change`. When does this event trigger compared to the previous one?
  * Answer: The event triggers only when a user leaves the input field and its value has changed.
* Question: What would happen if we would not remove all list item elements every time a user types into the input field?
  * Answer: For every typing, a new list (here: filtered list) would get appended to the previous list. The list would get longer, because there are never list item elements removed from it. By removing all list item elements for every typing, we make sure that the implentation logic starts with an empty list element and appends only items that match the search criteria.

## Rendering and Re-Rendering

Previously the word "display" was used when we showed HTML via JavaScript in the browser. Another popular word these days, taken from game engines, is "render". So instead of saying "we display the array as HTML list element", we can say "we render the array as HTML list element". That's only the terminology, however, in the last section we performed an actual rendering and re-rendering (read: display and updated display). First, we have the rendering in our code:

{title="main.js",lang="javascript"}
~~~~~~~
const list = [ ... ];

list.forEach((item) => {
  const itemNode = document.createElement('li');
  itemNode.textContent = item.title;
  document.querySelector('#list').appendChild(itemNode);
});

...
~~~~~~~

While the rendering happens only once when the JavaScript file gets executed, the re-rendering happens every time a user types into the input field:

{title="main.js",lang="javascript"}
~~~~~~~
...

document
  .querySelector('#search')
  .addEventListener('input', (event) => {
    // re-rendering step 1: remove content
    document.querySelector('#list').textContent = '';

    const searchTerm = event.target.value;

    const searchByTitle = (item) =>
      item.title.toLowerCase().includes(searchTerm.toLowerCase());

    // re-rendering step 2: add updated content
    list.filter(searchByTitle).forEach((item) => {
      const itemNode = document.createElement('li');
      itemNode.textContent = item.title;
      document.querySelector('#list').appendChild(itemNode);
    });
  });
~~~~~~~

When comparing both code snippets, you can see that both callback functions in the `forEach()` have identical implementation details. These callback functions are responsible for the actual rendering (and re-rendering), so let's extract them to one reusable function:

{title="main.js",lang="javascript"}
~~~~~~~
const list = [ ... ];

# leanpub-start-insert
const renderItems = (item) => {
  const itemNode = document.createElement('li');
  itemNode.textContent = item.title;
  document.querySelector('#list').appendChild(itemNode);
};
# leanpub-end-insert

# leanpub-start-insert
// render
list.forEach(renderItems);
# leanpub-end-insert

document
  .querySelector('#search')
  .addEventListener('input', (event) => {
    document.querySelector('#list').textContent = '';

    const searchTerm = event.target.value;

    const searchByTitle = (item) =>
      item.title.toLowerCase().includes(searchTerm.toLowerCase());

# leanpub-start-insert
    // re-render
    list.filter(searchByTitle).forEach(renderItems);
# leanpub-end-insert
  });
~~~~~~~

By extracting the rendering logic into one function, which is used by the initial render and every re-render, we can extend this one function with the knowledge that it applies to both renderings after all. In the following, we will not only show the title in the list item element, but also the author. First, remove the one line of code where the title gets rendered:

{title="main.js",lang="javascript"}
~~~~~~~
const renderItems = (item) => {
  const itemNode = document.createElement('li');
  document.querySelector('#list').appendChild(itemNode);
};
~~~~~~~

When opening the HTML file in the browser, you may see only two dots which represent both list items, but they are empty because no content is in there. You can check the "Elements" tab of your browser's developer tools to confirm it. From here we are going to add richer content to our list item element. The following code snippet shows how to add to `<span>` tags side by side, whereas one of them as the title and the other one a template literal with the author:

{title="main.js",lang="javascript"}
~~~~~~~
const renderItems = (item) => {
  const itemNode = document.createElement('li');
  document.querySelector('#list').appendChild(itemNode);

# leanpub-start-insert
  const titleNode = document.createElement('span');
  titleNode.textContent = item.title;
  itemNode.appendChild(titleNode);

  const authorNode = document.createElement('span');
  authorNode.textContent = ` by ${item.author}`;
  itemNode.appendChild(authorNode);
# leanpub-end-insert
};
~~~~~~~

Each item in the list has a `url` property too. So we could make use of it by rendering an `<a>` tag instead of a `<span>` tag. In addition, an anchor element needs an `href` attribute to actually link to some other place:

{title="main.js",lang="javascript"}
~~~~~~~
const renderItems = (item) => {
  const itemNode = document.createElement('li');
  document.querySelector('#list').appendChild(itemNode);

# leanpub-start-insert
  const titleNode = document.createElement('a');
# leanpub-end-insert
  titleNode.textContent = item.title;
# leanpub-start-insert
  titleNode.href = item.url;
# leanpub-end-insert
  itemNode.appendChild(titleNode);

  const authorNode = document.createElement('span');
  authorNode.textContent = ` by ${item.author}`;
  itemNode.appendChild(authorNode);
};
~~~~~~~

That's it. We are rendering each item from the list with all of its properties with only one function. This function is used at two places for the initial render and every following re-rendering when the user searches the list while typing into the input field. After all, this section should show you again how you gain full control over the HTML by using JavaScript's DOM API. You can render things initially when the JavaScript gets executed, but also re-render the things (or render new things or remove things), whenever something (e.g. an event, because a user types into an input field) happens.

### Exercises:

* Compare your JavaScript application and its code with this [React application](https://codesandbox.io/s/elastic-framework-pishg). Both are performing the same use case, and the React one may be more intimidating at this stage, however, a framework like React is the status quo for modern JavaScript applications. So once you feel comfortable enough with JavaScript, I encourage you to check out my other book called The Road to React.

