---
author: Joseph Cano
datetime: 2022-10-12T22:05:15Z
title: How to write better code
slug: "how-to-write-better-code"
featured: true
draft: false
tags:
  - advice
  - coding
  - programming
  - best practices
ogImage: ""
description:
  "15 simple, yet effective tips to produce better software"
---

I've been professionally building software for little over a year now. In this short amount of time, I've written a lot of code. I have also read a lot of code. My own code, and code from other people. Code that's terribly bad and code that's a real joy to work with. Turns out that good code mostly has the same characteristics. It's easy to read, it's easy to understand, it's easy to maintain and extend. It's as complex as necessary, but as simple as possible. In this post, I'm trying to describe what great code means (to me).

<hr/>

## Table of Contents

## 1. Understand the basics

Let's start with something obvious (but really important). No matter what you do in life, you need to understand the foundations. This is especially true for programming. I know there are people out there copying code from StackOverflow, pasting it into their editor and then wondering why stuff doesn't work. This doesn't make any sense. If you don't fundamentally understand what you're doing, you're gonna have a bad time. Learn how data types, algorithms and data structures work. Get your hands on different types and kinds of programming languages. Make sure to know your tools before jumping into something bigger.

## 2. Think before you write

As you mature as a software engineer, you probably notice that you tend to spend more time thinking about a problem and its solution than actually sitting down and writing code. That's because ***coding is thinking***. If you think about your problem first and have a solution in mind already, the actual coding part becomes easy. I often like to say that programming languages are a tool. They look different, they work different, they have their strengths and weaknesses. But if you master logical thinking and problem solving, you can use any programming language with a bit of experience.

## 3. Be consistent

I'd argue that consistency is one of the most important factors when writing software. If you follow the same rules across your entire codebase, it's a lot easier for other people to read, follow, and understand your code. Your code becomes more readable, understandable and maintainable. It's also easier for yourself (if you're working on a project alone). Keep your code clean, keep it simple, keep it consistent.

This applies to:

- File naming
- Indentation
- Variable naming
- Function naming
- Using single/double quotes
- etc

### ❌ Bad

```js
// Different file name styles
// Not all parameters with explicit type
// Odd indentations
// Unnecessary whitespaces
// Mix of single and double quotes
// Different variable naming style
// Different function naming style

// users-Service.ts
const sendEmail = async (mailSubject, body: string) => {
  const mailClient = new EmailClient()

    const response = await   emailClient.sendEmail(mailSubject, body)

  return response.status
}

// orders.ts
let stat = await sendEmail("Thank you for your order",
    'Your package is on the way.')
```

### ✅ Good

```js
// users.ts
const sendEmail = async (subject: string, body: string) => {
  const emailClient = new EmailClient()
  const response = await emailClient.sendEmail(subject, body)

  return response.status
}

// orders.ts
const status = await sendEmail('Thank you for your order', 'Your package is on the way.')

```

## Separate concerns

You should always advocate for code that has as little side effects and dependencies as possible. Concerns should be clearly separated, certain pieces of code should do one thing and do one thing well. For example, if you're working on a database service, avoid accessing the application state for accessing the current user ID. Instead, add a parameter that lets callers pass this information themselves. That way, consumers clearly understand which parameters are required in order to call a function. Also, the program doesn't depend on other parts of the software and behaves the same, no matter the state.

### ❌ Bad

```js
// orders.ts
import { store } from 'state'

const getUserOrders = () => {
  // Database call is depending on the shared application state
  // It's hard for consumers to understand this
  // It can have unpleasant side effects and makes it hard to discover problems
  return orders.filter(o => o.userId === store.userId)
}
```

### ✅ Good

```js
// orders.ts
const getUserOrders = (userId: string) => {
  // User ID is passed as parameters
  // The function is more "pure" and doesn't depend on other components/state
  return orders.filter(o => o.userId === userId)
}
```

## 5. Don't use magic numbers

Magic numbers and strings are bad. They are mostly inline variables that are used for a specific purpose that isn't immediately clear when looking at the code, which makes the code complicated to read and understand. Instead of throwing in a "magic number", extract a variable with a name that clearly indicates the purpose.

### ❌ Bad

```js
if (users.length >= 100) {
  // Which limit? What does 100 mean?
  console.log('Limit reached')
  return
}
```

### ✅ Good

