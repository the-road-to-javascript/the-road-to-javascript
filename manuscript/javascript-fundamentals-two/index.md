# Fundamentals of JavaScript: II

TODO summary

## Functions

Everything you have written so far in JavaScript can be called *a program* (also called routine in programming, but rarely in JavaScript). However, sometimes you want to extract parts of a program (also called subroutine) to reuse them without writing them twice. Functions can be used to extract these parts which are then reusable and executable.

```javascript
function askAndSayMyName() {
  console.log("What's your name?");
  console.log('I am Robin Wieruch!');
}
```

A **function declaration** starts with the `function` keyword, a descriptive name for this function, and an opening and closing parantheses. Everythign that follows inside of the curly brackets is the code which should run when this function gets called. Hence functions are like variables, except that they do not store any values, but code which runs when someone uses the function:

```javascript
// function declaration
function askAndSayMyName() {
  console.log("What's your name?");
  console.log('I am Robin Wieruch!');
}

// function calling
askAndSayMyName();

// function calling
askAndSayMyName();
```

Calling a function (also refered to as running/executing/invoking a function) is as straightforward as using the function's name adding paranthaseses at the end. In the last example, you can already see how this function allowed us to reuse code, because otherwise we would have written repetetive code as you can see in the next example:

```javascript
// repetition 1
console.log("What's your name?");
console.log('I am Robin Wieruch!');

// repetition 2
console.log("What's your name?");
console.log('I am Robin Wieruch!');
```

If there is nothing going in to a function, it could be seen as a blackbox which would only be useful to execute static code. Fortunately we can pass in so called **arguments** from the outside to our function which can be used in the inside of the function as so called **parameters**:

```javascript
function askAndSayMyName(parameter) {
  console.log("What's your name?");
  console.log(`I am ${parameter}!`);
}

const argument = 'Robin Wieruch';

askAndSayMyName(argument);
```

You can name your arguments and parameters whatever you want though:

```javascript
function askAndSayMyName(fullName) {
  console.log("What's your name?");
  console.log(`I am ${fullName}!`);
}

const myName = 'Robin Wieruch';

askAndSayMyName(myName);
```

As you can see, we declare our function, a variable `myName` and call the function with the variable as argument. Inside of the function, the variable is used as parameter called `fullName` which is only usable within this function. It's also possible to pass more than one argument to functions:

```javascript
function askAndSayMyName(firstName, lastName) {
  console.log("What's your name?");
  console.log(`I am ${firstName} ${lastName}!`);
}

const myFirstName = 'Robin';
const myLastName = 'Wieruch';

askAndSayMyName(myFirstName, myLastName);
```

At this time, you may have tried to use variables from the outside in a function without passing them as arguments. This works due to the concept of **scoping** (which we will learn more about later):

```javascript{1,2,6}
const myFirstName = 'Robin';
const myLastName = 'Wieruch';

function askAndSayMyName() {
  console.log("What's your name?");
  console.log(`I am ${myFirstName} ${myLastName}!`);
}

askAndSayMyName();
```

However, it's a best practice to have functions that only use variables which are passed as arguments to them. Under certian circumstances, you can use variables which are declared outside of a function without passing them as arguments, but try to avoid it for embracing best practice coding habits from the beginning when starting out with JavaScript.

While there exists an (optional) input for functions in the form of parameter(s), there also exists an (optional) output for functions in the form of a **return statement**:

```javascript
function getFullName(firstName, lastName) {
  const fullName = `${firstName} ${lastName}`;

  return fullName;
}

const myFirstName = 'Robin';
const myLastName = 'Wieruch';

const myFullName = getFullName(myFirstName, myLastName);

console.log(myFullName);
```

In this example, we interpolate the first and last name of a person to their full name and store it in a variable called `fullName`. Then we return this variable from the function. Now when someone calls this function, we can assign the returned value from this called function to a variable (here: `myFullName`). What's also possible is returning the value right away without declaring the so called **intermediate variable**:

```javascript{2}
function getFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

const myFirstName = 'Robin';
const myLastName = 'Wieruch';

const myFullName = getFullName(myFirstName, myLastName);

console.log(myFullName);
```

Since arguments are mostly values stored in variables, it's also possible to pass values to functions (1) or to use the returned value right away (2):

```javascript
function getFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

const robin = getFullName('Robin', 'Wieruch'); // (1)
console.log(robin);

console.log(getFullName('Sarah', 'Finnley')); // (2)
```

Functions allow us to write *[generic code](https://en.wikipedia.org/wiki/Generic_programming)* with the concept of *"fill in the blanks"* by using parameters. From the outside, we can call these functions and fill in the blanks with *specific* arguments while optionally getting something returned specific (e.g. full name of a user) from the function with the help of the return statement .

![](images/function-anatomy.png)

Functions enhance the concept of **DRY** (Don't repeat yourself) in code. Everything that can be extracted as function, because it is reused or used at multiple places of the application, helps us to keep the code maintainable and readable for others. Actually before we have learned about functions, we have already used one all the time: `console.log()`.

Functions are one of the most important **structural data types** in JavaScript. As a best practice, try to keep function names as descriptive as possible and keep functions scoped to one utility (e.g. `getFullName()` and `multiply()` should be two functions). As a beginner to coding, this may be one of these times that you feel overwhelmed by the sheer amount of information. However, take your time to grok the concept of a function and experiment with it in your code environment.

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

There are many more things to know about functions, although not all of them are must-knows for a JavaScript beginner. However, the book attempts to address these concepts early on, because it will make use of them throughout the book on certain occasions when there are other topics at stake. So don't shy away if you don't understand all of the following concepts right away, but keep them in the back of your head and refer back to them when they are used later.

Functions in JavaScript are super powerful, because, in contrast to many other programming languages, functions are treated as first-class citizens in JavaScript. By definition, a function becomes a first-class citizen when it can be stored in a variable and thus becomes a **function expression**. In contrast to a function declaration, a function expression can be used to carry functions around in variables:

```javascript
const hasExperience = function getExperience(yearsAsProfessional) {
  const isExperienced = yearsAsProfessional > 0;

  return isExperienced;
};

const yearsAsDeveloper = 7;
const isDeveloper = hasExperience(yearsAsDeveloper);

console.log(isDeveloper);
// true
```

A function is called an **anonymous function** when it has no name. This works for function expressions, because the function gets called with the name of the variable anyway. However, when debugging the code in the case of a bug, anonymous functions are more difficult to spot than named functions:

```javascript
const hasExperience = function (yearsAsProfessional) {
  return yearsAsProfessional > 0;
};
```

Function expressions have subtle differences compared to function declarations. While for a function expression the function gets created when the code reaches the variable declaration, for the function declaration the function gets created once at the start:

```javascript
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
```

Function expressions have their right to exist though. For example, you can use a function expression to create a function conditionally and thus only create one of both functions when the conditional runs:

```javascript
const isDeveloper = true;

const getConversationStarter = isDeveloper
  ? function () {
      return console.log('What programming languages do you speak?');
    }
  : function () {
      return console.log('What languages do you speak?');
    };

getConversationStarter();
```

As a rule of thumb: Use function declarations whenever you can, because you will run into less bugs (due to their early instantiation). In addition, because functions are such a fundamental building block in JavaScript code, function declarations are more eye-catching and therefore more readable than their function expression counterparts. However, get used to both, function declaration and function expressions, because you will see both of them out there in the wild.

### Exercises:

* Read more about [functions in JavaScript](https://javascript.info/function-basics).
* Read more about [function expressions](https://javascript.info/function-expressions).

## Working with Functions

In this section, we will dive deeper into functions and how we can use them as developers. Before we have only worked with one function, however, once programs become more complex, you will most likely use more than one function side by side or composed into each other. Let's take the following example of a function which creates a text for us:

```javascript
function getConversationStarter(firstName, lastName, isDeveloper) {
  const welcome = `Hi ${firstName} ${lastName}!`;

  const question = isDeveloper
    ? 'What programming languages do you speak?'
    : 'What languages do you speak?';

  return `${welcome} ${question}`;
}

const text = getConversationStarter('Robin', 'Wieruch', true);

console.log(text);
```

This function takes various arguments as input and uses them internally as parameters to create a text with a certain condition. Since we are assigning variables conditionally, we prefer using the ternary operator instead of the if-else statement. As exercise, try to write this function with if-else statements instead of the ternary operator and experience yourself how much more verbose it gets this way.

The function for creating our conversation starter has a few responsibilities. Let's split these responsibilities into multiple functions, in this case, our function should call another function:

```javascript{1-3,5-9,11,12,14}
function getName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

function getQuestion(isDeveloper) {
  return isDeveloper
    ? 'What programming languages do you speak?'
    : 'What languages do you speak?';
}

function getConversationStarter(firstName, lastName, isDeveloper) {
  const fullName = getName(firstName, lastName);
  const welcome = `Hi ${fullName}!`;
  const question = getQuestion(isDeveloper);

  return `${welcome} ${question}`;
}
```

As alternative, we could also evaluate one of the function's return values directly in the string interpolation, becuase we do not need the `fullName` variable anywhere else and we don't get any benefit to give it a descriptive name here, because the function already has a decriptive name:

```javascript{2}
function getConversationStarter(firstName, lastName, isDeveloper) {
  const welcome = `Hi ${getName(firstName, lastName)}!`;
  const question = getQuestion(isDeveloper);

  return `${welcome} ${question}`;
}
```

Now one could argue to go all the way and interpolate both directly in the return statement. But even though this would make the function's body more concise, it would make it in many eyes less readable:

```javascript
function getConversationStarter(firstName, lastName, isDeveloper) {
  return `
    Hi ${getName(firstName, lastName)}!
    ${getQuestion(isDeveloper)}
  `;
}
```

After all, what you can see from this example is that functions can call other functions. In a developer's words it's called "breaking down a problem into smaller problems and therefore smaller solutions" whereas the solutions stand for the functions. In your career as a JavaScript developer, you will see most likely functions calling other functions.

Reusability is another benefit of extracting functions from other functions. For example, another part of our program could reuse the `getName()` function now:

```javascript
const robinText = getConversationStarter('Robin', 'Wieruch', true);
console.log(robinText);

const sarah = getName('Sarah', 'Finnley');
const sarahText = `Hi, I'm ${sarah}.`;
console.log(sarahText);
```

If we would want to introduce an optional nickname, we could extend everything with this additional argument:

```javascript{1-2,12,15,24}
function getName(firstName, lastName, nickname) {
  if (nickname) return nickname;

  return `${firstName} ${lastName}`;
}

...

function getConversationStarter(
  firstName,
  lastName,
  nickname,
  isDeveloper
) {
  const welcome = `Hi ${getName(firstName, lastName, nickname)}!`;
  const question = getQuestion(isDeveloper);

  return `${welcome} ${question}`;
}

const robinText = getConversationStarter(
  'Robin',
  'Wieruch',
  'Hood',
  true
);
```

By breaking down functions onto smaller problem spaces, we can compose more complex functions out of these smaller functions (e.g. `getConversationStarter()`) or reuse functions in other areas of our code (e.g. `getName()`). Challenge yourself by writing a larger function and by extracting smaller functions from it.

### Exercises:

* Extend the example from before with more conditional text for the conversation which may or may not be passed on additional arguments that are passed to the function.
* Come up with problems that are solved by functions yourself. If you have created one function, split it into smaller parts.

## Classes

Even though the construct of a **class** is a shared concept across most programming languages, it was only introduced in modern JavaScript. Previously it was only possible to a create class like construct by using JavaScript's **prototype chain** ([in-depth article, but optional read at this stage](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)). While the prototype chain wasn't unknown to many JavaScript developers back in the days, it's not as often mentioned these days anymore, because we are mostly using classes in JavaScript instead.

A class is used in object-oriented programming languages. Since JavaScript is a **multi paradigm programming language**, using the **object-oriented programming (OOP)** paradigm in JavaScript is a popular choice. Another popular paradigm is called **functional programming (FP)** which doesn't make use of classes.

Let's get started with a class that represents a person by using the `class` keyword:

```javascript
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
}
```

In this example, we see a **class declaration** for a class with the name Person. After a class declaration, we can use this class with the `new` keyword to create an **instance**, in this case a person instance, from it:

```javascript{8,10-11}
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
}

const robin = new Person('Robin', 'Wieruch');

console.log(robin);
// Person { firstName: 'Robin', lastName: 'Wieruch' }
```

Except for the `new` keyword and the uppercase naming convention for a class, using a class to create an instance from it feels quite similar to using a function. One could say that a function is more ephemeral though, because by calling the class with the `new` keyword, we **instantiate** one or multiple (none ephemeral) instances from it:

```javascript
const robin = new Person('Robin', 'Wieruch');
const sarah = new Person('Sarah', 'Finnley');

console.log(robin);
// Person { firstName: 'Robin', lastName: 'Wieruch' }
console.log(sarah);
// Person { firstName: 'Sarah', lastName: 'Finnley' }
```

Think of a class like a factory for a thing: A class is like a cookie mold for many cookies of the same kind. Another example: Once an architect has done the blueprint for a house (class declaration), builders can create many houses (instances) from it.

![](images/class-analogy.png)

Functions in classes are called **methods** or **class methods**. The **constructor** is one of these methods which is mandatory, because it is used when this class gets instantiate with the `new` keyword. The constructor methods accepts optional arguments from the outside, here `firstName` and `lastName`, which are internally used as local variables. In this example, the parameters are used to assign its **instance properties** `firstName` and `lastName` by using the `this` keyword. In the context of a class, `this` means the class instance itself. Read it like "given these paramaters I (the class) assign them as values to this new instance of myself". Continuing from here, a developer can evolve a class with more instance properties and class methods:

```javascript
class Person {
  constructor(firstName, lastName, isDeveloper) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.isDeveloper = isDeveloper;
    this.nickname = null;
  }

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
}

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
```

We can see how a class helps us to encapsulate information (instance properties) and behavior (class methods) into one construct. Only when we create an instance of a class with its constructor, we can read its properties or call its methods (like functions by adding parantheses). The `.` notation (read: **dot notation**) is used to access an instance's properties and methods, which will work very similar for JavaScript objects as we will learn later.

![](images/class-anatomy.png)

It's worth to say that when using modern JavaScript with everyday frameworks such as React.js, you will only rarely see classes though. In order to encapsulate information like a class does for us, you would use JavaScript a object instead. However, understanding the concept of a class is helpful for many topics that follow in this book.

### Exercises:

* Add more instance properties and class methods to the Person class.
  * Create many person instances and use their methods.
* Come up with another class declaration for an Aircraft, Cat, or SmartHouse.
* Question: What does `typeof Person` return?
  * Answer: It returns `function`. Essentially a class is a function in disguise.
* Read more about classes in JavaScript [here](https://javascript.info/class) and [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes).
  * If there exists the concept of class declaration (similar to function declaration), find out whether there exists the concept of class expressions (similar to function express) as well.

* TODO Read more about FP vs OOP (inhertiance Devleoper>Person, React class component, public, private, static, new class keywords, prototype chain) (classes vs function composition, immutability vs mutability, pure functions vs side-effects)

## Methods of Primitives

Primitives (e.g. string, number, boolean) in JavaScript are supposed to represent only a value. However, you maye have noticed that primitives have special behavior attached to them. For example, all string primitives give us access to the same **built-in string methods** such as `toUpperCase()`:

```javascript
const fullName = 'Robin Wieruch';

console.log(fullName.toUpperCase());
// 'ROBIN WIERUCH'

console.log('Sarah Finnley'.toUpperCase());
// 'SARAH FINNLEY'
```

By using the `.` notation we can call methods on string instances. In this case, we want to to have the string transformed to its upper case representation. However, even though we call this built-in method, the value itself hasn't been changed afterward which is an important fact:

```javascript
const fullName = 'Robin Wieruch';

console.log(fullName.toUpperCase());
// 'ROBIN WIERUCH'

console.log(fullName);
// 'Robin Wieruch'
```

Functions on primtives are called methods the same way as functions on classes are called methods. They follow the same terminology, because they are attached to a data type where they are not mere functions anymore. Hence the term methods and in this case built-in methods, because you do not need to define these methods yourself but they come with the programmign language JavaScript.

Similar to JavaScript classes, there are not only methods on JavaScript primitives which can be accessed by using the dot notation, but also properties. The `length` property is a popular one for string primitives but also other data types which returns the size of characters in the case of a string:

```javascript
const fullName = 'Robin Wieruch';

console.log(fullName.length);
// 13
```

You may be thinking that strings (and other primitives) are not mere primitives, but rather something more complex such as JavaScript classes. At this point, you may have noticed the class equivalents for primitves too, which can be used to create instances of these primitives. However, they are rarely used in reality:

```javascript
const fullName = new String('Robin Wieruch');

console.log(fullName);
// [String: "Robin Wieruch"]
```

As you can see from the output, this creates a string instance rather than a string primitive. While the former is rarely used in JavaScript, the latter, called **string literal** in this case, will be your bread and butter. Equivalents are boolean literal and number literal which you have used before. However, both can be used almost interchangeably in most situations which raises the important fact that primitives can be more powerful beings by using their respective counterparts (e.g. `String()`).

With this knowledge, we can explain how properties (e.g. `length`) and methods (e.g. `toUpperCase()`) work on primitives: If a developer accesses a method on a string for example, JavaScript with the help of type coercion creates a more powerful `String` as counterpart where we can access the method (or properties). When the method has been called, this counterpart gets discared and we are left with only the primitive again:

```javascript
const fullName = 'Robin Wieruch';

console.log(typeof fullName);
// string

console.log(fullName.toUpperCase());
// ROBIN WIERUCH

console.log(typeof fullName);
// string
```

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

Up to this point, you have learned about primitive data types such as strings, numbers and booleans. One way of encapsulating these into one entity has been the JavaScript class. For example, a `Person` class can have properties such as `firstName`, `lastName` and a method such as `getFullName()`. However, an alternative and more widely use structural data type for this kind of work is the **JavaScript object**:

```javascript
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
};
```

In this example, an object gets declared as variable with the name `robin` whereas everything in the curly brackets are **properties** of this object. While the left-hand side of these properties is called **object keys** (short: keys or names, here: `firstName`, `lastName`, `yearBirth`, `isDeveloper`), the right-hand side is called **object values** (short: values). Essentially an object is a wrapper around a bunch of values (of any data type) which are grouped into an **entity** of a specific **domain** (e.g. person domain).

![](images/object-anatomy.png)

Therefore, we can have distinct entities represented by objects *without* declaring all their primitive values as variables one by one:

```javascript
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
```

If you want to access a **property** of an object, you can use the already learned **dot notation** or the alternative **bracket notation**:

```javascript{8-9}
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
};

