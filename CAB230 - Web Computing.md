# CAB230 Study Guide | 2022 Year 1 Semester 1

Dr Timothy Chappell | Notes for CAB230 at the Queensland University of Technology

<br>

<h1>Table of Contents</h1>
<ul>
	<li><a href="#CAB230">CAB230: Web Computing</a></li>
	<ul>
		<li><a href="#week1">Week 1</a>: Introduction</li>
		<li><a href="#week2">Week 2</a>: WebContentUIs</li>
		<li><a href="#week3">Week 3</a>: Web Requests and React</li>
		<li><a href="#week4">Week 4</a>: Web Design and SPAs</li>
		<li><a href="#week5">Week 5</a>: React State, Components and Accessibility</li>
		<li><a href="#week6">Week 6</a>: Assessment Work</li>
		<li><a href="#week7">Week 7</a>: REST and Node</li>
		<li><a href="#week8">Week 8</a>: Express Middleware</li>
		<li><a href="#week9">Week 9</a>: Security</li>
		<li><a href="#week10">Week 10</a>: Deployment</li>
		<li><a href="#week11">Week 11</a>: Asynchronous JS</li>
		<li><a href="#week12">Week 12</a>: </li>
		<li><a href="#week13">Week 13</a>: </li>
	</ul>
</ul>

<hr /> <br />

<h1 id="CAB230">CAB230: Web Computing</h1>
<p>The World Wide Web is the most important platform for software systems and an integral part of modern life. Many companies owe their existence to the web, through applications deployed over the Internet using web protocols. All IT professionals require a good understanding of the web and its architecture, especially software developers and those tasked with maintaining and implementing web-based software systems. This unit is a technical introduction to modern web computing. You will design and implement clean and responsive user interfaces, taking account of accessibility and internationalisation. We will provide an introduction to JavaScript and you will use it throughout the semester, gaining practical experience with HTML, CSS and frameworks such as React on the client side, and node.js, Express and the node ecosystem on the server side. You will understand security threats and their mitigation and gain practical experience deploying an internet facing web server using HTTPS.</p>

<br />

<h2 id="week1">Week 1: Introduction</h2>

### What is the web?

The web is an application layer on top of a network and is arguably the most important platform in computing. The web is made up of web requests sent by other connected devices, each containing packets of information and data following pre-defined conventions.

### Introduction to Javascript

Let's jump straight into a javascript example and we can break it down piece by piece after.

```js
let total = 0;
let count = 1;

while (count <= 20) {
  total += count;
  count += 1;
}

console.log(total);
```

The first 2 lines in the above example declare 2 new variables and assign them a value upon declaration. In Javascript variables must be created either using the `let` keyword or `const` keyword (previous versions of Javascript used the `var` keyword). The `let` keyword creates a mutable variable (meaning the data can be changed later on) while the `const` keyword creates an immutable variable (meaning once declared the data cannot be changed). It must also be noted that at the end of every statement a `;` must be placed.

On line 4 we create `while` loop that will repeat itself until the variable `count` is less than or equal to 20. Anything inside of the `while` loops body, i.e. anything inside of the `{}` brackets, will be repeated until its condition is met.

Line 5 and 6 take place inside of the `while` loops body with line 5 being shorthand for `total = total + count;` which just adds the value of `count` to `total`. Much like with `+=` we also have access to `-=`, `/=` and `*=` operators. Line 6 does the same however we add 1 to `count`.

Line 9 is the final line in the example program and it simply prints the variable `total` to the terminal screen using the `console.log()` method.

Now that we've had a brief introduction to an example program lets break down some of the other concepts Javascript provides.

### Declarations

The example below shows a brief introduction to declaration and concatenation.

```js
// Integers
let x = 3.14;
const y = 67;
y = 23; // Error - cannot reassign const

// Strings
// Javascript is case sensitive so these 2 variables are seperate
// Javascript strings also don't care if you use single '' or double "" quotes, they are one in the same
let hello = "Hello, world!";
let Hello = "Hello, world!";

// We can concatenate strings
let text1 = "Hello";
let text2 = "world";

let finalConcatText = text1 + ", " + text2;
let finalFormatText = `${text1}, ${text2}`; // notice we used `` not ''/""

// Booleans
// Javascript booleans use lowercase true and false
let success = true;
let failure = false;
```

### Equality

Equality in Javascript can be a little funny to learn due to the ability to decide whether we want loose or strict equality.
Loose equality works by first converting the values of the two operands being compared to a common type then comparing the values. Here we see in the example below that even though we assign `x` to the value `10`, when compared to `"10"` Javascript still evaluates this condition as `true` even though the values aren't necessarily the same datatype.

```js
// Initial values
let x = 10;

// Loose equality/inequality example
x == 5; // false
x == "5"; // false
x == "10"; // true

x != 5; // true
x != "5"; // true
x != "10"; // false
```

With strict equality however, Javascript checks whether the two operands are equal considering value and datatype.

```js
// Initial values
let x = 10;

// Strict equality/inequality example
x === 5; // false
x === "10"; // false
x === 10; // true

x !== 5; // true
x !== "10"; // true
x !== 10; // false
```

It's highly recommended not to use `==` unless there is a purpose behind it, always use `===` when comparing values.

### Logical Operators

Logic operators work just as we'd suspect them to in Javascript following the conventions of math and other languages.

```js
// Initial values
let x = 10;
y = 20;

// && - Logical AND
x < y && y === 20; // true
x < y && y > 20; // false
x >= 10 && !(y === 200); // true

// || - Logical OR
x < y && y === 20; // true
x < y && y > 20; // true
x < 10 && !(y === 200); // true
```

### Conditional Statements

in Javascript an `if` statement allows us to run conditional code, statements of code only run if a certain condition is met. There are 3 types of if statements, if statement, if-else statement, and cascading if statements.

```js
let myCredits = 156;

const graduate = 288;
const second = 192;
const first = 96;

if (myCredits >= graduate) {
  console.log("Bachelor of IT Graduate");
} else if (myCredits >= second) {
  console.log("Third Year Student");
} else if (myCredits >= first) {
  console.log("Second Year Student");
} else {
  console.log("First Year Student");
}
```

We also have to `switch` statements in Javascript.

> "The switch statement is often used as an alternative to an if-else construct if a single expression is tested against three or more conditions." - [Microsoft](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/switch)

```js
let intDay = 3;
let strWeekDay = "";

switch (intDay) {
  case 0:
  case 1:
  case 2:
  case 3:
  case 4:
  case 5:
    strWeekDay = "Week Day";
    break;
  case 6:
    strWeekDay = "Weekend";
    break;
  default:
    strWeekDay = "Invalid Day";
}
```