```js
// Add separate variable that clearly indicates what "100" stands for
const earlyAccessUserLimit = 100

if (users.length >= earlyAccessUserLimit) {
  console.log('Early access user limit reached')
  return
}
```

## 6. Don't reinvent the wheel

Programming is fun. As engineers, we tend to want to write our own solutions for almost everything, because we love solving problems. It doesn't always make sense though. Try to leverage other frameworks, tools and services and focus on solving your own problem. There is so much great software out there you can use – mostly even free of charge. Go use it! Every line of code you don't write, you don't have to maintain.

## 7. Use fewer dependencies

Conversely, don't pull in a package or use another provider for everything. If there is a very simple solution to your problem, don't add too much overhead by adding an external dependency. There are literally npm packages that provide one single function. Don't overuse packages. Know when it makes sense to use a third-party service or package instead of writing your own code.

## 8. Use self-explanatory names

As already mentioned in "Be consistent", it's crucial to use self-explanatory, simple names across your entire codebase. Don't use unnecessary abbreviations. Don't use arbitrary names. Good code reads like a book. It's easy to understand, it's easy to maintain, it's a joy to work with.

This applies to:

- Files
- Functions
- Variables
- Parameters

### ❌ Bad

```js
// What does this mean?
const maxMbs = 10

// Get orders from where/whom?
const getOrders = (id: string) => {
  ...
}

// Matching what?
const matchingOrders = orders.filter(x => x.status === 'fulfilled')
```

### ✅ Good

```js
const fileSizeLimitMb = 10

const getOrdersByUserId = (userId: string) => {
  ...
}

const unfulfilledOrders = orders.filter(o => o.status !== 'fulfilled')
```

## 9. Don't over engineer (YAGNI)

In programming, there is a principle called "YAGNI" (You ain't gonna need it), which states that functionality should not be added unless deemed necessary. You should always keep this in mind. Only implement new functionality when you actually need it, not when you think you will need it in the future. Because, most likely, you never will. Also, don't build a feature in the most complex way. Abstraction can be great where it makes sense, but it can also be a real pain if used mindlessly. Remember, every new code needs to be maintained, so it's better to only add code that's actually required. Otherwise it only adds overhead and doesn't bring any value.

## 10. Avoid duplication/redundancy

There's also a principle called "DRY" (Don't repeat yourself), which states that you should avoid redundancy (don't duplicate code, have a single source of truth) at all costs. This holds true for code, data and comments.

- Don't copy or duplicate code
- Don't store data redundantly
- Don't add comments that don't add context

It's better to write clean, reasonable code and refrain from comments rather than writing less readable code and adding comments. Also, code duplication is one of the worst things you can do. Whenever you need to reuse a piece of code, extract it into a separate file/module/function depending on the language you're using.

## 11. Refactor if necessary

Don't be afraid of refactoring your code if there is a necessity. Software evolves, and so should you. It's better to get rid of a technical debt and refactor that piece of code instead of carrying it along and grit your teeth on it. Every now and then, take some time to go through your code and take the time to refactor and make it better instead of adding another feature. It's worth it in the long run.

## 12. Don't make assumptions

You shouldn't make any assumptions about how your code will behave in certain situations. Even though you think your code can never enter state X, it doesn't mean that it won't. Handle errors. Expect the unexpected. Make sure your code runs, no matter the state or outcome. This is especially important for user inputs – you can never know what kind of data a user will enter. I often like to apply Murphy's law in this context – anything that can go wrong will go wrong at some point.

## 13. Take advantage of immutability

Whenever possible (and reasonable), try to use immutable data types and avoid manipulating existing variables directly. It might seem cumbersome first, but your code becomes way more predictable and less error-prone if you work with immutable objects. Changing existing variables directly can have unintended, hard to find side effects, which you should avoid if necessary. You literally protect yourself from making dumb mistakes.

## 14. Introduce environment variables

Always introduce environment variables for data that shouldn't be hard-coded into your software. For example, database connection strings, file system paths and app preferences. Never store data like this directly in your code. It's a lot better to inject information from outside – that way, you keep everything in one place, can make changes quickly, and most importantly, don't expose confidential in your source code.

## 15. Get in the zone

Programming requires concentration, it requires focus. When you tackle a problem, make sure to get in the zone. Silence notifications. Think into the problem and its possible solutions. If your mind is not free, you will find yourself jumping around, not being concentrated and thus, not getting anything done. Get in the zone, and don't break the flow.
