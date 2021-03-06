---
title: Express and Co.
date: '2021-03-06T18:18:34.067Z'
description: 'We take a look at how the Express family came to be and how they are related.'
---

## What is Express?

According to the Express team, Express is a ["fast, unopinionated, minimalist web framework for Node.js".](https://expressjs.com/) 
Let's break that down for a second and talk about what that means.

### Fast

It is fast enough for a production workload, but it is not trying to be the fastest.

### Unopinionated

Framework's that require a project to follow specific patterns is called opinionated.
An unopinionated framework is the opposite, an unopinionated framework doesn't require a project to follow specific patterns.

### Minimalist

Just as a piece of software needs to define what it is trying to do, it also needs to decide what it doesn't do as well.
When a piece of software is minimalist, it tries to do one thing well.

### Framework

A framework is a skeleton that you can build a project around.
There are frameworks built on Express that provide more features and opinions.
You can see the list that the Express team has complied [here.](http://Expressjs.com/en/resources/frameworks.html)
For the rest of this post, we are going to be focussing on ["fast, unopinionated, minimalist web framework for Node.js".](https://expressjs.com/)

## Why would you use Express?

### User story:

> Ted, a project manager, has a website that doesn't have a backend to save user state yet.
> Ted's team consists of front end developers who know Javascript.
> Ted tasks Phil (one of his developers) with figuring out how to implement a backend.
> Phil reads about this new technology(it's 2010 in this story btw) called Node.js that let's him write javascript and have it run on the server.
> He start looking for how to implement a HTTP server in Node.js.
> He starts implementing the backend using backend using the http package from the standard library of Node.
> Development is slow as the standard library is low level and designed to be a building blocks for higher level abstractions.
> One of his fellow developers, Lem, tell him about this new framework called Express.
> They audit the code of this framework and like how this framework structures writing HTTP servers and provides abstractions over the Node.js http library.
> Development speeds up as they are writing less boiler plate code and are able to concentrate on the business logic.
> As the project evolves the new developers are able to be onboarded faster then if they wrote all of the logic in house because their Express backend follows a standard layout.
> As they are implementing new features like password hashing(they had a security consultant tell them they need this, Phil and Lem were just front end developers after all) they discover more features that that are common across backends are already implemented by middleware.

Using a framework like Express provides a few main advantages over implementing everything in-house:

- Implementing everything in house costs money and doesn't provide a benefit to the business.

- Using a well tested common implementation will probably have less bugs then an in house project.

- New developers to your project will have a shorter onboarding time if they are familiar to Express.

- The team can leverage existing packages from the ecosystem to enhance the project.

## Alternatives by the numbers

I have compiled the table below based on a search on NPM on March 6, 2021, for ["web framework".](https://www.npmjs.com/search?q=web%20framework&ranking=popularity)
I limited the results to web frameworks for a server with greater than 500,000 weekly downloads. I also removed any frameworks based on Express.

| **Package name** | **Weekly Downloads** | **First version** |
| :--------------: | :------------------: | :---------------: |
|     Express      |      17,130,052      |    2010-05-22     |
|     Connect      |      4,516,888       |    2010-06-03     |
|       Koa        |       872,258        |    2013-11-07     |

So if you know your history of these projects you will probably laugh.
All three of these projects are from the same team.

## Quick history lesson

Express and Connect started development around the same time.
As described by the team behind Connect ["Connect is an extensible HTTP server framework for Node.js using 'plugins' known as middleware".](https://github.com/senchalabs/connect)
If you are familiar with Express that should sound like the Express middleware.
That is because, before Express 4, Connect was the package that provided the default middleware for Express.

### What is Connect and how is it related to Express?

#### [Dependency graph for Express prior to Express 4](https://Expressjs.com/en/guide/migrating-4.html#core-changes)

Node.js's built-in HTTP server &rightarrow; Connect &rightarrow; Express

Express depended on Connect and extended its functionality with routing, templating, sending files, and JSONP.

#### [Dependency graph for Express 4 and newer](https://Expressjs.com/en/guide/migrating-4.html#core-changes)

Node.js's built-in HTTP server &rightarrow; Express &rightarrow; Express/Connect middleware

In Express 4 they moved the middleware from Connect into its own packages and removed Expresses dependency on Connect.
Connect has not received a new release since May 17, 2019.

### [What is Koa](https://Koajs.com/)

["Koa is a new web framework designed by the team behind Express, which aims to be a smaller, more expressive, and more robust foundation for web applications and APIs."](https://Koajs.com/) ["Philosophically, Koa aims to 'fix and replace Node.js', whereas Express 'augments Node.js'." -Express team](https://github.com/Koajs/Koa/blob/master/docs/Koa-vs-Express.md)

#### Dependency graph for Koa

Node.js's built-in HTTP server &rightarrow; Koa &rightarrow; Koa middleware

In contrast to Express and Connect, Koa doesn't use the req and res objects from Node.js's built-in HTTP server but it's own abstraction on them: ctx.request and ctx.response. Express/Connect middleware is also not compatible with Koa. Koa's has a different ecosystem of middleware.

#### Why isn't Koa the next version of Express or Connect?

The Express team has a great writeup on it [here](https://github.com/Koajs/Koa/blob/master/docs/Koa-vs-Express.md) but the short answer is to migrate from Express to Koa would require a rewrite on an application so the team made a different library.