In the example above there are a few things we can note. if the value of `intDay` is 0-5 it will match at its appropriate case and 'fall' through until it hits a `break` statement. The `break` statement will stop it from 'falling' through any more cases. If the value of `intDay` is 6 it will match at `case 6:` and if the value of `intDay` matches none of the cases it will match at `default`.

### For Loops

A `for` loop is a type of iteration that will continue to loop through a block of code a specified amount of times.

```js
// Counter controlled loop
for (let count = 1; count <= 100; count++) {
  console.log(count);
}
```

In the example above we declare a variable called `count` inside of the `for` loop statement, tell it to keep looping everything inside of its body until `count` is less than or equal to 100, and finally after every loop +1 to `count`.

### While and Do-While Loops

A `while` loop is a type of iteration that will continue to loop through a block of code as long as the specified condition is true. It first checks the condition, then if `true` will run whats inside the body. When working with `while` loops it's important to be careful not to create infinite loops (loops without any break condition).

```js
let count = 1;

while (count <= 100) {
  console.log(count);
  count++;
}
```

Unlike with a `while` statement which checks the condition first then runs the code block a `do{} while` conditions run the body first, then check if the condition is `true`.

```js
let count = 0;

do {
  count++;
  console.log(count);
} while (count < 100);
```

### String Immutability

Strings in Javascript are immutable, they can't be changed. However, they can be reassigned values.

```js
let text = "Hello";

console.log(text);     # "Hello"

// this has 0 effect on the string
// but be aware that the compiler doesn't complain
text[2] = 'f';

console.log(text);     # "Hello"

text = "Hello, world!";

console.log(text);     # "Hello, world!"
```

### Special Characters

There are special characters we can embed into strings that allow us to manipulate the final product in certain ways.

| Character | Effect                          |
| --------- | ------------------------------- |
| \n        | Create a newline                |
| \t        | Creates a 4 space tab           |
| \'        | Allows an embedded single quote |
| \"        | Allows an embedded double quote |
| \\        | Creates a backslash             |

### Functions

In Javascript functions are fundamentally values which are assigned to an identifier through an assignment statement. They allow us to assign repeated bodies of code to a value so we only need to reference that value to access the body of code. There are 2 main ways we can create a function and both work in slightly different ways but the key difference being is

- Functions created via assignment need to be defined before the identifier is used. Meaning we cannot call the function above its declaration, only below.
- Functions created via declaration are 'hoisted' by the system to the top of the scope. Meaning we can declare the function anywhere in the code and have access to it above and below.

```js
// Declaration function
const cube = (x) => {
  return Math.pow(x, 3);
};

// or

const square = function (x) {
  return Math.pow(x, 2);
};

// Assignment function
function quartic(x) {
  return Math.pow(x, 4);
}
```

Another difference to be noted between the two is how they work when it comes to scope. Functions declared through declaration can be accessed no matter where they are in the codes scope. However, assignment functions can only be access in the same scope that they are defined in.

```js
{
  const cube = (x) => {
    return Math.pow(x, 3);
  };

  console.log(quartic(2)); // 16
  console.log(cube(3)); // 27

  function quartic(x) {
    return Math.pow(x, 4);
  }
}

console.log(quartic(3)); // 81
console.log(cube(4)); // ReferenceError

// Output
// 16
// 27
// 81
// console.log(cube(4)); ReferenceError: cube is not defined
```

### Objects

Objects are 'record types' that enable us to define fields and tie them to a value. These are different to objects defined in OOP as they behave in slightly different ways. Let's take a look at an example of how we define objects in Javascript:

```js
let lucy = {
  name: "Lucy",
  age: 6,
};

console.log(typeof lucy); // object
console.log(lucy); // { name: 'Lucy', age: 6 }
console.log(lucy.name); // Lucy
console.log(lucy["age"]); // 6

// It is advised not to add properties to objects like this
// as it can become error prone
lucy.colour = "golden";

console.log(lucy); // { name: 'Lucy', age: 6, colour: 'golden' }
```

We can also declare constructors for an object using a method property.

```js
function Dog(name, age) {
  this.name = name;
  this.age = age;
  this.toString = () => {
    return `<${name}, ${age}>`;
  };
}

let lucy = new Dog("Lucy", 6);

console.log(lucy); // Dog { name: Lucy, age: 6, toString: [Function] }
console.log(lucy.toString()); // <Lucy, 6>
```

This can also be achieved using classes. Below is a quick example however we will go over them later in the course.

```js
class Dog {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  toString() {
    return `<${this.name}, ${this.age}>`;
  }
}

let lucy = new Dog("Lucy", 6);

console.log(lucy); // Dog { name: Lucy, age: 6 }
console.log(lucy.toString()); // <Lucy, 6>
```

### JSON (JavaScript Object Notation)

JSON is a Javascript format for storing and exchanging data. Javascript provides a number of useful functions for working with JSON such as functions to translate JSON to and from string representations. Two such functions are `JSON.stringify()` and `JSON.parse()`.

### Scope

In Javascript we have this concept of scope where values can only be access if the thing trying to access them is in their 'scope'. Javascript contains 3 different scopes consisting of global scope, function scope and block scope each functioning in different ways.

```js
{
  // let and const provide block scope
  let x = 2;
  const y = 4;

  // var does not have block scope
  // the var keyword is old Javascript and is heavily recommended against using
  var z = 2;
}

// x and y cannot be accessed here
// z can be accessed here
```

```js
// Local/Function Scope

// cannot access y here

function x() {
  let y = "foo";
  // can access y here
}

// cannot access y here
```

```js
// Global Scope
let y = "foo";
// can access y here

function x() {
  // can access y here
}
```

<br />

<h2 id="week2">Week 2: WebContentUIs</h2>

### Internet Protocol Suite

The internet protocol suite, also known as TCP/IP, is a collection of communication protocols used in the internet. It's made up of 4 main layers:

1. Application: This layer consists of the standard communication standards and applications used.
2. Transport: This layer provides the channel for communications needed by applications.
3. Internet: This layer defines the addressing and routing structures needed.
4. Link: This layer handles the transferring of data across the network.

### IP Addresses

IP addresses are numerical labels that are assigned to devices upon connecting to a network. IP addresses are used for a variety of reasons but the main 2 are network identification (identification of the host network) and location addressing (where the device is located in the network). IP address themselves can be hard to remember, this is why IP addresses can also have domain names mapped to them. When a domain name is searched the network will query the DNS servers and search for the IP address registered with the domain.

