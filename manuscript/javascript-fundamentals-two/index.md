# JavaScript Fundamentals: Part II

So far, you have learned about variables and values, their associated data types, implicit type coercion and explicit type conversion, and a few control structures such as the if-else statement in JavaScript. That's already 25% through the fundamentals of JavaScript. In the following 25%, you will learn about extracting reusable parts of code from your program with functions and more complex data structures beyond primitives such as objects and arrays.

## Functions

Everything you have written so far in JavaScript can be called *a program* (also called routine in programming, but rarely in JavaScript). However, sometimes you want to extract parts of a program (also called subroutine in programming) to reuse them without writing them twice. Functions can be used to extract these parts, which become reusable and executable.

{title="index.js",lang="javascript"}
~~~~~~~
function askAndSayMyName() {
  console.log("What's your name?");
  console.log('I am Robin Wieruch!');
}
~~~~~~~

A **function declaration** starts with the `function` keyword, a descriptive name for this function, and an opening and closing parantheses. Everything that follows inside of the curly braces is the code which should run when this function gets called. Hence functions are like variables, except that they do not store any values, but instead code which runs when someone calls the function:

{title="index.js",lang="javascript"}
~~~~~~~
// function declaration
function askAndSayMyName() {
  console.log("What's your name?");
  console.log('I am Robin Wieruch!');
}

// function call
askAndSayMyName();

// function call
askAndSayMyName();
~~~~~~~

Calling a function (also refered to as running/executing/invoking a function) is as straightforward as using the function's name with added paranthaseses at the end. In the last example, you can already see how this function allowed us to reuse code, because otherwise we would have written repetetive code as the next example shows:

{title="index.js",lang="javascript"}
~~~~~~~
// repetition 1
console.log("What's your name?");
console.log('I am Robin Wieruch!');

// repetition 2
console.log("What's your name?");
console.log('I am Robin Wieruch!');
~~~~~~~

If there is nothing going in to a function, it could be seen as a blackbox which would only be useful to execute **static code**. Fortunately we can pass in so called **arguments** from the outside to our function which can be used in the inside of the function as so called **parameters**:

{title="index.js",lang="javascript"}
~~~~~~~
function askAndSayMyName(parameter) {
  console.log("What's your name?");
  console.log(`I am ${parameter}!`);
}

const argument = 'Robin Wieruch';

askAndSayMyName(argument);
~~~~~~~

Equipping a function with parameters, using those parameters within the function, and passing arguments from the outside enables writing **dynamic code** in functions. It's worth to know that arguments and parameters do not need to share the same name, just the order matters when using more than one argument/parameter pair:

{title="index.js",lang="javascript"}
~~~~~~~
function askAndSayMyName(fullName) {
  console.log("What's your name?");
  console.log(`I am ${fullName}!`);
}

const myName = 'Robin Wieruch';

askAndSayMyName(myName);
~~~~~~~

As you can see, we declare our function, a variable `myName` and call the function with the variable as argument. Inside of the function, the variable is used as parameter called `fullName` which is only usable within this function. As mentioned earlier, it's also possible to pass more than one argument to functions:

{title="index.js",lang="javascript"}
~~~~~~~
function askAndSayMyName(firstName, lastName) {
  console.log("What's your name?");
  console.log(`I am ${firstName} ${lastName}!`);
}

const myFirstName = 'Robin';
const myLastName = 'Wieruch';

askAndSayMyName(myFirstName, myLastName);
~~~~~~~

At this time, you may have tried to use variables from the outside in a function without passing them as arguments. This works due to the concept of **scoping** (which we will learn more about later):