console.log(robin.firstName); // dot notation
console.log(robin['isDeveloper']); // bracket notation
```

By using a property name, one can access its value. While the dot notation should be the default, the bracket notation can be used to evaluate expressions if needed:

```javascript{8,10-11}
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
};

const nameKey = 'Name';

console.log(robin['first' + nameKey]);
console.log(robin['last' + nameKey]);
```

Another example for the special use of having the bracket notation instead of the dot notation are cases where we do not know the property name in advance, like in a function:

```javascript
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
```

Same way as using mere primtives, an object's properties can be used to interpolate whole sentences. Try the following and add more properties to the object and extend the sentence yourself:

```javascript
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
```

Since objects can have any data type as property, they can have (anonymous) functions (called **methods** in objects) and objects (so called **nested objects**) too. While methods in objects are not often used, using nested objects is a common theme when writing JavaScript:

```javascript{6-13,15-17}
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
  getAge: function (year) {
    return year - 1991;
  },
  kid: {
    firstName: 'Liam',
    lastName: 'Wieruch',
  },
};

console.log(robin.kid.firstName);
console.log(robin.kid.lastName);
console.log(robin.getAge(2021));
```

Note how one can access an nested object's property by using multiple dot (or bracket) notations (e.g. `robin.kid.firstName`). Furthermore, notice how a method of an object can be called like any other function, it just needs to be accessed by the dot notation first.

The last example violated the principle of DRY, because we had to write the value `1991` twice. Let's change this by using the `this` keyword, which we have used before in our JavaScript class, to get a reference to the instance (here: object) itself:

```javascript{7}
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
  getAge: function (year) {
    return year - this.yearBirth;
  },
  kid: {
    firstName: 'Liam',
    lastName: 'Wieruch',
  },
};
```

Another example would be getting an introduction for this object by calling a method on it. We did this before by interpolating the object's properties into a text. This time we will do it with a method though:

```javascript
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
```

Now we know how to declare and how to access an object. While we created the objects with the **object literal notation** (also called **initializer notation** or short **literal notation**) in our examples, alternative to this would be the `new Object()` or `Object.create()` syntaxes. The latter are only rarely used though, so stick to the literal notation for now.

Once declaring and accessing objects works, it should also be possible to assign or reassign properties to an object. Both dot and bracket notation work, and they also work for nested objects, however, the dot notation should be the default as mentioned before:

```javascript
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
```

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
* In this section, there was a place where we printed a text of the object's properties by using string itnerpolation with template literals. Do the same thing, but with a function defined as method in the object.

## Arrays

An **array** in JavaScript represents a list of items. Informally it's also called **list** or **list of items** or sometimes **entries**. While objects (from the last section) represent one entity (here: object) with certain properties defined in curly brackets, arrays represent multiple entities (here: strings, numbers, but also objects) in a list defined in brackets.

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];
```

Before we had arrays, one may have defined these names the following way with primitves:

```javascript
const firstNameOne = 'Robin';
const firstNameTwo = 'Sarah';
const firstNameThree = 'Esther';
```

Now we can put these into a list, like we have done before by comma separating the values, or like the following example shows by using comma separated variables:

```javascript
const firstNameOne = 'Robin';
const firstNameTwo = 'Sarah';
const firstNameThree = 'Esther';

const firstNames = [firstNameOne, firstNameTwo, firstNameThree];
```

Often inserting the values directly like we did before makes more sense though, because we want to get away from defining variables like `firstNameOne` just to reference them later in an array anyway. That's why we have arrays in the first place. Apart from declaring an array with an **array literal notation**, one could also use `new Array()` as alternative. The latter are only rarely used though, so stick to the literal notation for now:

```javascript
const lastNames = ['Wieruch', 'Finnley', 'Shaw'];
```

In contrast to objects, arrays are a list of similar items (persons, fruits, aircrafts, prime numbers, ages). Even though it's possible to mix data types in an array, it's not commonly done. So usually one ends up with an array with one kind of data type in a list. So whenever you have a mix of data types in an array, ask yourself whether an object wouldn't be a better suited for this use case:

```javascript
// good
const primeNumbers = [2, 3, 5, 7];

// bad
const robinAsArray = ['Robin', 'Wieruch', true, 1991];

// better
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  isDeveloper: true,
  yearBirth: 1991,
};
```

As mentioned, arrays can hold a list of objects too. The last examples have shown you lists of first and last names where each first name relates to a last name. So we can put these relations into objects and then put these objects into an array:

```javascript
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
```

As before, we can define them as inline values too, so that you do not need to specify each person as a standalone variable. Furthermore, one can access items from an array by using the **bracket notation**. Since we do not have property names like for objects, we can access arrays only by their indexes (read: position of an item in the list):

```javascript
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
```

You can see that arrays are zero indexed like most things in JavaScript. Hence in order to access the first person in the array, you need to get the `0` and not the `1` indexed item. Note that we cannot use the dot notation for accessing indexed items in arrays, because the dot notation does not work for property names that start with a digit (e.g. `0` or `4thOfJuly`). It's the same for objects: If you have an object `holidays` with the property name `4thOfJuly`, you can only access it with `holidays['4thOfJuly']` and not `holidays.4thOfJuly`.

![](images/array-anatomy.png)

Once declaring and accessing arrays works, it should also be possible to assign or reassign an item in a list. It goes the same way as for other variables, only that we (re)-assign specific items by their indexes in an array:

```javascript
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
```

An array is classified under the umbrella of the object data type. Except for primitives like string, number and boolean, the only more complex data types are function and object. So essentially everything that doesn't fall under these called out data types is of type object (e.g. array). Therefore, it's also possible to access built-in properties (and methods) of arrays:

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

console.log(firstNames.length);
// 3
```

In this case, the `length` property returns us size of the array (which translates internally to "the highest index + 1"). Most often the `length` property is used to get the size of the list (previous example) or to get the last item of a list (next example):

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

console.log(firstNames[firstNames.length - 1]);
// 'Esther'
```

