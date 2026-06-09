# Javascript

## Rules
- never use single letter variable names, EXCEPT in for() loops, for example `for(i=0; i < 5; i++)`
- always use descriptive names for variables and functions
- don't use `var` due to scoping concernts, prefer `const` and `let`


```javascript
// GOOD - descriptive names

const product = {};
let counter = 0;

function updateCounter() {}

// BAD - single letter or vague naming

var c=0;

function uc(){};

```
