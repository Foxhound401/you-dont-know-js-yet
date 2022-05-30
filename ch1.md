## Jumping the gaps

For new and incompatible syntax, the solution is transpiling. Transpiling is a contrived and community-invented term to describe using a tool to convert the source code of a program from one form to another ( but still as textual source code ). Typically, forwards-compatibility problems related to syntax are solve by ysing a transpiler ( the most common one being Babel to convert from that newer JS syntax version to an equivalent older syntax).

For example, a developer may write a snippet of code like:

```javascript
if (something) {
  let x = 3;
  console.log(x);
} else {
  let x = 4;
  console.log(x);
}
```

This is how the code would look in the source code tree for that application. But when producing the file(s) to deploy to the public website, the Babel transpiler might convert that code to look like this:

```javascript
var x$0, x$1;
if (something) {
  x$0 = 3;
  console.log(x$0);
} else {
  x$1 = 4;
  console.log(x$1);
}
```

The original snippet relied on `let` to create block-scoped `x` variables in both the `if` and `else` clauses which did not interfere with each other. An equivalent program (with minimal re-working) that Babel can produce just chooses to name two different variables with unique names, producing the same non-interference outcome.