IP address and domain name example:

| IP Address   | Domain Name    |
| ------------ | -------------- |
| 43.245.43.93 | www.qut.edu.au |

### GET and POST Requests

When communicating with the web we can use the HTTP protocol to send requests. These can consist of retrieving data such as static webpages and web resources (GET requests) and sending data such as form data (POST requests). Once a request has been sent the server will respond with a status report regarding the request. These reports will contain useful information such as the request status code, request date and the server sending the status report.

Here is an example of a simple GET request from the Mozilla site:

```HTTP
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: en-US
```

```HTTP
HTTP/1.1 404 Not Found
Date: Tue, 15 Mar 2022 20:18:22 GMT
Server: Apache
Content-Length: 29769
Content-Type: text/html

<!DOCTYPE html...>
```

Here is an example of a simple POST request and response from the Mozilla site:

```HTTP
POST /contact_form.php HTTP/1.1
Host: developer.mozilla.org
Content-Length: 64
Content-Type: application/json

{
	"Id": 12345,
	"Customer": "John Smith",
	"Quantity": 1,
	"Price": 10.00
}
```

```HTTP
HTTP/1.1 200 OK
Content-Length: 19
Content-Type: application/json

{"success":"true"}
```

### The DOM

When the web was first invented they only supported static webpages. This means that there was no dynamic changing that happened on webpages meaning if we wanted something to change we had to refresh the page. The DOM, Document Object Model, is a data representation of all the objects, elements and the structure of a document, or webpage. Each element in HTML (head, title, a, p) correspond to an object in the DOM. Here is an example of how the DOM is structured:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Blog</title>
  </head>
  <body>
    <h1>Blog 01 - My first blog</h1>
    <p>Hello, this is my first blog</p>
    <p>See my other articles <a href="#">here</a></p>
  </body>
</html>
```

```
├── html
│   ├── head
│   │   ├── title
│   │   │   ├── "My Blog"
│   ├── body
│   │   ├── h1
│   │   │   ├── "Blog 01 - My first blog"
│   │   ├── p
│   │   │   ├── "Hello, this is my first blog"
│   │   ├── p
│   │   │   ├── "See my other articles"
│   │   │   │    ├── a
│   │   │   │    │   ├── "here"
```

We can also interact with the DOM and its elements using javascript commands. Here are a few example commands and what they do:

| Access Methods                               | Definition                                                                |
| -------------------------------------------- | ------------------------------------------------------------------------- |
| document.getElementById("main")              | Returns the element with id="main" and null otherwise                     |
| document.getElementsByTagName("p")           | Returns an array of all "p" tag elements from the document                |
| document.getElementsByClassName("highlight") | Returns an array of all elements with class="highlight" from the document |
| document.querySelectorAll("div > p")         | Returns an array of all elements matching the CSS selector "div > p"      |

### Data Binding

Data binding is a useful and powerful tool used in nearly all applications. Data binding is the concept of binding data from one source to another. This can be done in a variety of ways however a common method is to use the Model-View-ViewModel architectural pattern. Let's take a look at what each of these do and how they interact with each other. The Model is the first layer, this is what houses all the back-end data and core app logic. The View is the front-end user-interface the user interacts with, this can consist of text boxes, labels and so on. The ViewModel is what binds the data between these two layers allowing them to interact and sync data with each other.

### One-way Binding

One-way data binding is the concept of data only flowing in a single direction. An example of this in react is if data changes in a component then it will also update the View with the new data.

```jsx
const App = () => {
  const name = "John Doe";

  return <h1>Welcome, {name}</h1>;
};
```

In this example if the data in `name` changes, so will the data displayed in the `<h1>` tags.

### Two-way Binding

Two-way data binding is the concept of data flowing in both directions from View to Model and Model to View. An example of this in react is dynamically changing a welcome message depending on a users input.

```jsx
const App = () => {
  const [username, setUsername] = useState("");

  return (
    <div>
      <h1>Welcome, {username}</h1>
      <input
        type="text"
        value={username}
        onChange={(e) => setUsername(e.target.value)}
      />
    </div>
  );
};
```

In this example we can see the text in the `<h1>` tag will dynamically update depending on what the user types in the `<input />` box. In ReactJs this is done using state and this will be talked about later on.

### ReactJs

ReactJs is a component-based Javascript library developed by Facebook. It is based around creating reusable JSX components which can handle state and dynamic updates. ReactJs has so many more features and tricks that we will go over as they come into play.

Here is a small example of a simple ReactJs program:

```jsx
import React, { useState } from "react";

import login from "../auth.js";

const loginScreen = () => {
  const [username, setUsername] = useState("");
  const [password, setPassword] = useState("");

  const handleLogin = () => {
    login(username, password);
  };

  return (
    <div>
      <form>
        <label for="username">Username: </label>
        <input
          type="text"
          name="username"
          value={username}
          onChange={(e) => setUsername(e.target.value)}
        />

        <label for="password">Password: </label>
        <input
          type="password"
          name="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
        />

        <button type="button" onClick={handleLogin} />
      </form>
    </div>
  );
};
```

### React Native

React Native is an extension to ReactJs designed for developing mobile applications. React Native compiles to mobile specific native code allowing to build cross-platform mobile applications using only a single language, React Native.

Here is a small example of a simple React Native application:

```jsx
import React from "react";
import { View, ScrollView, Text, Image } from "react-native";

const blogs = [
  {
    blogHeaderImage: { uri: "../assets/blog01/headerImage.jpg" },
    blogTitle: "Blog 01",
    blogBody: "Lorum Ipsum...",
  },
  {
    blogHeaderImage: { uri: "../assets/blog02/headerImage.jpg" },
    blogTitle: "Blog 02",
    blogBody: "Lorum Ipsum...",
  },
];

const BlogTemplate = (props) => {
  return (
    <View>
      <View>
        <Image
          src={props.blogHeaderImage}
          style={{ width: 200, height: 100 }}
        />
        <Text>{props.blogTitle}</Text>
      </View>

      <View>
        <Text>{props.blogBody}</Text>
      </View>
    </View>
  );
};

const App = () => {
  return (
    <ScrollView>
      <Text>Welcome to my React Native blog app</Text>
      <View>
        {blogs.map((blog) => (
          <BlogTemplate {...blog} />
        ))}
      </View>
    </ScrollView>
  );
};
```

### What is JSX?

JSX, or Javascript XML, is a React-specific syntax that allows for HTML code to coexist inside of Javascript code. In the below example we can see `<h1>` tags nested into Javascript code as well as Javascript variables embedded into our HTML code. It's important to remember when we return JSX code we must only return a single value. This is why everything returned gets surrounded in a `<div>` tag.

```jsx
const user = {
  firstName: "John",
  lastName: "Doe",
};