{title="index.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
const myFirstName = 'Robin';
const myLastName = 'Wieruch';
# leanpub-end-insert

function askAndSayMyName() {
  console.log("What's your name?");
# leanpub-start-insert
  console.log(`I am ${myFirstName} ${myLastName}!`);
# leanpub-end-insert
}

askAndSayMyName();
~~~~~~~

However, it's a best practice to have functions that only use variables which are passed as arguments to them. Under certian circumstances, you can use variables which are declared outside of a function without passing them as arguments, but try to avoid it for embracing best practice coding habits from the beginning when starting out with JavaScript.

While there exists an (optional) input for functions in the form of parameter(s), there also exists an (optional) output for functions in the form of a **return statement**:

{title="index.js",lang="javascript"}
~~~~~~~
function getFullName(firstName, lastName) {
  const fullName = `${firstName} ${lastName}`;

  return fullName;
}

const myFirstName = 'Robin';
const myLastName = 'Wieruch';

const myFullName = getFullName(myFirstName, myLastName);

console.log(myFullName);
~~~~~~~

In this example, we interpolate the first and last name of a person to their full name and store it in a variable called `fullName`. Then we return this variable from the function. Now when someone calls this function, we can assign the returned value from this called function to a variable (here: `myFullName`). What's also possible is returning the value right away without declaring the so called **intermediate variable**:

{title="index.js",lang="javascript"}
~~~~~~~
function getFullName(firstName, lastName) {
# leanpub-start-insert
  return `${firstName} ${lastName}`;
# leanpub-end-insert
}

const myFirstName = 'Robin';
const myLastName = 'Wieruch';

const myFullName = getFullName(myFirstName, myLastName);

console.log(myFullName);
~~~~~~~

Since arguments are mostly values stored in variables, it's also possible to pass values to functions (1) or to use the returned value right away (2):

{title="index.js",lang="javascript"}
~~~~~~~
function getFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

const robin = getFullName('Robin', 'Wieruch'); // (1)
console.log(robin);

console.log(getFullName('Sarah', 'Finnley')); // (2)
~~~~~~~

Functions allow us to write *[generic code](https://en.wikipedia.org/wiki/Generic_programming)* with the concept of *"fill in the blanks"* by using parameters. From the outside, we can call these functions and fill in the blanks with *specific* arguments while returning something specific (e.g. full name of a user) from the function with the help of the return statement.

![](images/function-anatomy.png)

Functions enhance the concept of **DRY** (Don't repeat yourself) in code. Everything that can be extracted as function, because it is reused or used at multiple places of the application, helps us to keep the code maintainable and readable for others. Actually before we have learned about functions, we have already used one built-in function all the time: `console.log()`.

Functions are one of the most important **structural data types** in JavaScript. As a best practice, try to keep function names as descriptive as possible and keep functions scoped to one utility (e.g. `getFullName()` and `multiplyNumbers()` should be two distinct functions). As a beginner to coding, this may be one of these times that you feel overwhelmed by the sheer amount of information. However, take your time to grok the concept of a function and experiment with it in your code environment.

### Exercises:

* Read more about [functions in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions).
* Read more about [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself).
* Create a function which adds two numbers and returns the sum of it.
* Create a function which mulitplies two numbers and returns the product of it, but this time make sure that the code still runs without flaws if a developer inputs strings which represent numbers instead of numbers as arguments. Thus take care of the data type conversion internally before using the arithmetic operator.
* Create a function which tells us based on one's professional years as a developer (e.g. takes `yearsAsDeveloper` number as argument) whether this person is a developer (e.g. returns `isDeveloper` boolean).
* Question: What's `typeof getFullName`?`
  * Answer: function.
* Question: What's `typeof getFullName('Robin', 'Wieruch')`?`
  * Answer: string. Becuase we are calling the function and return a string, the typeof operator evaluates the returned string.
* Question: What happens if we only provide one argument to a function which accepts two arguments (e.g. `getFullName('Robin')`)?
  * Answer: All arguments not provided will lead to paramaters being `undefined`.

## Function Expressions

There are many more things to know about functions, although not all of them are must-knows for a JavaScript beginner. However, the book attempts to address these concepts early on, because it will make use of them throughout the book on certain occasions when there are other topics at stake. So don't shy away if you don't understand all of the following concepts for functions right away, but keep them in the back of your head and refer back to them when they are used later.

Functions in JavaScript are powerful, because, in contrast to many other programming languages, functions are treated as first-class citizens in JavaScript. By definition, a function becomes a first-class citizen when it can be stored in a variable and thus becomes a **function expression**. In contrast to a function declaration, a function expression can be used to carry a function around as a variable:

{title="index.js",lang="javascript"}
~~~~~~~
const hasExperience = function getExperience(yearsAsProfessional) {
  const isExperienced = yearsAsProfessional > 0;

  return isExperienced;
};

const yearsAsDeveloper = 7;
const isDeveloper = hasExperience(yearsAsDeveloper);

console.log(isDeveloper);
// true
~~~~~~~

A function is called an **anonymous function** when it has no name. This works for function expressions, because the function gets called with the name of the variable anyway. However, when debugging the code in the case of a bug, anonymous functions are more difficult to spot than named functions:

{title="index.js",lang="javascript"}
~~~~~~~
const hasExperience = function (yearsAsProfessional) {
  return yearsAsProfessional > 0;
};
~~~~~~~

Function expressions have subtle differences compared to function declarations. While for a function expression the function gets created when the code reaches the variable declaration, for the function declaration the function gets created once at the start:

{title="index.js",lang="javascript"}
~~~~~~~
// works due to function declaration

console.log(multiplyThis(3, 4));

function multiplyThis(a, b) {
  return a * b;
}

// does not work due to function expression

console.log(multiplyThat(3, 4));
// ReferenceError: Cannot access 'multiplyThat' before initialization

const multiplyThat = function (a, b) {
  return a * b;
};
~~~~~~~

You will learn more about this concept called **hoisting** which enables this behavior later. Anyway, function expressions have their right to exist though. For example, you can use a function expression to create a function conditionally and thus only create one of both functions when the conditional runs:

{title="index.js",lang="javascript"}
~~~~~~~
const isDeveloper = true;

const getConversationStarter = isDeveloper
  ? function () {
      return console.log('What programming languages do you speak?');
    }
  : function () {
      return console.log('What languages do you speak?');
    };

getConversationStarter();
~~~~~~~

As a rule of thumb: Use function declarations whenever you can, because you will run into less bugs (due to their early instantiation). In addition, because functions are such a fundamental building block in JavaScript code, function declarations are more eye-catching and therefore more readable than their function expression counterparts. However, in contrast function expressions can signal that you want to pass this function around as value (e.g. passing a function into another function as argument). So get used to both, function declaration and function expressions, because you will see both of them out there in the wild. Especially when it comes to callback functions, as we will learn later, you will more often see function expressions.

### Exercises:

* Read more about [functions in JavaScript](https://javascript.info/function-basics).
* Read more about [function expressions](https://javascript.info/function-expressions).

## Working with Functions

In this section, we will dive deeper into functions and how we can use them as developers. Before we have only worked with one function, however, once programs become more complex, you will most likely use more than one function side by side or composed into each other. Let's take the following example of a function which creates a text for us:

{title="index.js",lang="javascript"}
~~~~~~~
function getConversationStarter(firstName, lastName, isDeveloper) {
  const welcome = `Hi ${firstName} ${lastName}!`;

  const question = isDeveloper
    ? 'What programming languages do you speak?'
    : 'What languages do you speak?';

  return `${welcome} ${question}`;
}

const text = getConversationStarter('Robin', 'Wieruch', true);

console.log(text);
~~~~~~~

This function takes various arguments as input and uses them internally as parameters to create a text with a certain condition. Since we are assigning variables conditionally, we prefer using the ternary operator instead of the if-else statement. As exercise, try to write this function with if-else statements instead of the ternary operator and experience yourself how much more verbose it gets this way. Hint: You have to use `let` instead of `const` for `question`, declare but not initialize it, and initialize it with conditionally within the if and else blocks.

The function for creating our conversation starter has a too many responsibilities. A good practice is splitting responsibilities into multiple functions for having smaller functions to reason about. They become functions with more atomic responsibilities:

{title="index.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
function getName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}
# leanpub-end-insert

# leanpub-start-insert
function getQuestion(isDeveloper) {
  return isDeveloper
    ? 'What programming languages do you speak?'
    : 'What languages do you speak?';
}
# leanpub-end-insert
~~~~~~~

In this case, our function from the start could call these other smaller functions and aggregate their return values:

{title="index.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
function getConversationStarter(firstName, lastName, isDeveloper) {
  const fullName = getName(firstName, lastName);
# leanpub-end-insert
  const welcome = `Hi ${fullName}!`;
# leanpub-start-insert
  const question = getQuestion(isDeveloper);
# leanpub-end-insert

  return `${welcome} ${question}`;
}
~~~~~~~

As alternative, we could also evaluate one of the function's return values directly in the string interpolation, because we do not need the `fullName` variable anywhere else and we don't get any benefit to give it a descriptive name here, because the function already has a decriptive name:

{title="index.js",lang="javascript"}
~~~~~~~
function getConversationStarter(firstName, lastName, isDeveloper) {
# leanpub-start-insert
  const welcome = `Hi ${getName(firstName, lastName)}!`;
# leanpub-end-insert
  const question = getQuestion(isDeveloper);

  return `${welcome} ${question}`;
}
~~~~~~~

Now one could argue to go all the way and interpolate both directly in the return statement. But even though this would make the function's body more concise, it would make it in many eyes less readable:

{title="index.js",lang="javascript"}
~~~~~~~
function getConversationStarter(firstName, lastName, isDeveloper) {
  return `
    Hi ${getName(firstName, lastName)}!
    ${getQuestion(isDeveloper)}
  `;
}
~~~~~~~

After all, what you can see from this example is that functions can call other functions. In a developer's words it's called "breaking down a problem into smaller problems" and therefore smaller solutions whereas each solution stands for one function. In your career as a JavaScript developer, you will often see functions calling other functions.

Reusability is another benefit of extracting functions from other functions. For example, another part of our program could reuse the `getName()` function now:

{title="index.js",lang="javascript"}
~~~~~~~
const robinText = getConversationStarter('Robin', 'Wieruch', true);
console.log(robinText);

const sarah = getName('Sarah', 'Finnley');
const sarahText = `Hi, I'm ${sarah}.`;
console.log(sarahText);
~~~~~~~

If we would want to introduce an optional nickname, we could extend everything with this additional argument:

{title="index.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
function getName(firstName, lastName, nickname) {
  if (nickname) return nickname;
# leanpub-end-insert

  return `${firstName} ${lastName}`;
}

...

function getConversationStarter(
  firstName,
  lastName,
# leanpub-start-insert
  nickname,
# leanpub-end-insert
  isDeveloper
) {
# leanpub-start-insert
  const welcome = `Hi ${getName(firstName, lastName, nickname)}!`;
# leanpub-end-insert
  const question = getQuestion(isDeveloper);

  return `${welcome} ${question}`;
}

const robinText = getConversationStarter(
  'Robin',
  'Wieruch',
# leanpub-start-insert
  'Hood',
# leanpub-end-insert
  true
);
~~~~~~~

By breaking down functions onto smaller problem spaces, we can compose more complex functions out of these smaller functions (e.g. `getConversationStarter()`) or reuse functions in other areas of our code (e.g. `getName()`). Challenge yourself by writing a larger function and by extracting smaller functions from it.

### Exercises:

* Extend the example from before with more conditional text for the conversation which may or may not be passed on additional arguments that are passed to the function.
* Come up with problems that are solved by functions yourself. If you have created one bigger function, split it into smaller functions and aggregate their result in one main function.

## Classes

Even though the construct of a **class** is a shared concept across most programming languages, it was only introduced in modern JavaScript. Previously it was only possible to a create class like construct by using JavaScript's **prototype chain** ([in-depth article, but optional read at this stage](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)). While the prototype chain was known to many JavaScript developers back in the days, it's not as often mentioned these days anymore, because we are mostly using classes in JavaScript instead.

A class is used in object-oriented programming languages. Since JavaScript is a **multi paradigm programming language**, using the **object-oriented programming (OOP)** paradigm in JavaScript is a popular choice. Another popular paradigm is called **functional programming (FP)** which doesn't make use of classes.

Let's get started with a class that represents a person by using the `class` keyword:

{title="index.js",lang="javascript"}
~~~~~~~
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
}
~~~~~~~

In this example, we see a **class declaration** for a class with the name Person. After a class declaration, we can use this class with the `new` keyword to create an **instance**, in this case a person instance or instance of Person, from it:

{title="index.js",lang="javascript"}
~~~~~~~
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
}

# leanpub-start-insert
const robin = new Person('Robin', 'Wieruch');
# leanpub-end-insert

# leanpub-start-insert
console.log(robin);
// Person { firstName: 'Robin', lastName: 'Wieruch' }
# leanpub-end-insert
~~~~~~~

Except for the `new` keyword and the uppercase naming convention for a class, using a class to create an instance from it feels quite similar to using a function. One could say that a function is more ephemeral though, because by calling the class with the `new` keyword, we **instantiate** one or multiple (none ephemeral) instances from it:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = new Person('Robin', 'Wieruch');
const sarah = new Person('Sarah', 'Finnley');

console.log(robin);
// Person { firstName: 'Robin', lastName: 'Wieruch' }
console.log(sarah);
// Person { firstName: 'Sarah', lastName: 'Finnley' }
~~~~~~~

Think of a class like a factory for a thing: A class is like a cookie mold for many cookies. Another example: Once an architect has done the blueprint for a house (class declaration), builders can create many houses (instances) from it.

![](images/class-analogy.png)

Functions in classes are called **methods** or **class methods**. The **constructor** is one of these methods which is mandatory, because it runs when this class gets instantiate with the `new` keyword. The constructor method accepts optional arguments from the outside, here `firstName` and `lastName`, which are internally used as parameters. In this example, the parameters are used to assign a class' **instance properties** `firstName` and `lastName` by using the `this` keyword. In the context of a class, `this` means the instantiated class instance itself. Read it like "given these paramaters I (the class) assign them as values to this new instance of myself". Continuing from here, a developer can evolve a class with more instance properties and class methods:

{title="index.js",lang="javascript"}
~~~~~~~
class Person {
# leanpub-start-insert
  constructor(firstName, lastName, isDeveloper) {
# leanpub-end-insert
    this.firstName = firstName;
    this.lastName = lastName;
# leanpub-start-insert
    this.isDeveloper = isDeveloper;
    this.nickname = null;
# leanpub-end-insert
  }

# leanpub-start-insert
  getFullName() {
    return `${this.firstName} ${this.lastName}`;
  }

  setNickname(nickname) {
    this.nickname = nickname;
  }

  getRate(isShortTermProject) {
    if (this.isDeveloper && isShortTermProject) {
      return '$250.00';
    } else if (this.isDeveloper && !isShortTermProject) {
      return '$120.00';
    } else {
      return '$25.00';
    }
  }
# leanpub-end-insert
}

# leanpub-start-insert
const robin = new Person('Robin', 'Wieruch', true);

console.log(robin.nickname);
// null
robin.setNickname('Hood');
console.log(robin.nickname);
// 'Hood'

console.log(robin.getFullName());
// 'Robin Wieruch'

console.log(robin.getRate(true));
// '$250.00'
# leanpub-end-insert
~~~~~~~

We can see how a class helps us to encapsulate information (instance properties) and behavior (class methods) into one construct. Only when we create an instance of a class with its constructor, we can read its properties or call its methods (like functions by adding parantheses). The `.` notation (read: **dot notation**) is used to access an instance's properties and methods, which will work very similar for JavaScript objects as we will learn later.

![](images/class-anatomy.png)

It's worth to say that when using modern JavaScript with everyday frameworks such as React.js, you will only rarely see classes though. In order to encapsulate information like a class does for us, you would most often use a JavaScript object instead. However, understanding the concept of a class is helpful for many topics that follow in this book.

### Exercises:

* Add more instance properties and class methods to the Person class. Begin with your personal variables that you came up with earlier.
  * Create many person instances and use their methods.
* Come up with another class declaration for an Aircraft, Cat, or SmartHouse.
* Question: What does `typeof Person` return?
  * Answer: It returns `function`. Essentially a class is a function in disguise.
* Read more about classes in JavaScript [here](https://javascript.info/class) and [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes).
  * If there exists the concept of class declaration (similar to function declaration), find out whether there exists the concept of class expressions (similar to function express) as well.

## Methods of Primitives

Primitives (e.g. string, number, boolean) in JavaScript are supposed to represent only a value. However, you may have noticed that primitives have special behavior attached to them. For example, all string primitives give us access to the same **built-in string methods** such as `toUpperCase()`:

{title="index.js",lang="javascript"}
~~~~~~~
const fullName = 'Robin Wieruch';

console.log(fullName.toUpperCase());
// 'ROBIN WIERUCH'

console.log('Sarah Finnley'.toUpperCase());
// 'SARAH FINNLEY'
~~~~~~~

By using the `.` notation we can call methods on string instances. In this case, we want to have the string transformed to its upper case representation. However, as an important fact, even though we call this built-in method, the value itself hasn't been changed afterward:

{title="index.js",lang="javascript"}
~~~~~~~
const fullName = 'Robin Wieruch';

console.log(fullName.toUpperCase());
// 'ROBIN WIERUCH'

console.log(fullName);
// 'Robin Wieruch'
~~~~~~~

Functions on primtives are called methods the same way as functions on classes are called methods. They follow the same terminology, because they are attached to a data type where they are not mere functions anymore. Hence the term methods and in this case built-in methods, because you do not need to define these methods yourself but they come with the programming language JavaScript.

Similar to JavaScript classes, there are not only methods on JavaScript primitives which can be accessed by using the dot notation, but also properties. The `length` property is a popular one for string primitives but also other data types. In the case of a string, the `length` returns the sum of all characters:

{title="index.js",lang="javascript"}
~~~~~~~
const fullName = 'Robin Wieruch';

console.log(fullName.length);
// 13
~~~~~~~

At this point, you may be thinking that strings (and other primitives) are not mere primitives, but rather something more complex such as JavaScript classes. In addition, you may have noticed the class equivalents for primitves too, which can be used to create instances of these primitives. However, they are rarely used in reality:

{title="index.js",lang="javascript"}
~~~~~~~
const fullName = new String('Robin Wieruch');

console.log(fullName);
// [String: "Robin Wieruch"]
~~~~~~~

As you can see from the output, this creates a string instance rather than a string primitive. While the former is rarely used in JavaScript, the latter, called **string literal** in this case, will be your bread and butter. Equivalents are boolean literal and number literal which you have used before, but also object and array literals as you will get to know later. However, both ways to create a variable of a certain type can be used almost interchangeably in most situations which raises the important fact that primitives can be more powerful beings by using their respective counterparts (e.g. `String()`).

With this knowledge, we can explain how properties (e.g. `length`) and methods (e.g. `toUpperCase()`) work on primitives: If a developer accesses a method on a string for example, JavaScript with the help of type coercion creates a more powerful `String` as counterpart where we can access the method (or properties). When the method has been called, this counterpart gets discared and we are left with only the primitive again. However, as the following example shows, we cannot retrace this behavior properly by using logging and the `typeof` operator:

{title="index.js",lang="javascript"}
~~~~~~~
const fullName = 'Robin Wieruch';

console.log(typeof fullName);
// string

console.log(fullName.toUpperCase());
// ROBIN WIERUCH

console.log(typeof fullName);
// string
~~~~~~~

Type coercion as we have learned before is a powerful concept in JavaScript. In the case of methods (and properties) on primitives, it shows again how it can be used to create a more powerful programming language where we can access more than mere values but also their respective properties and methods.

### Exercises:

* Read more about [methods on primitives in JavaScript](https://javascript.info/primitives-methods).
* Find more examples of [built-in string methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#instance_methods).
  * Find and use the equivalent built-in string method for `toUpperCase()`.
    * Answer: The equivalent method is called `toLowerCase()`.
  * Question: Find and use the equivalent built-in string method for string concatenation/interpolation which you have learned about in a previous section.
    * Answer: The equivalent method is called `concat()`.
  * Use more popular built-in string methods such as `includes()`, `slice()`, `split()`, `substring()`, and `trim()`.
    * Question: Find out the difference between `indexOf()` and `lastIndexOf()`?
      * Answer: While `indexOf()` finds the first index of the occurence, `lastIndexOf()` finds the last index of it.
    * Question: Can it happen that `indexOf()` returns `-1`.
      * Answer: Yes, if no occurence is found.
    * Question: Can `indexOf()` be used to determine for an if-else condition whether a string occured in another string? Is there an alternative to it?
      * Answer: Yes. If the `indexOf()` method returns something greater than `-1` as index, the string is included. As alternative one could use the `includes()` method.
    * Question: Find out the difference between `replace()` and `replaceAll()`?
      * Answer: While `replace()` replaces only one occurence, `replaceAll()` replaces all of them.

## Objects

Up to this point, you have learned about primitive data types such as strings, numbers and booleans. One way of encapsulating these into one entity has been the JavaScript class. For example, a `Person` class can have properties such as `firstName`, `lastName` and a method such as `getFullName()`. However, an alternative and more widely used structural data type for this kind of work is the **JavaScript object**:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
};
~~~~~~~

In this example, an object gets declared as variable with the name `robin` whereas everything in the curly braces are **properties** of this object. While the left-hand side of these properties is called **object keys** (also called: property names, names, or keys, here: `firstName`, `lastName`, `yearBirth`, `isDeveloper`), the right-hand side is called **object values** (also called: values). Essentially an object is a wrapper around a bunch of values (of any data type) which are grouped into an **entity** of a specific **domain** (e.g. person domain).

![](images/object-anatomy.png)

Therefore, we can have distinct entities represented by objects *without* declaring all their primitive values as variables (as we did before) one by one:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
};

const sarah = {
  firstName: 'Sarah',
  lastName: 'Finnley',
  yearBirth: 1988,
  isDeveloper: false,
};
~~~~~~~

If you want to access a **property** of an object, you can use the already learned **dot notation** or the alternative **bracket notation**:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
};

# leanpub-start-insert
console.log(robin.firstName); // dot notation
console.log(robin['isDeveloper']); // bracket notation
# leanpub-end-insert
~~~~~~~

By using a property name, one can access its value. While the dot notation should be the default, the bracket notation can be used to evaluate expressions if needed:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
};

# leanpub-start-insert
const nameKey = 'Name';
# leanpub-end-insert

# leanpub-start-insert
console.log(robin['first' + nameKey]);
console.log(robin['last' + nameKey]);
# leanpub-end-insert
~~~~~~~

Another example for the special use of having the bracket notation instead of the dot notation are cases where we do not know the property name in advance, like in a function:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  nickname: 'Hood',
  yearBirth: 1991,
  isDeveloper: true,
};

function getNameOfPersonByKey(person, key) {
  if (key === 'fullName') {
    return person.firstName + ' ' + person.lastName;
  }

  if (key === 'nickname' && !person.nickname) {
    return 'This person has no nickname.';
  }

  return person[key];
}

console.log(getNameOfPersonByKey(robin, 'fullName'));
console.log(getNameOfPersonByKey(robin, 'firstName'));
console.log(getNameOfPersonByKey(robin, 'nickname'));
~~~~~~~

Same way as using mere primtives, an object's properties can be used to interpolate whole sentences. Try the following and add more properties about your person to the object and extend the sentence yourself:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
};

console.log(
  `Hi, my name is ${robin.firstName} ${robin.lastName}, I am ${
    robin.isDeveloper ? 'a developer' : 'not a developer'
  } and I am ${2021 - robin.yearBirth} years old.`
);
~~~~~~~

Since objects can have any data type as property, they can have (anonymous) functions (called **methods** in objects) and objects (so called **nested objects**) too. While methods in objects are not often used, using nested objects is a common theme when developing with JavaScript:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
# leanpub-start-insert
  getAge: function (year) {
    return year - 1991;
  },
  kid: {
    firstName: 'Liam',
    lastName: 'Wieruch',
  },
};
# leanpub-end-insert

# leanpub-start-insert
console.log(robin.kid.firstName);
console.log(robin.kid.lastName);
console.log(robin.getAge(2021));
# leanpub-end-insert
~~~~~~~

Note how one can access an nested object's property by using multiple dot (or bracket) notations (e.g. `robin.kid.firstName`). Furthermore, notice how a method of an object can be called like any other function, it just needs to be accessed by the dot notation first.

The last example violated the principle of DRY, because we had to define the value `1991` twice in our object. Let's change this by using the `this` keyword, which we have used before in our JavaScript class, to get a reference to the instance (here: object) itself and therefore to its properties:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
  getAge: function (year) {
# leanpub-start-insert
    return year - this.yearBirth;
# leanpub-end-insert
  },
  kid: {
    firstName: 'Liam',
    lastName: 'Wieruch',
  },
};
~~~~~~~

