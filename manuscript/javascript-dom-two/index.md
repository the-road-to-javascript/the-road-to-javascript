# JavaScript and the DOM: Part II

Putting everythign together, the JavaScript fundamentals especially with asynchronous data and the DOM API, we can start to write real world JavaScript applications. The following sections will give you a glimpse of what's possible when combining JavaScript with third-party data from a remote API and the DOM API. You will notice that once you get comfortable with it, nothing will stop you from creating rich data yet flexible client-side JavaScript applications. However, you will also notice how it gets more difficult to maintain such applications once they grow in size. Usually that's the turning point where modern frameworks like React.js would come in to help. But let's take only one step at a time.

## Asynchronous Rendering

We have learned about rendering and asynchronous data previously. Putting both together, we would be able to render data which gets requested asynchronously from a data source. For the following implementation of a real world JavaScript application, we will continue with our previous project. Our *index.html* file gets a fresh start with the following content in the `<body>` tag. By having a list element (read: `<ul>` tag) in place, we can already anticipate that we are going to render a list of items eventually:

{title="index.html",lang="html"}
~~~~~~~
<div id="app">
  <ul id="list" />
</div>

<script type="module" src="/main.js"></script>
~~~~~~~

In the following steps, we want to render asynchronous data (here: list of items) which we request with a library (here: axios) from a third-party API (here: Hacker News API). Since we already installed axios before, we can import it right away. However, if you happen to start with a new project, you have to install it with `npm install axios`. From there, we can start with the implementation in our *main.js* file:

{title="main.js",lang="javascript"}
~~~~~~~
import axios from 'axios';

const API = 'http://hn.algolia.com/api/v1/search?query=javascript';

axios
  .get(API)
  .then((response) => {
    console.log(response.data.hits);
  });
~~~~~~~

Before we request the data with axios, we define the API endpoint as constant string (hence it is all UPPER_CASE). Extracting the `API` string from inline string to standalone variable comes with several benefits:

* First, the string gets a descriptive name. If we would just use it as inline string within the `get()` method, it would not be immediately clear what the string represents. By extracting it, every developer just reading through the file catches what the string is for and how it may be used.
* Second, the string becomes reusable for other parts of the application. That's called **premature optimization**, because at the moment there are no other parts where the string is used. However, since we are extracting the string as a variable already for the first benefit, this is just another benefit on top which we gain in the long run.
* Third, once the string gets reused at multiple place, due to the nature of reusability, we can change the string's value at one place and therefore it gets reflected at all the places where it is used as variable.

Once the JavaScript promise resolves from the API call, we can use the response of the request where we find all the data. In order to display the data in the browser, we iterate over each item of the list with the array's built-in `forEach()` method and render a HTML element with the item's `title` by using the DOM API:

{title="main.js",lang="javascript"}
~~~~~~~
import axios from 'axios';

const API = 'http://hn.algolia.com/api/v1/search?query=javascript';

axios
  .get(API)
  .then((response) => {
# leanpub-start-insert
    response.data.hits.forEach((item) => {
      const itemNode = document.createElement('li');
      itemNode.textContent = item.title;
      document.querySelector('#list').appendChild(itemNode);
    });
# leanpub-end-insert
  });
~~~~~~~

As we have learned before, we can extend the rendering by not only rendering the `title` property, but also the `author` and `url`. Therefore we create one list item element (read: `<li>` tag) and append all the properties with inline elements (read: `<span>` tag). In the specific case of the `url` property, we are using an anchor element (read: `<a>` tag), because we want to enable the user to navigate to this specific URL:

{title="main.js",lang="javascript"}
~~~~~~~
import axios from 'axios';

const API = 'http://hn.algolia.com/api/v1/search?query=javascript';

axios
  .get(API)
  .then((response) => {
    response.data.hits.forEach((item) => {
# leanpub-start-insert
      const itemNode = document.createElement('li');
      document.querySelector('#list').appendChild(itemNode);

      const titleNode = document.createElement('a');
      titleNode.textContent = item.title;
      titleNode.href = item.url;
      itemNode.appendChild(titleNode);

      const authorNode = document.createElement('span');
      authorNode.textContent = ` by ${item.author}`;
      itemNode.appendChild(authorNode);
# leanpub-end-insert
    });
  });
~~~~~~~

You see that the rendering is not much different from the rendering that we did in previous sections. The only difference here is that everything is done after the JavaScript promise resolves successfully with our data. This way, we are not using made up data anymore, but real world data from a third-party server and its API.

### Exercises:

* The API returns a list of items. Each item has more properties than `title`, `author`, and `url`. Try to render some more properties yourself.
* In order to render a HTML table instead of a HTML list, you could exchange the list elements (here: `ul`, `li`) with table elements (e.g. `table`, `th`, `td`).

## Error Handling

- asdasd
- force such error by changing the API endpoint to something that does not exist

{title="main.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
const API = 'http://hn.algolia.com/api/v1/filter?query=javascript';
# leanpub-end-insert
~~~~~~~

-- qwdqwdqwd

{title="main.js",lang="javascript"}
~~~~~~~
axios
  .get(API)
  .then((response) => {
    ...
  })
# leanpub-start-insert
  .catch(() => {
    const errorNode = document.createElement('p');
    errorNode.textContent = 'Something went wrong.';
    errorNode.style.color = 'red';
    document.querySelector('#app').appendChild(errorNode);
  });
# leanpub-end-insert
~~~~~~~

- qwdqwdwq

### Exercises:

- qwdqwd TODO

## User Feedback

{title="main.js",lang="javascript"}
~~~~~~~
import axios from 'axios';

const API = 'http://hn.algolia.com/api/v1/search?query=javascript';

# leanpub-start-insert
const loadingNode = document.createElement('p');
loadingNode.textContent = 'Loading ...';
document.querySelector('#app').appendChild(loadingNode);
# leanpub-end-insert

axios
  .get(API)
  .then((response) => {
    response.data.hits.forEach((item) => {
      const itemNode = document.createElement('li');
      document.querySelector('#list').appendChild(itemNode);

      const titleNode = document.createElement('a');
      titleNode.textContent = item.title;
      titleNode.href = item.url;
      itemNode.appendChild(titleNode);

      const authorNode = document.createElement('span');
      authorNode.textContent = ` by ${item.author}`;
      itemNode.appendChild(authorNode);
    });

# leanpub-start-insert
    loadingNode.parentNode.removeChild(loadingNode);
# leanpub-end-insert
  })
  .catch((error) => {
    const errorNode = document.createElement('p');
    errorNode.textContent = 'Something went wrong.';
    errorNode.style.color = 'red';
    document.querySelector('#app').appendChild(errorNode);

# leanpub-start-insert
    loadingNode.parentNode.removeChild(loadingNode);
# leanpub-end-insert
  });
~~~~~~~

### Exercises:

asd

## Server-Side Search

asd

{title="index.html",lang="html"}
~~~~~~~
<div id="app">
# leanpub-start-insert
  <label for="search">Search: </label>
  <input id="search" />
# leanpub-end-insert

  <ul id="list" />
</div>

<script type="module" src="/main.js"></script>
~~~~~~~