const formatName = (user) => {
  return `${user.firstName} ${user.lastName}`;
};

const WelcomeUser = (props) => {
  return (
    <div>
      <h1>Welcome, {formatName(props.user)}</h1>
    </div>
  );
};

ReactDOM.render(<WelcomeUser {...user} />, document.getElementById("root"));
```

### React Components

ReactJs was built with components in mind. React components are reusable sections of code that work similar to functions but are used to create elements which can be used, generally, for the front end.

Here is an example of a React component that displays a welcome message to the user:

```jsx
const user = [
	firstName: 'John',
	lastName: 'Doe'
]

const WelcomeUser = () => {
	return (
		<div>
			<h1>Welcome, {user.firstName} {user.lastName}</h1>
		</div>
	);
}

ReactDOM.render(
	<WelcomeUser />,
	document.getElementById('root')
);
```

### Props

React props work very similar to how arguments get passed into functions. When we want to pass props to a component we first need to pass that component the `props` object. We can then define what props we want to pass when calling the component and use these props by their name in the component using props.propName.

Here we create a `WelcomeUser` component that takes in the `props` object and uses the username thats passed in:

```jsx
const WelcomeUser = (props) => {
  return (
    <div>
      <h1>
        Welcome, {props.firstName} {props.lastName}
      </h1>
    </div>
  );
};

ReactDOM.render(
  <WelcomeUser firstName="John" lastName="Doe" />,
  document.getElementById("root")
);
```

We can also pass in an object as a prop and use its attribute names tied to the object to reference those values:

```jsx
const user = [
	firstName: 'John',
	lastName: 'Doe'
]

const WelcomeUser = (props) => {
	return (
		<div>
			<h1>Welcome, {props.firstName} {props.lastName}</h1>
		</div>
	);
}

ReactDOM.render(
	<WelcomeUser {...user} />,
	document.getElementById('root')
);
```

<br />

<h2 id="week3">Week 3: Web Requests and React</h2>

### Multitasking in Javascript

Javascript is a synchronous programming language, that's to say, it is single-threaded and can only execute a single operation at a time. It's because of this that if we attempt to do more than one thing at a time, operations are stacked in order of execution and while each operation is being processed nothing else can happen. This is a major problem when dealing with websites and applications as say we need to request some data from an API, we'd like the program to be able to keep running while we request this data. In a single-threaded programming language this is not possible as the application will freeze and not respond until that process, in this instance the API call, has finished.

Asynchronous programming is a way we can fix this issue. In asynchronous programming multiple functions and code blocks can be run at the same time without the need to freeze the application. Using the example above, using asynchronous Javascript programming, we could call for data from our API while the user can still interact and move around the page. There are three main approaches to doing this in Javascript:

1. Callback functions
2. Promises
3. Async and await

### Callback Functions

Callback functions are essentially functions that are passed in as arguments to be executed at some other later time. For example, let's say on our HTML page we have a button:

```HTML
<button id='callback-btn'>Click here</button>
```

And in our Javascript file we have an event listening waiting for that button to be pressed. When the button gets pressed we callback to a function that simply prints to the console 'Button pressed'.

```javascript
document.queryselector("#callback-btn").addEventListener("click", () => {
  console.log("Button pressed");
});
```

So as we can see, `.addEventListener()` is taking in 2 parameters, the event listener type 'click' and the second being the callback function.

### Promises

A promise is a special Javascript object that can hold the future value of an asynchronous operation. A promise can be in 1 of three states at any given time:

- Pending: This is the initiate state, it is neither fulfilled or rejected
- Fulfilled: This state is true when the operation has been completed and the promise now contains the retrieved data
- Rejected: This state is true when the operation has failed

Promises work by chaining functions from each other using the keyword `.then()`. We can also use `.catch()` at the end of our chain to throwback any errors we retrieve. For example, let's say we want to print to the console the returned data if, and only if, the fetch request returns a valid response, without having to freeze our application waiting for the API callback. We can use promises for this as such:

```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((response) => {
    if (response.ok) {
      return response.json();
    }

    throw new Error("Failed network response");
  })
  .then((result) => {
    console.log(result);
  })
  .catch((error) => console.log(`Problem with error message: ${error}`));
```

We can also use Async/Await to accomplish the same thing:

```javascript
{
	() => {
		try {
			const response = await fetch('https://jsonplaceholder.typicode.com/posts/1')

			if (!response.ok) {
		    throw new Error('Failed network response');
		  }

			console.log(await response.json());
		} catch (error) {
			console.log(`Problem with error message: ${error}`);
		}
	}
}
```

### Elements of a HTTP Session

A HTTP session generally consists of 3 main phases:

1. The client establishes a TCP connection with the server. By default this is setup on port 80.
2. The client then sends to the server and waits for a response back.
3. Finally, the client receives a response from the server containing information about the server request and, if successful, the data that was requested.

A server response will always contain a response code, some of these are important to know. Here is a small list of some important codes:

- 200 OK
- 400 Bad Request
- 401 Unauthorised
- 403 Forbidden
- 404 Not Found
- 500 Internal Server Error

### Fetch

We saw the use of the `fetch()` function in an earlier example when talking about promises but we'll go in a little more detail here. We can simulate GET and POST requests in Javascript using the `fetch()` function. The fetch request works by passing in the url for the data and an optional parameter containing headed data for the request being sent (i.e. authorisation tokens). Here is a simple fetch request using the `fetch()` method and some promises to simulate a GET request:

```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((response) => response.json())
  .then((json) => console.log(JSON.stringify(json)));
```

Here is a simple fetch request using the `fetch()` method and some promises to simulate a POST request:

```javascript
const headerContent = {
  method: "POST",
  body: JSON.stringify({
    title: "foo",
    body: "bar",
    userId: 1,
  }),
  headers: {
    "Content-type": "application/json; charset=UTF-8",
  },
};

fetch("https://jsonplaceholder.typicode.com/posts", headerContent)
  .then((response) => response.json())
  .then((json) => console.log(json));
