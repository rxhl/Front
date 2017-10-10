---
layout: post
title: Scaffolding a web app with Yeoman
comments: true
---

In this brief tutorial, we will learn why and how to use Yeoman to build our next application. 

No unnecessary GIFs and anecdotes, here's what we will go through.

1. What is Scaffolding?
2. What is Yeoman?
3. Scaffolding a web app

<img class="no-shadow" alt="Yeoman logo" src="/Front/assets/img/6/yeoman.png" style="width: 70%; height: auto; display: block; margin: 0 auto;"/>

### **What is Scaffolding?**

The literal meaning of scaffolding is,

>A temporary structure on the outside of a building, made usually of wooden planks and metal poles, used by workers while building, repairing, or cleaning the building.

Something like this,

<img alt="Scaffolding" src="/Front/assets/img/6/scaffolding.jpg" style="width: 70%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Scaffolding</em></p>

In the above scenario, the wooden planks and steel rods provide the builders an easy way (or a guideline) to construct the building.

Similarly, while starting a new application, it's rather cumbersome to setup the build environment. A typical process might include,

* Setting up the directory structure
* Including CSS preprocessors (Sass), jQuery, Bootstrap and other libraries
* Creating a Gulp/Grunt file to automate menial tasks
* Setting up Babel and other exquisite environments

The above steps pertain to creating a generic web application. Specific applications such as React, Angular, Ember or even ASP.NET require certain additional steps. Evidently, tracking and following the best practices for each one of them becomes tedious. And a lot of effort is spent on setting things up rather than focussing on the actual application. Enter my boy, Yeoman.


### **What is Yeoman?**

The Yeoman team does a really good job in putting up their introduction.

>Yeoman helps you to kickstart new projects, prescribing best practices and tools to help you stay productive.

Yeoman allows us to focus on our application rather than setting up its environment and it works for *any* kind of application, well mostly. Essentially, we run a bunch of commands and Yeoman creates a full fledged workflow for us aka *scaffolding*. Let's get started!

### **Scaffolding a web app**

First, install Yeoman.

```
$ npm install -g yo
```

Also install the generator template

```
$ npm install -g generator-webapp
```

Create a directory for the new app, I'm creating `myApp`.

```
$ mkdir myApp
$ cd myApp
```
Hit it!

```
$ yo webapp
```
Yeoman will ask you a bunch of questions regarding the tools and libraries to include. I'm creating a generic app, so I'll go with the defaults.

<img alt="My App" src="/Front/assets/img/6/myapp.png" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Selecting default options for the app</em></p>

Select your options and Yeoman will install the required NPM and Bower components. If you look into `myApp` directory, you'll find everything from a gulpfile to a custom 404 page to kickstart your application.

<img alt="Directory structure" src="/Front/assets/img/6/tree.png" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>App structure as created by Yeoman</em></p>

Next run the gulpfile to build your application.

```
gulp build
```
And serve it.

```
gulp serve
```
Your application is now live at `localhost:9000` without writing a single line of code. 

<img alt="My App" src="/Front/assets/img/6/app.png" style="width: 90%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Creating a new app with Yeoman</em></p>

This is extremely handy while starting out a new project. While this was for a generic application, similar *recipes* exist for scaffolding an [Angular](https://github.com/yeoman/generator-angular) or [React](https://github.com/react-webpack-generators/generator-react-webpack) app as well. They can be viewed [here](http://yeoman.io/generators/).


### Furthermore

Hope you liked this quick intro to Yeoman. I too wish I had discovered it earlier! Get started with the official Yeoman [docs](http://yeoman.io/learning/index.html).
