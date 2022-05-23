# nodejs-notes

Notes taken by me a Frontend Engineer while learning NodeJS to kick off his Full-stack career. I followed the course [The Complete Node.js Course](https://codewithmosh.com/p/the-complete-node-js-course). So if you did this course already, you'll see some similarities here. You can use it as a starter book for NodeJS.

## Table of Content

- [Getting Started](#getting-started)
  - [What is NodeJS](#what-is-nodejs)
  - [How NodeJS Works](#how-nodejs-works)
    - [Blocking and Synchronous System](#blocking-and-synchronous-system)
    - [Non-Blocking and Asynchronous System](#non-blocking-and-asynchronous-system)
  - [Reasons Behind the Popularity of NodeJS](#reasons-behind-the-popularity-of-nodejs)

## Getting Started

### What is NodeJS

NodeJS is a **Javascript runtime** **(not a programing language, not even a framework)**, built on top of **the fastest JS Engine V8 (the core of Google Chrome)**. NodeJS allows us to run the JS Engine outside the browser.

> Runtime is a special program that **supports the execution of computer programs written in a programing language**.

Before 2009, it's not possible to run Javascript code on server i.e. outside of browser. **In 2009, Ryan Dahl, an American Software Engineer**, came up with a brilliant idea. Every browser contains a JS engine inside and use it to execute JS programs. What he did is he integrated that engine in a C++ program. And that program is now known as NodeJS.

### How NodeJS Works

Basically, NodeJS is single-threaded, non-blocking and asynchronous by nature.

Okay, don't worry if you are not familiar with these buzzwords. I'm explaining them.

Before talking about non-blocking and asynchronous system I would love to explain blocking and synchronous system. I think it'll help us to understand what problem we face in which system.

#### Blocking and Synchronous System

First of all, think about a scenario. We have a server of **100 threads capacity**. In that server, there are **100 requests** coming simultaneously and the server is **processing these requests in 100 threads separately**. And every request includes some database operation. Now, database operations may take some time to be finished. So a thread can not be free to use until database operations end. Now, think, **what will we do if there 150 requests coming at a time?**

We can do 2 things to solve this problem.

1. We can **keep extra 50 requests in a queue** and whenever a thread is free, we can assign that thread to the first request in the queue.

2. Or we can **upgrade the server** to that point where it can serve 150 requests at a time.

But both of them are not cost-efficient. This is an example of how the framework **like ASP.Net, Ruby on Rails works, blocking and synchronous way.**

> It's blocking as extra requests have to wait until the processing of a request in a thread gets finished.

> And it's synchronous as requests are processed one by one (according to the order of their appearance in the server) in a synchronous way. That means one request is not processed until processing of another request is finished.

#### Non-Blocking and Asynchronous System

NodeJS provides an elegant solution to this problem. What it does is **it processes all the requests in one thread**. Whenever it receives a request, **it initiates the process for that request and then go for the next request and initiate the process for that request and so on**.

In the background, these processes keep running. **Whenever a process gets finished, it places the output to Event Queue**.

**When an output of a request placed in the Event Queue, JS engine send the response to the client (who initiates the request)**.

> In this way, one request is not getting blocked by the another one. That's why it's non-blocking.

> As one request processing is started before finishing the processing of another one, that's why it's asynchronous.

### Reasons Behind the Popularity of NodeJS
