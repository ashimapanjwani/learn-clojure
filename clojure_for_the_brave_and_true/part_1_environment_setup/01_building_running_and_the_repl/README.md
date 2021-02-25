# Chapter 1: Building, Running, and the REPL


### Topics Covered

* Basic overview of Clojure and Leiningen
* Initial Setup
* Create a new Clojure project with Leiningen 
* Run the Clojure project
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


### Leiningen

Leiningen is a tool used to build and manage Clojure projects. You'll be using it for the 
following tasks:
* Creating a new Clojure project
* Running the Clojure project
* Building the Clojure project
* Using the REPL


### Initial Setup

* Must have Java version 1.6 or later installed. Check your version by running `java -version` 
  in your terminal.
* Install Leiningen using the instructions on the [Leiningen home page](http://leiningen.org/). 
  When you install Leiningen, it automatically downloads the Clojure compiler, *clojure.jar*.
  

### Creating a new Clojure project

To create a new Clojure project, type the following in your terminal:
```
lein new app clojure-noob
```
The project skeleton that gets created contains a few noteworthy files:
* *project.clj* is a configuration file for Leiningen. It helps Leiningen answer such 
  questions as “What dependencies does this project have?” and “When this Clojure program runs, 
  what function should run first?”
* In general, the source code is saved in *src/<project_name>*. In this case, the file 
  *src/clojure_noob/core.clj* is where you’ll be writing your Clojure code for a while. 
* *test* directory contains tests, and 
* *resources* is where you store assets like images.


### Running the Clojure Project

Open *src/clojure_noob/core.clj* in your editor. You should see this:
```clojure
(ns clojure-noob.core
    (:gen-class))

(defn -main
      "I don't do a whole lot...yet."
      [& args]
      (println "Hello, World!"))
```
Replace the text `"Hello, World!"` with `"I'm a little teapot!"`.

Next, navigate to the clojure_noob directory in your terminal and enter:
```
lein run
```
You should see the output `"I'm a little teapot!"`.

The `-main` function is the entry point to your program, and it runs 
when you execute `lein run` at the command line.


### Building the Clojure Project

In order to share your work with people who don’t have Leiningen 
installed, you can create a stand-alone file that anyone with Java 
installed can execute. To create the file, run this:
```
lein uberjar
```
This command creates the file *target/uberjar/clojure-noob-0.1.0-SNAPSHOT-standalone.jar*. 
You can make Java execute it by running this:
```
java -jar target/uberjar/clojure-noob-0.1.0-SNAPSHOT-standalone.jar
```
The file *target/uberjar/clojure-noob-0.1.0-SNAPSHOT-standalone.jar* is 
your new Clojure program, which you can distribute and 
run on almost any platform.


### Using the REPL

The REPL is a tool for experimenting with code. It allows you to interact with a running program 
and quickly try out ideas. It does this by presenting you with a prompt where you can enter code. 
It then *reads* your input, *evaluates* it, *prints* the result, and *loops*, presenting you with 
a prompt again.

This process enables a quick feedback cycle that isn’t possible in most other languages.

To start a REPL, run this:
```
lein repl
```
The output should look like this:
```
nREPL server started on port 28925
REPL-y 0.1.10
Clojure 1.9.0
Exit: Control+D or (exit) or (quit)
Commands: (user/help)
Docs: (doc function-name-here)
(find-doc "part-of-name-here")
Source: (source function-name-here)
(user/sourcery function-name-here)
Javadoc: (javadoc java-object-or-class-here)
Examples from clojuredocs.org: [clojuredocs or cdoc]
(user/clojuredocs name-here)
(user/clojuredocs "ns-here" "name-here")
clojure-noob.core=>
```
The last line, `clojure-noob.core=>`, tells you that you’re in the `clojure-noob.core` namespace 
(we'll cover namespace in detail in the later chps). The prompt also indicates that your
code is loaded in the REPL, and you can execute the functions that are defined. Let's go ahead 
and execute the `-main` function now:
```clojure
clojure-noob.core=> (-main)
I'm a little teapot!
nil
```
You just used the REPL to evaluate a function call. Try a few more basic Clojure functions:
```clojure
clojure-noob.core=> (+ 1 2 3 4)
10
clojure-noob.core=> (* 1 2 3 4)
24
clojure-noob.core=> (first [1 2 3 4])
1
```
You added some numbers, multiplied some numbers, and took the first element from a vector.

Going forward, you'll be presented with code without REPL prompts like so:
```clojure
(do (println "no prompt here!")
(+ 1 3))
; => no prompt here!
; => 4
```
When you see code snippets like this, lines that begin with `; =>` indicate the output of the 
code being run. In this case, the text `no prompt here` should be printed, and the return value of 
the code is `4`.

All Lisps, Clojure included, employ *prefix notation*, meaning that the operator always comes first
in an expression.

Conceptually, the REPL is similar to Secure Shell (SSH). In the same way that you can use SSH to 
interact with a remote server, the Clojure REPL allows you to interact with a running Clojure 
process. This feature can be very powerful because you can even attach a REPL to a live production
app and modify your program as it runs.
