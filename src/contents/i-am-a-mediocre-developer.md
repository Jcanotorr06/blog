---
author: Joseph Cano
datetime: 2022-09-24T02:44:14Z
title: I am a Mediocre Developer
slug: "i-am-a-mediocre-developer"
featured: false
draft: false
tags:
  - advice
  - motivation
ogImage: ""
description:
  "I personally know some developers who are very talented and can create wonderful pieces of software with no or little struggle. Because of these gifted individuals, our industry is full of high expectations. But the sad truth is: not everyone is a ninja/guru/rockstar developer."
---

I personally know some developers who are very talented and can create wonderful pieces of software with no or little struggle. Because of these gifted individuals, our industry is full of high expectations. But the sad truth is: not everyone is a ninja/guru/rockstar developer.

And that's exactly who I am: a mediocre developer. This article will guide you through surviving in the industry if you are not a genius.

<hr/>

## Table of Contents

## I Google the Simplest Things All of the Time

<span style="font-size:36px;font-weight:bold;">I</span> fail to remember a lot of the things. Like functions and methods from the standard library, arguments positions, package names, boilerplate code and so on.

So, I have to google it. And I do it on a daily basis. I also reuse code from old projects. Sometimes I even copy-paste answers from StackOverflow or Github. Yes, it is actually a thing: [StackOverflow Driven Development](https://meta.stackoverflow.com/questions/361904/what-is-stack-overflow-driven-development).
But I am not alone. A lot of other developers do it too. There's a [popular twitter discussion](https://twitter.com/dhh/status/834146806594433025) which was started by the creator of **Ruby on Rails**.

But why is that bad in the first place? Well, there are several disadvantages about it:

1. It allows you to copy bad design decisions or vulnerable code from other people
2. It forms a specific mindset: if we can not google something up, then "Houston, we have a problem"
3. When the internet will go down, we won't be able to work

But, I don't think that it is a big problem. It even may serve as your secret weapon. I have some pieces of advice to follow to decrease negative effects.

### How to Survive

1. Use an **IDE** to get autocompletion and suggestions, so you won't have to google the language basics
2. Remember where (not how) you have already solved this problem. So you can always look there for the solution
3. All code you paste into the project should be analyzed, refactored, and reviewed later. This way we won't harm the project with the bad code, but help it with the fast solution

## I Keep Things Straight Simple

Machines always do what they are told. Sometimes they are just told to do the wrong thing. So, the main problem in software development is not machines, but developers' mental capacity. It is very limited. So, we - mediocre developers - cannot waste it to create complex abstractions, obscure algorithms, or unreadable long code blocks. [Just keep it simple](https://en.wikipedia.org/wiki/KISS_principle).

But how can we tell that this code is simple and that one is complex? We need to use ``WTFs/Minute`` method to measure code quality.

![code-quality-measurement](https://res.cloudinary.com/practicaldev/image/fetch/s--RTnc6j1i--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://i2.wp.com/commadot.com/wp-content/uploads/2009/02/wtf.png%3Fresize%3D550%252C433)

The principle is very easy and clear to understand. Whenever you find something in the code you do not understand - it is too complex. What can you do?

1. Rewrite it to have cleanner design
2. Provide documentation
3. Add comments to the most tricky parts. But remember, that comments are the code smell themselves

### How to Write Simple Things From the Beginning

1. Use correct names for variables, functions, and classes
2. Make sure that every part of your program [does only one thing](https://en.wikipedia.org/wiki/Single_responsibility_principle)
3. Prefer [pure functions](https://en.wikipedia.org/wiki/Pure_function) over regular functions
4. Prefer regular functions over classes
5. Fallback to classes only in a strong need

## I Do Not Trust Myself

Some developers proved to deliver high-quality code. Like this woman: Margaret Hamilton, lead software engineer of the Apollo Project. In this picture she is standing next to the code she wrote for the moon mission:

![margaret-hamilton](https://res.cloudinary.com/practicaldev/image/fetch/s--G4sZPf_1--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://cdn8.openculture.com/2017/08/29205628/margaret-hamilton-mit-apollo-code_0.jpg)

But, whenever I write any code - I do not trust myself. I can screw things up really badly even in the easiest parts of the project. This may include:

1. Language errors
2. Logic errors
3. Design errors
4. Style errors
5. Security errors
6. WTF errors (my all-time favorite!)

And there is no magic book about "learn how to write bug-free code". And it is perfectly normal. [All software has bugs](https://m.signalvnoise.com/software-has-bugs-this-is-normal-f64761a262ca).

The thing is: anyone should not be allowed to write code with obvious errors. At least, we should try. But how can I protect the project from myself? There are multiple ways to do it.

### How to Cope

1. Write tests. Write a lot of tests. Starting from integration tests down to unit tests. Run it in the ``CI`` before each pull request. This will protect you from some logical errors
2. Use static typing or optional static typing. For example, we use [mypy](http://mypy-lang.org/) with ``python`` and [flow](https://flow.org/) with ``javascript``. Positive effects: cleaner design and "compile time" checks
3. Use automated style checks. There are tons of the style checkers for every language
4. Use quality checks. Some tools run some complex heuristic algorithms on your code base to detect different problems like this line has too many logics inside, this class is not needed, this function is too complex
5. Review your code. Review it before merging to ``main``. And sometime after the merge
6. [Pay other people to audit your code](https://wemake.services/meta/rsdp/audits/). This technique has a huge positive influence! Because when developers look at your code for the first time it is easier for them to spot inconsistencies and bad design decisions.

## After the Application is Deployed, I Still Do Not Trust Myself

Oh, at last, my application is in production. It is working now. I can have a short nap, nothing is going to break. Wait, no! Everything is going to break. And yes, I mean it: **everything**.

Actually, there are some tools to make finding and fixing existing problems easier.

1. [Sentry](https://sentry.io/welcome/). When an error happens for any of your users - you will be notified. Has bindings to almost any programming language
2. Different [services](https://papertrailapp.com/) and [tools](https://www.elastic.co/products/kibana) to collect logs from multiple processes and servers into one place
3. [Server monitoring](https://grafana.com/). That's the place where you can configure monitors for CPUs, disks, networks, and memory. You can even spot the time to scale before the users will actually break your service

**To put it shortly**, we need to monitor our application in production. We sometimes use all of these tools, sometimes only the most required parts.

## Constantly learning

Wow, that's a lot of things to learn. But that's how it works. If we want to write good software we need to constantly learn how to do it. There are no short ways or magical tricks. Just learn how to be better every single day.

In conclusion, we need to understand two basic things:

1. Problems happen to everyone. The only thing that matters is how ready we are for these problems
2. We can reduce the sources of the problems to some acceptable rates

And it has nothing to do with your mental capacity or mindset.