```

### Class-Based Components

We can create components using either classes or functions. Classes were how components were originally made however with new updates we can now create components using functions. Below is an example of how to create a function using classes.

```jsx
class App extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div className="App">
        <h1>Hello World!</h1>
      </div>
    );
  }
}
```

### Function-Based Components

Function based components can be create using either the `function` keyword or tying an anonymous function to a variable.

```jsx
// Function
function App() {
  return (
    <div className="App">
      <h1>Hello World!</h1>
    </div>
  );
}

// Anonymous function tied to variable
const App = () => {
  return (
    <div className="App">
      <h1>Hello World!</h1>
    </div>
  );
};

export default App;
```

### Component State

There are a few ways we can modify the state of our components and these depend on how we defined our components. To create and modify the state of a class based component we first need to create a constructor for our class and create our state variables there. We can then alter the state of these variables using the `setState()` method.

```jsx
class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      // Here we define a state variable `count`
      // and assign its starting value to `0`
      count: 0,
    };
  }

  // Will be called as soon as the componenet is mounted
  componentDidMount() {
    document.title = `You clicked ${this.state.count} times`;
  }

  // Will be called everytime the component updates
  componentDidUpdate() {
    document.title = `You clicked ${this.state.count} times`;
  }

  render() {
    return (
      <div className="App">
        <h1>Total count is: {count}</h1>

        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Press me to +1 to count
        </button>
      </div>
    );
  }
}
```

We can do the same using function based components but in a slightly different way. Function based components use things called hooks to alter and manage state. To create a state variable we first must declare the variable along with a function to alter the variable and tie them both together using the `useState()` function. It's important to remember we also need to import `useState` from the `react` library to be able to use it.

```jsx
import React, { useState, useEffect } from "react";

const App = () => {
  // Here we say
  // - count: this is our state variable
  // - setCount: we use this to change the value of our state variable
  // - useState(0): the value in here is the initial value for our state variable
  const [count, setCount] = useState(0);

  // Will update when component mounts and updates
  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });

  return (
    <div className="App">
      <h1>Total count is: {count}</h1>

      <button onClick={() => setCount(count + 1)}>
        Press me to +1 to count
      </button>
    </div>
  );
};
```

<br />

<h2 id="week4">Week 4: Web Design and SPAs</h2>

### Single Page Applications (SPA)

An SPA, or single page application, is an instance of a web-app where there consists of only a single page where elements of the page refresh and update instead of the need to re-route to a new page completely.

Advantages:

- Generally after the initial load of the webpages recourses the webpage retains a constant speed and rarely dips
- Due to web resources being able to be cached the website can be run offline without any issues
- Due to the web-app consisting of only a single page there exists compatibility with native mobile applications

Disadvantages:

- Search engine optimisation can be difficult to get right due to web crawlers generally only indexing the main page
- If the user has disabled Javascript then the webpage won't work
- The initial load of the webpage can be slow as all resources need to be loaded at once

### React Routing

We can route from page to page in ReactJs using a popular library called `BrowserRouter`. In `BrowserRouter` each `Link` needs to have a corresponding `Route` to specify which page the user gets directed to.

```jsx
// index.js
import ReactDOM from "react-dom";
import { BrowserRouter, Routes, Route, Link } from "react-router";

const Home = () => {
  return (
    <div>
      <h1>Welcome to my Home Page</h1>
      <p>Keep on reading to learn more about React Routing</p>
    </div>
  );
};

const Blogs = () => {
  return (
    <div>
      <h1>My Blogs</h1>
      <p>Keep on reading to learn more about my blogs</p>
    </div>
  );
};

const App = () => {
  return (
    <BrowserRouter>
      <div className="App">
        <nav className="navBar">
          <Link to={"/"}>Home</Link>
          <Link to={"/blogs"}>Blogs</Link>
        </nav>

        <main>
          <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/blogs" element={<Blogs />} />
          </Routes>
        </main>
      </div>
    </BrowserRouter>
  );
};

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

React Router also provides to us a collection of utility hooks that we can use. Here are a few examples:

- `useParams`: Access path parameters
- `useSearchParams`: Access query string parameters
- `useNavigate`: Navigate to a page programatically without the need to include a link

### Web Design Principles: Content

The content we write on our website should follow some simple rules. It should be:

1. Fresh and interesting: The content should not be re-hashed or something not worth someones time. Always write interesting content that is updated and can keep peoples interest.
2. Quality over quantity: The quality of the content itself is much more important than the quantity of such content.
3. Not just copy-pasted content: Make sure the content you're writing is original and not just re-hashed from some other website. Give people a reason to want to view your content otherwise they will just go to where you copied the content from.
4. Have a voice: Have a reason for displaying and sharing your content. Provide something new and refreshing for the audience to view.

It's important to follow the mantra "write for lazy people" when creating new content. Most of the time people want to get their information in the shorted possible way, they don't want have to go out of their way to read something. Provide the most important content at the top and section everything into logical categories for people to browse.

### Web Design Principles: Organisation

When designing a large website, or even a small one, it's important to map out all the content and understand how it everything relates to each other. Then separate the content into logical categories and group them together, these will become your content sections or even seperate pages/routes.

A good navigation system will go a long way with users as it allows them to easily see where they on the website at any given time and allows them to easily navigate to other content on the page. Your navigation should be consistent across your whole website, make users learn something once and never change it. Findability of content also plays a big part into the organisation of your webpage as it refers to the quality of design and how it enables a user to find specific content they are looking for.

### Web Design Principles: Visual Design

### Web Design Principles: Compatibility

### Web Design Principles: Performance

### Web Design Principles: Interactivity

### Web Design Principles: Accessibility (week 5 lecture)

<br />

<h2 id="week5">Week 5: React State, Components and Accessibility</h2>

### Redux

### Context

### Constate

### Component Hierarchies

pass state variables and state variable functions down through components

### ReactStrap

<br />

<h2 id="week6">Week 6: Assessment Work</h2>
No new content

<br />

<h2 id="week7">Week 7: REST and Node</h2>

### Node

Node is a JS compiler and run-time originally Google but is now open source and maintained by the community. Node.js is server side Javascript used to support rapid server connections and processing. Let's create a simple hello world web server in Node.js:

```js
const http = require("http");

const hostname = "127.0.0.1";
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader("Content-Type", "text/plain");
  res.end("Hello World\n");
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

### REST

REST os a set of principles that define how web standards, such as HTTP and URIs, are sipposed to be used.

### Express

Express is an application framework designed for node. To use Express we must first install it using `npm install express -g`. Let's take a look at a very simple hello world express program:

```js
const express = require("express");
const app = express();

const hostname = "127.0.0.1";
const port = 3000;

app.get("/", (req, res) => {
  res.send("Hello World!");
});