Since an array falls under the data type of objects, there are not only properties attached to this entity, but also methods. Let's explore some of the more popular ones in this section. One of the first **built-in array methods** you will learn about is `push()` which adds a new item to end of a list:

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

firstNames.push('Liam');

console.log(firstNames);
// ['Robin', 'Sarah', 'Esther', 'Liam']
console.log(firstNames.length);
// 4
```

Usually we are using `push()` whenever we want to add a new item to a list. In a previous example, we have assigned a new item directly by using an index (e.g. `firstNames[3] = 'Peter'`) which you will only rarely perform. In contrast to `push()`, the method `pop()` removes the last item from the list:

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

firstNames.pop();

console.log(firstNames);
// ['Robin', 'Sarah']
console.log(firstNames.length);
// 2
```

Note that both method modify the array without the need of assigning them to a new variable. We will learn more about this behavior later when speaking about **mutability vs immutability**. For now, just focus on the built-in array methods themsevles. In the exercise, you should try out more of them. Several of these array methods will come up during the next sections of the book though. For example, a popular one is `includes()` which will inform you whether a certain item is part of the list by returning a boolean:

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

const hasSarah = firstNames.includes('Sarah');
const hasLiam = firstNames.includes('Liam');

console.log(hasSarah, hasLiam);
// true false
```

As a final example for this section, we will see how to remove a specific item from an array by using the `indexOf()` and `splice()` method:

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

const index = firstNames.indexOf('Sarah');

console.log(index);
// 1

const removedItem = firstNames.splice(index, 1);

console.log(removedItem);
// [ 'Sarah' ]
console.log(firstNames);
// [ 'Robin', 'Esther' ]
```

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

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

for (let index = 0; index < firstNames.length; index++) {
  console.log(firstNames[index]);
}
```

This code snippet loops over our list of first names and prints each name to the console. If this reads like magic to you, let us go back a bit and see a more basic example. Essentially a loop will do something a number of times until a condition is met. First take the following example, where you want to move your avatar in a computer game 3 steps forward, which isn't using a loop:

```javascript
console.log(`My avatar moved 1 step(s).`);
console.log(`My avatar moved 2 step(s).`);
console.log(`My avatar moved 3 step(s).`);
console.log(`My avatar arrived the desired destination.`);
```

You can see a reapting pattern here which can grow very much in size once your avatar attempts to move a lot of steps. Hence this example isn't DRY. Let's see how this looks in a loop statement:

```javascript
for (let step = 0; step < 3; step++) {
  console.log(`My avatar moved ${step + 1} step(s).`);
}

console.log(`My avatar arrived the desired destination.`);
```

If you check the console, you will find the following printed output:

```text
My avatar moved 1 step(s).
My avatar moved 2 step(s).
My avatar moved 3 step(s).
My avatar arrived the desired destination.
```

Essentially a loop statement does always the same thing: perform a certain action a specific number of times. The for statement takes three expressions in parantatheses: initial expression, condition expression, and increment expression. Most often you will encounter the initial expression as a variable which is defined with 0. If the condition expression evaluates to true (e.g. `0 < 3`), the loop's body in curcly braces gets executed. If the condition evaluates to false though, the for loop terminates (read: it jumps out of the curly braces and continues with the next line of code below the for statement). After each execution of a loop's body, the update condition executes (e.g. increment by one) and we continue with the condition expression.

![](images/for-statement.png)

Normally loops are used whenever you have a number for the condition at your hand: number primitive or `array.length`. The latter is the most common scenario, where you want to iterate over an array to perform some action. For example, in an array of persons, I could increment the age by one for every individual:

```javascript
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
```

When iterating over an array, the structure of a for statement is often the same: start with an initial expression that initializes a variable (usually `i` that stands for index) with 0 and increment this variable until it reaches the size (read: `length`) of the array. In the for statement, get access to each item (e.g. `persons[i]`) from the list by using the **iterator** (here: `i`). Then do something with the item. Another example would be splitting an array into two arrays based on a condition:

```javascript
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
```

Last, take the following task and try to solve it yourself. If you have difficulties to get to a solution, do not worry and check out the solition below. Task: You have an array of persons whereas each person has a `fullName` and a `yearBirth` as key/value properties. Based on today's year, calculate each person's age in a loop statement and add it as additional property to each person. Now try it yourself first before checking the following solution:

```javascript
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
```

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

## Callback Functions

We have learned about all the fundamental ingredients (functions, arrays and loops) which enable us to learn about an advanced concept with the name **callback functions**. A callback function is nothing more than a function that is passed as argument to another function and executed within this function:

```javascript
function sayThis() {
  console.log('This!');
}

function sayThatAndMore(callbackFunction) {
  console.log('That!');

  callbackFunction();
}

sayThatAndMore(sayThis);

// That!
// This!
```

The example seems pretty artificial, however, it's just the most minimal way to show what it means to pass a function to another function and execute it there. Remember that a function can be passed same as any other value. But do not use the executing parentatheses. Only within the other function, you execute the function with the parentatheses.

![](images/callback-function.png)

You may be wondering what's the benfit of having such construct. Essentially we get the control of executing anything we want (e.g. `sayThis()`) in another function (e.g. `sayThatAndMore()`) which may already have other implementation details (e.g. `console.log('That!')`). In other words: We are able to execute anything we want in addition to what's already defined in `sayThatAndMore()`.

However, we will start with a more tangible example and evolve it over the course of this section to a scenario which will use a callback function eventually. Imagine you have an array of persons and you want to find a specific person by their first name:

```javascript
const persons = [
  {
    firstName: 'Robin',
    lastName: 'Wieruch',
  },
  {
    firstName: 'Sarah',
    lastName: 'Finnley',
  },
];
```

As we have learned, you can use a for statement to loop over all persons and an if-else statement to find the searched person based on a condition. In the following code snippet, we assing the currently iterated person to the variable `sarah` whenever the iterated person's `firstName` matches the condition of being "Sarah":

```javascript{3-12}
const persons = [ ... ];

let sarah;

for (let i = 0; i < persons.length; i++) {
  if (persons[i].firstName === 'Sarah') {
    sarah = persons[i];
  }
}

console.log(sarah);
// { firstName: 'Sarah', lastName: 'Finnley' }
```

Next, we want to make this utility reusable by declaring a function for it. Actually you can also say that you are going to extract this functionality into a function. This function should take a `firstName` as argument to make it reusable for other search criteria (read: search condition) and not only the first name "Sarah":

```javascript{1-11,24-25}
function findPerson(persons, firstName) {
  let person;

  for (let i = 0; i < persons.length; i++) {
    if (persons[i].firstName === firstName) {
      person = persons[i];
    }
  }

  return person;
}

const persons = [
  {
    firstName: 'Robin',
    lastName: 'Wieruch',
  },
  {
    firstName: 'Sarah',
    lastName: 'Finnley',
  },
];

const sarah = findPerson(persons, 'Sarah');
const robin = findPerson(persons, 'Robin');
```

The function takes the `persons` and a `firstName` as argument, iterates over the `persons`, finds the correct `person` by their `firstName`, and returns this person as value from the function. Whoever calls this functions receives as returned value the found person (given that the person is included in the array). By having this function at place now, we can call this function for any `persons` and `firstName` combination. Essentially we made this functionality reusable by creating a function for it.

Can you see how all of our gathered knowledge comes together in this example and allows us to write such elaborate code? Do not worry if you weren't able to come up with this yourself. It takes time to know how to construct such things, but with more time passing, and with seeing more exmaples solving specific problems, you should be able to pull these off yourself eventually.

Now we have a general purpose function which allows us to find any person by their first name. However, what if the next hurdle would be that we do not want to find a person only by their first name, but also by their last name? For example, we could extend the [function's signature](https://developer.mozilla.org/en-US/docs/Glossary/Signature/Function) with more parameters:

```javascript{1,6-7,18}
function findPerson(persons, firstName, lastName) {
  let person;

  for (let i = 0; i < persons.length; i++) {
    if (
      persons[i].firstName === firstName ||
      persons[i].lastName === lastName
    ) {
      person = persons[i];
    }
  }

  return person;
}

const persons = [ ... ];

const sarah = findPerson(persons, null, 'Finnley');
```

This solution is great and works for the given task. However, can you see a scenario where this function does not scale (read: does not stay usable for growing requirements)? For example, what if a person would consist of more properties such as nickname and middleName. We would always have to change the `findPerson` function to accomodate our requirement. As alternative, let's enter the concept of callback functions again and see how a callback function will help us here:

```javascript{1,5,15-17,19}
function findPerson(persons, findCondition) {
  let person;

  for (let i = 0; i < persons.length; i++) {
    if (findCondition(persons[i])) {
      person = persons[i];
    }
  }

  return person;
}

const persons = [ ... ];

const findSarah = function (person) {
  return person.firstName === 'Sarah';
};

const sarah = findPerson(persons, findSarah);
```

Can you spot what we have done here? We defined a function expression on the outside (here: `findSarah()`) which takes a person as argument and evaluates to `true` whenever it's called with a person's first name that is "Sarah". You can try it yourself: the console output of `findSarah(persons[0])` should return `false`, because it's "Robin", while `findSarah(persons[1])` returns `true`, because it's indeed "Sarah". However, now this function is passed as callback function to `findPerson()` and is used as a condition (better: function that returns a condition in the form of a boolean) inside of `findPerson()`.

Uncovering this mechanism in JavaScript and understanding it will feel like a superpower eventually, because now we can pass any condition we want by changing the callback function without changing the actual function `findPerson()` anymore:

```javascript
const findWieruch = function (person) {
  return person.lastName === 'Wieruch';
};

const wieruch = findPerson(persons, findWieruch);
```

Callback functions allow us to pass implementation details from the outside in the form of a function to another function. Essentially it gives us control over the other function, because we can pass arbitrary code to it. In this other function then, the callback function gets then executed. Next, I want you to check out the following code:

```javascript
const persons = [
  {
    firstName: 'Robin',
    lastName: 'Wieruch',
  },
  {
    firstName: 'Sarah',
    lastName: 'Finnley',
  },
];

const findSarah = function (person) {
  return person.firstName === 'Sarah';
};

const sarah = persons.find(findSarah);

console.log(sarah);
// { firstName: 'Sarah', lastName: 'Finnley' }
```

Apparently, there is already the built-in array method called `find()` which does exactly what we have implemented before: find an item in a list based on a condition; whereas the condition is returned from callback function which has access to each person. It's exactly the same callback function that we have used before and it can be changed the same way as we have done before:

```javascript
const persons = [ ... ];

const findWieruch = function (person) {
  return person.lastName === 'Wieruch';
};

const wieruch = persons.find(findWieruch);
```

Basically we have implemented our own version of `find()` before which is kinda an advanced thing to pull off. However, this way you got a better understanding of what the callback function -- that we are passing as argument to `find()` -- performs internally. Otherwise it would be a black box for you. Keep in mind that for most people writing JavaScript it's still a black box, because they never attempted to implement this functionality themselves. Instead, they discovered the built-in array method and went with it. So I want to encourage you that even though you may not grasp everything right now, you are tapping your toes into advanced territorry here.

Callback functions that are used for built-in array methods have access to each item of the list. It's also noteworthy that often callback functions get inlined as arguments, because they are not used somewhere else and are just there for this one purpose. However, it comes with the drawback that it gets less readable, so in contrast extracting them as function expression (as we had before) makes your code often more readable:

```javascript
// callback function as inlined argument
// makes code less readable though

const wieruch = persons.find(function (person) {
  return person.lastName === 'Wieruch';
});
```

Let's discuss two other built-in array methods that accept callback functions as arguments. First, `every()` returns `true` whenever the condition for *every* item in the callback function returns `true`. In this example, if all persons are developers, the method will return `true`. Otherwise it returns `false`:

```javascript
const persons = [
  {
    firstName: 'Robin',
    lastName: 'Wieruch',
    isDeveloper: true,
  },
  {
    firstName: 'Sarah',
    lastName: 'Finnley',
    isDeveloper: false,
  },
];

const isDeveloper = function (person) {
  return person.isDeveloper;
};

const isEveryoneDeveloper = persons.every(isDeveloper);

