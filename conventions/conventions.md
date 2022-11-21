# Coding Conventions

- They are style guideline for programming and typically cover naming and declaration rules of variables and functions. Rules for the use of whitespace and indentation, prgramming practices.
- Secure quality, keep code clean a readable.
- Could be documented rules for team to follow.

## Variable Naming

- Use Camel case `getUserCredentials`.
  - This makes variable and function names easier to read.
- Use Meaningful names.
  `const a = 365` vs `const DAYS_IN_A_YEAR=365`

- Begin Booleans with `is` or `should`. for instance:
  use `isOld` not `old`.

- Use nouns for class names. `class Car` not `class MakeCar`
- Use pascal case for class names.
- Capitalize Constant values `const PI`
- Avoid One letter variables unless your dealing with something like a `for` loop.

## Function Naming

- Be concise but favour descriptive names over concise names `findUser` or `findUserByEmailAndPassword`.
- Use Consistent verbs per concept (functions will usually create , read,update or delete).

```js
returnUsers;
retrieveUsers;
```

- always start with verbs

```js
// an article returning an article
//bad
const article = () => {};
const articleSelected = () => {};
// Good
// function that checks if an article is selected and return boolean👇🏿
const isArticleSelected = () => {};
// Function that gets article.
const getArticle = () => {};
//    verb
const normalizeUser = () => {};
```

- Try to make your variables and functions less generic.

```js
// create an article object
// Bad
const data = { title: "some title" };
// Generic but good
const article = { title: "some title" };
const isLoading = true;
const url = "http://google.com";
//  best
const isArticleLoading = true;
const deleteArticleUrl = "http://google.com";
```

## Magic Numbers

- This a random varible or hack to solve something.
- Example

  - in the example below `50` is a magic number.

  ```js
  element.addEventListener("blur", (event) => {
    const height = event.target.height + 50;
  });
  ```

  - To solve this move the `50` to a variable that can be understood.
    ```js
    element.addEventListener("blur", (event) => {
      const padding = 25;
      const heightWithPaddings = event.target.height + padding * 2;
    });
    ```

  ```

  ```

```js
for (let i = 0; i < 86400; i += 0) {
  //...
}
```

- Instead use

```js
const SECONDS_IN_A_DAY = 86400;

for (let i = 0; i < SECONDS_IN_A_DAY; i += 0) {
  //...
}
```

## Comments

- Sign that your quote is not self expanatory.
- Code should be self documented.
  ![comments](/cleanJs/Images/comments.jpg)
- Every one has there own view on how to use comments.
- If you have a comment to describe your code then you probably have bad variable names.

```js
//Bad
// We are mapping through users to get their names
```

- 👆🏿 This is bad beacuse its explaining exactly what the code is doing.
- Probably use them if the code has some very complicated logic 👇🏿.

```js
//Good
// Don't return `set.add` because its not chainable in Internet Explorer 11.
```

## Deep Nesting

- If your code contains a lot of nested loops delegate it into a function.

```js
cosnt exampleArray = [[['value']]];

exampleArray.forEach(element => {
    array1.forEach(element => {
        array3.forEach(element => {
            console.log(element);
        })
    })
});
```

### Problems

- Deep nesting
- Code Repeatition

### Solution

- create a function to loop through all arrays and return a value.

```js
const retrieveFinalValue = (element) => {
  //  Check if element is array
  if (Array.isArray(element)) {
    // inner array
    return retrieveFinalValue(element[0]);
  }

  return element;
};
```

## Avoid Large/Long functions

- Functions should not do more than they should.

```js
const addMultiplySubtract = (a, b, c) => {
  // addition
  // multiply
  //subtract
  // return (addition,subtration,multiplcation)
};
```

- **Soln** - Create different functions to separate the logic

```js
const add = (a, b, c) => a + b + c;
const multiply = (a, b, c) => a * b * c;
const subtract = (a, b, c) => a - b - c;
```

## DRY - Dont Repeat Yourself

- Its better to extract reapeated code to its own function.
- For instance, the array example [above](#deep-nesting).
- levearage destructing in terms or objects

## Sticking To Code Style.

- Try linters like `eslint` or even use coding styles by big companies like `airbnb`.

## Short Code vs Long Code.

- [Watch this](https://youtu.be/tiolFUyXIEo)
- [And This](https://www.freecodecamp.org/news/long-code-vs-short-code/)