server.listen(port, () => {
  console.log(`Express app listening at http://${hostname}:${port}/`);
});
```

We can handle routing using the `Router` class.

```js
const express = require("express");
const router = express.Router();

router.get("/", (req, res) => {
  res.send("Home page");
});

router.get("/about", (req, res) => {
  res.send("About page");
});

module.exports = router;
```

### Express Generator

Express generator will create and setup a lot of the necessary boilerplate for an Express application. To use it we must first install it using `npm install express-generator -g` and then we can create an Express application using `express helloworld`.

### JSON Web Tokens

JWT is an open standard for securing information stored as a JSON object through transmission. We can use JWT tokens to authenticate a user upon login and use that token then to access API's behind authentication points. The overall structure of a JWT token is a chain of encoded character segments separated by dots. An example being `xxxxxx.yyyyyyyy.zzzzzzzz` with `x` being the header, `y` containing the information and `z` being a validation signature.

#### The Header

The header is a JSON object containing two pieces of important information:

1. The type of token
2. The algorithm used for the signature

```
{
	"alg": "HS256",
	"typ": "JWT"
}
```

#### The Payload

The payload include all the information we want to transfer.

```
{
	"email": "admin@mail.com",
	"exp": 158371382, // Expiration time
	"iat": 23983201  // Issued at time
}
```

#### The Signature

The signature is a secret key used to encode the token. The header and payload are put through a hashing algorithm encoded with the secret key. This allows us to ensure and verify that the token is genuine and valid.

### Using the Token

So how do we use our token? Before we can use the token we first need to obtain it. We can do this by sending a POST request to our API with a body containing our login information. This will return an authorization token which we can then use.

```js
const bearer;

fetch("https://jsonplaceholder.typicode.com/users/login", {
	method: "POST",
	headers: {
		"Content-Type": "application/json",
	},
	body: JSON.stringify({
		email,
		password,
	})
}).then(res => res.json()).then(data => bearer = data.token);
```

We can now use it by passing it through the 'Authorization' header as such:

```
{
 header:
	 Authorization: Bearer <token>
}
```

We can use this header as an additional parameter inside of our fetch request in Javascript like:

```javascript
fetch("https://jsonplaceholder.typicode.com/api/premium", {
	method: "GET",
	headers: {
		Authorization: `Bearer ${bearer}`
	}
}).then(res => res.json()).then(data => /*do something */ )
```

<br />

<h2 id="week8">Week 8: Express Middleware</h2>

### Middleware

Middleware functions are special functions which have access to:

- The request object - `req`
- The response object - `res`
- The next middleware function in the cycle - `next`

The `next` function passes control to the next middleware. If we don't want to continue the chain we simply don't call `next()` at the end of our middleware function.

Middleware functions can be passed in through a couple different methods:

- The middleware function itself
- A series of middleware functions separated by a comma
- An array of middleware functions

```js
const express = require("express");
const app = express();
const port = 3000;

const logOriginalUrl = (req, res, next) => {
  console.log(`Request URL: ${req.originalUrl}`);
  next();
};

const logMethod = (req, res, next) => {
  console.log(`Request Type: ${req.method}`);
  next();
};

const middlewareFunctions = [logOriginalUrl, logMethod];

app.get("/user/:id", middlewareFunctions, (req, res, next) => {
  res.send(`User: ${req.params.id}`);
});

app.listen(port, () => {
  console.log(`Example app listening on port: ${port}`);
});
```

### Knex

Knex is a SQL query builder for node and express. It helps to manage connectivity and connection pooling. Whenever we initialise a new app we need to create/edit the `knexfile.js` to include all the needed and required information for our database.

```js
module.exports = {
  client: "mysql",
  connection: {
    host: "127.0.0.1",
    database: "myScheme",
    user: "root",
    password: "",
  },
};
```

```js
router.get("/api/city", (req, res, next) => {
  req.db
    .from("city")
    .select("name", "district")
    .then((rows) => {
      res.json({ Error: false, Message: "Success", City: rows });
    })
    .catch((err) => {
      console.log(err);
      res.json({ Error: true, Message: "Error in MySQL query" });
    });
});
```

### Helmet

Helmet is a collection of security middlewares that sets headers and allows us to avoid some common vulnerabilities,

```js
const express = require("express");
const helmet = require("helmet");

const app = express();

