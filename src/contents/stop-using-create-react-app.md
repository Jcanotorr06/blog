---
author: Joseph Cano
datetime: 2022-12-02T20:55:52Z
title: Stop Using Create React App
slug: "stop-using-create-react-app"
featured: true
draft: false
tags:
  - advice
  - react
  - web developement
  - cra
  - js
ogImage: ""
description:
  "Create React App is what almost every developer (including myself) learned to use first when learning the JavaScript library React. It supports all the configurations out of the box. But when your project code grows you might face higher build times, a slower start in the development server and waiting 2 to 5 secs to reflect the changes you have made in code and this might increase rapidly when the app grows on a larger scale."
---
<div>
    <img src="https://i.ytimg.com/vi/ToEp--KcXcA/maxresdefault.jpg"/>
</div>
Create React App is what almost every developer (including myself) learned to use first when learning the JavaScript library React. It supports all the configurations out of the box. But when your project code grows you might face higher build times, a slower start in the development server and waiting 2 to 5 secs to reflect the changes you have made in code and this might increase rapidly when the app grows on a larger scale.

This increases:

1. Development time, as we need to wait for 2 to 6 secs for each change.
2. Production Build Time, it might take around 10 to 20 minutes to deploy a quick fix.
3. Time, Time is money 🙂.

## Table of Contents

## Why is CRA Dev Server So Slow?

CRA uses [Webpack](https://webpack.js.org/) to bundle the code into one file. Webpack bundles the entire code, so if your codebase is very large more than 10k lines you might see a slower start in the development server and a long waiting time to see the changes made.
![image](https://res.cloudinary.com/practicaldev/image/fetch/s--3yZ0a8cx--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x88w1bkng42yg8iyzlz2.png)

While this is super convenient for the beginner this leads to problems later in the development process such as:

- Slower loading speeds
- No ability for staging production builds
- Hard to configure if you dislike the default configuration

Create React App uses Client Side Rendering (CSR) to bundle the Javascript files and builds one single file to render it all on the client. This is all done within the client’s browser as React does not have access to Server Side Rendering (SSR) in the default configuration. Create React App abstracts everything inside of a project and the single dependency that is being used react-scripts which as a beginner might be amazing, one less thing to worry about! But now as a beginner, you might not know about what transpiler(babel) or bundler(web pack) is being used and you might not have any idea what these even are (they are very important parts of the Javascript web development cycle)!!

So coming from the rampant abstraction, it stands to deal with the numerous over simplifications within Create React App can lead to some troubles understanding vital parts of Javascript.

## What are the Alternatives?

### Vite

![Vite Logo](https://uploads-ssl.webflow.com/5fad4717a287d5c593a913c3/628caf2b60b4f2460c9f1ca9_Vite%20-%20Main%20Image.jpg)

[Vite](https://vitejs.dev/), is a build tool created by [Evan You](https://vitejs.dev/), the creator of [Vue](https://vuejs.org/). It allows for faster developement thanks to super fast Hot Module Reloading (HMR), fast cold start times, and CSS + JSX + Typescript support out of the box.

Although Vite is opinionated, it can be extended via its Plugin API and JavaScript API. It allows developers to serve code natively using ES Modules during development, which negates the need for a bundle step.

In development mode, Vite splits the application code into two.

One is the dependency code, i.e. code imported from node_modules. This code is processed using esbuild. Esbuild is a javascript bundler written in Go that processes around 10-100 times faster than Webpack.

Two is the application code e.g. the custom-written code for the application such as .jsx, .vue, or .scss files.

Unlike Webpack, Vite uses route-based code splitting to load only the parts of the code that need to be loaded, unlike Webpack which has to rebundle everything.

Using Vite can dramatically improve the performance of coding many languages during development, and reduce the feedback loop time which is ordinarily incurred with Webpack.

Vite was initially created to serve as the future foundation of Vue.js tooling. Although as of 2.0 Vite is now fully framework-agnostic, supporting frameworks such as [React](https://reactjs.org/), [Svelte](https://svelte.dev/), and many others.

To get started with Vite, simply use

```bash
yarn create vite
```

```bash
npm create vite
```

```bash
pnpm create vite
```

### Next.js

![nextjs logo](https://assets.vercel.com/image/upload/v1662090959/front/nextjs/twitter-card.png)

Next.js is a [React framework built by Vercel](https://vercel.com/) (formerly Zeit) to make server-side rendering (SSR) easier for React applications regardless of where your data comes from.

Next.js also supports static exporting, [incremental static regeneration](https://nextjs.org/docs/basic-features/data-fetching/incremental-static-regeneration), image and font optimization, improved SEO and unlike CRA, it is actually production ready.

To get started with Next.js, simply use:

```bash
yarn create next-app --typescript
```

```bash
pnpm create next-app --typescript
```