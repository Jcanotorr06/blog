---
author: Joseph Cano
datetime: 2022-09-29T20:23:35Z
title: Stop Using The "!" Bang Operator In JavaScript
slug: "stop-using-bang-operator"
featured: true
draft: false
tags:
  - javascript
  - advice
ogImage: ""
description:
  You may think you are writing cleaner code using the bang operator, but in reality you are just opening yourself up to a plethora of bugs.
---

One of the more common questions you'll find in online formus is why write `user == null` instead of `!user`. Most people will look at these two pieces of code and assume they do the same thing, so they go with the shorter option, but there are actually massive differences between these two. These differences are why I always write out the full `user == null` code to prevent myself from running into common issues related to `!user`.

## Table of contents

## How Does The "!" Bang Operator Work

In its simplest form the bang operator just negates whatever you pass after it.

```js
!true // false
!false // true
```

The operator gets a bit more complex when you deal with values that are not already booleans, though. In order to properly work the bang operator must first convert whatever value it is used on to a boolean which sometimes has unintended consequences.

Let's assume we are checking to see if our user object exists. We know that the user can either be `null`, `undefined`, or a full user object. In this scenario !user and `user == null` will work exactly the same.

```js
!null // true
!undefined // true
!{ name: "Kyle" } // false

null == null // true
undefined == null // true
{ name: "Kyle" } == null // false
```

## Why The Bang Operator Can Be Bad

What happens if we are checking user input for a number, though. We know the values can either be `null`, `undefined`, or a number. In this scenario `!number` and `number == null` will act exactly the same, **except** for the number 0.

```js
!0 // true
!1 // false

0 == null // false
1 == null // false
```

The reason for this discrepancy is because the bang operator needs to convert the number to a boolean in order to negate the boolean and the number 0 is considered false when converting to a boolean. This can easily lead to bugs in your program that are difficult to catch.

```js
const numberOfChildren = getUserInput()
if (!numberOfChildren) {
  alert("You need to enter a value for number of children")
} else {
  submitForm()
}
```

In this example it is impossible for the user submit the form with a value of 0 children even though the intent with this check is to just ensure the user entered a value for children and not to exclude users with 0 children.

This is not only an issue with the number 0, though. `NaN` and empty strings, `""`, also evaluate to false when converted to a boolean which means you could get unintended results when using the bang operator if all you wanted to check was if the value was null or undefined.

This type of conversion between types is called implicit type coercion and is something I almost always try to avoid in JavaScript since it leads to many potential bugs. This is also why I almost always use triple equals, `===`, instead of double equals, `==`, since triple equals never does type coercion.

## Conclusion

While the bang operator may seem like a great tool for writing less code, I personally find that it leads to more bugs than it is worth which is why I almost never use the bang operator in my code.