console.log(isEveryoneDeveloper);
// false
```

In the follow up example, the array built-in method `some()` returns true if *some* item in the callback function returns `true`. In other words: At least one item needs to match the condition in order to have the function return `true`. If none of the items matches, it will return `false` though:

```javascript{7,9,10}
const persons = [ ... ];

const isDeveloper = function (person) {
  return person.isDeveloper;
};

const isSomeoneDeveloper = persons.some(isDeveloper);

console.log(isSomeoneDeveloper);
// true
```

Callback functions are a powerful construct in JavaScript. Yet they are not easily to grasp for beginners, so it's totally fine if you didn't get the custom `findPerson()` implementation right away (and still don't get it). What's important is that you understand how it's possible to pass functions into other functions which is often used for built-in methods such as array methods like `find()`, `every()`, and `some()`. In the end, callback functions are nothing more than functions that are passed as arguments to other functions.

### Exercises:

* Read more about [callback functions in JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function).
* Question: What would be the result if we were looking for a person which isn't in the array?
  * Answer: The result would be `undefined`, because `person` stays undefined while the if-else statement never meets the condition.
* Extend the for statement with a [break statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration#break_statement) which allows you to escape early from a loop whenever your job is done (e.g. you have found "Sarah" in the array of persons).
* Question: What would happen if two persons would match the search criteria (e.g. two persons have the name "Robin") in our `findPerson()` function from this section? Does the result change with and without break statement?
  * Answer: With a break statement, the function would return the first match, because it would break out of the loop after it. Without a break statement, the loop would look further for more matches. Once the second match is found, it would get assigned to the variable and overwrite the old match. Thus the last match gets returned.
* Read more about the built-in array methods [every()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every) and [some()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some).
* Question: What's the difference between the array built-in methods `indexOf()` and `findIndex()`.
  * Answer: While `indexOf()` just takes a JavaScript primitive as argument (like we did in a previous section), `findIndex()` allows more complex conditions by enabling you to use a callback function instead.
* In this section, we implemented `findPerson()` which works very similar to `find()`. The only difference was that `findPerson()` used as argument the `persons` array, while `find()` is a method called on the `person` array. Otherwise the passing of the callback function is the same and led us to the same results. Now, try to implement `some()` or `every()` yourself. Use the `findPerson()` function as blueprint, because `every()` and `some()`a re not much different, because they use a for statement and if-else statement too. If you don't succeed, do not worry. However, if you succeed, tap yourself on the back, because this is already advanced JavaScript.

## Reverse Engineering

The term **reverse engineering** is used in programming whenever there is already a solution to a problem and one tries to go backwards from this solution to understand all its single details which often leads ultimately to implementing a duplicated or alternative solution to it. While reverse engineering is not strictly bound to JavaScript and is not taught in every programming book, I want to take the time here to exercise reverse engineering on one example, because you will come across this phenomen more than once in your career as a developer.

In the previous section, we have learned about the built-in arrays `find()` method when we learned about the fundamental principle of a callback function in JavaScript. While the `find()` method returns one item from a list (if this item is present in the list in the first place), it does not return multiple items from a list in the case of multiple items meeting the search criteria. Fortunatly, there is the popular built-in array method called `filter()` which you will use quite often as JavaScript developer.

The `filter()` method takes a callback function which has access to every item as argument and returns a boolean which defines whether this item gets included in the filtered array (the from the method returned array) or not:

```javascript
const persons = [
  {
    fullName: 'Robin Wieruch',
    kids: ['Liam'],
  },
  {
    fullName: 'Sarah Finnley',
    kids: [],
  },
  {
    fullName: 'Esther Shaw',
    kids: ['Karl', 'Simone'],
  },
];

const hasKids = function (person) {
  return person.kids.length > 0;
};

const parents = persons.filter(hasKids);

console.log(parents);
// [
//   { fullName: 'Robin Wieruch', kids: ['Liam'] },
//   { fullName: 'Esther Shaw', kids: ['Karl', 'Simone'] },
// ]
```

In this example, we filter the array for persons who have kids. In code, we check whether the kids array for each person is greater than `0` in order to include them in the new `parents` array. Essentially `filter()` works very similar to `find()` from the previous section. The only difference is that `find()` returns only one item and `filter()` returns an array. So when looking for multiple possible matches, you would always use `filter()` over `find()`.

Next we will reverse engineer the `filter()` method, because we want to undertsand how it works internally and not just accepts that it's there. The filter operation is performed on an array (here: `persons`) and uses a callback function (here: `hasKids()`). With this knowledge, we will create our own more specific `filterParents()` function which takes at the beginning only one argument (here: `persons`) and should eventually return the same result as the `filter()` method from before:

```javascript
function filterParents(persons) {

}

const persons = [
  {
    fullName: 'Robin Wieruch',
    kids: ['Liam'],
  },
  {
    fullName: 'Sarah Finnley',
    kids: [],
  },
  {
    fullName: 'Esther Shaw',
    kids: ['Karl', 'Simone'],
  },
];

const parents = filterParents(persons);
```

The new `filterParents()` function has to iterate over all items of the list (here: `persons` that are passed from the outside as arguments). For every item that meets the search criteria (here: the person has a filled array with kids), the item gets pushed into a new array which eventually gets returned from the function:

```javascript{2-10}
function filterParents(persons) {
  let parents = [];

  for (let i = 0; i < persons.length; i++) {
    if (persons[i].kids.length > 0) {
      parents.push(persons[i]);
    }
  }

  return parents;
}
```

Now the search criteria is an implementation detail of `filterParents()`. By using a callback function as additional argument for this function, we can extract this implementation detail and tell the function from the outside what condition it has to meet to filter the array into a new array:

```javascript{1,5,15-17,19}
function filterParents(persons, hasKids) {
  let parents = [];

  for (let i = 0; i < persons.length; i++) {
    if (hasKids(persons[i])) {
      parents.push(persons[i]);
    }
  }

  return parents;
}

const persons = [ ... ];

const hasKids = function (person) {
  return person.kids.length > 0;
};

const parents = filterParents(persons, hasKids);
```

If you have a look at the `filterParents()` function, it does not solve any parents/persons/hasKids specific task anymore. It merely filters a list based on a condition which we provide with a callback function. So we can **refactor** (read: modify code without changing implementation details, e.g. just changing variables names) the specific `filterParents()` function to an abstract `filter()` function:

```javascript{1-11,19}
function filter(list, filterCondition) {
  let filteredList = [];

  for (let i = 0; i < list.length; i++) {
    if (filterCondition(list[i])) {
      filteredList.push(list[i]);
    }
  }

  return filteredList;
}

const persons = [ ... ];

const hasKids = function (person) {
  return person.kids.length > 0;
};

const parents = filter(persons, hasKids);
```

Changing code (e.g. functions) from **specific** (sometimes called **concrete**, e.g. `filterParents()`) to **abstract** (sometimes called **generic**, e.g. `filter()`) will become your second nature as developer eventually. The terms abstract and generic are very loosely used in JavaScript, however, in other programming languages they are more nuanced. However, do not jump too early on the abstraction wagon, because first you need to master writing code that's specific to one problem. Abstraction comes with more maturity as a developer.

Now, the final form of our `filter()` function is not much different from the built-in array's `filter()` method. While the former uses an array and a callback function as arguments, the latter operates on the array's method and passes the callback function to it as argument. Congratulations, you have implemented the popular `filter()` method yourself! Generally speaking, it's a good idea to implement some of the array's built-in methods yourself. It helps you to learn the fundamentals of JavaScript and to get better at JavaScript.

If you recap the last two sections about the `find()` and the `filter()` methods, you did the same thing for both method just in a different order. For the `find()` method, you implemented first your own function and then learned about the built-in array method. For the `filter()` method, it was the other way around: You learned first about the method and then reverse engineered it to your own implementation.

![](images/reverse-engineering.png)

Strictly speaking we didn't reverse engineer, but just started with a solution and tried to implement this solution from scratch. However, the gist is often similar, because when you reverse engineer you want to understand the implementation details and want to arrive at the same (or an alternative) solution.

### Exercises:

* Read more about [the array's built-in filter method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter).
* Question: Is there a shorter version to express the condition `person.kids.length > 0`?
  * Answer: Yes. It's `!person.kids.length`. If `length` is `0`, the logical NOT `!` operator negates and coerces `0` to `true`. In other words: The manually converted value for `Boolean(0)` is `false` plus the `!` negates it to `true`.

## Map and Reduce

When working in more complex applications, you will often have to modify data. For example, if you read data from a file or a server, the data is not always "well-shaped". Hence you will often perform **data manipulation** to get the data in a desired shape for your use case. One of the most common data manipulations you will hear about is the combination of filter, map, and reduce.

You have already learned about the array's built-in `filter()` method before. Now you will learn about the more advanced `map()` and `reduce()` methods. While not all of these three built-in array methods need to be used for every data manipulation use case, applying one or the other often already helps you to manipulate JavaScript arrays (and objects) into any shape.

All of these data manipulation methods use callback functions. While `filter()` is one of the easier ones out of the three, `map()` and `reduce()` are a bit more advanced, because their use cases are for beginners more abstract. Let's check out `map()` first. Essentially `map()` allows you to modify every item in an array:

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];

const multiplyByTen = function (number) {
  return number * 10;
};

const products = numbers.map(multiplyByTen);

console.log(products);
// [10, 20, 30, 40, 50, 60, 70, 80, 90]
```

In a more elaborate example, you may want to derive a `hasKids` boolean as property from the `kids` array. So whenever a `person` has a filled array of `kids`, which means that kids have a `length` greater than `0`, we assign the `person` a new `hasKids` property and set it to `true`. If the array is empty, the `person` sets this new propery `hasKids` to `false`:

```javascript
const persons = [
  {
    fullName: 'Robin Wieruch',
    kids: ['Liam'],
  },
  {
    fullName: 'Sarah Finnley',
    kids: [],
  },
];

const hasKids = function (person) {
  person.hasKids = person.kids.length > 0;

  return person;
};

const parents = persons.map(hasKids);

console.log(parents);
// [
//   { fullName: 'Robin Wieruch', kids: ['Liam'], hasKids: true },
//   { fullName: 'Sarah Finnley', kids: [], hasKids: false },
// ]
```

The `map()` method, like most other built-in array methods, iterates over all items. Internally a loop is running, like we have learned before when we have used the for statement for the `find()` and `filter()` functions, which helps you in the case of map to modify all items. You could also use an if-else statement in the callback function of the `map()` method to modify only specific items.

The built-in `reduce()` method is the hardest of all three to grasp and most developer pick it up only after being months into JavaScript. So don't worry if you don't get and use it right away. However, I want to expose you to these popular methods, because you will certainly see them in your career as a JavaScript developer.

So while `map()` allows you to modify every item and returns an array of the same size (e.g. `parents`), `reduce()` can alter the size or the whole structure (e.g. from array to object) of your array. The most straightforward example you will see out there is calculating the sum of numbers with the help of reduce:

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];

const sumAll = function (result, item) {
  return result + item;
};

const sum = numbers.reduce(sumAll);

console.log(sum);
// 45
```

In contrast to the other method's callback functions, reduce's callback function has as first argument the accumulator (called in code most often `acc` rather than `result`) and as second argument the current item (called in code most often `value` rather than `item`). As comparison, in our previous examples, the current item has been `person`. The accumulator, in this case the `result`, is the value which is carried over from every iteration and in this case summed up to the current value. The `reduce()` method accepts a third argument which let's you specify the accumulator you want to start with:

```javascript{7,10}
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];

const sumAll = function (acc, value) {
  return acc + value;
};

const sum = numbers.reduce(sumAll, 10);

console.log(sum);
// 55
```

Previously, `reduce()` coerced the initial accumulator to `0`, because we were using the `+` operator on numbers and we didn't specify any initial accumulator. However, this time we explicitly set the initial accumulator to `10`, hence our result is not `45` but `55`. You can read the function the following way: "We start with an accumulator. When iterating through the first item in the list, we return the sum of the initial `acc` (here: `10`) and the current value (here: `1`). When iterating through the second item in the list, we return the sum of the `acc` (here: `11`) -- which has been computed in the previous iteration -- and the current value. This goes on until we have added all the numbers on top of the initial accumulator of 10."

The `reduce()` method can be used for any data manipulation of an array that isn't a fit for `filter()` or `map()`. Here the book isn't going any deeper into `reduce()`, but we will maybe see more usages of it (and the other methods) later. Another noteworthy fact about these methods is that they can be *chained* onto each other:

```javascript{11-13}
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];

