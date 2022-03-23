# Topic: PROGRAMMING PARADIGM

## OOP. What is OOP? Why should we use OOP?

OOP stands for object-oriented programming. Like its name, OOP means focusing on objects and building things upon them. In real world, almost everything is an entity with some data and some behaviors, which OOP can be used to articulated quite exactly, compared to other programming paradigms like procedural programming or functional programming.

## What is the 4 principles of OOP?

The four principles of OOP are encapsulation, abstraction, inheritance, and polymorphism.

- Encapsulation is a feature of OOP that wraps things into a unity, like wraps methods and fields into a class, wrapping classes into a package.
- Abstraction means when we use a class, we only care about its public things, like public fields, methods, and don't care about its private stuff, about how it is implemented under the surface.
- Inheritance allows a class to inherit the properties and characteristics of other classes.
- Polymorphism allows using the same type and the same function call for same same but different action of related entities.

## What is composition? Compare composition vs inheritance

Composition is a has-a relationship. Like a house has rooms, a car has wheels. In OOP, the composition relationship is represented as fields in a class.

Inheritance is an is-a relationship. Like a dog is an animal, a rose is a flower. In OOP, the inheritance relationship is represented as a class inheriting another class.

## Interface vs abstract class

The key difference between abstract class and interface is the relationship between it and the classes that extend or implement it.

When class A extends the abstract class B, class A is a B. For example, a cat is an animal. But when class A implements an interface C, it only means A has C characteristics, like the Cat class can implement Climbing Tree interface.

## Explain class constructor. Why does the constructor not return any value?

To be defined.

## What does private, protected, public means and what are the difference?

These keywords indicate the access scope of things like methods, fields in an OOP language.

- Things with "private" scope can be accessed by things in the same class.
- Things with "default" scope can be accessed in the same package.
- Things with "protected" scope is being able to be accessed by things in the same package and outside things that has inheritance relationship.
- Things with "public" scope can be accessed by everything.

## Functional programming. What is FP? Why should we use FP?

To be defined.

## FP characteristics

Some highlight characteristics of functional programming are:

- Immutability: variable should be set once and not changed.
- Pure function: the return value should depend only on the input value, and create no side effect.
- Function is first-class citizen. We can create a function, assign a function to a variable, pass it as a parameter and return it as a value.

## What is immutability and why is it important?

To be defined.

## What are pure functions and why are they important to functional programming?

To be defined.

## What does it mean when a function is a first-class citizen?

To be defined.

## Lazy evaluation

To be defined.

## What is higher-order functions?

To be defined.

## What are currying and partial application?

To be defined.

## What are pure and impure functions?

To be defined.

## Difference between flatMap() and map()

To be defined.

## Explain functor, applicative, monoid, monad

- Functor is a type class that wraps value in a context and defines a fmap. A fmap is the function that takes another function and a wrapped value, then return a new wrapped value.
- Applicative is a type class that wraps value in a context and defines a function that can take a value in a wrapped context and a function in a wrapped context, apply the function to value, then return the result wrapped in the context.
- Monoid: to be defined.
- Monad is a type class that wraps value in a context and defines a function that can take a value in a wrapped context and a function in a wrapped context, apply the function to value, then return the result wrapped in the context. But the different thing between applicative and monad is the return type of the function. In applicative, the function returns the value directly, while in monad, the function returns the value wrapped in a context.