app.use(helmet());
```

### Asynchronous Calls in Node

In the first example the `console.log()` will be called before `moreWork()` and the program will block and stop until our `readFileSync()` code has finished executing. In the second example however we run `readFile()` asynchronously therefore no longer blocking our program. It's because of this `moreWork()` will typically be called first before our `console.log()`.

```js
const fs = require("fs");
const data = fs.readFileSync("/file.md"); // Program will block here until the file is read
console.log(data); // This line then gets called first
moreWork(); // Then this line
```

```js
const fs = require("fs");
fs.readFile("/file.md", (err, data) => {
  if (err) throw err;
  console.log(data);
});
moreWork(); // This will now typically run first as it's no longer being blocked
```

<br />

<h2 id="week9">Week 9: Security</h2>

### What is Security?

Security, and in particular IT security, is the practice of protecting a wide collection of systems, networks, and programs from attackers and bad actors.

### Open Security Standards

Open security standards are global security standards published by security organisations.

### Internet Engineering Taskforce (IETF)

### Open Web Application Security Project (OWASP)

The top 10 threats presented by OWASP are:

#### 1 - Injection

Injection is the process of "injecting" malicious code into some system. There are many different injection attacks all "injecting" through different forms of medium such as SQL, LDAP, XPath, NoSQL queries, OS commands, XLM parsers, SMTP headers, Expression languages, ORM queries, any many many more.

#### 2 - Broken Authentication

There are many many ways that an authentication system could be broken:

- If the application does not account for credential stuffing then attackers can take huge lists of exposed login details from data breaches and attempt a login of every exposed account hoping for a match.
- Application session timeouts can be a major problem if they aren't set to the right amount of time. If a user logs into some account on a public computer and, instead o flogging out, just closes the browser if the session timeout is too long an attacker can use the same browser an hour later and have the user still be authenticated.

#### 3 - Sensitive Data Exposure

Sensitive data exposure occurs when companies storing sensitive data don't take the proper precautions to encrypt and hide that sensitive data.

#### 4 - XML External Entities (XXE)

An attacker is able to exploit vulnerable XML processors by uploading an XML document containing malicious code. Many of the older XML processors allow specification of an external entity, a URI that is dereferenced and evaluated during XML processing.

#### 5 - Broken Access Control

Exploitation of access control by an attacker can have massive impacts on a company and the data they store. By actors gaining access to accounts with high privileges they may be able to access many confidential files and information as well as possibly being able to manipulate and delete data.

#### 6 - Security Misconfiguration

An unpatched flaw, outdated software, default accounts, unprotected files, unused pages. All things that, if configured incorrectly, can lead to unauthorized access by an attacker resulting in information and system compromises. Security misconfiguration can happen at any level of the application stack so it's important to make sure all parts are secure and up-to-date.

#### 7 - Cross-Site Scripting (XSS)

#### 8. Insecure Deserialization

The impact of a deserialization exploit can lead to the attackers being able to remotely execute malicious code.

#### 9. Using Components with Known Vulnerabilites

While it's easy to just find a useful component off the internet and use it in our applications we need to take in account that components security. A single out-of-date component with the wrong permissions can bring our whole application down. It's important to always check what you're installing and make sure all used libraries are up to date.

#### 10 - Insufficient Logging and Tracking

Companies not sufficiently tracking or logging often can be their downfall. Attackers rely on this lack of monitoring and inability to respond to an attack in a timely manner.

### Internet Security Research Group (ISRG)

### Transport Layer Security (TLS)

TLS is a security protocol designed specifically to provide privacy and secure data communications over some network. A major use-case of TLS is its use in encrypting communications between web applications and servers. TLS was built upon SSL and was originally named SSL 1.3 before TLS 1.0 but was changed before publication due to it's disassociation with Netscape.

HTTPS is an implementation of TLS on top of the HTTP protocol. There are three main components of TLS: encryption, authentication and integrity. In the terms of secure data transfer the main point of encryption is to hide the data in transit from third parties. Authentication ensures that the parties in the data transaction are who they claim to be. Finally, integrity verifies that the data that has been sent has not been edited, tampered or altered in any way or form by a third party (or even from data loss during transfer).

For a website to be considered safe and have a HTTPS encryption it must first have an SSL/TSL certificate. This certificate contains information about the websites public key, domain name, certificate issuers digital signature, and more. SSL/TSL certificates are used for authenticating an origin servers identity.

These certificates are issued by trusted third-party certificate authorities (CA). The CA will generate and sign a certificate with their private key and issue it out for it to be installed on the websites origin server. These certificates can also be self-signed meaning technically anyone can generate and create an SSL certificate by generating a public-private key pairing and including all relevant information. Self-signed certificates however are not considered trustworthy by browsers and will still mark the site as not being secure even though there does exist a HTTPS connection.

### NPM Audit

Audit is a built in NPM command that will tell you if any packages in use have any know dependencies.

### HTTPS with Express

Making Express use HTTPS is as simple as passing in the certificate files when starting the server.

```js
const fs = require("fs");
const https = require("https");
const privateKey = fs.readFileSync("sslcert/server.key", "utf8");
const certificate = fs.readFileSync("sslcert/server.crt", "utf8");

const credentials = { key: privateKey, cert: certificate };
const express = require("express");
const app = express();

// Express configuration goes here

const server = https.createServer(credentials, app);
server.listen(443);
```

### Security Middlewares

Helmet is an extremely configurable security middleware that, out of the box, enforces some security basics.

```js
const express = require("express");
const helmet = require("helmet");

const app = express();

app.use(helmet());
```

### Logging and Log Rotation

Logging is a complicated task and a painful one at that. Although painful however logging is an extremely important task as to finding out general information about our routes as well as any errors or warnings that may come up. Morgan is a tool that helps us create logs quick and easy without any of the fuss. Morgan collects logs from the servers and makes them easy for us to read.

```js
var express = require("express");
var morgon = require("morgan");
var path = require("path");
var rfs = require("rotating-file-stream");

var app = express();

// Create a rotating write stream
var accessLogStream = rfs("access.log", {
  interval: "1d", // Rotate daily
  path: path.join(__dirname, "log"),
});

// Setup the logger
app.use(morgan("combined", { stream: accessLogStream }));

app.get("/", function (req, res) {
  res.send("Hello world!");
});
```

### Password Hashing

Password hashing is an absolute must no matter how small or large your application is. Bcrypt is the current industry standard for password hashing however this will most likely slowly change overtime as more research and technologies come out.

```js
const queryUsers = req.db.from("users").select("*").where("email", "=", email);

queryUsers
  .then((users) => {
    if (users.length > 0) {
      console.log("User already exists");
      return;
    }

    // Insert user into the DB
    const saltRounds = 10;
    const hash = bcrypt.hashSync(password, saltRounds);
    return req.db.from("users").insert({ email, hash });
  })
  .then(() => {
    console.log("Successfully inserted user");
  });
```

### HTTP Cookies

Cookies are small chunks of data that are sent from the server to the users browser. These packets of data hold state information during an HTTP(S) session. Cookies have been slowly replaced by the Web Storage API.

### Web Storage API

Web Storage API provides two mechanisms with a common interface for storing information in the browser. Both of these entities are based around a <key, value> storage type.

1. sessionStorage - Session storage stores the data so long as the page is open. Everything in that storage is cleared upon the browser/tab is closed.
2. localStorage - Local storage stores the data for as long as we want and only clears things via JS calls or browser operations.

<br />

<h2 id="week10">Week 10: Deployment</h2>

### NGNIX Web Server

NGINX is a free, open-source HTTP web server. Throughout this unit we will be using NGINX as a reverse proxy.

```
http {
	upstream myproject {
		server 127.0.0.1:8000 weight=3;
		server 127.0.0.1:8001;
		server 127.0.0.1:8002;
		server 127.0.0.1:8003;
	}

	server {
		listen: 80;
		server_name www.domain.com;
		location / {
			proxy_pass http://myproject;
		}
	}
}
```

### Proxy Servers

A proxy server is a router that handles requests and response traffic. The proxy server will intercept any request that comes through and forward it to a relevant server that will handle it and send a response. The proxy server can also forward a response to the client. A forward proxy sits on the client side while the reverse proxy sits on the server side.

Proxies are typically used for content filtering. They can be used to restrict certain users from accessing certain content and can be used to provide anonymity to users if setup as such.

We can use a reverse proxy for:

- TLS/SSL encryption
- Load balancing
- Caching of response content
- Compression of content
- Security

### PM2

PM2 is a process manager for node applications. We install it first by running `sudo npm install pm2@latest -g`.

<br />

<h2 id="week11">Week 11: Asynchronous JS</h2>

### Callback Style

We've looked at callbacks before but let's take a quick look at them again to refresh our mind. We use a callback when to want to allow a function to respond when something is complete. We invoke this function with an error object and, if required, the result.

```js
doRequest("https://google.com", (error, result) => {
  if (error != null) {
    // by convention, error will be null if no error occurs
    handleError();
    return;
  }

  handleResult(result);
});
```

### A Quick Refresh of Promises

If we remember back we said a Promise is a promise that some value will be there in the future. This allows us to use data as if it was there even though it isn't. A Promise can be in one of three states at any given point:

1. 'pending' - This is the state that occurs before the Promise has resolved
2. 'fulfilled' - This is the state that occurs once the Promise has resolved successfully
3. 'rejected' - This is the state that occurs if the Promise runs into any errors upon executing

A Promise enforces a standard of how we control the flow. We use `.then()` to chain on some flow of control successfully running if there occurs no errors. We can then use `.catch()` to catch any errors that may occur and conditionally run something else.

```js
doRequest("https://google.com")
  .then((result) => {
    // Do something with the result
  })
  .catch((error) => {
    // If an error occurs, catch it here and do something with it
    // This function is only invoked if the promise holds the state of 'rejected'
  });
