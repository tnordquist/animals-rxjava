---
title: Reactive Programming
description: "Defines reactive programming as a development model structured around asynchronous data streams"
menu: Reactive Programming
order: 10
---

## Reactive Programming

Reactive programming is about reacting when a value emits from an observed data stream. A
program can be written to create data streams of many types based on just about anything that can
happen or change, e.g., click events, HTTP requests (in the case of Animals), changes on a variable,
cache events, measures from a sensor, etc. This process causes the application to become inherently
asynchronous.

## Observer pattern

> The observer pattern is a software pattern in which an object, called the subject, maintains a list
of its dependents, called observers, and notifies them automatically of any state changes, usually
by calling one of their methods. It is mainly used to implement distributed event handling systems.
In those systems, the subject is usually called a "stream of events" or "stream source of events",
while the observers are called "sink of events".The stream nomenclature simulates or adapts to a 
physical setup where the observers are physically separated and have no control over the emitted 
events of the subject/stream-source. This pattern then perfectly suits any process where data 
arrives through I/O, that is, where data is not available to the CPU at startup, but can arrive 
"randomly" (HTTP requests, GPIO data, user input from keyboard/mouse/..., distributed databases and 
blockchains, ...). Most modern languages have built-in "event" constructs which implement the 
observer pattern components. While not mandatory most 'observers' implementations will use 
background threads listening for subject events and other support mechanism from the kernel...
[Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern)



 
