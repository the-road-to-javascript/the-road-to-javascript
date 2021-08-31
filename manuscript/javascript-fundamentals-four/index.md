# JavaScript Fundamentals: Part IV

TODO summary

## Asynchronous Data with Promises

Do you remember when we had phone calls? We introduced ourselves on the phone, the other person introduced themselve, and the both of you started to have a conversation in real-time where each participant said something alternately. In programming, this is called synchronous communication.

In contrast, these days we are used to text people instead. When texting, people usually do not answer immediatly but will answer eventually. Once you get an answer, you will write back at some point. The communication shifted from being synchronous to asynchronous, because no one expects an instant reply anymore. The benefit: While you have a conversation with someone, you have time in between messages to have another conversation with someone else. In addition, you can choose when to continue a conversation.

Now data is an universal usable word. In programming, data refers to any information. Most of the time, data is used within an application or used for communication between applications (e.g. client-server communication). As we already learned, in JavaScript this information is expressed with different data types and structures such as strings, booleans, numbers, objects or arrays.

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

In terms of **asynchronous data**, data could be voices or messages from the example before; essentially information which is send with a delay. The Promise in JavaScript is a built-in object which acts as container for transfering asynchronous data from one application to another. A JavaScript Promise represents literally the promise that we get some data eventually. In the case of the texting example, it's the message itself which we are promised to receive at some point.

![](images/async-conversation.png)

As a developer, you will often ask another application (e.g. client asks server) for data. In a traditional **client-server architecture** all the application-wide data is stored in a database. A backend application is used to read from and to write to this database. This backend acts also as the one server for many client applications. For example, while Sarah has one client application (e.g. app) on her phone, Robin has one client application on his notebook (e.g. browser). Now when both users start their applications, they need to request all the messages -- which have been written between both in their ongoing conversation -- from the server and will receive a response eventually (also called **request response communication model**).

![](images/client-server-architecture.png)

In code, you will create a promise as kind of token for this data, but not the data itself, because it arrives with a delay. So when holding this promise, you don't know its data yet, but you have the reference to the promise which enables you to be notified whenever the data arrives:

{title="index.js",lang="javascript"}
~~~~~~~
// made up function which returns a promise
const promise = getAsynchronousData();

promise.then((result) => {
  console.log(result);
});
~~~~~~~

A promise offers methods like `then()` which can be used to execute callback functions asynchronously whenever the data arrived successfully. Then the developer can display this data in the browser for example, whereas before there was only a loading spinner indicating that the data will arrive eventually. Other methods like `catch()` enable you to react on errors whenever the server fails to return the data.

Usually we do not create a Promise from scratch as we will see later when we will be requesting data for real. However, because we have no backend application with data at the moment, we will create a Promise with the help of a callback function: The callback function gives us access to parameters such as the `resolve()` function which enables us to fill the promise with data. In addition, we are using a timer to fake a delay.

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

  const artificialDelay = 3000;

  setTimeout(() => resolve(data), artificialDelay);
});
~~~~~~~

With this promise at our hand, which usually comes from a backend application where we do not know the data in advance, we can register a callback function as argument of the promise's `then()` method which executes whenever the data resolves successfully:

{title="index.js",lang="javascript"}
~~~~~~~
promise.then((result) => {
  console.log(result);
});
~~~~~~~

There may be two questions popping up in your head. First, you may be wondering why we need the `setTimeout()` method. In our Promise, we need the timeout to create an artificial delay. Without the timeout, the promise would resolve immediatly; which is fine and works too, but which doesn't mimic the client-server communication behavior where it takes time until data arrives on a client from a remote server.

Second, you may be wondering why we are not just using the `setTimeout()` method without a Promise like we have seen it in a previous section. While we could create the artificial delay this way, we wouldn't hold any variable as reference which represents the promised data. By having a promise at our hand after we make a request to a server, we can move this promise like any other value around (e.g. as argument for a function) and call methods (e.g. `then()` and `catch()`) on it.

Sometimes a request to a server will fail, for example when the data cannot be found or a user isn't authorized to see the data. Then we do not get any data, but an error. We can mimic this behavior with a Promise as well by using the `reject()` instead of the `resolve()` function. In addition, we can create error objects in JavaScript by using the built-in Error object:

{title="index.js",lang="javascript"}
~~~~~~~
const promise = new Promise((resolve, reject) => {
  const error = new Error('Not authorized.');
  const artificialDelay = 3000;

  setTimeout(() => reject(error), artificialDelay);
});
~~~~~~~

Next we can react to rejecting promises with the promise's `catch()` method:

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

Promises can be chanined as well. So usually when using `then()` and `catch()` to handle successful and errornous asynchrnous data requests, you will chain both onto a promise:

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

After all,

### Exercises:

* TODO QUESTION Cannot be found 404, not authorized 401
* Read more about [Promises in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise).
  * See more examples in action about [Promises](https://javascript.info/promise-basics).
