# The `this` keyword in JavaScript

## Instructions

At a high level, this week is about building an effective process for learning unfamiliar language features and patterns.  In this workshop, you'll practice using this process to understand how the `this` keyword works in JavaScript.

### Learning objectives

1. Describe the `this` keyword as similar to `self` in Ruby.
2. Explain some of the similarities and differences between the behaviour of the `this` keyword and the behaviour of `self` in Ruby.
3. Explain the rules that govern the value of the `this` keyword.

### Getting visibility

A great way to understand code is to first tighten the loop, then get visibility.  In this workshop, we'll practice getting visibility.  As you go through the workshop, try using `console.log()` to inspect the values of:

* `this`
* Variables
* Parameters
* Function return values

### Questions (30 mins)

* Pair up.

* Clone this repo.

* Open the `index.html` file in your web browser.

* Open the browser console.

* You should see `hello!`.

* Open `index.js` in your text editor.

* Paste the code for question 1 (below) into `index.js`.

* Play around with the code using the techniques for getting visibility. Answer the questions that are in comments.

* Discuss your answers with your pair partner.

* Swap driver and navigator.  Continue with the next question.

### Plenary (15 mins)

We'll come back together for a short plenary to discuss our answers to the questions.

## Questions

Note: the code in many of these questions is not realisitic or idiomatic JavaScript.  It's just for illustrating clear examples of the behaviour of the `this` keyword.

### Question 1

```js
function Person() {
  // What is the value of `this` at this point in the program?
  // What other variable in the program has the same value?
};

var person = new Person();
```

### Question 2

```js
function Person() {
  // What is the value of `this` at this point in the program? Why?
};

// In this version, the programmer has forgotten to put `new` before
// `Person()`
var person = Person();
```

### Pause

Questions 1 and 2 start to explore the effects of the `new` keyword.  But they are only a starting point.  Many things remain a mystery.  Like, what value does `person` get assigned in question 2? Later questions in this workshop will prompt you to explore some of these mysteries.  But many mysteries will remain.

After you complete each question, ask yourself, "What could I change about the code to more fully explore the behaviour I'm seeing?" Make the change to the code, form a hypothesis about what the effect will be, then run the code to see if you're right.  Repeat the process.

### Question 3

```js
function Person() {
  this.count = 5;

  // On what object is the `count` property now stored?
};

// Oh no! Accidentally left out `new` AGAIN!
Person();

// Bonus question: on what object is the `Person` function
// stored?
```

### Question 4

```js
function Person() {
  this.name = "Mary";
};

Person.prototype = {
  exclaimName: function() {
    // What is the value of `this` the first time `exclaimName` is run?
    // What about the second time?
    // Research project: Why?

    return this.name + "!";
  }
};

var person = new Person();
console.log(person.exclaimName());

var exclaimName = person.exclaimName;
console.log(exclaimName());
```

### Question 5

```js
function Person() {
  this.name = "Mary";
};

function exclaimName() {
  // What is the value of `this` the first time `exclaimName` is run?
  // What about the second time?
  // Research project: Why?

  return this.name + "!";
};

console.log(exclaimName());

var person = new Person();
person.exclaimName = exclaimName;
console.log(person.exclaimName());
```

### Question 6

```js
// What value does `this` have here?
this;
```

### Question 7

```js
function exclaimName() {
  // What is the value of `this` the first time `exclaimName` is run?
  // What about the second time?
  // What about the third time?
  // Research project: what's the difference between call and apply?

  return this.name + "!";
};

console.log(exclaimName());

var exclaimMary = exclaimName.call({ name: "Mary" });
console.log(exclaimMary);

var exclaimIsla = exclaimName.apply({ name: "Isla" });
console.log(exclaimIsla);
```

### Question 8

Can you list the rules that govern the value of `this`?

## Resources

* [Understand JavaScript's this with clarity](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)
* More examples of the `this` keyword in JavaScript in the [Count project repo](https://github.com/maryrosecook/count)
