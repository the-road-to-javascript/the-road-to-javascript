# JavaScript Fundamentals: Part I

JavaScript is eating the world of software engineering and web development. This is a bold statement to start a book with, however, developers across the globe feel this sentiment. The [Stack Overflow survey from 2021](https://insights.stackoverflow.com/survey/2021#most-popular-technologies-language-prof) shows that 68.62% of the respondents see JavaScript as the most popular technology in the category of programming, scripting, and markup languages followed closely (55.9%) by its related HTML/CSS markup and style sheet languages. The survey also sees *"moderate gains for TypeScript [a more powerful variant of JavaScript]"* with an absolute of 36.42% in popularity. If you want to go further down the rabbit hole in this survey, you will see mainly JavaScript frameworks and libraries among the most popular ones across all programming languages.

![](images/so.png)

GitHub ([aquired by Microsoft in 2018](https://blogs.microsoft.com/blog/2018/10/26/microsoft-completes-github-acquisition/)) is one of the most popular websites which manages developer's and company's code. GitHub as a platform for managing code doesn't need a survey to conclude the most popular programming languages, because it has all the codebases in their cloud for internal analytics. Once a year, they keep us updated about the [most popular languages](https://octoverse.github.com) and so it states that JavaScript was the most popular one from 2014 to 2020 followed by TypeScript as a rising star.

![](images/github.png)

Independent from your prior exposure to programming, you should have noticed the advances of tech around you as well. This may have been one motivational trigger for you to start learning JavaScript. However, there are many other triggers such as learning a new skill, getting your foot into a well paying industry, or being able to work remotely while sustaining your desired lifestyle. Regardless of your motivation, learning to code is hard. That's why I always keep saying to beginners: "It's a marathon and not a sprint, so make sure to enjoy the journey. The road will be bumpy, however, every bump gives you a challenge for getting closer to your goal."

### JavaScript

[JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) is a dynamic programming language and is one of the three pillars for the world wide web. Together with HTML and CSS, it's the language running in a browser which makes websites like Facebook, Twitter, and Airbnb work. Nowadays every browser has a dedicated JavaScript engine to execute the code on a user's device.

According to Wikipedia, JavaScript powers 97% the world's websites. While HTML and CSS are used to display static content like tables and images, JavaScript is the engine which makes a website interactive. It happens when you click the like button on Facebook, when you scroll down and more content is loaded on Twitter, or when you filter a list for the most popular books on Amazon. That's why modern websites are rather called web applications by developers, because they are more than just static content on a page.

![](images/three-pillars.png)

Prior the release of JavaScript, websites were only HTML (structure) and CSS (style). With only these two pillars, the world wide web was already a groundbreaking achievement, because information could be displayed online and users were able to navigate from website to website with a browser as their client. However, beyond that there was not much interactivity going on. After a website was loaded from a web server, it was just displayed in a user's browser.

When the developer community saw a lack of interactivty, there was a big desire in changing this behavior to make websites more than just static pages where a user could navigate from one page to another. Brendan Eich took this opportunity when working at Netscape and released JavaScript in 1995. The name JavaScript (short: JS) still confuses people these days, because it signals a direct relation to the programming language [Java](https://en.wikipedia.org/wiki/Java_(programming_language)). However, there is no link between them. Java happened to be quite popular back in the days and using JavaScript as a name was more of a marketing ploy when Netscape released it.

![](images/three-pillars-tasks.png)

JavaScript runs mainly on the client-side (frontend) in contrast to other server-side (backend) programming languages (e.g. PHP). I say mainly, because there are popular technologies like [Node.js](https://en.wikipedia.org/wiki/Node.js) (2009) by Ryan Dahl which brought JavaScript to the backend/server as well. Anyway, as mentioned earlier, when a user visits a website via their browser (client), all HTML, CSS, and JavaScript is loaded as files from a web server. While HTML and CSS get interpreted and displayed in the browser, JavaScript gets executed by the browser's JavaScript engine.

From its release up to the early 2010 years, JavaScript got smiled at by many veteran developers as inferior scripting language. These days, the tide has turned. What started as a scripting language in the browser which made animations and user interactions happen, has become a giant in the industry used not only by websites, but also on desktop, mobile (e.g. React Native), backend (e.g. server-side JavaScript with Node.js), internet of things, embedded systems, machine learning (e.g. Tensorflow.js), and crypto. The most popular frameworks (e.g. React.js) are used among many large players in the industry.

From my own experience as someone who is conducting workshops and consulting work, I can verify the ever increasing demand for JavaScript in every vertical industry, the high rates/salaries of freelancers/employers, and the shortage of developers in every company. So I am happy to have you on board for this journey and I hope my enthusiasm for JavaScript gets well reflected in this book.

### Frameworks and Libraries

You may have heard about libraries and frameworks when it comes to programming in general. You will get to understand these terms while reading the book, however, since I already associated the term framework with React.js, I want to give you a brief introduction here.

Once you mastered JavaScript, you will eventualyl learn more tools that build on top of JavaScript. These tools are commonly refered to as libraries and frameworks which are build (mostly) in JavaScript and used in JavaScript applications. They make you more productive as a developer and can be installed and used in your JavaScript codebase with a few clicks. For example, a library might be there to help you with conversion rates from one currency (EUR) to another currency (USD), so that you as a developer do not have to take care about the indivudual conversion rates. You just use the library to convert an amount from EUR to USD. In contrast, a framework is larger than a library, because it offers you a whole suite of tools. For example, React.js is one popular framework which helps you to architect modern web applications with JavaScript.

![](images/pyramid.png)

Anyway, the best investment for your career as a web developer would be learning JavaScript. Everything that follows, for example popular frameworks such as React.js which sit on top of JavaScript, are there to make you more productive later. However, the popularity might change in the long term: These days it's React that's popular, but no one knows what it will be in a few years. So if you learn the JavaScript fundamentals properly, you can always take your knowledge with you to the next popular JavaScript framework.

### ECMAScript

[ECMAScript](https://en.wikipedia.org/wiki/ECMAScript) (short: ES) is the underlying specification of JavaScript. While JavaScript is its most popular implementation, there are others like JScript (programming language), V8 (JS engine), SpiderMonkey (JS engine) implementing the ES standard. Anyway, what's most important for you as aspiring JavaScript developer are the changes that are coming every year to it.

![](images/ecmascript.png)

These changes started with ES1 (1997), ES2 (1998), ES3 (1999), had a huge pause for 10 years with the abandoned ES4, and continued with ES5 (2009) and ES5.1 (2011). These days, you will often hear the term **ES6** or **ES2015** when people speak about **modern JavaScript**. After ES6, the community agreed on yearly updates (hence the new naming convention based on the year) which will not be as impactful as ES6 though, because it was a major milestone and the biggest update to the language. In this book, you will learn modern JavaScript with ES6 and beyond without forgetting about the noteworthy parts from older ECMAScript versions.

### TypeScript

Throughout this introduction, you may have noticed me not only mentioning JavaScipt but also TypeScript -- which seems to gain more traction when looking at the data. For people being new to programming: [Typescript](https://www.typescriptlang.org) is a superset of JavaScript developed by Microsoft. So if it's a superset and gains more popularity, why not learn TypeScript instead? Keeping it short: Essentially TypeScript inherits everything from JavaScript, but it's a strictly typed language whereas JavaScript is a loosely dynamic language. The latter makes learning programming often easier for beginners. However, based on your prior exposure to coding, here are two learning tracks you could take:

* No prior coding experience: For getting started, learn JavaScript first. After you feel comfortable with JavaScript, you *could* dip your toes into TypeScript a couple of months later. However, that's not a requirement. I have seen most people stick to JavaScript for a while (read: years) before taking the leap to TypeScript. So after this introduction, do not worry about TypeScript anymore and just focus on JavaScript. If you get through this book, it's already a tremendous achievement!

* Prior coding experience in other programming languages: If you are familiar with anohter programming language, you may feel more comfortable in a strongly typed language like TypeScript. I want to give you three options here depending on your programming skill level: (1: Beginner) Learn only JavaScript with this book. (2: Intermediate) Learn JavaScript with this book and try TypeScript afterward. Then use what feels more comfortable to you for getting the leap from beginner to advanced JavaScript/TypeScript developer. (3: Advanced) Migrate the code from this book right away to TypeScript while reading it.

### Exercises:

* Read more about [the evolution from website to web applications](https://www.robinwieruch.de/web-applications).
* Read more about [the history of JavaScript](https://en.wikipedia.org/wiki/JavaScript).
* Read more about [Brendan Eich and what he is up to these days](https://en.wikipedia.org/wiki/Brendan_Eich).
* Read more about [ECMAScript (ES)](https://en.wikipedia.org/wiki/ECMAScript) and how it evolves JavaScript with its [proposals from stage 0 to 3](https://github.com/tc39/proposals) by the TC39.

## Hello JavaScript

*If you have any trouble with the following setup, you can also watch this video as introduction. TODO*

Developers spend most of their time in a software where they can write code. This software is usually called **editor** or **IDE** (integrated development environment). I will use both terms interchangeably throughout this book. To get you started, we will install and use the most popular one called Visual Studio Code (VSCode). So as first step in your career as a JavaScript developer, head over to [VSCode's website](https://code.visualstudio.com), download it, and install it. Afterward start it as your favorite new place where you will spend most your time as a developer.

Usually JavaScript runs in the browser and thus you should not need to install anything else to execute it. And that's what we will do once we put JavaScript together with HTML and CSS later in this book. However, to kick things off, we will take a different approach by learning *only* JavaScript *without* HTML/CSS *outside* of the browser: entering Node.js -- the JS runtime for the backend.

Starting things off with Node.js does not mean that you will learn server-side JavaScript, that you will become a backend developer, or that you will not run JavaScript in the browser eventually. It just means that we will establish a learning environment where you can learn *only* JavaScript without any displayed (also called **rendered**) HTML/CSS in the browser. Instead, you will write code, execute it with a command, and see its plain output. Later in this book though, we will switch over to the common client-side JavaScript which is executed in the browser with HTML and CSS.

As second step in your career as a JavaScript developer, you need to install Node.js to execute only JavaScript from within VSCode. Head over to [Node's website](https://nodejs.org/en), download the latest recommended release, and install it. After it has been installed, open VSCode and enable the **intergated terminal** (also called terminal, command line, or command line interface (CLI) -- which I will use interchangeably throughout this book). On the command line, type the following command which should output your current Node version if you have installed it correctly:

{title="Command Line",lang="text"}
~~~~~~~
node --version
~~~~~~~

What's missing is a physical place on your machine for your first JavaScript project. Open up your Finder (MacOS), File Explorer (Windows), or your equivalent on Linux and create a folder (e.g. folder with the name "LearnJavaScript") for your first project somewhere (e.g. folder with the name "Projects") where you want to keep all your future JavaScript projects. After creating this folder, open VSCode and open the folder of your new project with it. There create a new file with the name *index.js* and fill it with the following content:

{title="index.js",lang="javascript"}
~~~~~~~
console.log('Hello JavaScript');
~~~~~~~

With VSCode and Node, you are good to go to execute your first JavaScript. Open the integrated terminal (most often I will call it command line in the future) in VSCode and type:

{title="Command Line",lang="text"}
~~~~~~~
node index.js
~~~~~~~

Node should run your server-side JavaScript file and should output "Hello JavaScript" on the command line. In the future, whenever you change code in your JavaScript file, run the node command again. Congratulations, you have executed your first code in JavaScript.

### Exercises:

* Learn to use [VSCode](https://code.visualstudio.com/learn), apply a [custom theme](https://code.visualstudio.com/docs/getstarted/themes) for a more personal touch, and make VSCode to your second home!

## Values and Variables

Imagine you are about to move from one city to another city and you have to pack all your stuff. You gather a bunch of boxes for all your belongings and label them with their content. This way, when you unpack these boxes later, you know what's in there without opening them. Values and variables in programming are similar to this analogy. While values are all your belongings in these boxes, the variables are the labels which mark the boxes.

Values and variables are the most fundamental building blocks in JavaScript (and other programming languages). A value is a representation of data (any piece of information). For example, the previously used "Hello JavaScript" is a value. Since we have put it into a `console.log()` statement, it's printed for us. The same would happen for printing my name as value. Change the code accordingly and run it again with `node index.js` on the command line.

{title="index.js",lang="javascript"}
~~~~~~~
console.log('Robin Wieruch');
~~~~~~~

A value can have different represenations called **data types**; which we will learn about more in depth later. For example, in the following the value changes from a **string** data type to a **number** data type:

{title="index.js",lang="javascript"}
~~~~~~~
console.log(1988);
~~~~~~~

Essentially a value regardless of the data type is the unit of information that we have in JavaScript. In contrast, a variable is used to store a value. The following shows how to create a variable with a value and how to reuse it by printing it multiple times. This way, we do not need to write the value over and over again, but use its variable as a reference. If the value changes, we have to change it only at one place and not multiple places:

{title="index.js",lang="javascript"}
~~~~~~~
let firstName = 'Robin';

console.log(firstName);
console.log(firstName);
~~~~~~~

Behind the scenes, the machine running the code allocates memory for this variable, because it needs to be able to retrieve its stored value every time we use it. Then it replaces the variable with the actual value. Now you can change the value of the variable at one place and it will be reflected at all the places where it is used. Try it yourself, by changing the `firstName` to your own name. Then run the `node index.js` command again.

What's noteworthy: The previous paragraph mentioned memory allocation when variables get created in JavaScript. This happens for other programming languages as well. However, since JavaScript is a so called **high level programming language**, we do not need to take care of the memory allocation. In other programming languages such as C++, which is a **low level programming language**, a developer has to take care of these things.

![](images/variable-value.png)

In JavaScript, variables are usually created in [camelCase](https://en.wikipedia.org/wiki/Camel_case). So it's not `first_name` (snake_case) or `first-name` (kebab-case), but `firstName` as we have used it in the example above. Other naming conventions that are allowed for specific cases are `FIRST_NAME` (UPPER_CASE or SCREAMING_SNAKE_CASE) or `FirstName` (PascalCase).

{title="index.js",lang="javascript"}
~~~~~~~
let yearBirth = 1988;

console.log(yearBirth);
~~~~~~~

In conclusion, variables are there to reference values in your code. Meaning: You declare a variable with a value once and then reuse it as reference later when you need to do something with it (e.g. printing it with `console.log()`). This makes values reusable and helps developers to change values only once and not everywhere in the codebase. In addition, there are naming conventions for programming languages which should be followed to make the code more readable to other developers. You should get an overvier about these conventions by going through the exercises.

### Exercises:

* Read more about [the different naming conventions in JavaScript](https://www.robinwieruch.de/javascript-naming-conventions) and find out what it means to have **descriptive** variable names.
* Declare variables yourself. For example, declare variables for your last name and your age and print them on the command line. In the following, I will not always use the `console.log()` statement for the examples, but you should continue using it for the sake of undertstanding and learning.

## Code Quality

Structuring your code in a readable and natural way is important, because you can pick it up later more easily when reading through code that's more than a day old, but also other developers have an easier time to understand what you want to accomplish with your program. Eventually you will end up working in a team of developers where it's one of the most important virtues to write quality code.

### Code Structure

As someone new to programming, it's not intuitive from the beginning how to structure code in a readable flow. We will learn later about a tool which helps us with structuring our code (also called **code formatting**), however, for the early sections of this book you have to sturcture the code yourself to get comfortable with it. Now take for example the following code snippet:

{title="index.js",lang="javascript"}
~~~~~~~
let yearBirth
=
1988;

console.log(
  yearBirth);
~~~~~~~

It's valid JavaScript and it executes when you run the node command to start the program. However, it's not readable and writing readable code is one of the most important things when working in a team of developers. Fortunatelly, most code in JavaScript ends naturally with a semicolon. This semicolon can be used as assistance to arrange the lines of code in a readable format:

{title="index.js",lang="javascript"}
~~~~~~~
let yearBirth = 1988;

console.log(yearBirth);
~~~~~~~

If you leave a blank line in between is often a matter of taste. This doesn't mean that there should be a blank line between every line of code though. Usually you want to form **logical blocks of code** like one block for variables and one block for printing statements:

{title="index.js",lang="javascript"}
~~~~~~~
let firstName = 'Robin';
let yearBirth = 1988;

console.log(firstName);
console.log(yearBirth);
~~~~~~~

JavaScript is *most of the time* able to execute code without semicolons, however, it's not always the case. Thus, whenever you can use semicolons as a best practice to end statements. The majority of the JavaScript community stands behind this rule.

### Comments

Comments are used in every programming language. They are pieces of text in your code which will not be executed and are only there for documentation purposes. Hence comments can be used for a variety of use cases. A single line comment can be performed with a leading double slash:

{title="index.js",lang="javascript"}
~~~~~~~
// I am a comment

// I am another comment
~~~~~~~

It can be used to comment code (for example, if something broke it's always useful to exclude some lines of code with a comment to find the error) or to annotate a line of code with a text above or next to it:

{title="index.js",lang="javascript"}
~~~~~~~
// console.log('Robin Wieruch');

// I am printing something
console.log('Robin Wieruch');

console.log('Robin Wieruch'); // I am printing something
~~~~~~~

You can also use multiline comments with a block comment with a slash and asterisk:

{title="index.js",lang="javascript"}
~~~~~~~
/*
  everything in this block will be commented

  console.log('Robin Wieruch');
*/
~~~~~~~

Anyway, I will use comments throughout this book to annotate code for you. However, while reading this book and coding alogn, you should use comments for learning purposes (e.g. adding explanations, showing alternatives from the book, linking to external URLs as explanations). Once you are working with other developers on an application, you will most likely see comments when things are not sufficently self-descriptive (e.g. variable names) and need further explanation.

### Debugging

Developers are problem solvers. This does not only apply *"Implement an application which solves the following use case."*, but also to *"Why does this line of code not work?"*. The latter will be your bread and butter as a developer, will come across your way on a daily basis, and is called **debugging**.

Debugging is mostly followed by noticing a **bug** in your code. A bug is not literally a bug, however, it was named after one in 1947 when a team of computer scientist at the Harvard University reported [the world's first bug in a computer program](https://www.nationalgeographic.org/thisday/sep9/worlds-first-computer-bug/). These days, every time a bug happens in your code, there is some kind of unexpected or unintended behvaior. Frequently this will also lead to your entire program failing.

Regarding the previous section, you will notice that not all variable names are allowed: For example, the word `new` and `class` are reserved, starting a variable name with a number will lead to an error, and most other symbols (except for the dollar sign and the underscore) cannot be used for a variable declaration:

{title="index.js",lang="javascript"}
~~~~~~~
let new = 'Robin';
~~~~~~~

Try it yourself, by giving your variable a name that isn't allowed. For example, using `new` would lead to the following error in VSCode:

{title="Command Line",lang="text"}
~~~~~~~
'new' is not allowed as a variable declaration name.
~~~~~~~

If you try to run the code with the node command, you will see the following syntax error:

{title="Command Line",lang="text"}
~~~~~~~
/Users/me/the-road-to-javascript/index.js:1
let new = 'Robin';
      ^^^

SyntaxError: Unexpected token 'new'
~~~~~~~

Errors in JavaScript describe what's wrong (here: syntax) and where to find the errornous code (here: line 1). Start early to read your errors carefully, because tracking down errors (debugging) in code will become your daily duty as a developer. If you get stuck on a bug, invest the time to solve it yourself, because perseverance is what makes you a great developer.

### Exercises:

* Read more about [Code Structure in JavaScript](https://javascript.info/structure).
  * See more examples in action about [Code Style](https://javascript.info/coding-style).
* Read more about [allowed identifiers for variables in JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/Identifier).
* Try single line and block comments yourself and use them while reading this book to annotate your code.
  * Use hotkeys: Select some code and press the hotkey `Ctrl+/` for a single line comment and `Ctrl+Shift+/` for a block comment. On MacOS use `Cmd` instead of `Ctrl` and `Option` instead of `Shift`.
* Read more about [what style of JavaScript to avoid](https://javascript.info/ninja-code).
* Read more about [troubleshooting JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_went_wrong).
  * Get familiar with JavaScript error messages, so try to use a reserved variable name like `class` or a not allowed variable name like `1988`. Also try to `console.log()` a variable that's not declared. Read the error messages carefully and get familiar with them. Do not see errors (bugs) as an enemy, but as an opportunity to become a better developer.

## Data Types: Primitives

Every programming language comes with data types which help developers to represent different kinds of information. You have learned about two of them already: string and number. While a **string** represents a sequence of characters (essentialy text) in quotes (single or double -- choose and stick to one of them), a **number** represents fixed point (also called integer or int) or floating point (also called decimal or float) digits which can be positive or negative:

{title="index.js",lang="javascript"}
~~~~~~~
// string
let firstName = 'Robin';
let lastName = 'Wieruch';
let mobilePhone = '+49 173 777 666';

// number (here: fixed point)
let countryCodePhone = 49;
let phone = 173777666; // not my real number :-P

// number (here: floating point)
let height = 1.80;

// yes, it's height in meters ;-)
~~~~~~~

In contrast, the **boolean** is the logical data type which can have the representations `true` or `false`. Based on a boolean, JavaScript code can make decisions (e.g. if-else statement which we will get to know later) when it evaluates these values:

{title="index.js",lang="javascript"}
~~~~~~~
// boolean
let isDeveloper = true;
let isLawyer = false;
~~~~~~~

Two other widely used data types are called **undefined** and **null**. Essentially both are empty values, but they can be distinguished with this metaphor: *"I always had the plan to have two children when I was young. Now, after I got my first kid with the name Liam, I still have the plan to have a second kid one day. But it's not defined yet (and therefore `undefined`). However, I am not planning to have a third child, so I keep it intentionally empty."*:

{title="index.js",lang="javascript"}
~~~~~~~
let firstKidName = 'Liam';
let secondKidName = undefined;
let thirdKidName = null;
~~~~~~~

It's worth to know that the value `undefined` does not need to be defined as value. Instead, one can just not initialize the variable. Try to output the following variable with a printing statement:

{title="index.js",lang="javascript"}
~~~~~~~
let secondKidName;
~~~~~~~

When using `null`, it signals a more deliberate choice of an empty value. For example, I do not have a middle name, so I leave it empty by choice, not because it's not defined yet and may be defined in the future:

{title="index.js",lang="javascript"}
~~~~~~~
let middleName = null;
~~~~~~~

Newer and less used data types are [Symbol (ES2015)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol) and [BigInt (ES2020)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt) which I will not cover in this book, because they are not very much adopted yet. As a JavaScript beginner and even as advanced JavaScript developer, for a while you will not cross these data types.

![](images/data-types.png)

Altogether, there are 7 data types categorized as **primitives** in JavaScript: String, Number, Boolean, Undefined, Null, Symbol, and BigInt -- whereas you will most likely not often (or never) see Symbol and BigInt. Apart from primitives, there is also the is the category of **structural data types** (e.g. Object) which we will learn more about later.

### Exercises:

* Create a whole set of variables `firstName`, `middleName`, `lastName`, `country`, `street`, `age`, `isDeveloper`, `phone`, `countryCodePhone`, `hasKids`, `isMarried`, `countSiblings`, `countPets`, and `height` and assign your personal attributes as values to them.
* Question: What happens if you try to create a string variable with an opening double quote and an ending single quote?
  * Answer: You get an syntax error, because JavaScript is looking for the respective double quote which ends the string. But there is only a single quote which does not make sense.
* Question: Is it possible to create a string variable which represents a number?
  * Answer: Yes. For example `let someNumber = '42';`. But the underlying data type, as you will learn later, is of type string and not number.
* Question: When would it be reasonable to mix double and single quotes for string variables?
  * Answer: If the quote is part of the text like in `let text = 'He said that "I am a good developer"';`.
* Read more about [JavaScript's primitive data types](https://developer.mozilla.org/en-US/docs/Glossary/Primitive).
  * Read more about [JavaScript's string primitive](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String).
  * Read more about [JavaScript's number primitive](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number).
  * Read more about [JavaScript's boolean primitive](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean).
  * Read more about [JavaScript's undefined primitive](https://developer.mozilla.org/en-US/docs/Glossary/undefined).
  * Read more about [JavaScript's null primitive](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null).
* See more examples in action about [data types in JavaScript](https://javascript.info/types).

## Variable Declaration and Initialization

When storing a value into a variable, there are a few things to note. First of all, we have seen how to **create** (also called **define**) a variable in JavaScript. In technical terms, a so called *variable declaration* automatically happens when we *initialize* a new variable with a value:

{title="index.js",lang="javascript"}
~~~~~~~
// variable declaration and initialization
let firstName = 'Robin';

console.log(firstName);
// 'Robin'
~~~~~~~

What's interesting about this, is that this is also called a variable initialization, because a value is assigned to the variable. Essentially the variable initializes. So declaring and initializing a variable can happen in one line of code. In contrast, if no value is assigned, it's only a **variable declaration**:

{title="index.js",lang="javascript"}
~~~~~~~
// variable declaration
let firstName;

console.log(firstName);
// undefined
~~~~~~~

If a value gets assigned, it's **called variable initialization** (also called **variable assignment** as we will learn next):

{title="index.js",lang="javascript"}
~~~~~~~
// variable declaration
let firstName;

// variable initialization
firstName = 'Robin';

console.log(firstName);
// 'Robin'
~~~~~~~

This leads me to the next topic of assigning and re-assigning a value to a variable. The last code snippet has shown you how to **assign a variable** when there hasn't been a value defined before. The variable has been declared but not initialized. However, when the variable already has a value, **re-assigning a variable** to a new value is possible too:

{title="index.js",lang="javascript"}
~~~~~~~
// variable assignment
let age = 30;

// variable re-assignment
age = 31;

console.log(age);
// 31
~~~~~~~

A re-assignment can also happen based on another variable or the same variable (e.g. like `age` in the following example). In the following example, we are using the arithmetic `+` operator:

{title="index.js",lang="javascript"}
~~~~~~~
let age = 30;
age = age + 1;

console.log(age);
// 31
~~~~~~~

It's also possible to declare/initialize a new variable based on other variables (e.g. `age`) or values (e.g. `1`). While the old variable and its value stay intact, the new variable's value gets created:

{title="index.js",lang="javascript"}
~~~~~~~
let age = 30;
let newAge = age + 1;

console.log(age);
// 30
console.log(newAge);
// 31
~~~~~~~

JavaScript is a so called loosely typed and dynamic language. It's a **loosely typed language**, because a developer does not need to tell the data type explicity (like in strongly typed languages such as TypeScript) for a variable:

{title="index.js",lang="javascript"}
~~~~~~~
// variable declaration and initialization in TypeScript
let age: number = 30;
~~~~~~~

It's also a **dynamic language**, because it offers dynamic typing which allows a developer to assign and re-assign a variable to different data types:

{title="index.js",lang="javascript"}
~~~~~~~
let age = 30; // from number

age = '30 years'; // to string
~~~~~~~

Over the long run, JavaScript's properties of being a loosely typed, dynamic, and high level programming language running in the browser helped the language evolve to the giant in our industry with a high adoption rate by people being new to programming.

This section has taught you about different terms when creating and changing variables in JavaScript. It's okay if you don't know all of these terms from the top of your head, however, the book tries to establish a baseline for a vocabulary, so that you always can refer back to certain sections if terms are unclear to you.

### Exercises:

* Read more about [variables in JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Variables).
* Questions: What happens if you `console.log()` a variable that's declared and initialized.
  * Answer: You get the variable's value printed.
* Questions: What happens if you `console.log()` a variable that's declared but not initialized.
  * Answer: You will get `undefined` printed on the console.
* Questions: What happens if you `console.log()` a variable that's not declared.
  * Answer: You will get an error.
* Question: What's the advantage of defining ones age in a computer program with `yearBirth` instead of `age`?
  * Answer: If the computer program gets older, the `age` in the program would have to change whereas the `yearBirth` could stay the same. Thus, when using `yearBirth`, with every passing year the program would still be without bugs.
* From the previous section's exercises, where you came up with variables about yourself, change the `age` variable to `yearBirth`.

## let, const, and var

When you learned about variables and values, you have used both on the left and right of the equation. What I never explained until yet was the keyword `let`, which is used to declare a variable for the first time. Afterward, it isn't needed anymore for (re-)assignments:

{title="index.js",lang="javascript"}
~~~~~~~
let age = 30;

age = 31;
~~~~~~~

There are two other keywords to define variables in JavaScript: `const` and `var`. While `let` and `const` were introduced in modern JavaScript (ES6), `var` has been in JavaScript from the very beginning:

![](images/var-let-const.png)

In modern JavaScript, `var` isn't used anymore because it has issues with **hoisting** and **scoping** (terms which the book will address later). The other keywords `let` and `const` address these issues in modern JavaScript and are therefore mainly used these days throughout every JavaScript project. This makes it easier for us, because we are left with only two options `let` and `const`.

Essentially `const` works the same way as `let`, the keyword `const` is just used whenever the value of a variable is not allowed to change. For example, when I get older every year, my age increments by one:

{title="index.js",lang="javascript"}
~~~~~~~
let age = 30;

// after one year has passed
age = 30 + 1;
~~~~~~~

In contrast, once you are born you cannot change your year of birth. If one tries to change the `yearBirth` variable which is declared with `const`, we would see the following error:

{title="index.js",lang="javascript"}
~~~~~~~
const yearBirth = 1988;

yearBirth = 1990;

// yearBirth = 1990;
//           ^

// TypeError: Assignment to constant variable.
~~~~~~~

The big question in the room: When to use `let` and when to use `const`? Essentially `let` is used when a variable changes throughout the codebase and `const` is used when a variable will not change. If you want to take the simple road, you could use `let` everywhere, because then you can have both: variables that change and variables that do not change. However, as a best practice, use `const` whenever a variable should not change. In programming, having variables that do not change is an advantage, because less bugs get introduced this way. Once variables start to change, we loose some stability and predictability in our code and its easier to run into problems. We will get more into this topic later in the book.

### Exercises:

* Read more about [variables in JavaScript](https://javascript.info/variables).
* From the previous section's exercises, where you came up with variables about yourself, change all the variable declarations from `let` to `const` where you think that they should be treated as constants.
* Questions: What happens if you try to declare an undefined (declare but do not initialize) variable with the keyword `const`.
  * Answer: This should lead to an syntax error: `Missing initializer in const declaration`.
* Question: What happens if you try to declare a variable without let, const, or var.
  * Answer: This is possible, but should be avoided. The book will later explain why this is the case.
* Question: What happens if you try to declare a variable with var instead of let/const and you try to change it?
  * Answer: It's possible to change the variable the same way as it is possible with `let`.

## Arithmetic Operators

So far, we have only defined variables with their values. In real JavaScript code, you will do something with these values eventually, otherweise there would be no need to assign them to variables in the first place. In this section, we will talk through your first kind of operators in JavaScript. The book touches *only several* operators in this section and throughout the rest of the book, because there are too many operators to cover all of them. But be assured that we will cover the most popular ones.

You have already learned about one operator before: the `+` operator. It's one of several **arithmetic operators**. Another one is the `-` operator. While the `+` operator is used for addition, the `-`, `*`, and `/` operators are used for subtraction, multiplication, and division:

{title="index.js",lang="javascript"}
~~~~~~~
const yearBirth = 1988;
const yearGraduation = 2014;
const today = 2021;

console.log('age:', today - yearBirth);
// age: 33

console.log('age at graduation:', yearGraduation - yearBirth);
// 'age at graduation: 26'

console.log('years as developer:', today - yearGraduation);
// 'years as developer: 7'

/*
  Note how we used values as
  comma separated values
  in the console.log statements
  which is useful for printing
  multiple values in one line
*/
~~~~~~~

Let's advance the previous example by **extracting values as variables**:

{title="index.js",lang="javascript"}
~~~~~~~
const yearBirth = 1988;
const yearGraduation = 2014;
const today = 2021;

const age = today - yearBirth;
console.log({ age });
// { age: 33 }

const ageGraduation = yearGraduation - yearBirth;
console.log({ ageGraduation });
// { ageGraduation: 26 }

const yearsAsDeveloper = today - yearGraduation;
console.log({ yearsAsDeveloper });
// { yearsAsDeveloper: 7 }

/*
  Note how we used variables
  with curly braces
  in the console.log statements
  which is useful for printing
  values with their variable name
*/
~~~~~~~

Extraction of variables is a best practice, because it allows you to define descriptive names for values (e.g. `age`). Another benefit is reusing these variables for successive operations which you will often perform in more elaborate programs:

{title="index.js",lang="javascript"}
~~~~~~~
const yearBirth = 1988;
const yearGraduation = 2014;
const today = 2021;

const age = today - yearBirth;
const ageGraduation = yearGraduation - yearBirth;

const yearsAsDeveloper = age - ageGraduation;
console.log({ yearsAsDeveloper });
// { yearsAsDeveloper: 7 }
~~~~~~~

Note how we used `const` instead of `let` here, because none of the variables got changed. Instead, we created new variables based on already defined variables. Keep this in mind as a best practice, because we want to use `const` whenever possible. There is one more fact to know about the last example:

{title="index.js",lang="javascript"}
~~~~~~~
const yearBirth = 1988;
const yearGraduation = 2014;
const today = 2021;

const age = today - yearBirth;
const ageGraduation = yearGraduation - yearBirth;
~~~~~~~

We have learned about one operator (`-`) in this code snippet, but actually there are two: The `=` operator sits in the category of **assignment operators**. One might wonder: What's stopping JavaScript from evaluating the `=` operator before the other `-` operators? This concept is called **operator precedence** where JavaScript executes operators in a particular order (e.g, the `-` operator gets executed before the `=` operator).

This was only the introduction to operators with the example of arithmetic operators. We will cover more operators, such as relational and equality, but also logical operators, throughout this book.

### Exercises:

* From the previous section's exercises, where you came up with variables about yourself, calculate your age based on today's year and your `yearBirth`.
* Question: In one of the previous examples, we calculated `yearsAsDeveloper` based on `yearGraduation` and `yearBirth`. What's a simpler way to calculate `yearsAsDeveloper` from the variables in this examples?
  * Answer: The simpler and more straightforward way would be `const ageGraduation = today - yearGraduation;`.
* Read more about [operators in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators).
  * Use all artihmetic operators including the `%` and the `**` operators.
  * Use the increment and decrement operators.
    * Use and understand the `++` operator, because you will use this later.
  * Dip your toe into some relational and equality operators.
  * See more examples in action about [arithmetic operators in JavaScript](https://javascript.info/operators).
* Read more about [operator precedence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence).
  * Look into the table and veryify the `=` and `-` operator's precedence.
  * Question: What's the result of 2 * (4 + 3) and how to you explain it with the concept of operator precedence?
    * Answer: The parentheses change the execution order of the `*` and `+` operators. The result is 14.

## String Operations

While you have learned about operators which have been mostly used for number primitives, there are also string operations that you can perform on string primitives. For example, sometimes you want to create a new string based on two string values which is called **string concatenation**. The + operator helps you here to concatenate strings:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const lastName = 'Wieruch';

console.log('My name is' + firstName + lastName);
~~~~~~~

This will print "My name isRobinWieruch" though, so when concatenating a string with the + operator, always think about the spaces between variables and/or values. In this case, we can put an empty string between the variables/values and also add the punctation at the end of the sentence:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const lastName = 'Wieruch';

# leanpub-start-insert
console.log('My name is ' + firstName + ' ' + lastName + '.');
# leanpub-end-insert
~~~~~~~

Using the + operator is not used as much anymore in modern JavaScript since it got **template literals**. When using template literals, you have to use backticks instead of single or double quotes which distinguishes it from its legacy version:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const lastName = 'Wieruch';

# leanpub-start-insert
console.log(`My name is ${firstName} ${lastName}.`);
# leanpub-end-insert
~~~~~~~

In this particular case, you have used template literals for **string interpolation**. However, template literals can also be used for **multi-line strings**:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const lastName = 'Wieruch';

# leanpub-start-insert
const introduceYourself = `
  Hello,

  my name is ${firstName} ${lastName}.
`;
# leanpub-end-insert

# leanpub-start-insert
console.log(introduceYourself);
# leanpub-end-insert
~~~~~~~

Since backticks are superior to single/double quotes, there are developers who are using these as default for all strings:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = `Robin`;
const lastName = `Wieruch`;
~~~~~~~

However, this is more a matter of taste at this point in time and many developers still prefer to use only backticks (template literals) when they are needed (e.g. string interpolation, multi-line strings). Backticks are often still there to signal that there is something more going on than just having a string.

### Exercises:

* Read more about [template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals).
  * Find out how to use [long literal strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) which are different from multi-line strings.
* Read more about [strings in JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Strings).
* Extend the `introduceYourself` variable by interpolating it with an `age` (number) variable. Use more of the variables that describe yourself and interpolate them into the text.
* From the variables that describe yourself, interpolate `countryCodePhone` and `phone` into a new `phoneWithCountryCode` variable.

## Type Conversion and Coercion

Type conversion and type coercion is the concept of explicity (manually) and impliclty (automatically) changing a value's data type from one type to another (e.g. string to number, number to string, string to boolean). Any type, whether it's a primitive data type or structural data type can be changed, however, we will focus on the primitives here, because we didn't touch the strucutral data types (e.g. object) yet.

We will start with the implicit/automatic **type coercion** first. Often type coercion happens when using different data types in combination with operators. If you have followed the exercise from the last section, you may have noticed something odd. Let's recap the exercise where I asked you to extend the introduction with your age:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const lastName = 'Wieruch';
# leanpub-start-insert
const age = 30;
# leanpub-end-insert

const introduceYourself = `
  Hello,

  my name is ${firstName} ${lastName}
# leanpub-start-insert
  and I am ${age} years old.
# leanpub-end-insert
`;

console.log(introduceYourself);
~~~~~~~

What you are experiencing here is called type coercion which happens every time when JavaScript changes data types behind the scenes. In this case, the `age` variable with the data type number is coerced to a string data type to be used in the template literal. Hence we are able to print a sentence even though we have interpolated it with a number data type. Before you continue reading, ask yourself what's printed when executing the following code snippet:

{title="index.js",lang="javascript"}
~~~~~~~
const yearBirth = '1991';
const age = 30;
const yearToday = yearBirth + age;

console.log(yearToday);
~~~~~~~

Against ones expecations this prints "199130" and not 2021. Whenever a string is involved, the arithmetic `+` operator becomes a string operation like we have learned before. Thus every number just gets concatenated. Changing all variables to number data types fixes this issue:

{title="index.js",lang="javascript"}
~~~~~~~
# leanpub-start-insert
const yearBirth = 1991;
# leanpub-end-insert
const age = 30;
const yearToday = yearBirth + age;

console.log(yearToday);
# leanpub-start-insert
// 2021
# leanpub-end-insert
~~~~~~~

JavaScript automatically adjusts data types for us under the hood, which is not always the desired behavior, however, once we get used to it, it saves us lots of extra work which we would normally have to perform with manual/explicit **type conversions**. The following example shows this redundancy:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const lastName = 'Wieruch';
const age = 30;

const introduceYourself = `
  Hello,

  my name is ${firstName} ${lastName}
# leanpub-start-insert
  and I am ${String(age)} years old.
# leanpub-end-insert
`;

console.log(introduceYourself);
~~~~~~~

In contrast, manual type conversion is sometimes needed as we have seen in one of the code snippets from before. It's not always the case that we have the best suited data types at our hands, so we need to adjust them sometimes manually:

{title="index.js",lang="javascript"}
~~~~~~~
const yearBirth = '1991';
const age = 30;
# leanpub-start-insert
const yearToday = Number(yearBirth) + age;
# leanpub-end-insert

console.log(yearToday);
// 2021
~~~~~~~

Considering the primitives string, number, and boolean, we can use their counterparts `String()`, `Number()`, and `Boolean()` to manually transform them from one data type to another:

{title="index.js",lang="javascript"}
~~~~~~~
let yearBirth = '1991';
yearBirth = Number(yearBirth);
yearBirth = String(yearBirth);
~~~~~~~

Previously you have also learned about operators in JavaScript. Occasionally the **unary operator** `typeof` helps us to retrieve the data type of a variable:

{title="index.js",lang="javascript"}
~~~~~~~
let yearBirth = '1991';
# leanpub-start-insert
console.log(typeof yearBirth);
# leanpub-end-insert

yearBirth = Number(yearBirth);
# leanpub-start-insert
console.log(typeof yearBirth);
# leanpub-end-insert

yearBirth = String(yearBirth);
# leanpub-start-insert
console.log(typeof yearBirth);
# leanpub-end-insert
~~~~~~~

Coercion and conversion from string to number and vice versa is most of the time straightforward and makes intuitively sense. Boolean conversion from boolean to number/string can be explained too. While a string conversion prints "true"/"false" (strings) instead of true/false (booleans), a number conversion prints 1/0 (numbers):

{title="index.js",lang="javascript"}
~~~~~~~
console.log(String(true), String(false));
// 'true' 'false'
console.log(Number(true), Number(false));
// 1 0
~~~~~~~

The other way around, boolean conversions from number/string to boolean are a bit more complicated. Most of the time when converting a string/number to a boolean you will get `true` as result:

{title="index.js",lang="javascript"}
~~~~~~~
console.log(Boolean('Robin'));
// true
console.log(Boolean(30));
// true
~~~~~~~

Essentially this conversion always results in true when the string or number values are defined. If they are not defined, null, or have some other for JavaScript interpreted falsy value (e.g. number `0` or empty string `''`), the conversion will result in false:

{title="index.js",lang="javascript"}
~~~~~~~
console.log(Boolean(undefined)); // false
console.log(Boolean(null)); // false
console.log(Boolean(0)); // false
console.log(Boolean('')); // false
~~~~~~~

This knowledge will later help us to make decisions in JavaScript not only based on booleans, but also implictly on empty strings or `undefined`/`null`. Anyway, while type coercion helps us as a developer not to take care of the conversions manually all the time, type conversion gives us the tools whenever we have to perform it ourselves.

### Exercises:

* Read more about [type coercion in JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/Type_coercion).
* Read more about [type conversion in JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/Type_Conversion).
  * See more examples in action about [type conversion](https://javascript.info/type-conversions).
* Read more about [unary operators in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators#unary_operators).
* Question: What's the result of `0 / 0` in JavaScript?
  * Answer: NaN - Not a number.
* Question: What's `typof NaN`?
  * Answer: number. It's not a valid number, but it's still of type number.
* From the variables that describe yourself, convert `countSiblings` and `countPets` into their respective `hasSiblings` and `hasPets` variables by using `Boolean()`.

## If-Else Statement

Imagine an elevator which just dropped a person at the 7th floor. One person at the 1st floor is already waiting for the elevator and pushed the button a while ago. Another person just arrived at the elevator at the 8th floor and pushes the button. Where should the elevator go next? Should it go to the person who was the first (fairness) or should it go to the person who is the nearest (efficience)? These kinds of decisions need to be made in computer programs.

![](images/if-else.png)

Code is not just a straight road of statements, but a road with junctions to the left and to the right. A computer program has to make decisions eventually. Based on booleans, it can make these decisions with **if-else statements**:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const isDeveloper = true;

if (isDeveloper) {
  console.log(`${firstName} is a developer.`);
} else {
  console.log(`${firstName} may be still a student.`);
}
~~~~~~~

Having a boolean at your hand makes this decision making the most straightforward: If the boolean in the parentheses (called **condition**) evaluates to `true`, then go into the first (here: `if`) block of curly braces. If the boolean evaluates to `false`, go into the second (here: `else`) block and execute its code. The `else` block is optional though. Hence it's also common to have only the `if` block which only executes if the boolean evaluates to `true`:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const isDeveloper = true;

if (isDeveloper) {
  console.log(`${firstName} is a developer.`);
}
~~~~~~~

If this statement only executes one line in its block, then it can be expressed in a shorter version without curly braces too. Note however that it's recommended to use the curly bracktes for having the blocks more explicit:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const isDeveloper = true;

# leanpub-start-insert
if (isDeveloper) console.log(`${firstName} is a developer.`);
# leanpub-end-insert
// but it's better to use curly braces
~~~~~~~

In the other direction of just having one `if` without an `else` statement, there can be more than one condition expressed by using additional else-if statements in between:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const isDeveloper = true;
# leanpub-start-insert
const isLawyer = false;
# leanpub-end-insert

if (isDeveloper) {
  console.log(`${firstName} is a developer.`);
# leanpub-start-insert
} else if (isLawyer) {
  console.log(`${firstName} is a lawyer.`);
# leanpub-end-insert
} else {
  console.log(`${firstName} may be still a student.`);
}
~~~~~~~

This code has one flaw though, which we will adress properly in one of the next sections when we learn about logical operators. But can you spot it right now? Hint: What's printed if Robin is a developer and a lawyer? Try it yourself in the code.

An if-else statement (with optional else-if statements) always runs only the block of the first truthful (also called truthy) condition. All the following blocks are ignored. If you would want to fix this without logical operators (which we introduce later), you would have to use two if-else statements:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const isDeveloper = true;
const isLawyer = false;

if (isDeveloper) {
  console.log(`${firstName} is a developer.`);
} else {
  console.log(`${firstName} may be still a student.`);
}

if (isLawyer) {
  console.log(`${firstName} is a lawyer.`);
} else {
  console.log(`${firstName} may be still a student.`);
}
~~~~~~~

The drawback is that if both booleans are `false`, the code would execute both else blocks with their same instructions which wouldn't be desired either.

The if-else statement is one of the most used tools as a developer, because it enables one to move from coding a sequence of instructions to coding a tree of instructions with decision making based on conditions. Therefore not all code will be executed and only certain parts of the code will meet the conditions along the way. The if-else statement is one of several **control structures** (which enabled **control flows** in JavaScript) you will learn about.

### Exercises:

* From your personal variables, print something depending based on your `isMarried` and `hasKids` status.
* Read more about [if-else in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else).
  * Read more about [the lesser used switch-case in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch).
  * Read more about [a conditional in JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/Conditional).

## Relational and Equality Operators

For many if-else statements you will not always have a boolean at your hand. Instead, you will make decisions based on other primitive or structural types which are evaluated into booleans. For example, **relational operators** are used to derive booleans from an expression between two values of a relation:

{title="index.js",lang="javascript"}
~~~~~~~
const yearsAsDeveloper = 7;

const isDeveloper = yearsAsDeveloper > 0;

console.log(isDeveloper);
// true
~~~~~~~

The newly created `isDeveloper` boolean can be used in an if-else statement as condition now. However, since the expression evaluates to an boolean anyway, we can use this *on the fly* as a condition in the if-else statement, because it will evaluate within the parentheses:

{title="index.js",lang="javascript"}
~~~~~~~
const yearsAsDeveloper = 7;

if (yearsAsDeveloper > 0) {
  console.log(`
    I am a developer with
    ${yearsAsDeveloper} years of experience
  `);
}
~~~~~~~

Operators such as `>` (greater than), `<` (less than), `<=` (less than or equal), `>=` (greater than or equal), `==` (equality or double equal operator), or `===` (strict equality, identity, or tripple equal operator) are used to derive booleans or to make on the fly decisions based on the derived booleans in conditional statements such as the if-else statement.

You may have noticed that there are two similar equality operators `==` (equality operator) and `===` (strict equality operator). While the **equality operator** (also called **comparison operator**) coerces its values to a number data type if both values are of different types, the **strict equality operator** does not perform a coercion and keeps the data types intact:

{title="index.js",lang="javascript"}
~~~~~~~
console.log(1 == '1'); // leads to 1 == 1
// true

console.log(1 === '1'); // keeps data types
// false
~~~~~~~

In other words, the equality operator does not care about data types. Therefore, it's a good rule of thumb to use the strict equality operator whenever you can to leave less room for errors, because most of the time you do want to compare values and their respective data types. As counterparts to both operators, there are also `!==` (strict non-equality) and `!=` (non-equality) operators.

### Exercises

* Read more about [the if-else statement in JavaScript](https://javascript.info/ifelse).
* See more examples in action about [relational and equality operators in JavaScript](https://javascript.info/comparison).
* Read more about [equality operators in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness).
  * Read more about [JavaScript's equality operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Equality).
  * Read more about [JavaScript's strict equality operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality).
* Question: What happens if you compare `4 >= 5`?
* Question: What happens if you compare `3 <= 3`?
* Question: What happens if you compare `true > false`?
  * Answer: You get `true` as result, because when using a relational operator on booleans, `true` is coerced to `1` and `false` is coerced to `0`.
* Question: What happens if you compare `'A' > 'a'`?
  * Answer: You get false as result, because when using a relation operator on strings, the underlying character's [unicode](https://en.wikipedia.org/wiki/List_of_Unicode_characters) is used where `'A'` comes earlier in the unicode table than `'a'` and therefore isn't greater.
* Come up with variables yourself and apply comparison and relational operators on them without and with if-else statements.

## Statements vs Expressions

Stepping a bit away from the actual code, this section will explain the terms statements and expressions. Both have been used in this book before, but without any explanation yet. Now we will address this, because these terms will come across more often when speaking code.

**Statements** execute to make something happen in code. So a statement can be a `console.log()` statement (because it's a method as we will learn later) or control structures such as an if-else statement. So essentially a statement gives instructions on how a piece of code has to execute.

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const fullName = `${firstName} Wieruch`;
const yearsAsDeveloper = 7;

if (yearsAsDeveloper > 0) {
  console.log(`${fullName} is a developer.`);
} else {
  console.log(`${fullName} may be still a student.`);
}
~~~~~~~

However, the last code snippet shows expressions too. In contrast to statements, **expressions** are used *to produce* a value. Hence you hear people say 1 + 2 *"results in"* or *"evaluates to"* 3. These are all words that describe the same term. So essentially expressions are values assigned to variables, variables that are derived from other values/variables (e.g. booleans derived from relational operators), conditions used for if-else statements, and everything else where a value appears.

![](images/statement-vs-expression.png)

In conclusion, as mentioned partly before, the right-hand side of an value to variable assignment is called an expression. If the value happens to be just a plain data type such as `Robin` or `7`, it's also called **literal**, because the values that get produced are litteraly written down.

### Exercises:

* Go through the code from the previous sections and mentaly assign each part in a line of code either statement, expression or both.
* Read more about [the hierarchy of statements (e.g. control structures and declarations)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements).

## Logical Operators

Beyond relational and equality operators which compute to booleans, there are also logical operators. Do you recall the flaw that we had with "Robin being a developer and a lawyer" ?

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const isDeveloper = true;
const isLawyer = true;

if (isDeveloper) {
  console.log(`${firstName} is a developer.`);
} else if (isLawyer) {
  console.log(`${firstName} is a lawyer.`);
} else {
  console.log(`${firstName} may be still a student.`);
}
~~~~~~~

The flaw of this decision tree is that it would only execute the first block: "Robin is a developer." This introduces an errornous behavior (read: bug), because Robin is a lawyer as well. What's missing are operators which can combine more than one boolean value: entering **logical operators**. In this case, the problem can be solved with an **logical && (AND) operator** which evaluates to `true` if all of the participating booleans are `true`:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const isDeveloper = true;
const isLawyer = true;

# leanpub-start-insert
if (isDeveloper && isLawyer) {
  console.log(`${firstName} is a developer and a lawyer.`);
# leanpub-end-insert
} else if (isDeveloper) {
  console.log(`${firstName} is a developer.`);
} else if (isLawyer) {
  console.log(`${firstName} is a lawyer.`);
} else {
  console.log(`${firstName} may be still a student.`);
}
~~~~~~~

The printed output will result in "Robin is a developer and a lawyer." Even though the other two conditions in the following else-if parenthaseses evaluate to `true` too, these blocks will not execute, because one of the earlier conditions (here: `isDeveloper && isLawyer`) already evaluated to `true` and therefore executed its block.

The equivalent of the logical AND operator is the **logical || (OR) operator** which evalutes to `true` if at least one of participating booleans is `true`:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const isDeveloper = true;
const isLawyer = true;

if (isDeveloper && isLawyer) {
  console.log(`${firstName} is a developer and a lawyer.`);
# leanpub-start-insert
} else if (isDeveloper || isLawyer) {
  console.log(`${firstName} is a developer or a lawyer.`);
# leanpub-end-insert
} else {
  console.log(`${firstName} may be still a student.`);
}
~~~~~~~

While relational and equality operators are used to derive booleans from other primitives, using logical AND and OR operators is always helpful when combining multiple booleans into one boolean. Last but not least, you should know about the **logical ! (NOT) operator** which is there to flip a boolean from `false` to `true` or from `true` to `false`:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const isDeveloper = true;

if (!isDeveloper) {
  console.log(`${firstName} is not a developer.`);
} else {
  console.log(`${firstName} is a developer.`);
}
~~~~~~~

If you deal with booleans and conditions (e.g. if-else statement), you will often use logical AND and OR operators to combine booleans or flip them with the logical NOT operator. Play around with all variations of these to get comfortable with them.

### Exercises:

* Read more about [JavaScript's logical AND operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND).
* Read more about [JavaScript's logical OR operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR).
* Read more about [JavaScript's logical NOT operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_NOT).
* Play around with all three logical operators and experience its varying outcome first hand.

## Truthy and Falsy

In JavaScript there exists the concept of truthy and falsy values. You already know about one truthy and one falsy value: `true` and `false`. These are explicit truthy and falsy values, however, there are implicit ones too. In this section, we want to explore these implicit logical values, because they are helpful to shortcut if-else statements with the help of coercion.

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const middleName = null;
const lastName = 'Wieruch';

if (middleName) {
  console.log(`${firstName} ${lastName} has a middle name!`);
}
~~~~~~~

In this example, the output will not be printed, because Robin Wieruch has no middle name. Everything that's used as a condition in an if-else statements gets coerced into a boolean. Therefore, the variable `middleName` with its value `null` is coerced into false, because `null` is a falsy value. Other falsy values are `undefined`, `0`, and empty string:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
# leanpub-start-insert
const middleName = '';
# leanpub-end-insert
const lastName = 'Wieruch';

if (middleName) {
  console.log(`${firstName} ${lastName} has a middle name!`);
}
~~~~~~~

In contrast, if a variable with the data type string or number is defined, it is coerced into a truthy value. The following code snippet prints the output, because there is a defined middle name:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Sarah';
const middleName = 'Maria';
const lastName = 'Finnley';

if (middleName) {
  console.log(`${firstName} ${lastName} has a middle name!`);
}
~~~~~~~

Both, truthy and falsy values can be negated by using the logical NOT operator:

{title="index.js",lang="javascript"}
~~~~~~~
const firstName = 'Robin';
const middleName = '';
const lastName = 'Wieruch';

# leanpub-start-insert
if (!middleName) {
  console.log(`${firstName} ${lastName} has no middle name!`);
# leanpub-end-insert
}
~~~~~~~

You see that lots of things derive from data type coercion and conversion in JavaScript. Data types which are not booleans are coerced into booleans when they are needed in a boolean context such as an if-else statement. Initially that's a lot to digest, however, it helps one in the long run to shortcut decision makings.

### Exercises:

* Read more about [logical operators in JavaScript](https://javascript.info/logical-operators).
* Read more about [truthy values](https://developer.mozilla.org/en-US/docs/Glossary/Truthy).
* Read more about [falsy values](https://developer.mozilla.org/en-US/docs/Glossary/Falsy).
* Use your variables from before and put them as conditions in if-else statements. See whether these conditions coerce into a truthy or falsy value and therefore whether the code in the if block runs.
* From the variables that describe yourself, convert `countSiblings` and `countPets` into their respective `hasSiblings` and `hasPets` boolean variables by using the double NOT `!!` operator.

## Ternary Operator

Personally I learned about **ternary operators** pretty late in my career as a developer. And this is okay, because everything that can be done with a ternary operator can be done with a if-else statement. However, ternary operators become more popular these days -- especially when using modern frameworks like React.js. The ternary operator (also called **conditional operator**) makes an if-else statement more concise. Take the following example:

{title="index.js",lang="javascript"}
~~~~~~~
const yearsAsDeveloper = 7;
const isDeveloper = yearsAsDeveloper > 0;

let hourlyRate;

if (isDeveloper) {
  hourlyRate = `$${12.5 + yearsAsDeveloper * 12.5}`;
} else {
  hourlyRate = `$12.50`;
}

console.log(hourlyRate);
// '$100'
~~~~~~~

In this example, we declare an `undefined` variable `hourlyRate` where we will assign the value based on a decision making process (e.g. if-else statement) eventually. Even though it's questionable whether this example of calculating once hourly rate as a freelance developer makes sense, we can see how decision making can be used to define variables based on a condition. However, this is one of the best use cases for the ternary operator, because it shortens the process of assigning a value to a variable conditionally:

{title="index.js",lang="javascript"}
~~~~~~~
const yearsAsDeveloper = 7;
const isDeveloper = yearsAsDeveloper > 0;

# leanpub-start-insert
const hourlyRate = isDeveloper
  ? `$${12.5 + yearsAsDeveloper * 12.5}`
  : `$12.50`;
# leanpub-end-insert

console.log(hourlyRate);
// '$100'
~~~~~~~

The anatomy of the ternary operator consists of the following buildings blocks:

![](images/ternary-operator.png)

If you think about it, a ternary operator (or if-else statement) could be used to assign booleans based on comparison/relational operator too. However, since a comparison or relational operator already evlautes a result into a boolean, it becomes redundant to do it oneself:

{title="index.js",lang="javascript"}
~~~~~~~
const yearsAsDeveloper = 7;

// redundant, but it works
const isDeveloper = yearsAsDeveloper > 0 ? true : false;

console.log(isDeveloper);
// true
~~~~~~~

It's also possible to nest ternary operators into each other, but it's not recommended because the code becomes less readable. Anyway, ternary operators are a great way to keep if-else statements short. However, be comfortable with using if-else statements first before dipping your toes into its more concise sibling.

### Exercises:

* Read more about the [ternary operator in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator).
