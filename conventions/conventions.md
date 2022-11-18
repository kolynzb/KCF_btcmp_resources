# Coding Conventions

- They are style guideline for programming and typically cover naming and declaration rules of variables and functions. Rules for the use of whitespace and indentation, prgramming practices.
- Secure quality, keep code clean a readable.
- Could be documented rules for team to follow.

## Variable Naming
- Use Camel case `getUserCredentials`.
- Use Meaningful names.
- Be concise but favour descriptive names over concise names `findUser` or `findUserByEmailAndPassword`.
- Use Consistent verbs per concept (functions will usually create , read,update or delete).
```js
returnUsers
retrieveUsers
```
- Make Boolean read well in control structures. for instance:
use `isOld` not `old`

- Use nouns for class names. `class Car` not `class MakeCar`
- Use pascal case for class names.
- Capitalize Constant values `const PI`
- Avoid One letter variables
## Magic Numbers

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

## Deep Nesting

- If your code contains a lot of nested loops delgate it into a function.

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

## Problems

- Deep nesting
- Code Repeatition

## Solution

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

## Stop Writing Comments

- Sign that your quote is not self expanatory.
- Code should be self documented.
  ![comments](/cleanJs/Images/comments.jpg)

## Avoid Large functions

- Functions should not do more than they should.

```js
const addMultiplySubtract = (a, b, c) => {
  // addition
  // multiply
  //subtract
  // return (addition,subtration,multiplcation)
};
```

- __Soln__ - Create different functions to separate the logic 

```js
const add = (a, b, c) => a + b + c;
const multiply = (a, b, c) => a * b * c;
const subtract = (a, b, c) => a - b - c;
```

## DRY - Dont Repeat Yourself
- Its better to extract reapeated code to its own function.
- For instance, the array example [above](#deep-nesting).
- levearage destructing in terms or objects