const multiplyByTen = function (number) {
  return number * 10;
};

const greaterThanFifty = function (number) {
  return number > 50;
};

const result = numbers
  .map(multiplyByTen)
  .filter(greaterThanFifty);

console.log(result);
// [ 60, 70, 80, 90 ]
```

Since `filter()`, `map()`, and `reduce()` all return a new array, we can straight away continue working on them by using the `.` notation. Only when the whole chain got evaluated, the result gets assigned to the variables (see operator precedence from one of the earlier sections, e.g. `.` precedes `=`). Anyway, chaining methods onto each other is just a shortcut. You could also write it this way:

```javascript
const products = numbers.map(multiplyByTen);
const onlyBigNumbers = products.filter(greaterThanFifty);
```

You can see how these three data manipulation methods will help you with any array modification. Another one you should have heard about, which is not really used for data manipulations though, is the infamous `forEach()` method. Essentially it is used as loop replacement (e.g. for loop) that you have learned earlier, however, there are some caveats to it. At this point, I don't want to go into much detail and rather just show you how it works by contrasting it to an example where we have used the for statement before to find "Sarah":

```javascript
const persons = [
  {
    firstName: 'Robin',
    lastName: 'Wieruch',
  },
  {
    firstName: 'Sarah',
    lastName: 'Finnley',
  },
];

let sarah;

// in this case the callback function is inlined
// but it can be passed as function too
// like in the filter, map, reduce examples
persons.forEach(function (person) {
  if (person.firstName === 'Sarah') {
    sarah = person;
  }
});

console.log(sarah);
// { firstName: 'Sarah', lastName: 'Finnley' }
```

In contrast to the other shown array methods, the `forEach` method does not return anything. The next section will dive more deeply into this noteworthy difference. Now, what about objects though? While arrays have an ordered list which can be iterated over in a loop/iteration or with an built-in array method, an object cannot be looped over that easily, because it has just key/value pairs. However, with the built-in `Object` we can turn these key/value pairs into a list of keys (or values):

```javascript
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
};

const keys = Object.keys(robin);

console.log(keys);
// [ 'firstName', 'lastName', 'yearBirth', 'isDeveloper' ]

const values = Object.values(robin);
console.log(values);
// [ 'Robin', 'Wieruch', 1991, true ]
```

If we would want to access each property with key *and* value in an array method, we could do the following transformation from object to array. We would transform an object to its keys, iterate over it with the `forEach()` method for arrays by chaining it,

```javascript
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1991,
  isDeveloper: true,
};

Object.keys(robin).forEach(function (key) {
  const value = robin[key];

  console.log(key, value);
});

// firstName Robin
// lastName Wieruch
// yearBirth 1991
// isDeveloper true
```

Now, don't worry if that's a lot to digest. At this point, I only want you to have seen these methods out in the wild and how they can be used. You are not supposed to know them off the top of your head now, but rather come back to this section oncde you are asked to manipulate some arrays (or objects) in your code. When working with data, `filter()`, `map()`, and `reduce()` will become swiss knife as a JavaScript developer.

### Exercises:

* In your favorite search engine, search for "filter map reduce" and open up the images tab. Go through these images to get a better sense of what these methods are doing and where they can help you.
* Read more about [built-in array methods in JavaScript](https://javascript.info/array-methods).
  * Read more about [the array's built-in map method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map).
  * Read more about [the array's built-in reduce method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce).
  * Read more about [the array's built-in forEach method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach).
* Read more about [the built-in Object and its methods in JavaScript](https://javascript.info/keys-values-entries).
  * Read more about [Object.keys()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys).
  * Read more about [Object.values()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values).
  * Read more about [Object.entries()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries).

## Mutability vs Immutability

Back to the fundamentals of programming and JavaScript. The last sections gave you lots of insights how to work with data in JavaScript. Often you will have to deal with data in the shape of arrays (e.g. list of users, articles, messages) which can be modified by using the `filter()`, `map()`, and `reduce()` methods. There is one concept in programming though which should be taught early on: mutability vs immutability.

The act of mutating a variable, which you will hear quite often when speaking to developers, can be translated into changing, modifying, altering, updating or manipulation a variable. So you may say that the data manipulation from before can also be called data mutation. But it's not that simple, because we have to differ between mutability and immutability.

![](images/mutation.png)

To start off: All JavaScript primitive values are immutable by default. This means, we cannot modify a JavaScript string for example. You may have seen by this time that we can access a string's characters not only with its built-in `charAt()` method but also with the bracket notation (similar to arrays):

```javascript
let adjective = 'Bold';

console.log(adjective[0]);
// 'B'
```

In the following case, we try to rewrite a string partially by changing its first character:

```javascript
let adjective = 'Bold';
adjective[0] = 'C';

console.log(adjective);
```

What does the last code snippet print to the console? You may have expected to see "Cold", but it's still "Bold". That's already the proof that values of JavaScript primitives, in this case strings, are immutable. In other words: primitive values cannot be changed, they can only be re-assigned:

```javascript
let adjective = 'Bold';
adjective = 'Cold';

console.log(adjective);
// 'Cold'
```

The ability to re-assign disappears though when using `const` instead of `let`. This is an important distinction, because many people wrongfully put `const` and immutability into the same basket, but `const` just means that a variable cannot be re-assigned whereas immutabilty means a variable cannot be changed.

![](images/reassign-variable.png)

It's also an important distinction for primtives that variables are not values, but that they point to values. The pointer can change to a new primtive value, but the primitive value itself cannot change. By using the `=` assignment operator, we can point a variable to a new value. The same happens when we declare one variable based on another variable, then re-assigning one variable to a new value does not change the other variable:

```javascript
let ageRobin = 30;
let ageSarah = ageRobin;

ageRobin = 31;

console.log(ageRobin);
// 31
console.log(ageSarah);
// 30
```

All these examples show that JavaScript values with a primitive data type (e.g. string, number, boolean) are immutable. You may have not thought about this fact before, however, it's a relief for every JavaScript developer that this is the default. It's not the default for more complex data structures such as objects and objects. These are mutable by default.


```javascript
const a = [1, 2];
const b = a;

a.push(3);

console.log(a);
// [1, 2, 3]
console.log(b);
// [1, 2, 3]
```

The last example shows two cases of mutability on arrays which are often major causes for unpredicted behavior (read: bugs): First, there exist built-in array methods (e.g. `push()`, `pop()`) which mutate arrays. In this example, adding an item to a list with `push()` will mutate the original array. But that's not everything to it. If another array (here: `b`) is based on an array (here: `a`), mutating the origin array will change the other array too (ripple effect).

Most developers discovering the mutability of arrays (and objects) have their struggle with it. What's the benefit of mutating the original array plus causing ripple effects when variables depend on each other? Imagine an ecommerce application where you have a shopping basket. The shopping basket lists 5 items that you wanna buy. As a developer, you know that this list is an array with 5 objects whereas each object has a title, price and so on. The benefit of mutability would be that you can change the variable once (e.g. remove an item from the shopping basket) and it would be reflected everywhere in the application.

![](images/mutation-benefit.png)

However, even though this may be a great implementation detail of the language itself, because it takes care of these updates for you, often it causes more harm than good. Especially these ripple effects throughout the application are a major cause for bugs in modern applications. Hence, developers try to avoid mutability in favor of immutability to achieve predictability rather than convencience. Meaning: Developers do not change arrays or objects, but instead create new values out of them and assign these to new variables. So the original variable/value pair stays instact. In the following, I want to give you some tools to avoid mutability on arrays (and objects) and embrace immutability instead.

### Immutable Tool 1: Immutable Methods

First, there are built-in array methods which embrace immutability. If you read through the [JavaScript documentation for built-in array methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array), always look for the section *"Return value"*. For instance, the built-in array method `push()` returns the new length of the property; which means in reverse that the array itself must change to get to the desired result of the operation (here: adding an item to the list):

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

const whatIsThis = firstNames.push('Liam');

console.log(firstNames);
// ['Robin', 'Sarah', 'Esther', 'Liam']

console.log(whatIsThis);
// 4
```

In contrast, the built-in array method `concat()` says in its documentation: *"[returns a] new Array instance"*. That's the term you are searching for when you want to embrace immutabuility over mutability, because returning a new array means that the original array does not change by calling the method:

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

const whatIsThis = firstNames.concat('Liam');

console.log(firstNames);
// ['Robin', 'Sarah', 'Esther']

console.log(whatIsThis);
// ['Robin', 'Sarah', 'Esther', 'Liam']
```

That's excactly what developers strive for these days: After variables have been assigned once, never change them again. Instead, derive new values from them by assigning these to new variables.

### Immutable Tool 2: Use Return Values

Striving for predictable code means embracing immutablity. As a rule of thumb: Always check for methods that return new values instead of changing the original values. You can already see the difference on how these methods are called. Use the one which let's you assign the returned new value to a new variable:

```javascript
// no assignment, often bad signal
const numbers = [1, 2, 3];
numbers.push(4);

// assignment of new value, good signal
const characters = ['a', 'b', 'c'];
const newCharacters = characters.concat('d');
```

Often you will find mutability/immutability pairs such as `push()` and `concat()` in the JavaScript documentation. Again, look for the methods that say explicitly that they are returning a new instance of an array. Every time you find such a pairing of methods, use the one that enforces immutability as a best practice.

### Immutable Tool 3: If Mutate, Copy!

If there is no immutable version of a method, you are sometimes forced to use a built-in array method which mutates the original array. Then you can perform the following trick to create a copy of the original array before using the method that mutates it. This way, the original array stays intact while only the copy gets mutated.

![](images/copy.png)

Since the copy (sometimes called clone) is a new variable, it will not cause any ripple effects when it gets mutated. For instance, the built-in array method `slice()` helps you to create a copy of an array:

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

const firstNamesCopy = firstNames.slice();

firstNamesCopy.push('Liam');

console.log(firstNames);
// ['Robin', 'Sarah', 'Esther']

console.log(firstNamesCopy);
// ['Robin', 'Sarah', 'Esther', 'Liam']
```

After all, fortunately there are more methods that return a new value (not mutating methods) than methods that modify the original value (mutating methods). The methods `filter()`, `map()`, and `reduce()` are all returning new arrays, hence do not modify the original array, and therefore are a best practice to use for embracing immutability. However, be aware of the methods (e.g. `push()`) that mutate the original value, because they will certainly cause uwnanted pitfalls in your code eventually.

Anyway, even though you see all these recommendations and best practices here, do not stress too much about mutability vs immutability as a JavaScript beginner. This section is only here to prepare you for these kind of behaviors, but it certainly cannot prevent them for you. You will likely run into them, experience them first hand, and then hopefully rememeber this section in order to solve them.

### Exercises:

* Question: Does a built-in string method such as `toUpperCase()` mutate a string?
  * Answer: No, because it returns a new string. The original string isn't changed. Trying it yourself, you can see that when you assign a new variable from `toUpperCase()`, e.g. `const upperFullName = fullName.toUpperCase();`, the `fullName` value stays intact while a new variable `upperFullName` gets assigned by the returned value.
* Question: If you want to embrace immutability, what built-in array methods would you use: `splice()` vs `slice()`?
  * Answer: If it should return a new value, one would need to use `slice()`. Pro tip: Using `slice()` without an argument returns a copy of the array.
* Question: We have used the built-in `concat()` method on an array and provided a string primitive value (e.g. `'Liam'`). What happens if you use an array instead of a string?
  * Answer: Usually it's the other way arround that `concat()` on an array is used to concatenate two arrays. However, as we have seen in this section, it's also possible to concat only one primitive value.

## Destructuring Assignment

The **destructuring assigment** is used in modern JavaScript and helps you to read from arrays and objects more efficiently. We will start of with an example which illustrates why the destructring assigment reshaped how we write concise JavaScript:

```javascript
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1988,
};

const firstName = robin.firstName;
const lastName = robin.lastName;

console.log(`My initials are ${firstName[0]}${lastName[0]}.`);
// My initials are RW.
```

