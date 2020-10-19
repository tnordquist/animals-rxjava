---
title: Singleton
description: ""
menu: Singleton
order: 30
---

To implement the singleton class, the simplest way is to make the constructor of the class as private.
    Eager initialization:
In eager initialization, the instance of Singleton Class is created at the time of class loading, this is the easiest method to create a singleton class.
public class SingletonClass {
private static volatile SingletonClass sSoleInstance = new SingletonClass();
    //private constructor.
    private SingletonClass(){}

    public static SingletonClass getInstance() {
        return sSoleInstance;
    }
}
    Lazy initialization:
This method will check if there is any instance of that class is already created? If yes, then our 
method (getInstance()) will return that old instance and if not then it creates a new instance of 
the singleton class in JVM and returns that instance. This approach is called as Lazy initialization.
public class SingletonClass {

    private static SingletonClass sSoleInstance;
    private SingletonClass(){}  //private constructor.
    public static SingletonClass getInstance(){
        if (sSoleInstance == null){ //if there is no instance available... create new one
            sSoleInstance = new SingletonClass();
        }

        return sSoleInstance;
   }
}
