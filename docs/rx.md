---
title: ReactiveX
description: ""
menu: ReactiveX
order: 20
---

*[ReactiveX or RX]: "Reactive eXtension"  
## Observables
[ReactiveX](http://reactivex.io), implements reactive programming principles by "composing
asynchronous and event-based programs by using observable sequences."

"ReactiveX extends the observer pattern to support asynchronous sequences of multiple items: 
ReactiveX operates on discrete values that are emitted over time and adds operators that allow you 
to compose sequences together declaritively while abstracting away concerns about things like 
low-level threading, synchronization, thread-safety, concurrent data structures, and non-blocking 
IO."

RX code creates and subscribes to data streams named Observables:
> The ReactiveX Observable model allows you to treat streams of asynchronous events with the same sort
of simple, composable operations that are used for collections of data items such as arrays or 
Lists. [ReactiveX](http://reactivex.io/intro.html#Reactive%20Programming)

## Single

Animals makes use of an Observable variant called "Single." A Single always emits one value or an
error notification, whereas Observable emits a series of values ranging from none to an infinite
number.

Animals applied the Single task to the method `getAnimals()`:
``` java
  @FormUrlEncoded
  @POST("getAnimals")
  Single<List<Animal>> getAnimals(@Field("key") String key);
``` 
 
The `loadAnimals()` method in AnimalViewModel subscribed to the Single tasks which brought in the 
`apiKey` and the `List<Animal>`:

``` java
animalService.getApiKey()
    .subscribeOn(Schedulers.io())
    .flatMap((key) -> animalService.getAnimals(key.getKey()))
    .subscribe(
        value -> animals.postValue(value),
        throwable::postValue
    );
```

A subscribed Single comes with two methods which are used to respond to notifications:

* `onSuccess`: a successfully emitted single item is passed to this method.

* `onError`: an item that cannot or was not emitted causes the Single to pass a Throwable.

In the case of Animals, the Single `getAnimals()` passed `List<Animal>` to `postValue(item)` if 
the Single successfully fetched the `List<Animal>` and passed `throwable` to `postValue(item)` if 
the Single did not successfully fetch `List<Animal>`.

A Single called only one of the methods and called it only once. The Single terminated, and the 
subscription to it ended once the Single called one of the methods.
   
   