Another example would be getting an introduction for this object by calling a method on it. We did this before by interpolating the object's properties into a text. This time we will do it with a method though:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
  getIntroduction: function (year) {
    return `Hi, my name is ${this.firstName} ${this.lastName}, I am ${
      this.isDeveloper ? 'a developer' : 'not a developer'
    } and I am ${year - this.yearBirth} years old.`;
  },
};

console.log(robin.getIntroduction(2021));
~~~~~~~

Now we know how to declare and how to access an object. While we created all the objects with the **object literal notation** (also called initializer notation, literal notation, object literal or literal) in our examples, alternative to this would be the `new Object()` or `Object.create()` syntaxes. Both are only rarely used though, so you can stick to the literal notation for most use cases.

Once declaring and accessing objects works, it should also be possible to assign or re-assign properties to an object. Both dot and bracket notation work, and they also work for nested objects, however, the dot notation should be the default as mentioned before:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  hasKids: false,
};

robin.nickname = 'Hood';
robin.hasKids = true;

console.log(robin.nickname);
// 'Hood'
console.log(robin.hasKids);
// true
~~~~~~~

For a beginner, a JavaScript object seems to be similar to a JavaScript class considering the use cases. However, objects are usually the default way to go for encapsulating related information into one entity. In contrast, classes are rather used when leaning more towards object-oriented programming in JavaScript. After all, objects are the perfect fit for collecting information in one entity that's related to another.