The code snippet illustrates how inefficient it is to read multiple properties from an object with a growing size of properties, because we need one line for assigning each property to a new variable. This example is a bit far fetched though, because one could also just use the `.` noation on an object inlined in the console statement without the intermediate variable assignment. However, often you need to assign an object's properties to new variables and once you have to perform this task for more than one property, the assignments grow linearly with the size of properties. Entering the destructuring assignment, specifically the **object destructuring assignment** (short: object destructuring or destructuring) which lets us assign an object's properties to new variables in one line:

```javascript{7}
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  yearBirth: 1988,
};

const { firstName, lastName } = robin;

console.log(`My initials are ${firstName[0]}${lastName[0]}.`);
// My initials are RW.
```

Basically you can assign each property from an object by using curly brackets on the left-hand side and the proptery name. When destructuring multiple properties, the list of properties becomes comma separated. If you want to have a different name for a property, you can use an alias which are used to avoid variable name collision:

```javascript
const robin = {
  firstName: 'Robin',
  lastName: 'Wieruch',
};

const sarah = {
  firstName: 'Sarah',
  lastName: 'Finnley',
};

const { firstName: robinName } = robin;
const { firstName: sarahName } = sarah;

console.log(`Hi ${robinName} and ${sarahName}.`);
// Hi Robin and Sarah.
```

The object destructring can be used for a function's parameters too:

```javascript
function getName({ firstName, lastName }, asInitials) {
  if (asInitials) {
    return `${firstName[0]}${lastName[0]}`;
  } else {
    return `${firstName} ${lastName}`;
  }
}

const person = {
  firstName: 'Robin',
  lastName: 'Wieruch',
};

console.log(getName(person, true));
// 'RW'
```

In contrast to the object destructuring, the **array destructuring assignment** (short: array destructuring or destructuring) is used not as often. They get more traction in modern frameworks such as React.js though. But see for yourself the following example of an array destructuring:

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

const [robin, sarah] = firstNames;

console.log(`${robin.toUpperCase()} & ${sarah.toUpperCase()}`);
// 'ROBIN & SARAH'
```

From a first look, array destructuring differs from object destructuring just by using a different bracket. However, since objects are unordered, you have to specify the property name which you want to extract. On the other hand, the destructured items from an array need to be destructured in order, because there is no explicit name to reference them. This can be a benefit though, because you can give the destructured items any name which only works with aliases for object destructuring.

![](images/destructuring.png)

It's noteworthy that all destructuring operations leave the original variable and its value intact. Thus, destructuring shouldn't prevent you from keeping your data structures immutable as discussed before. In contrast, destructuring makes you are more efficient programmer, because you access objects and arrays in a more concise manner.

### Exercises:

* Read more about [the destructuring assignment in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment).
  * See more examples in action about [the destructuring assignment](https://javascript.info/destructuring-assignment).
* Question: In the object destructuring assignment with the aliases for `robinName` and `sarahName`, what would happen if we would not use the aliases and just use the `firstName` destructuring for both variable assignments?
  * Answer: We would get an error: `SyntaxError: Identifier 'firstName' has already been declared`.

## Spread and Rest Operator

*Note: Do not mistake these operators with the three dots I have used previosuly in this book. Usually my books use `...` for an entire line of code to signal irrelevant code or code which isn't important for this parapgraph. The three dots are also used whenever data structures like arrays (e.g. `[ ... ]` ) and objects (e.g. `{ ... }` ) should not be repeated every time. There I show the data structure once and use the dots as placeholders afterward.*

In modern JavaScript, you will likely see the three dot `...` operator. When it is used on the right-hand side of an assignment, it's called spread operator. In contrast, when it is used on the left-hand side of an assignment, it's called rest operator.

![](images/spread-vs-rest.png)

The **spread operator** is usually used for arrays and objects and allows the developer to spread their values into places such as other arrays, objects, or even functions. One of the most common examples for the spread operator is spreading one data structure into another one, e.g. one array's entries get spread with the three dots into another array which may or may not have values itself:

```javascript
const firstNames = ['Robin', 'Sarah'];
const moreFirstNames = ['Liam', ...firstNames, 'Esther'];

console.log(moreFirstNames);
// [ 'Liam', 'Robin', 'Sarah', 'Esther' ]
```

The same applies for objects where the key/value pairs can be spreaded into another object:

```javascript
const privateLife = {
  firstName: 'Robin',
  lastName: 'Wieruch',
};

const professionalLife = {
  job: 'Developer',
  occupation: 'Self Employed',
};

const person = {
  ...privateLife,
  nickname: 'Hood',
  ...professionalLife,
  pet: 'Dog',
};

console.log(person);
// {
//   firstName: 'Robin',
//   lastName: 'Wieruch',
//   nickname: 'Hood',
//   job: 'Developer',
//   occupation: 'Self Employed',
//   pet: 'Dog'
// }
```

An operation with the spread operator is an immutable operation which means that the original value stays intact. See for yourself by printing `firstNames`, `privateLife`, or `professionalLife` to the console. The spread operator can also be used to copy arrays and objects, but only their first level. So if an array is multidimensional or an object nested into another object, you need to spread the lower levels too for really copying an immutable variant of them.

```javascript
const firstNames = ['Robin', 'Sarah'];
const copyFirstNames = [...firstNames];

const person = {
  firstName: 'Robin',
  lastName: 'Wieruch',
};
const copyPerson = { ...person };
```

Essentially the spread operator can be used whenever you want to create a new variable based on the content of another variable plus optional additional content if not creating only a copy of it. For example, you can spread an array into a new array and add a new item at the start of the array. Or you can spread an object into a new object and add properties to it.

```javascript
const person = {
  firstName: 'Robin',
  nickname: null,
  lastName: 'Wieruch',
};

const personWithNickname = {
  ...person,
  nickname: 'Hood',
};

console.log(personWithNickname);
// { firstName: 'Robin', nickname: 'Hood', lastName: 'Wieruch' }
```

As you can see from the last example, it's also possible to overwrite an property from a spreaded object by defining the same property name with a value after the spreading. So you can do lots of data manipulation on arrays and objects by only knowing about the spread operator without using built-in array or object methods.

While the spread operator expands its content, the **rest operator** kinda condenses it. The rest operator is not really called rest operator. Instead it's differentiated into rest destructuring and rest parameter. Let's begin with the **rest destructuring** which is used within the previously learned destructuring assignment:

```javascript
const person = {
  firstName: 'Robin',
  lastName: 'Wieruch',
  password: 'Geheim',
};

const { password, ...names } = person;

console.log(names);
// { firstName: 'Robin', lastName: 'Wieruch' }

console.log(`Hello, I am ${Object.values(names).join(' ')}!`);
// Hello, I am Robin Wieruch!
```

The rest destructuring is optionally used with three dots on the left-hand side of a destructring assignment. If it is used, it's always the last element of the destructuring which collects all the remaining properties. The same rest destructuring can be used for arrays where it collects all the remaining items in an array:

```javascript
const firstNames = ['Robin', 'Sarah', 'Esther'];

const [boy, ...girls] = firstNames;

console.log(`There is one boy: ${boy}`);
// There is one boy: Robin

console.log(`There are ${girls.length} girls: ${girls.join(', ')}`);
// There are 2 girls: Sarah, Esther
```

Essentially a rest destructring is always used when you want to separate certain items from an array or certain properties from an object. In contrast, the rest operator is called **rest parameter** in functions. It can be used optionally with its three dots as last parameter to collect all the remaining paramaters:

```javascript
function getSum(addendOne, addendTwo, ...moreAddends) {
  const remainingSum = moreAddends.reduce(function (sum, value) {
    return sum + value;
  });

  return addendOne + addendTwo + remainingSum;
}

const sum = getSum(1, 2, 3, 4);

console.log(sum);
// 10
```

While the spread operator is used on the right-hand side for shaping derived data structures from arrays and objects, the rest rest operator is used to collect all the remaining properties/items in a destructuring assignment or to collect all the remaining parameters in a function. Whiel you can certainly write modern JavaScript without knowing about these operators, you will likely see them in your day to day work.

### Exercises:

* Read more about [the rest operator and the spread operator in JavaScript](https://javascript.info/rest-parameters-spread).
  * Read more about [the spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax).
  * Read more about [the rest parameter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters).
* Question: What error is printed when the rest destrucutring is not used as last element?
  * Answer: `SyntaxError: Rest element must be last element`.
* Question: The example with the `getSum` function and the rest parameter has a bug. What's the bug, why does it happen, and how could we fix it?
  * Answer: If only two arguments get passed to the function, we will receive the error: `TypeError: Reduce of empty array with no initial value`. A rest parameter becomes an empty array when there is no rest. Hence the `reduce()` method operates on an empty array, which is fine, but not if no initial accumulator is provided. In order to fix it, we have to use `reduce(callbackFunction, 0)`, so using `0` as initial accumulator for the sum.

## Default Values, Variables, and Parameters

There are various techniques in JavaScript to address default values, variables or parameters. In this section, we will go through these step by step. Afterward, you have one section to refer to for handling such fallbacks. Let's get started with the usualy suspect: the if-else statement to conditionally assign a value to a variable or in this case to conditionally assign a fallback value:

```javascript
function getName(fullName, nickname) {
  if (fullName) {
    return fullName;
  } else if (nickname) {
    return nickname;
  } else {
    return 'Anonymous';
  }
}

console.log(getName('Robin Wieruch', 'Hood'));
// 'Robin Wieruch'

console.log(getName(null, 'Mr. X'));
// 'Mr. X'

console.log(getName(null, null));
// 'Anonymous'
```

As alternative, this could be done with a ternary operator as well. However, since there is more than one condition here, there needs to be more than one ternary operator which results in poor readability. For the sake of completeness though, here an example of a nested ternary operator:

```javascript{2}
function getName(fullName, nickname) {
  return fullName ? fullName : nickname ? nickname : 'Anonymous';
}

console.log(getName('Robin Wieruch', 'Hood'));
// 'Robin Wieruch'

console.log(getName(null, 'Mr. X'));
// 'Mr. X'

console.log(getName(null, null));
// 'Anonymous'
```

An if-else statement in its basic usage is totally fine to use for this problem. However, let's evaluate a few more advanced tools in comparison. In the end, you decide which feels most comfortable to you, but at least you have seen all of them to make an informed decision and to know what these are when you encounter them in your career as a JavaScript developer.

First, the logical OR operator can be used for such conditional fallbacks (also called **short circuiting** or **short circuit evaluation**). This operator returns its right-hand side operand if the left-hand side operand is a falsy (read: `false`, `undefined`, `null`, `0`, `''`) value. This is in the case of using only one logical OR operator. In the case of multiple logical OR operators, like in our case, you can interpret it as *"the first truthy value in the line gets returned"*:

```javascript{2}
function getName(fullName, nickname) {
  return fullName || nickname || 'Anonymous';
}

console.log(getName('Robin Wieruch', 'Hood'));
// 'Robin Wieruch'

console.log(getName(null, 'Mr. X'));
// 'Mr. X'

console.log(getName(null, null));
// 'Anonymous'
```

This approach has been used for a long time to provide fallback values if other values are not present (read: falsy). However, there is one flaw to it which is often a cause for bugs. What if my nickname should be a number and in this very specific case the number 0 (e.g. "Mr. 0"):

```javascript{5-6}
function getName(fullName, nickname) {
  return fullName || nickname || 'Anonymous';
}

console.log(getName(null, 0));
// 'Anonymous'
```

One might expect to see printed `0` instead of `'Anonymous'`, however, since `0` is a falsy value, the next right-hand side operand in the line of logical OR operators gets evaluated. In modern JavaScript, there is a more nuanced operator called the **nullish coalescing operator**. It's used similar to the logical OR operator, but evaluates only `null` and `undefined` to false and not other falsy values such as `''` or `0`:

```javascript{2,6}
function getName(fullName, nickname) {
  return fullName ?? nickname ?? 'Anonymous';
}

console.log(getName(null, 0));
// 0
```

While the logical OR operator is well supported in browsers and older Node.js versions, it comes with the nuanced flaw of evaluating all falsy values to false. In contrast, the nullish coalescing operator takes care of this flaw, is however only available in modern browsers (and modern Node.js) and therefore not widely used yet.

When using a function like we did in the previous examples, there is another approach called the **default paramater**. This means we can give each parameter a fallback value in case of the value being `undefined` or `null`:

```javascript
function getName(fullName = 'Anonymous') {
  return fullName;
}

console.log(getName('Robin Wieruch'));
// 'Robin Wieruch'

