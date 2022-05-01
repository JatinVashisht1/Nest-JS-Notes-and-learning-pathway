# Getting started with NestJS

## Node.js ecosystem
- node by design has minimilistic setup and developers are incharge of setting up
- developer can handle routing, API calls, setting up web sockets, code organization, etc
- There are many frameworks built on top of Node.js (most notably Express.js), but there is still alot of developer effort required
- Thus, the ultimate flexibility can be a bit of double edged sword.
### How is NestJS helping in this situation
- NestJS tries to tackle some of these problems by creating an abstraction or overall Framework around Node.js
- It provides an out of the box application architecture that allows developers and teams to create highly testable, scalable, loosely coupled, and easily maintainable.
- Nest uses **Express** by default under the hood, but it can be replaced with other frameworks such as **fastify**
## Key features of NestJS
- It is a layer above Node.js, abstracting away difficult tasks, tools, and boilerplate code
- It also provides a full fledged toolkit for the application development
- We can built Rest API's, MVC applications, microservices, GraphQL applications, web sockets, and even CLI's and cron jobs.
- It also provides a **dependency Injection** system which lets developer abstracting dependencies easily

## Installing NestJS CLI
- Get `current version` or `latest LTS version` of node in your system
- Install NestJS CLI from below command
```
npm i -g @nestjs/cli
```
- check if Nest is installed correctly
```
nest --version
```
### What is Nest CLI
- It is companion tool for NestJS that helps it generate run, compile and bundle our applications
- `nest --help` to see all commands of `Nest CLI`