```

### Misusing Promises

There are a few ways we can misuse a promise. One of the common misuses occurs when we place the `.catch()` before any of the `.then()` conditionals. Doing as such can cause unexpected behaviour as errors in the promise are handled in the first catch block this leaves the subsequent `.then()` chains not knowing that there were any errors. This causes the rest of the chain to activate and run as if nothing ever happened.

Another common misuse occurs when we try to mix variables from inside and outside the scope of promises. A good rule of thumb is, values outside of a promise can be used inside a promise but they should never be changed or mutated. Values inside of a promise should never be leaked outside.

Once you are inside of a promise chain you are not able to leave. All the code that's needed to run after the promise must be chained and completed inside of a `.then()` conditional.

```js
// don't do this

let requestResult = null;

doRequest("https://google.com").then((result) => {
  requestResult = result;
});

console.log(requestResult); // null
```

```js
// do this

doRequest("https://google.com").then((result) => {
  console.log(result); // the result
});
```

Another common misuse occurs when we try to nest promises inside of other promises. If a promise is returned from inside of a `.then()` or `.catch()` then the subsequent `.then()` will not run until the internal/nested promise has resolved. Unfortunately there are some cases where this is unavoidable. You should always try to just return the promise instead of calling `.then()` on an inner/nested promise.

```js
const x = doRequest("https://google.com");
console.log(x); // Promise<{ pending }>

x.then((result) => {
  console.log(result); // the result of doRequest('https://google.com');
  return doRequest("https://facebook.com");
}).then((result) => {
  // note that we don't get back the prmoise returned above (i.e google.com)
  console.log(result); // the result of doRequest('https://facebook.com');
});
```

It's important to remember that a promise is static. Once it is created you cannot change its value. We can wrap a function around a promise, return it and then we're able to chain execution onto that wrapper function to execute more code.

```js
// This is our wrapper function
const makeRequest = (url) => {
  doRequest(url)
    .then((result) => {
      return { statusCode: 200, body: result };
    })
    .catch((error) => {
      // this is a fictional property - you would need
      // to decide how this was determined
      if (error.fromServer) {
        return { statusCode: 500, error: error };
      }

      throw error;
    });
};
```

```js
// We can then chain execution onto this wrapper function
makeRequest("https://google.com").then((result) => {
  if (result.statusCode === 500) {
    console.log(`There was an error: ${result.error}`);
  } else {
    console.log(`Request was good: ${result.body}`);
  }
});
```

### Creating a Promise

We can create promises using the `Promise` object. We then need to pass in a `resolve` and `reject` parameter which will handle the different states of our promise. If our code is successful we call `resolve` otherwise `reject`.

```js
new Promise((resolve, reject) => {
  // do something asynchronous here
  if (error) {
    // if something went wrong during the above async code
    reject(error);
  } else {
    // assuming 'result' has the data we want
    resolve(result);
  }
});
```

Here is an example of using a Promise when reading data from a file. We first define our function which wraps our Promise.

```js
const fs = require("fs");

const readFileAsync = (filePath) => {
  return new Promise((resolve, reject) => {
    fs.readFile(filePath, "utf8", (err, res) => {
      if (err != null) {
        reject(err);
      } else {
        resolve(res);
      }
    });
  });
};
```

Then we can use it as such

```js
readFileAsync("~/Documents/some-file.txt")
  .then((result) => {
    // print the file data
    console.log(result);
  })
  .catch((err) => {
    // error could be caused by missing file or
    // some other interal issue
    console.log(err);
  });
```

### Async/Await

Async/Await is a relatively new syntax for Javascript and is used as an alternative to promises. In this syntax we put the keyword `async` before the `function` keyword such that:

```js
async function makeRequest() {}
// or
const makeRequest = async () => {};
```

The `await` keyword is only used inside of an `async` function and is put in front of promise values only. When our interpretor reaches an `await` keyword it suspends execution until the promise has resolved. Here is an full example of a request using Async/Await:

```js
async function makeRequest(url) {
  try {
    const result = await doRequest(url);
    return { statusCode: 200, body: result };
  } catch (e) {
    if (e.fromServer) {
      return { statusCode: 500, error: 3 };
    }

    throw e;
  }
}
```

It's important to note that Async/Await and Promises achieve the same thing through different syntactical means. Below is an example of how these two syntaxes compare:

```js
const result = await doRequest(url);
console.log(result);

// is the same as

doRequest(url).then((result) => {
  console.log(result);
});
```

### Promise.all

`Promise.all` is a utility provided to us that takes in an array of promises and returns a new promise that only resolves when all the promises in the array have resolved. If any of the promises fail and reject then you drop straight to the catch block bypassing the remaining promises. If your code relies on multiple promises that don't depend on each other for data, then it is much more efficient to combine and group them into a `Promise.all`. To put this into context, instead of doing this:

```js
doRequest("https://google.com").then((googleRes) => {
  doRequest("https://facebook.com")
    .then((facebookRes) => {
      // you have both promises and have both results here
    })
    .catch((e) => {
      // either of the promises have failed
    });
});
```

We can do:

```js
Promise.all([
  doRequest("https://google.com"),
  doRequest("https://facebook.com"),
])
  .then(([googleRes, facebookRes]) => {
    // we have results for both of the promises
  })
  .catch((e) => {
    // either of the promises have failed
    // you can't access any results if any promise fails
  });
```
