# Chapter 1: Building, Running, and the REPL


### Topics Covered

* Basic overview of Clojure and Leiningen
* Create a new Clojure project with Leiningen 
* Build the project to create an executable JAR file
* Execute the JAR file
* Execute code in a Clojure REPL


### Clojure

The Clojure language is a Lisp dialect with a functional emphasis whose syntax and semantics 
are independent of any implementation. The Clojure compiler, on the other hand, is an executable 
JAR (Java ARchive) file, *clojure.jar*, which takes code written in the Clojure language and compiles 
it to Java Virtual Machine ( JVM) bytecode. You’ll see *Clojure* used to refer to both the language 
and the compiler, which can be confusing if you’re not aware that they’re separate things.

This distinction is necessary because, unlike most programming languages, Clojure is a *hosted 
language*. Clojure programs are executed within a JVM and rely on the JVM for core features like 
threading and garbage collection. Clojure also targets JavaScript and the Microsoft Common Language 
Runtime (CLR), but this book only focuses on the JVM implementation.

Relationship between Clojure and the JVM:
* JVM processes execute Java bytecode.
* Usually, the Java Compiler produces Java bytecode from Java source code.
* JAR files are collections of Java bytecode.
* Java programs are usually distributed as JAR files.
* The Java program *clojure.jar* reads Clojure source code and produces Java bytecode.
* That Java bytecode is then executed by the same JVM process already running *clojure.jar*.
