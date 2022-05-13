# JavaScript Fundamentals: Part IV

Before we continue working on the HTML/JavaScript interoperability, we will take a step back and learn about asynchronous JavaScript first. When working in modern client applications, as a JavaScript developer you will be often asked to communicate to a server application. The communication between client and server is asynchronous and a JavaScript Promise is used as container for asynchronous data. In the following sections, you will learn how to work with asynchronous data by using promises and you will learn how to interact with third-party servers and their public APIs.

## Asynchronous Data with Promises

Do you remember when we had phone calls? We introduced ourselves on the phone, the other person introduced themselve, and the both of you started to have a conversation in real-time where each participant said something alternately. In programming, this is called synchronous communication.

In contrast, these days we are used to text people instead. When texting, people usually do not answer immediatly but will answer with a delay. Once you get an answer, you will write back at some point. The communication shifted from being synchronous to **asynchronous**, because no one expects an instant reply anymore. The benefit: While you have a conversation with someone, you have time in between messages to have another conversation with someone else and you decide when you want to pick up a conversation again. That's the whole synchronous vs asynchronous terminology.

The term **data** in programming refers to any information. Most of the time, data is used within an application or used for communication between applications (e.g. client-server communication). As we already learned, in JavaScript this information is expressed with different data types and structures such as strings, booleans, numbers, objects or arrays:

{title="index.js",lang="javascript"}
~~~~~~~
const messages = [
  {
    participant: 'Robin',
    text: 'Hi Sarah, how are you?',
  },
  {
    participant: 'Sarah',
    text: 'Hello Robin!',
  },
];
~~~~~~~

Last, the **Promise** in JavaScript is a built-in object which acts as container for transfering asynchronous data from one application to another. We didn't have such transfering of information yet, but we will soon get to know it. A JavaScript Promise represents literally the promise that we get some data eventually. In the case of the texting example, it's the message itself which we are promised to receive, but we do not know the actual information.

![](images/async-conversation.png)

As a developer, you will often ask another application (e.g. client asks server) for data. In a traditional **client-server architecture** all the application-wide data is stored in a database. A backend application is used to read from and to write to this database. This backend acts also as the one server for many client applications. For example, while Sarah has one client application (e.g. app) on her phone, Robin has one client application on his laptop (e.g. browser). Now when both users start their applications, they need to request all the messages -- which have been written between both in their ongoing conversation -- from the server and will receive a response eventually (also called **request response communication model**).

![](images/client-server-architecture.png)

On the client-side, you will create a Promise as kind of token for this data, but not the data itself, because it arrives with a delay due to the different locations of client and server. So when holding this promise, you don't know its data yet, but you have the reference to the promise which enables you to be notified whenever the data arrives:

{title="index.js",lang="javascript"}
~~~~~~~
// made up function
// which calls a server and
// which returns a promise
const promise = getDataFromServer();

promise.then((result) => {
  console.log(result);
});
~~~~~~~

A promise offers methods like `then()` which accept a callback function as argument and which gets executed whenever the data arrives successfully. Then the developer can display this data in the browser. While the data is not there yet, a loading spinner could be used to indicate the user that the data will arrive eventually. Other methods like `catch()` on the Promise enable you to act on errors whenever the server fails to return the data. Then an error message could be displayed to the user:

{title="index.js",lang="javascript"}
~~~~~~~
const promise = getDataFromServer();

# leanpub-start-insert
// show loading spinner
# leanpub-end-insert

promise
  .then((result) => {
# leanpub-start-insert
    // hide loading spinner
    // show result in browser
# leanpub-end-insert
  })
# leanpub-start-insert
  .catch((result) => {
    // hide loading spinner
    // show error message in browser
  });
# leanpub-end-insert
~~~~~~~

Because we have no server application with data but only a client application, we will create a Promise on the client application from scratch here. Later, when we will request data from a server, we do not need to perform this step:

{title="index.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
const promise = new Promise((resolve) => {
  // promise speicifc implementation
});
# leanpub-end-insert
~~~~~~~

The callback function gives us access to parameters such as the `resolve()` function. When calling the `resolve()` function, two things happen: The promise gets filled with the information that we pass as argument to the `resolve()` function. And the promise's `then()` method's callback function gets called:

{title="index.js",lang="javascript"}
~~~~~~~
const promise = new Promise((resolve) => {
# leanpub-start-insert
  const data = [
    {
      participant: 'Robin Wieruch',
      text: 'Hi Sarah, how are you?',
    },
    {
      participant: 'Sarah Finnley',
      text: 'Hi Robin!',
    },
  ];

  resolve(data);
# leanpub-end-insert
});
~~~~~~~

In addition, we can use a timer to fake the delay of a client-server communication:

{title="index.js",lang="javascript"}
~~~~~~~
const promise = new Promise((resolve) => {
  const data = [
    {
      participant: 'Robin Wieruch',
      text: 'Hi Sarah, how are you?',
    },
    {
      participant: 'Sarah Finnley',
      text: 'Hi Robin!',
    },
  ];

# leanpub-start-insert
  const artificialDelay = 3000;

  setTimeout(() => resolve(data), artificialDelay);
# leanpub-end-insert
});
~~~~~~~

With this client-side created promise at our hand, which usually comes from a server application where we do not know the data in advance like we do in this example, we can register a callback function as argument of the promise's `then()` method which executes whenever the data resolves successfully. Try it out yourself and see the result in the browser's developer tools:

{title="index.js",lang="javascript"}
~~~~~~~
const promise = new Promise((resolve) => {
  ...
});

# leanpub-start-insert
promise.then((result) => {
  console.log(result);
});
# leanpub-end-insert
~~~~~~~

There may be two questions popping up in your head. First, you may be wondering why we need the `setTimeout()` method. In our Promise, we need the time out to create an artificial delay. Without the time out, the promise would resolve immediatly; which is fine and works too, but which doesn't mimic the client-server communication behavior where it takes time until data arrives on a client from a remote server.

Second, you may be wondering why we are not just using the `setTimeout()` method without a Promise like we have seen it in a previous section. While we could create the artificial delay this way, we wouldn't hold any variable (here: `promise`) as reference which represents the container for the data. By having a promise at our hands after making a request to a server, we can move this promise like any other value around (e.g. as argument for a function) and call methods (e.g. `then()` and `catch()`) on it.

Sometimes a request to a server will fail, for example when the data cannot be found or a user isn't authorized to see the data. Then we do not get any data, but an error. We can mimic this behavior with a Promise as well by using the `reject()` instead of the `resolve()` function. In addition, we can create error objects in JavaScript by using the built-in `Error` object:

{title="index.js",lang="javascript"}
~~~~~~~
const promise = new Promise((resolve, reject) => {
  const error = new Error('Not authorized.');
  const artificialDelay = 3000;

  setTimeout(() => reject(error), artificialDelay);
});
~~~~~~~

Next we can act to a rejected promise with the promise's `catch()` method:

{title="index.js",lang="javascript"}
~~~~~~~
promise.then((result) => {
  console.log(result);
});

# leanpub-start-insert
promise.catch((error) => {
  console.log(error);
});
# leanpub-end-insert
~~~~~~~

Promises can be chanined as well. So usually when using `then()` and `catch()` to handle successful and errornous asynchrnous data requests, you will chain both onto a promise. With the previous implementation of the promise, either the successful or the errornous one, you will run into either the `then()` or the `catch()` block:

{title="index.js",lang="javascript"}
~~~~~~~
promise
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.log(error);
  });
~~~~~~~

There are two steps we did in this section: First, we created a promise on the client-side. We filled it with data and added an artifcial delay. With this implementation in place, it mimics nicely a promise coming from a remote server.

Second, we used the promise's `then()` method to receive a notification with the `result` when the promise resolves and the promise's `catch()` method to receive a notification when there is an error. Usually when dealing with data from a server, you will not create a promise from scratch in the first place. Instead, you will call a function which will just return a promise for you. From there you will be using the promise's `then()` and `catch()` methods in your application. However, I always feel it's a good exercises for beginners to create their own promise from scratch first before interacting with a real server where the promise is created for you.

### Exercises:

* Read more about [the evolution from website to web applications](https://www.robinwieruch.de/web-applications).
* Read more about [Promises in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise).
  * See more examples in action about [Promises](https://javascript.info/promise-basics).

## Client-Server Communication with APIs

When writing client-side applications with JavaScript, most of the time you will have to deal with a server which enables you to read and write data from and to a database via a server. For example, when writing articles for a blogging platform, these articles get written to a database. When a user visits an article on the blogging platform, the article gets read from the database. Between client and database sits the server which implements among other things the read and write operations to access the database.

In the following, we will not implement a server ourselves, because that would be lots of work, but use a third-party server which offers data for us. Usually that's the best learning experience you can get as an aspiring developer, because you get to work with real world data while not having to implement the server yourself. You are only in charge of the client application.

The communication channel between a client and server is called [API](https://en.wikipedia.org/wiki/API). When this API is publicly documented and can be used by anyone, it's also called a **public API**. You have heard about the term API before, because essentially [every interface in programming can be called API](https://www.robinwieruch.de/what-is-an-api-javascript) (e.g. browser API, DOM API, API of a JavaScript class). However, when JavaScript developers refer to an API without furhter specifying it, most often they refer to the API of a remote server.

The website [Hacker News](https://news.ycombinator.com/), which states itself as website for content *"that gratifies one's intellectual curiosity"*, features news about tech and entrepeurship. You can visit this website yourself as a user, but you can also use their [API](https://hn.algolia.com/api) as a developer, which we will do in the next steps, to query their data.

First, we will install a library called [axios](https://github.com/axios/axios) which is a popular choice in a JavaScript application when interacting with remote servers and their API. On the command line, install this library to your JavaScript application from the last sections (where you have learned to use the DOM API):

{title="Command Line",lang="text"}
~~~~~~~
npm install axios
~~~~~~~

In our JavaScript *main.js* file, we will start from zero with a blank file. First, import axios:

{title="main.js",lang="javascript"}
~~~~~~~
import axios from 'axios';
~~~~~~~

Second, declare Hacker News' API by using its specific search API endpoint. In this case, we are already setting a `query` (here: "javascript") as search criteria. Later, this `query` will be flexible -- which means that the user input decides what data gets queried:

{title="main.js",lang="javascript"}
~~~~~~~
import axios from 'axios';

# leanpub-start-insert
const API = 'https://hn.algolia.com/api/v1/search?query=javascript';
# leanpub-start-insert
~~~~~~~

Third, we make a HTTP GET request with axios' `get()` method to the API endpoint which returns a promise:

{title="main.js",lang="javascript"}
~~~~~~~
import axios from 'axios';

const API = 'https://hn.algolia.com/api/v1/search?query=javascript';

# leanpub-start-insert
const promise = axios.get(API);
# leanpub-end-insert
~~~~~~~

And fourth, whenever the data arrives for this promise, get notified in the promise's `then()` block to work with the response:

{title="main.js",lang="javascript"}
~~~~~~~
import axios from 'axios';

const API = 'https://hn.algolia.com/api/v1/search?query=javascript';

const promise = axios.get(API);

# leanpub-start-insert
promise.then((response) => {
  console.log(response);
});
# leanpub-end-insert
~~~~~~~

As you have learned before, you can also chain these methods onto each other. Because the `get()` method returns a promise, you can immediately continue to call methods (e.g. `then()`) on this promise:

{title="main.js",lang="javascript"}
~~~~~~~
import axios from 'axios';

const API = 'https://hn.algolia.com/api/v1/search?query=javascript';

# leanpub-start-insert
axios.get(API).then((response) => {
  console.log(response);
});
# leanpub-end-insert
~~~~~~~

Start the application and open your browser's "Console" tab. After a delay, you should see the logging of the `response` and its data structure. Browse through the deeply nested JavaScript object and get familar with it before adjusting the logging in your code which allows you to see the most relevant data for this query:

{title="main.js",lang="javascript"}
~~~~~~~
...

axios.get(API).then((response) => {
# leanpub-start-insert
  console.log(response.data.hits);
# leanpub-end-insert
});
~~~~~~~

Now the logging should show an array of the most popular JavaScript articles on Hacker News. Each of these articles in the array should have properties like `title`, `url` and `author` which we will display in the browser eventually. Previously we came up with this kind of data ourselves, now we are getting real world data from someone else.

However, not every request to a remote server is successful. In the case of an error, you want to deal with it. For example, if the Hacker News API would return an error, you cannot display your application's users a result. So instead you would show them an error message. When using a promise and its `then()` method, the best place to deal with error handling would be the `catch()` block:

{title="main.js",lang="javascript"}
~~~~~~~
...

axios
  .get(API)
  .then((response) => {
    console.log(response.data.hits);
  })
# leanpub-start-insert
  .catch((error) => {
    console.log(error);
  });
# leanpub-end-insert
~~~~~~~

Last but not least, you could move the implementation logic into a reusable function. This isn't a mandatory step, however, it should just illustrate where the `getDataFromServer()` function (the one that we had in an earlier section) comes from:

{title="main.js",lang="javascript"}
~~~~~~~
import axios from 'axios';

const API = 'https://hn.algolia.com/api/v1/search?query=javascript';

# leanpub-start-insert
const getDataFromServer = (url) => {
  return axios.get(url);
};
# leanpub-end-insert

# leanpub-start-insert
const promise = getDataFromServer(API);
# leanpub-end-insert

# leanpub-start-insert
promise
# leanpub-end-insert
  .then((response) => {
    console.log(response.data.hits);
  })
  .catch((error) => {
    console.log(error);
  });
~~~~~~~

Congratulations, you have requested data from a third-party server via its public API. You have used a popular third-party library called axios to perform the request, however, in the exercises you may be learning about another popular alternative which is natively supported by the browser. Anyway, requesting data from third-party servers is an empowering first step to wake a developer's curiosity. There are many [public APIs](https://github.com/public-apis/public-apis), so do not hesitate to use an API that pleases your interests.

### Exercises:

* Read through [Hacker News' API](https://hn.algolia.com/api) and get to understand the API endpoints and the returned data.
* Read more about [CRUD operations](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete), because we have used HTTP GET to read data from the API.
* Instead of axios which is a third-party library, try to use the browser's built-in [fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).
* Question: What happens if you open the API endpoint from the code as URL in the browser?
  * Answer: The API endpoint returns the JSON data that you have seen before in the browser's developer tools. Because the browser executes natively a HTTP GET request when an URL gets opened, and the server associates the URL plus HTTP GET request with JSON instead of HTML, it returns data for the specific query.