console.log(getName(null));
// 'Anonymous'
```

In this section, you have seen many variants of how to achieve a fallback if a value is not provided. If you have a function, the go-to solution is often the default parameter. If you can't use this approach, then your way to go would be the logical OR operator or the nullish coalescing operator. If this is too advanced at this time, just using the if-else statement is fine too.

## Exercises:

* Read about [short circuiting with the logical OR operator in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR).
  * Read more anout [short circuiting with the logical AND operator too](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND).
* Read more about the [nullish coalescing operator in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator).
  * See more examples in action about [the nullish coalescing operator](https://javascript.info/nullish-coalescing-operator).
  * [Can I Use](https://caniuse.com/mdn-javascript_operators_nullish_coalescing) is an important website for web developers. You can check different features of JavaScript there and see how well they are supported in modern browsers. Check how well the nullish coalescing operator is supported.
* Read more about [the default parameter in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters).
  * Question: What happens if a default parameter is used and we provide `0` as argument to the function call?
    * Answer: Even though `0` is a falsy value, the default parameter, similar to the nullish coalescing operator, only uses the default if the parameters is `null` or `undefined`.
  * Question: What happens if no argument is provided to a function which expects one argument though and has a default paramater in place for it?
    * Answer: The default parameter is used, because the argument that isn't provided results in a `undefined` parameter which thereby results in the default parameter being used.

## Optional Chaining

Nested objects in JavaScript are not a rarity. So far, you have only seen objects and nested objects which go only one level deep. However, in a real world application you will have to deal with objects that are nested by multiple levels. Take the following data as example:

```javascript
const response = {
  status: 200,
  data: {
    users: [
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
    ],
  },
};
```

This could be a real world response when asking for a remote server for data. You will learn later how you perform such requests, however, what matters is that nested objects are everywhere. In order to access these objects, you are using the dot notation. For example, reading the first user's `firstName` is done as follows:

```javascript
const firstName = response.data.users[0].firstName;
```

However, often you cannot be sure whether all nested properties are there. For example, the `data` could be empty, because the request to the remote server was errornous:

```javascript{2-3}
const response = {
  status: 404,
  data: null,
};

const firstName = response.data.users[0].firstName;
```

In this case, you would get an JavaScript error when reading the `users` property, because `data` is `null` and there is no `users`: `TypeError: Cannot read property 'users' of null`. In the worst case, this could break your whole application. Now, in order to safely access the data, one could add a safety check before:

```javascript
let firstName;

if (response.data) {
  firstName = response.data.users[0].firstName;
}
```

In the case of data being `null`, the condition would evaluate to `false` and we would leave `firstName` undefined. On the other hand, in the case of data being filled, the condition evaluates to true and `firstName`, if users are there, would get assigned. You may have already heard the next flaw from the last sentence: *"if users are there"*. In the case of a successful response, it could still happen that there are no `users` in the database of the remote server:

```javascript
const response = {
  status: 200,
  data: {
    users: [],
  },
};
```

Even with our safety check in place, we would get `TypeError: Cannot read property 'firstName' of undefined` this time. Hence we would need to extend the condition to check for a filled users array:

```javascript
if (response.data && response.data.users.length) {
  firstName = response.data.users[0].firstName;
}
```

You see how data from a third-party adds lots of uncertanty, because you never know whether everything is there as expected. If something is missing and you are not checking for it, the whole application may break. However, using an if-else statement as safety check everytime seems tedious as well. In modern JavaScript, we can use **optional chaining** to access nested objects safely without throwing errors even though intermediate properties are missing:

```javascript{8}
const response = {
  status: 200,
  data: {
    users: [],
  },
};

const firstName = response.data?.users[0]?.firstName;
```

The `?` allows you to access properties of objects with a safety check. Whenever this property isn't there, the dot notation won't go any further to access deeper nested properties. So if `data` is not there, it won't continue accessing `users` anymore and instead assign `undefined` to `firstName`.

Optional chaining makes your life as a developer easier, because you don't need to fill your codebase with if-else statements to access deeply nested objects. Instead, you can use optional chaining with `?` after every property to apply this kind of safety check instead.

### Exercises:

* Read more about [optional chaining in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining).
  * See more examples in action about [optional chaining](https://javascript.info/optional-chaining).
  * [Can I Use](https://caniuse.com/mdn-javascript_operators_optional_chaining) is an important website for web developers. You can check different features of JavaScript there and see how well they are supported in modern browsers. Check how well optional chaining is supported.

## Problem Solving

Problem solving is a developer's everyday business. Hence this section of the book will walk you through a problem that you may face as a developer and how you could approach it. Therefore this section will not introduce any new JavaScript feature, but instead use the features that you have learned before. The problem: Given a list of full names, return the initials for each full name in a list:

```javascript
const fullNames = [
  'Robin Wieruch',
  'Sarah Finnley',
  'Esther Shaw',
  'Liam Hugsley',
];

const nameInitials = ...

console.log(nameInitials);
// ['RW', 'SF', 'ES', 'LH']
```

Solving a problem comes always down to breaking the problem into smaller problems. In the following, we will approach each part step by step and will conclude with a solution eventually. First we remove complexity from the problem: given only one name (and removing the compelxity of having a list of names), return the initials of this one name. First, we extract one name from the array:

```javascript
const fullNames = [
  'Robin Wieruch',
  'Sarah Finnley',
  'Esther Shaw',
  'Liam Hugsley',
];

const fullName = fullNames[0];
console.log(fullName);
// 'Robin Wieruch'
```

Second, in order to get the initials of the first and last name, we somehow need to distinguish first and last name into separate variables. Fortunatelty there is the built-in `split()` method for strings which splits a string into an array of strings at a given character or characters. In this case, we want to split the string at the empty space:

```javascript{4,6-7}
const fullNames = [ ... ];

const fullName = fullNames[0];
const names = fullName.split(' ');

console.log(names);
// ['Robin', 'Wieruch']
```

Third, we can use array destructuring to separate both items in the list into two string variables with descriptive names:

```javascript{5,7-8}
const fullNames = [ ... ];

const fullName = fullNames[0];
const names = fullName.split(' ');
const [firstName, lastName] = names;

console.log(firstName, lastName);
// 'Robin' 'Wieruch'
```

Fourth, since strings can be accessed like arrays by using indexes, we can use the zero index to get the first letters of first and last name:

```javascript{6-7,9-10}
const fullNames = [ ... ];

const fullName = fullNames[0];
const names = fullName.split(' ');
const [firstName, lastName] = names;
const firstNameInitial = firstName[0];
const lastNameInitial = lastName[0];

console.log(firstNameInitial, lastNameInitial);
// 'R' 'W'
```

Finally, we can concatenate both initials for first and last name into a new initial for the full name:

```javascript
const fullNames = [ ... ];

const fullName = fullNames[0];
const names = fullName.split(' ');
const [firstName, lastName] = names;
const firstNameInitial = firstName[0];
const lastNameInitial = lastName[0];
const nameInitial = `${firstNameInitial}${lastNameInitial}`;

console.log(nameInitial);
// 'RW'
```

The code literally shows how we solved this problem for a single full name step by step. Now, you can leave the code this way or condense it by putting certain operations in one line. For example, accessing the first full name, splitting it, and retrieving first and last name from it could be put in one line. Furthermore the same would apply for accessing the initials of each name and interpolating them into a new string:

```javascript{3-4}
const fullNames = [ ... ];

const [firstName, lastName] = fullNames[0].split(' ');
const nameInitial = `${firstName[0]}${lastName[0]}`;
```

Refactoring code like this from more to less (or less to more) lines comes always with the tradeoff for readability. While you don't want to have your code too much condensed, because makes it less readable due to lots of dot notations, chained methods, and none existent intermediate descriptive variable names, you don't want to leave your code too bloated where each line only serves one atomic purpose and it gets difficult for someone to see the forest for the trees. In the end, always ask yourself whether you would be comfortable reading and understanding your code after months have passed and whether your teammates working on the same codebase would feel the same way. For example, one could a "genius" coder and put everything in one operation:

```javascript{3-5}
const fullNames = [ ... ];

const nameInitial =
  fullNames[0].split(' ')[0][0]
  + fullNames[0].split(' ')[1][0];
```

This seems to be one refactoring step too much. Simplicity often trumps cleverness in code. Another developer reading this code would have to trust you that this operation returns the initials of the full name, because they need to look twice what's happening here. Speaking of twice, the code isn't DRY too, because we redundantly apply the split operation on the same value. So going back to the previous example, we can see how it makes sense keeping it as two operations for the sake of readability and DRYness:

```javascript
const fullNames = [ ... ];

const [firstName, lastName] = fullNames[0].split(' ');
const nameInitial = `${firstName[0]}${lastName[0]}`;
```

Anyway, we didn't finish the problem yet. We projected the complex problem onto a smaller problem by coming up with a solution for a single full name and not a list of full names. Now we need to elevate the solution so that it macthes the complex problem as well. Since we are dealing with an array and we want to apply an operation for every entry in the array, we can use a for statement:

```javascript{8-11}
const fullNames = [
  'Robin Wieruch',
  'Sarah Finnley',
  'Esther Shaw',
  'Liam Hugsley',
];

let nameInitials = [];
for (let i = 0; i < fullNames.length; i++) {
  // do the operation
}

console.log(nameInitials);
// []
```

Within this loop, we can move the operation from before. Do not forget to change how the `fullNames` get accessed. Rather than accessing the `0` indexed item (like `fullNames[0]`) for every pass through of the loop, we want to access the looped item (like `fullNames[i]`) itself:

```javascript{5-6}
const fullNames = [ ... ];

let nameInitials = [];
for (let i = 0; i < fullNames.length; i++) {
  const [firstName, lastName] = fullNames[i].split(' ');
  nameInitials.push(`${firstName[0]}${lastName[0]}`);
}

console.log(nameInitials);
// ['RW', 'SF', 'ES', 'LH']
```

We could use `concat()` over `push()` here for the sake of immutability and best practice, however, since the `nameInitials` got only initialized before and isn't used somewhere else, it's okay to just mutate it here and fill it up with the items. But you could also use `concat()` instead, just showing off `put()` here, because at some occassions it's okay to use it.

We have solved the problem and at your stage of learning JavaScript this is an awesome result. However, I want to take this solution one step further by using one of our popular built-in array methods on the `fullNames` rather than using the for statement. Could you think of one array method without looking at the next code that would be the perfect fit for this case?

```javascript{3-6}
const fullNames = [ ... ];

const nameInitials = fullNames.map(function (fullName) {
  const [firstName, lastName] = fullName.split(' ');
  return `${firstName[0]}${lastName[0]}`;
});
```

The built-in `map()` method matches perfectly for this transformation, because it allows one to map one array to a new array by performing an operation for each item in the list. Last but not least, as a cherry on top, you could make this utilty reusable for other stakeholders in a larger application by putting it into a function.

Finally you have your finished solution for the problem. You are a problem solver now! In this section, we solved a problem by breaking it down into smaller problems. First, we projected a complex problem space on a simpler problem space (meaning in this case: operating on a string rather than an array). Then we approached the simpler problem step by step by breaking it down into a sequence of problems and refactored our final solution into a more condensed version without going overboard with the refactoring. Last, we projected the simpler problem onto the more complex problem again by just using our previous solution within a loop for the array. After all, even though this section didn't teach you much new about JavaScript itself, I hope it gave you a good impression on how to solve problems as a day to day developer.

### Exercises:

* Question: When we retrieved the first full name from the list of full names, we used the bracket notation `fullNames[0]`. How could you access the the first full name with array destructuring instead?
  * Answer: With array destructuring, we could extract the first full name bu destructuring only the first item from the list: `const [fullName] = fullNames;`
* Extract the utility of retrieving a list of initials from a list of names into a reusable function.

## Arrow Functions

You have learned a lot about functions at this point: as a beginner, you know that there are functions in JavaScript and that they are first-class citizens (meaning: they can be passed around as values). As an aspiring intermediate JavaScript developer, you know about callback functions. Now, as a modern JavaScript developer, we will get to know the modern concept of **arrow functions**. Take the following function as example which is not using an arrow function yet:

```javascript
function getFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

const person = {
  firstName: 'Robin',
  lastName: 'Wieruch',
};

