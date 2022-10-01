---
author: Joseph Cano
datetime: 2022-10-01T20:12:35Z
title: All the Ways to Center a Div
slug: "all-the-ways-to-center-a-div"
featured: false
draft: false
tags:
  - html
  - css
  - tutorial
ogImage: ""
description:
  Centering a div is something we need to do all the time as web developers, and yet it still can be a challenge. There are many approaches you can take to accomplish it. Below I'll explore all the ways to center one div inside another.
---
Centering a div is something we need to do all the time as web developers, and yet it still can be a challenge. There are many approaches you can take to accomplish it. Below I'll explore all the ways to center one div inside another.

All of the examples will be using the following HTML:

```html
<div class="outer-div">
  <div class="inner-div"></div>
</div>
```

Each example has these shared base styles:

```css
.outer-div {
  background-color: red;
  width: 150px;
  height: 150px;
}

.inner-div {
  background-color: blue;
  width: 50px;
  height: 50px;
}
```

<div>
    <div style="background-color:red;width:150px;height:150px;">
        <div style="background-color:blue;width:50px;height:50px;">
        </div>
    </div>
</div>

There is a 150x150 red outer div, and a 50x50 blue inner div. The goal is to find all the ways to center the blue div vertically and horizontally inside the red div and get this end result:

<div>
    <div style="background-color:red;width:150px;height:150px;display:flex;">
        <div style="background-color:blue;width:50px;height:50px;margin:auto;">
        </div>
    </div>
</div>

<hr/>

## Table of Contents

## 1. Flexbox

```css
.outer-div {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

OR

```css
.outer-div {
  display: flex;
  justify-content: center;
}

.inner-div {
    align-self: center;
}
```

OR

```css
.outer-div {
  display: flex;
}

.inner-div {
    margin: auto;
}
```

## 2. CSS Grid

```css
.outer-div {
  display: grid;
  place-content: center;
}
```

OR

```css
.outer-div {
  display: grid;
  align-items: center;
  justify-content: center;
}
```

OR

```css
.outer-div {
  display: grid;
}

.inner-div {
  align-self: center;
  justify-self: center;
}
```

## 3. Absolute Positioning

```css
.outer-div {
  position: relative;
}

.inner-div {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
}
```

OR

```css
.outer-div {
  position: relative;
}

.inner-div {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  margin: auto;
}
```

<hr/>

## Try these out yourself in CodePen!

<p class="codepen" data-height="300" data-theme-id="dark" data-default-tab="html,result" data-slug-hash="NWMMjqN" data-user="jcanotorr06" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/jcanotorr06/pen/NWMMjqN">
  Center a Div</a> by Jcanotorr06 (<a href="https://codepen.io/jcanotorr06">@jcanotorr06</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
