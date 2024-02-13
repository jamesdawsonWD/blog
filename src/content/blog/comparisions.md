---
title: "The difference between == and === in javascript"
description: "Understanding the difference ."
pubDate: "Feb 13 2024"
heroImage: "/blog-comparisions.png"
---

In JavaScript, comparing values can be done in two primary ways: using strict equality (`===`) and loose equality (`==`). These operators may seem similar at first glance, but they behave quite differently and can leaving you scratching your head if you don\'t know what is going on.

## Strict Equality (`===`)

Strict equality checks if the values on either side **are of the same type and equal in value**. That is it, nice and simple and should be your go to comparision tool. Let's check out some basic examples

#### Examples:

```javascript
3 === 3 
// True, because both the type (number) and value (3) match.

3 === '3' 
// False, because the types differ (number vs. string).

true === true 
// True, because both the type (boolean) and value (true) match.

null === null 
// True, because both the type and value match (null is a singular value of the type null).

[] === [];
// False, because even though both sides are arrays, they are different instances in memory.
```

## Loose Equality (`==`)

Loose equality checks if the values on either side **can be considered equal after type coercion**. This means JavaScript will try to convert the values to a common type before making the comparison. While this can be useful, it can also lead to some almost laughable comparisions.

#### Examples:

```javascript
0 == false 
// True, because `0` is considered falsy, similar to `false`.

2 == '2' 
// True, because the string `'2'` is coerced to the number `2`.

null == undefined 
// True, because `null` and `undefined` are treated as equal in the context of loose equality.

[] == '' 
// True, because an empty array coerces to an empty string.

[1,2] == '1,2'; 
// True, because the array is coerced to a string, matching the right-hand side.
```

## Notable Gotchas

Understanding the nuances of JavaScript's equality operators can help avoid common pitfalls. Here are a few examples that illustrate these "gotchas":

```javascript
// Two distinct arrays are separate instances in memory. This makes sense.
[] === [] 

// NaN is the only JavaScript value not equal to itself. Something that is not a number does not equal something else that is not a number. OK...
NaN === NaN 

// JavaScript considers positive and negative zero to be strictly equal. Logical.
0 === -0 

// Coercing an array into a string is just so crazy...
[1,2] != "1,2" 

// Even under loose equality, NaN is not considered equal to the string representation of itself. Poor NaN.
NaN == "NaN" 

// A non-empty string is truthy, but it does not coerce to the boolean false under loose equality.
"false" == false
```

## Conclusion

Use `'==='`.