console.log(getFullName(person.firstName, person.lastName));
// 'Robin Wieruch'
```

Seeing arrow functions in a side-by-side comparison, you see that they make functions more concise by removing the function keyword and using an arrow instead:

```javascript
const getFullName = (firstName, lastName) => {
  return `${firstName} ${lastName}`;
};
```

You can also see how an arrow function is only available as function expression, thus the more official name **arrow function expression**. But that's not all to arrow function's conciseness. If an arrow function only has a return statement in its body, one can remove the curly brackets and the return keyword:

```javascript
const getFullName = (firstName, lastName) =>
  `${firstName} ${lastName}`;
```

Essentially this strips down a function to its essential parts and ecourages keeping functions small. However, often you will have functions with more lines of code in their body, so stripping away the return keyword and the curly brackets does not become the default.

![](images/arrow-function-anatomy.png)

When arrow functions are used as callback functions, their conciseness encourages us to inline them as anonymous arrow functions. With the function keyword, this turned out to be less readable and thus we extracted the function expression as a separated variable declaration (see callback function section). However, when using arrow functions as inlined functions, it becomes more readable:

```javascript
const fullNames = [
  'Robin Wieruch',
  'Sarah Finnley',
  'Esther Shaw',
  'Liam Hugsley',
];

const nameInitials = fullNames.map((fullName) => {
  const [firstName, lastName] = fullName.split(' ');
  return `${firstName[0]}${lastName[0]}`;
});

console.log(nameInitials);
// ['RW', 'SF', 'ES', 'LH']
```

However, if the arrow function has multiple lines of code in its body (like in the previous example), it's still a tradeoff between readability and a developer's convencience. It's arguable often still a good idea to extract it as a named arrow function expression:

```javascript
const getInitials = (fullName) => {
  const [firstName, lastName] = fullName.split(' ');
  return `${firstName[0]}${lastName[0]}`;
};

const nameInitials = fullNames.map(getInitials);
```

However, if a callback function (here the arrow function) is a one-liner due to the missing return keyword (also called **implicit return statement**), it's often used as inlined anonymous arrow function:

```javascript
const names = [
  'Robin Wieruch',
  'Sarah Finnley',
  'Esther Shaw',
  'Liam Hugsley',
];

const firstNames = names.map((name) => name.split(' ')[0]);

console.log(firstNames);
// ['Robin', 'Sarah', 'Esther', 'Liam']
```

In modern JavaScript, the majority of your time you will see arrow function expressions over function expressions. There will be times when you will see function declarations though. For once, they put more emphasize to the function in contrast to other data types such as strings or objects, but also because there are subtle yet important differences between arrow functions and functions which we will talk about later.

### Exercises:

* Read more about [arrow functions in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions).
  * See more examples in action about [arrow functions](https://javascript.info/arrow-functions-basics).

## Hoisting

Whenever you run code in JavaScript, hoisting takes places before the execution of the actual code. It's the act of allocating memory for variable and function declarations. The following two code snippet illustrate how hoisting works for function declarations. First, you have been writing similar code throughout the book where function declaration is followed by function call:

```javascript
function getFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

const fullName = getFullName('Robin', 'Wieruch');
```

Due to hoisting, a function declaration can be called before it has been actually declared:

```javascript
const fullName = getFullName('Robin', 'Wieruch');

function getFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}
```

Hoisting allocates all function delcarations into memore before the actual code runs. The same does not apply for function expressions (or arrow function expressions) though, because it would throw an error (`ReferenceError: Cannot access 'getFullName' before initialization`):

```javascript
const fullName = getFullName('Robin', 'Wieruch');

const getFullName = (firstName, lastName) =>
  `${firstName} ${lastName}`;
```

As mentioned in the beginning, hoisting is also applicable to variables, but only variables declared with `var`. These variables get initialized with `undefined` before the executing code (after the hoisting) eventually reaches the actual declaration. Please read more about this in the exercises which also explains why `var` should not be used anymore.

Active use of hoisting is rarely seen in JavaScript these days, because `var` disappeared in favor of `const`/`let` and function declarations are most often replaced by arrow functions. However, when you climb the ladder to being an advanced JavaScript developer, you will find some occassions where it makes sense to have a function declaration for the benefit of hoisting.

### Exercises:

* Read more about [hoisting in JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting).
* Read more about [how var is different from const and let in JavaScript](https://www.robinwieruch.de/const-let-var).

## Scope

The term scope needs to get touched eventually, because its a fundamental block of JavaScript. While you will think actively about how you scope your code, scoping is your every day companion when you write functions and control structures (e.g. if-else statement, for statement). The **scope** is defined as the current context of execution. In order to understand this statement, let's walk through the following example which presents us with two scopes:

```javascript
function getFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

const fullName = getFullName('Robin', 'Wieruch');
```

While the **global scope** is everything outside of the function, the **function scope** (sometimes more unspecifically called **local scope**) is everything inside the function. Even though the present code has these two scopes, and they act for us behind the scenes, we cannot really grasp them by having this example. So let's change the example to something more questionable:

```javascript
const firstName = 'Robin';
const lastName = 'Wieruch';

function getFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

const fullName = getFullName(firstName, lastName);
```

The code works the same as before, however, you may feel confused by the variable names which stems from `firstName` and `lastName` being declared and passed to the function as arguments, but beging used as parameters with the same name within the function. Hence we usually try to differ paramater names from argument names whenever the argument's get declared as variables before the functions. Anyway, this code works though, because the function uses the values from its own scope first. If the values are not there, it reaches into the next available scope outside (until it reaches the global scope) as we can see in the next example:

```javascript
const firstName = 'Robin';
const lastName = 'Wieruch';

function getFullName() {
  return `${firstName} ${lastName}`;
}

const fullName = getFullName();
```

The examples shows us that inner scopes can reach into outer scopes, however, vice versa the outer scope cannot reach into inner scope. In the following case, we would receive a `ReferenceError: fullName is not defined`, because it is only defined in the function's scope but the global scope cannot reach into it for the printing:

```javascript
const firstName = 'Robin';
const lastName = 'Wieruch';

function getFullName() {
  const fullName = `${firstName} ${lastName}`;
}

getFullName();

console.log(fullName);
```

It's noteworthy to say that scope is the matter which prevents us from declaring a variable with the same name twice in the same context (e.g. declaring `firstName` twice in the global scope). Anyway, after all the current scope you are in (meaning: context of execution, e.g. inside a function's body when executing the function) gives you knowledge about what variables can be accessed.

### Exercises:

* Question: In the example where `getFullName()` did not return `fullName` but only assigned it to a variable and we tried to read `fullName` outside of the function, we got an error. How could this be fixed without returning the `fullName` from `getFullName()`?
  * Answer: One could declare `fullName` before the function call, this way the function call could assign `fullName` without another declaration (e.g. `fullName = ${firstName} ${lastName}`), then it would be accessible for the printing statement. However, even though this works, this should not be done in real code. Instead always return your result from the function.
* Read more about [scope in JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/Scope).
  * Read more about [scope in depth](https://javascript.info/closure).
  * Read more about [block scopes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/block).
* Read more about [this in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this) which is not strictly tied to the topics of scopes, but to the execution context as well.

### Exercises:

* Read more about [this in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this).
* Read more about [JavaScript arrow functions and their special characteristics](https://javascript.info/arrow-functions).

## Standard Built-In Objects and Methods

JavaScript as a language offers lots of built-in objects and methods. You have learned about built-in methods that are available on certain data structures like arrays before, but also have used built-in methods such as `console.log()` or built-in objects such as `Boolean` (see type conversion/coercion) or `Object` (with methods such as `Object.keys()`) which are everywhere accessible. In this section, we want to explore more of these built-in yet in the global scope accessible objects and methods.

A widely used built-in object is `Date`. If you go through all the data structures that we have learned about before, you will miss one that represents a single moment in time. As alternative, you could use a string primitive, like `const birthday = '2021-07-17'`, however, working with this variable would be tedious, because you would need to use built-in string methods to access and/or modify the day, month, or year. Hence, JavaScript offers the `Date` which enables us to work comfortable with temporal date structures:

```javascript
const birthday = new Date('2021-07-17');
```

Next we can conveniently access the date's properties by using built-in methods for this date object which wouldn't be available on a string primitive:

```javascript{2}
const birthday = new Date('2021-07-17');
const yearBirth = birthday.getFullYear();
```

If we would want to change a date's properties, say the year, we could mutate the date object directly with a built-in method:

```javascript{2}
const birthday = new Date('2021-07-17');
birthday.setFullYear(2020);
```

The `Date` object has its quirks (see exercises) which may be addressed in the future by a new built-in `Temporal` object. Until `Temporal` is usable in all modern browsers, we have to use `Date` though. In general, working with dates in programming is one of the most complex subjects, especially when it comes to timezones and having users in your application from different countries. However, this book will not go into more detail here and you will have to experience these things yourself eventually when working more thouroughly with dates in the future.

We only scratched the surface of the `Date` object here and you should definetly take some time to go through the referenced marerial in the exercises. In addition, `Date` is only one of many global objects in JavaScript. I encourage you to explore more of these built-in objects as exercise as well, expecially the JSON and Math objects should be explored.

Global objects such as `Date`, `JSON`, or `Math` are only one side of the coin. There are also global methods such as `setTimeout()` which will be our prime example for built-in methods. However, again I encourage you to explore other popular built-in methods such as `setInterval()` by yourself.

```javascript
setTimeout(() => {
  console.log('I print after 3 seconds');
}, 3000);

console.log('I print immediately');
```

The built-in `setTimeout()` method takes two arguments: a callback function which executes after a certain time and a number which represents that certain time in milliseconds. Usually the `setTimeout()` method is used to create a delay in your program. While `setTimeout()` executes the callback function only once, the `setInterval()` method is used to execute a callback function periodically.

```javascript
const interval = setInterval(() => {
  console.log('I print every 1 second');
}, 1000);

setTimeout(() => {
  console.log('I stop the interval');
  clearInterval(interval);
}, 4000);
```

Built-in objects and methods enrich JavaScript as programming languages. Apart from these, JavaScript offers a rich ecosystem of so called Web APIs. An **API** ([application programming interface](https://www.robinwieruch.de/what-is-an-api-javascript)) is nothing more than a communication channel to access features from a certain feature. This often just translates to using functions, objects, or methods on objects: For example, the Web API offers an object called `URL` which helps you to work with URLs in JavaScript.

![](images/javascript-ecosystem.png)

A programming language grows with its ecosystem. JavaScript comes with lots of built-in standards such as data types, statements (e.g. control structures) and operators. There are built-in objects and methods, as we have learned in this section, but also before when we used the `console.log()` statement or the `Object.keys()` methods to transform an object to an array of its property names. In addition to all of these built-in standards, the language offers a huge ecosystem of Web APIs which can be used for very specific purposes such as URLs or browser storage (only usable in the browser and not Node.js, hence it's also referred to as more specific **browser API**).

### Exercises:

* Question: How would you create a date which represents the current day and time?
  * Answer: We would use `new Date()` without providing any arguments.
* Question: How would you access a date's day?
  * Answer: You may think it's `birthday.getDay()` but it's `birthday.getDate()`.
* Question: Which result would you get if you would access the birthday's month by using `birthday.getMonth()`?
  * Answer: You may think it's `7` but it's `6`, because the months (in contrast to year and day) are zero indexed.
* Question: What's `typeof birthday` if `birthday` has been created with `Date`?
  * Answer: object. Essentially everything that's not a primitive (e.g. string) or function is an object in JavaScript.
* Read more about [setTimeout() and setInterval() in JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Timeouts_and_intervals).
* Read more about [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date).
  * See more examples in action about [Date](https://javascript.info/date).
* Read more about [other global objects in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects).
  * JSON is a programming languages independent format which is mainly used for data transfer (e.g. client-server communication) or configuration (e.g. setting properties of your IDE or JavaScript project). Read more about [the JSON object which helps you with this data format in JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON).
    * See more examples in action about [the JSON object](https://javascript.info/json).
  * Read more about [the Math object which helps you with mathmatical operations in JavaScript beyond arithmetic operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math).
* Read more about [JavaScript's ecosystem and how to access it via its APIs](https://developer.mozilla.org/en-US/docs/Web/API).
  * Read more about [the URL API](https://developer.mozilla.org/en-US/docs/Web/API/URL).
