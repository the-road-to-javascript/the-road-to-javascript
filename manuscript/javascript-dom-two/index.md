# JavaScript and the DOM: Part II

TODO summary

# Rendering Asynchronous Data

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

- body tag

{title="index.html",lang="html"}
~~~~~~~
<div id="app">
  <ul id="list" />
</div>

<script type="module" src="/main.js"></script>
~~~~~~~

- asdqwdqwdqwd

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

- asdwdqqwd

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

- qwdqwdqw

### Exercises:

- qwdqwd TODO

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