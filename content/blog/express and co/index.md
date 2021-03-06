---
title: Express and co
date: '2021-03-06T18:18:34.067Z'
description: 'We take a look at how the Express family came to be and how they are related.'
---

## What is Express?

According to the Express team, Express is a "fast, unopinionated, minimalist web framework for Node.js".
Let's break that down for a second and talk about what that means.

### Fast

It isn't the fastest but it is fast enough for a production workload.

### Unopinionated

Framework's that require a project to follow certain patterns is called opinionated.
A unopinionated framework is the opposite, a unopinionated framework doesn't require a project to follow certain patterns.

### Minimalist

Just as a piece of software needs to define what it is trying to do.
It also needs to decide what it doesn't do as well.When a piece of software is minimalist it tries to do one thing well.

### Framework

A framework is a skeleton that you can build a project around.
There are frameworks built on Express that provide more features and opinions.
You can see the list that the Express team has complied [here](http://Expressjs.com/en/resources/frameworks.html).
For the rest of this post we are going to be focussing on "fast, unopinionated, minimalist web frameworks for Node.js".

## Alternatives by the numbers

I have complied the table below based off a search on NPM on March 6, 2020 for ["web framework."](https://www.npmjs.com/search?q=web%20framework&ranking=popularity) 
I manually filtered out the results that were not a web framework for a server and removed any that were based off of express.
I have limited the results to packages with greater then 500,000 weekly downloads.

| **Package name** | **Weekly Downloads** | **First version** |
| :--------------: | :------------------: | :---------------: |
|     Express      |      17,130,052      |    2010-05-22     |
|     Connect      |      4,516,888       |    2010-06-03     |
|       koa        |       872,258        |    2013-11-07     |

So if you know your history of these projects you will probably laugh.
All three of these projects are from the same team.

## Quick history lesson

Express and Connect started development around the same time.
As described by the team behind Connect "Connect is an extensible HTTP server framework for Node.js using "plugins" known as middleware." 
If you are familiar with Express that should sound like the Express middleware.
That is because before Express 4, Connect was the package that provided the default middleware for Express.

### What is Connect and how is it related to Express?

#### [Dependency graph for Express prior to Express 4](https://Expressjs.com/en/guide/migrating-4.html#core-changes)

** Node.js's builtin http server &rightarrow; Connect &rightarrow; Express **

Express depended on Connect and extended it's functionality with routing, templating, sending files, and JSONP.

#### [Dependency graph for Express 4 and newer](https://Expressjs.com/en/guide/migrating-4.html#core-changes)

** Node.js's builtin http server &rightarrow; Express &rightarrow; Express/Connect middleware **

In Express 4 they moved the middleware from Connect into it's own packages and removed Expresses dependency on Connect.
Connect has not received a new release since 17 May, 2019.

### [What is Koa](https://koajs.com/)

"Koa is a new web framework designed by the team behind Express, which aims to be a smaller, more expressive, and more robust foundation for web applications and APIs." "Philosophically, Koa aims to "fix and replace Node.js", whereas Express "augments Node.js"." [-Express team](https://github.com/koajs/koa/blob/master/docs/koa-vs-Express.md)

#### Dependency graph for Koa

** Node.js's builtin http server &rightarrow; Koa **

In contrast to Express and Connect Koa doesn't use the req and res objects from Node.js's builtin http server but it's own abstraction on them: ctx.request and ctx.response.

#### Why isn't Koa the next version of Express or Connect?

The Express team has a great writeup on it [here](https://github.com/koajs/koa/blob/master/docs/koa-vs-Express.md) but the short answer is to migrate from Express to Koa would require a rewrite on an application so the team made a different library.