### Exercises:

* Read more about [objects in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects).
  * Read more about [Object initializer in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer).
  * See more examples in action about [objects in JavaScript](https://javascript.info/object).
* Read more about [object methods in JavaScript](https://javascript.info/object-methods).
* Question: Instead of the `const` keyword, which keyword to declare an object could be used to re-assign it to a new value?
  * Answer: `let` and `var` whereas `let` is the preferred way in modern JavaScript.
* Question: What happens if you access a property of an object that isn't there.
  * Answer: You get `undefined`, because it isn't defined.
* Question: How would you access a nested object's property by using the bracket instead of the dot notation?
  * Answer: Taken the example, `robin['kid']['firstName']` would work. Still note that using the dot notation is preferred if no expression is needed.
* Question: What's the output when logging `this` to the console in an object's method?
  * Answer: One will get the whole object printed to the console, because `this` refers to the object from where the method is called.
* Question: What's `typeof person`?
  * Answer: An object is classified as object data type. While the object data type holds many kinds of structural data types under its umbrella (e.g. object, array), the object itself is one specific representation of it.
* Question: Declare a class with the name `Person` and instantiate an instance with the variable name `robin` from it. What's `typeof robin`?
  * Answer: object. An instance of a class is classified under the umbrella of the object data type. So if one says "an instance of a class", you can also read it as "an object of a class".
* Question: What's `typeof null`?
  * Answer: object. Indeed this is a fundamental bug in JavaScript. Read more, if you want to explore [how it came to this bug](https://2ality.com/2013/10/typeof-null.html).
* Question: Why is it possible to re-assign an object's property even though it has been declared with `const` and not `let`?
  * Answer: The declaration with `const` only enforces that the variable itself cannot get a new reference (read: re-assigned). However, the underlying properties can change. The same will be the case for JavaScript arrays.

## Arrays

An **array** in JavaScript represents a list of items. Informally it's also called **list** or **list of items**. While objects (from the last section) represent one entity (here: object) with certain properties defined in curly braces, arrays represent multiple entities (here: strings, numbers, but also objects) in a list defined in brackets.

{title="index.js",lang="javascript"}
~~~~~~~
const firstNames = ['Robin', 'Sarah', 'Esther'];
~~~~~~~

Before we had arrays, one may have defined these names the following way with primitves:

{title="index.js",lang="javascript"}
~~~~~~~
const firstNameOne = 'Robin';
const firstNameTwo = 'Sarah';
const firstNameThree = 'Esther';
~~~~~~~

Now we can put these into a list, like we have done before by comma separating the values, or like the following example shows by using comma separated variables:

{title="index.js",lang="javascript"}
~~~~~~~
const firstNameOne = 'Robin';
const firstNameTwo = 'Sarah';
const firstNameThree = 'Esther';

const firstNames = [firstNameOne, firstNameTwo, firstNameThree];
~~~~~~~

Often inserting the values directly like we did before makes more sense though, because we want to get away from defining numbered variables like `firstNameOne` just to reference them later in an array anyway. That's why we have arrays in the first place. Apart from declaring an array with an **array literal notation**, one could also use `new Array()` as alternative. The latter are only rarely used though, so stick to the literal notation for now:

{title="index.js",lang="javascript"}
~~~~~~~
const lastNames = ['Wieruch', 'Finnley', 'Shaw'];
~~~~~~~

In contrast to objects, arrays are a list of similar items (persons, fruits, aircrafts, prime numbers, ages). Even though it's possible to mix data types in an array, it's not commonly done. So usually one ends up with an array with one kind of data type in a list. So whenever you have a mix of data types in an array, ask yourself whether an object wouldn't be a better suited for this use case:

{title="index.js",lang="javascript"}
~~~~~~~
// good
const primeNumbers = [2, 3, 5, 7];

// bad
const robinAsArray = ['Robin', 'Wieruch', true, 1991];

// better
const robinAsObject = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  isDeveloper: true,
  yearBirth: 1991,
};
~~~~~~~

As mentioned, arrays can hold a list of objects too. The last examples have shown you lists of first names whereas each first name likely relates to a last name. So we can put these relations into objects and then put these objects into an array:

{title="index.js",lang="javascript"}
~~~~~~~
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
};

const sarah = {
  firstName: 'Sarah',
  lastName: 'Finnley',
};

const esther = {
  firstName: 'Esther',
  lastName: 'Shaw',
};

const persons = [robin, sarah, esther];
~~~~~~~

As before, we can define them as inline values too, so that you do not need to specify each person as a standalone variable. Furthermore, one can access items from an array by using the **bracket notation**. Since we do not have property names like for objects, we can access arrays only by their indexes (read: position of an item in the list):

{title="index.js",lang="javascript"}
~~~~~~~
const persons = [
  {
    firstName: 'Robin',
    lastName: 'Wieruch',
  },
  {
    firstName: 'Sarah',
    lastName: 'Finnley',
  },
  {
    firstName: 'Esther',
    lastName: 'Shaw',
  },
];

console.log(persons[0]);
// { firstName: 'Robin', lastName: 'Wieruch' }
console.log(persons[1]);
// { firstName: 'Sarah', lastName: 'Finnley' }
console.log(persons[2]);
// { firstName: 'Esther', lastName: 'Shaw' }
~~~~~~~

You can see that arrays are zero indexed like most things in JavaScript. Hence in order to access the first person in the array, you need to get the `0` and not the `1` indexed item. Note that we cannot use the dot notation for accessing indexed items in arrays, because the dot notation does not work for property names that start with a digit (e.g. `0` or `4thOfJuly`). It's the same for objects: If you have an object `holidays` with the property name `4thOfJuly`, you can only access it with `holidays['4thOfJuly']` and not `holidays.4thOfJuly`.

![](images/array-anatomy.png)

Once declaring and accessing arrays works, it should also be possible to assign or re-assign an item in a list. It goes the same way as for other variables, only that we (re)-assign specific items by their indexes in an array:

{title="index.js",lang="javascript"}
~~~~~~~
const firstNames = ['Robin', 'Sarah', 'Esther'];

firstNames[0] = 'Liam';

console.log(firstNames);
// [ 'Liam', 'Sarah', 'Esther' ]
console.log(firstNames[0]);
// 'Liam'

firstNames[3] = 'Peter';

console.log(firstNames);
// ['Liam', 'Sarah', 'Esther', 'Peter'];
console.log(firstNames[3]);
// 'Peter'
~~~~~~~

An array is classified under the umbrella of the object data type. Except for primitives like string, number and boolean, the only more complex data types are function and object. So essentially everything that doesn't fall under these data types is of type object (e.g. array). Since an array is an object in disguise, it's also possible to access built-in properties (and methods) of arrays:

{title="index.js",lang="javascript"}
~~~~~~~
const firstNames = ['Robin', 'Sarah', 'Esther'];

console.log(firstNames.length);
// 3
~~~~~~~

In this case, the `length` property returns us size of the array (which translates internally to "the highest index + 1"). Most often the `length` property is used to get the size of the list (previous example) or to get the last item of a list (next example):

{title="index.js",lang="javascript"}
~~~~~~~
const firstNames = ['Robin', 'Sarah', 'Esther'];

console.log(firstNames[firstNames.length - 1]);
// 'Esther'
~~~~~~~

Since an array falls under the data type of objects, there are not only properties attached to it, but also methods. Let's explore some of the more popular ones in this section. One of the first **built-in array methods** you will learn about is `push()` which adds a new item to end of a list:

{title="index.js",lang="javascript"}
~~~~~~~
const firstNames = ['Robin', 'Sarah', 'Esther'];

firstNames.push('Liam');

console.log(firstNames);
// ['Robin', 'Sarah', 'Esther', 'Liam']
console.log(firstNames.length);
// 4
~~~~~~~

Usually we are using `push()` whenever we want to add a new item to a list. In a previous example, we have assigned a new item directly by using an index (e.g. `firstNames[3] = 'Peter'`) which you will only rarely perform. In contrast to `push()`, the method `pop()` removes the last item from the list:

{title="index.js",lang="javascript"}
~~~~~~~
const firstNames = ['Robin', 'Sarah', 'Esther'];

firstNames.pop();

console.log(firstNames);
// ['Robin', 'Sarah']
console.log(firstNames.length);
// 2
~~~~~~~

Note that both methods modify the array without the need of assigning them to a new variable. We will learn more about this behavior later when speaking about **mutability vs immutability**. For now, just focus on the built-in array methods themsevles. In the exercise, you should try out more of them. Several of these array methods will come up during the next sections of the book though. For example, a popular one is `includes()` which will inform you whether a certain item is part of the list by returning a boolean:

{title="index.js",lang="javascript"}
~~~~~~~
const firstNames = ['Robin', 'Sarah', 'Esther'];

const hasSarah = firstNames.includes('Sarah');
const hasLiam = firstNames.includes('Liam');

console.log(hasSarah, hasLiam);
// true false
~~~~~~~

As a final example for this section, we will see how to remove a specific item from an array by using the `indexOf()` and `splice()` method:

{title="index.js",lang="javascript"}
~~~~~~~
const firstNames = ['Robin', 'Sarah', 'Esther'];

const index = firstNames.indexOf('Sarah');

console.log(index);
// 1

const removedItem = firstNames.splice(index, 1);

console.log(removedItem);
// [ 'Sarah' ]
console.log(firstNames);
// [ 'Robin', 'Esther' ]
~~~~~~~

While `indexOf()` finds the position (index) of "Sarah" in the array, splice separates a part from the array by using a start index as first argument and a count as second argument. Read it as: "How many items should be removed? 1, which is the second argument. And which item should be removed? Item with index 1, which is the first argument."

The array which represents a list of items is a complex yet powerful data structure in JavaScript. While JavaScript objects pair keys and values of a certain domain into one structure, arrays help us to collect related information in lists. There can be arrays of objects and there can be objects that have arrays as properties.

### Exercises:

* Read more about [arrays in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Array).
  * See more examples in action about [arrays in JavaScript](https://javascript.info/array).
  * Use popular built-in array methods such as `reverse()` and `join()`. We will explore more popular ones later.
  * How do the methods `shift()` and `unshift()` differ from `push()` and `pop()`?
  * Find out the difference between `slice()` and `splice()`.
* Question: Declare an array with two items and assign a new value `array[3]`. What's do you get if you print `array[2]` to the console?
  * Answer: undefined. We got two values in our array, one empty spot (`undefined` at the index of `2`), and one more value at the index of `3`.
* Question: What happens if you try to access an array's item by using the dot notation instead of the bracket notation?
  * Answer: Using something like `firstNames.0` will lead to a syntax error. Only bracket notation is allowed to access items in arrays, because they are indexed with a digit where bracket notation is needed (same as for objects).
* Question: How would you create a multidimensional (e.g. 2-dimensional) array?
  * Answer: `const twoDimensionalArray = [[1, 2, 3], [4, 5, 6], [7, 8, 9]];`
* Question: Where are multidimensional arrays used?
  * Answer: In day to day web development, you will rarely see multidimensional arrays. However, if you get into areas such as machine learning or graphic computations (rarely with JavaScript though), multidimensional arrays would be your bread and butter.
* Question: The last example from this section, where we remove an item from a list by using its index has a bug. Can you spot it? If you spot it, how can it be solved?
  * Answer: The bug occurs when we try to remove an item which isn't there. For example, try to remove the string "Liam" from the array. The index will be `-1`, because "Liam" cannot be found in the array. By using `firstNames.splice(-1, 1)` we will get a wrong result.
* Create a `person` object which has a property `children` that is represented by an array of strings (e.g. children's names) or objects (e.g. child entities with `firstName`, `lastName` etc.).

## Loops and Iterations

We have learned about all the essential data types in JavaScript: primitives such as strings, numbers and booleans, but also more structural data types such as functions, objects and arrays. While we have learned about these data types, we also explored operators and type coercion. We have also learned about control structures such as the if-else statement.

Since you have learned about arrays in JavaScript, the natural next step would be learning about **loop statements** which are also a control structure. A loop in JavaScript (and other programming languages) helps us to **iterate** (read: to loop, to go over) a list of items. Take for example the **for statement** which is the most popular one in JavaScript:

{title="index.js",lang="javascript"}
~~~~~~~
const firstNames = ['Robin', 'Sarah', 'Esther'];

for (let index = 0; index < firstNames.length; index++) {
  console.log(firstNames[index]);
}
~~~~~~~

This code snippet loops over our list of first names and prints each name to the console. If this reads like magic to you, let us go back a bit and see a more basic example. Essentially a loop will do something a number of times until a condition is met. First take the following example (which isn't using a loop yet), where you want to move your avatar in a computer game 3 steps forward:

{title="index.js",lang="javascript"}
~~~~~~~
console.log(`My avatar moved 1 step(s).`);
console.log(`My avatar moved 2 step(s).`);
console.log(`My avatar moved 3 step(s).`);
console.log(`My avatar arrived the desired destination.`);
~~~~~~~

You can see a reapting pattern here which can grow very much in size once your avatar attempts to move a lot of steps. Hence you could say that this example isn't DRY. Let's see how this looks in a loop statement:

{title="index.js",lang="javascript"}
~~~~~~~
for (let step = 0; step < 3; step++) {
  console.log(`My avatar moved ${step + 1} step(s).`);
}

console.log(`My avatar arrived the desired destination.`);
~~~~~~~

If you check the console, you will find the following printed output:

{title="index.js",lang="text"}
~~~~~~~
My avatar moved 1 step(s).
My avatar moved 2 step(s).
My avatar moved 3 step(s).
My avatar arrived the desired destination.
~~~~~~~

Essentially a loop statement does always the same thing: perform a certain action a specific number of times. The for statement takes three expressions in parantatheses: initial expression, condition expression, and increment expression. Most often you will encounter the initial expression as a variable which is defined with 0. If the condition expression evaluates to true (e.g. `0 < 3`), the loop's body in curly braces gets executed. If the condition evaluates to false though, the for loop terminates (read: it jumps out of the curly braces and continues with the next line of code below the for statement). After each execution of a loop's body, the update condition executes (e.g. increment by one) and we continue with the condition expression.

![](images/for-statement.png)

Normally loops are used whenever you have a number for the condition at your hand: number primitive or `array.length`. The latter is the most common scenario, where you want to iterate over an array to perform some action. For example, in an array of persons, we could generate the initials of the first and last name for every individual:

{title="index.js",lang="javascript"}
~~~~~~~
const persons = [
  {
    firstName: 'Robin',
    lastName: 'Wieruch',
  },
  {
    firstName: 'Sarah',
    lastName: 'Finnley',
  },
  {
    firstName: 'Esther',
    lastName: 'Shaw',
  },
];

for (let i = 0; i < persons.length; i++) {
  const firstNameInitial = persons[i].firstName.charAt(0);
  const lastNameInitial = persons[i].lastName.charAt(0);

  persons[i].initials = firstNameInitial + lastNameInitial;
}

console.log(persons);
// [
//   { firstName: 'Robin', lastName: 'Wieruch', initials: 'RW' },
//   { firstName: 'Sarah', lastName: 'Finnley', initials: 'SF' },
//   { firstName: 'Esther', lastName: 'Shaw', initials: 'ES' },
// ];
~~~~~~~

When iterating over an array, the structure of a for statement is often the same: start with an initial expression that initializes a variable (usually `i` that stands for index) with `0` and increment this value until it reaches the size (read: `length`) of the array. In the for statement, get access to each item (e.g. `persons[i]`) from the list by using the **iterator** (here: `i`). Then do something with the item.

Another example would be splitting an array into two arrays based on a condition:

{title="index.js",lang="javascript"}
~~~~~~~
const persons = [
  {
    fullName: 'Robin Wieruch',
    isDeveloper: true,
  },
  {
    fullName: 'Sarah Finnley',
    isDeveloper: false,
  },
  {
    fullName: 'Esther Shaw',
    isDeveloper: true,
  },
];

// declare two empty arrays
// which will be filled in the loop
let developers = [];
let nonDevelopers = [];

for (let i = 0; i < persons.length; i++) {
  if (persons[i].isDeveloper) {
    developers.push(persons[i]);
  } else {
    nonDevelopers.push(persons[i]);
  }
}

console.log(developers);
// [
//   { fullName: 'Robin Wieruch', isDeveloper: true },
//   { fullName: 'Esther Shaw', isDeveloper: true },
// ]

console.log(nonDevelopers);
// [{ fullName: 'Sarah Finnley', isDeveloper: false }]
~~~~~~~

Last, take the following task and try to solve it yourself. If you have difficulties to get to a solution, do not worry and check out the solition below. Task: You have an array of persons whereas each person has a `fullName` and a `yearBirth` as key/value properties. Based on today's year, calculate each person's age in a loop statement and add it as additional property to each person. Now try it yourself first before checking the following solution:

{title="index.js",lang="javascript"}
~~~~~~~
const persons = [
  {
    fullName: 'Robin Wieruch',
    yearBirth: 1990,
  },
  {
    fullName: 'Sarah Finnley',
    yearBirth: 1988,
  },
  {
    fullName: 'Esther Shaw',
    yearBirth: 1992,
  },
];

for (let i = 0; i < persons.length; i++) {
  persons[i].age = 2021 - persons[i].yearBirth;
}
~~~~~~~

As said, loops are usually used for iterating over arrays (but sometimes also when just having a number primitive at your hands). Then based on the iterator (the running index), you can grab the item from the list and do something with it. The most popular loop as control structure you will encounter is the for statement that you have just learned about, but there are various other loop mechanims in JavaScript such as the popular **for-of** statement and the less popular **while** and **do-while** statements.

### Exercises:

* Read more about [loops and iterations in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration).
  * Refactor (read: adjust, modify, change) the for statements that we have used for arrays from this section to for-of statements.
  * Find out the difference between the for-of statement and the for-in statement.
  * See more examples in action about [loops/iterations in JavaScript](https://javascript.info/while-for).
* Question: What are common control structures in JavaScript?
  * Answer: if-else statement, switch-case statement, for statement.
* Question: Why does the indexing in a loop start with 0 and not with 1?
  * Answer: As a developer you are free to choose your variable for the initial expression in a loop statement. So it's valid to have 1 instead of 0 as well. However, since JavaScript is zero indexed (see arrays), it's common to use 0.
* Question: Why is `i` used as iterator?
  * Answer: `i` stands for index. Since most often developers loop over arrays, the variable stands for the index which will enable you to access each item in the array within the loop. As common sense, index is shortened to `i`. If you happens to have a loop in a loop, you will often see `i` for the outer loop and `j` for the inner loop.
* Question: What does `i++` stand for?
  * Answer: `i++` is just a shorthand for `i = i + 1`, so essentially incrementing the value by 1. You have learned about this in the Arithmetic Operator section's exercises.

