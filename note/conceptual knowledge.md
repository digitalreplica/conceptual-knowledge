---
is_a:
  - "[[note]]"
of:
  - "[[concept]]"
---
# Introduction

Knowledge is a complex thing, built on millions of individual concepts, most of which mean different things to different people. Conceptual knowledge is a set of building blocks to stitch those concepts together into a cohesive whole. It starts with a fundamental [[concept]], then uses [[relationship]](s) to define other concepts and how they interrelate. The result is a tree-based knowledge structure that models each person's individual way of thinking, while allowing comparisons by both humans and computers.

**Concepts + relationships = knowledge**

## Concept
Most [[concept|concepts]] are so ingrained in our brains that its actually quite hard to define them. Conceptual knowledge defines concepts by linking out to external sources of truth that can be followed if needed. So the simplest way to define a concept is-a:

**concept**
```
equals:: [concept | Wikipedia](https://en.wikipedia.org/wiki/Concept)
```

Wikipedia has quite a decent article on what a concept is, so if you're not sure or just want a refresher, go read it. Conceptual knowledge refines it only slightly by emphasizing that concepts can be related to other concepts, and defining methods for doing so.

## Relationships
Relationships are ways of linking concepts together into a larger knowledge structure. Conceptual knowledge defines three primary relationships for concepts. The example above used one already. It's easy to create other relationships, to build all the nuanced ways knowledge and things can interrelate.

Relationships also link your knowledge structure to the vast amount of knowledge humanity has already collected. Like with the definition of concept, it creates an internal concept in your knowledge structure by linking it to a external resource. That's the shortcut that allows complex structures to be created quickly, while allowing different structures to be compared.

### Is
The word [[is_a]] has several different meanings, but conceptual knowledge always uses it with the meaning,  "`_____ is a _____`". For example, color is a concept, and red is a color.

``` mermaid
flowchart LR
	red --is--> color --is--> concept
```

It takes just a couple of concepts and relationships to sketch out a basic knowledge of colors. That's really all the structure needed to create most real world things. Let's show a few more examples.

``` mermaid
flowchart LR
	Alice --is--> person --is--> concept
```

``` mermaid
flowchart LR
	philosophersstone([Harry Potter and the Philosopher's Stone]) --is--> book --is--> concept
```

Is defines a one-way relationship. Red is a color, but not all colors are red.

### From
New concepts are created by combining existing ones and adding your new way of thinking about them. The `from` relationship shows these derived concepts. 

The simplest example is joining two concepts together. Let's combine the concepts of `toy` and `truck` to make a new `toy truck` concept.

``` mermaid
flowchart LR
	toytruck[toy truck] --is--> concept
	toytruck -.from.-> toy --is--> concept
	toytruck -.from.-> truck --is--> concept
```

But we also can take one concept and change it a bit to make a slightly different concept. A good example of this is a recipe. Assume you find a good one on the internet, but alter it to your tastes.

``` mermaid
flowchart LR
    subgraph internet
	    internetrecipe([recipe])
	end
    subgraph me
	    myrecipe[recipe] -.from.-> internetrecipe
    end
```

### Equals
The `equals` relationship shows that two concepts are identical. It is primarily used to define a concept using an external source of truth. Let's show this in Alice's knowledge structure.

``` mermaid
flowchart LR
    subgraph internet
	    conceptwikipedia([concept - Wikipedia])
	end
    subgraph Alice
	    concept1[concept] <--equals--> conceptwikipedia
    end
```

Unlike `is`, `equals` is a two way relationship. And like in math, if `a = b` and `b = c`, then `a = c`. This is how two different knowledge structures can be linked and compared. Let's assume Bob defines his concept the same way.

``` mermaid
flowchart TB
    subgraph internet
	    conceptwikipedia([concept - Wikipedia])
	end
    subgraph Alice
	    concept1[concept] <--equals--> conceptwikipedia
    end
    subgraph Bob
	    concept2[concept] <--equals--> conceptwikipedia
    end
```

Alice and Bob can now know they're thinking about the same thing, since they share a common source of truth.

# Conceptual knowledge in detail
Conceptual knowledge is a bottom-up approach, using the basic building blocks shown to create knowledge structures of any level of complexity. But it's designed to be quick and simple, dropping in a few concepts and relationship to make simple structures. Then when more complexity is needed, the simple structure can be expanded just enough to add something new.

For programmers, this is similar to [classes in the Java programming language](https://www.w3schools.com/java/java_classes.asp). It starts with a base `Class`, and all other classes derive from it.

## Defining new relationships
The power of conceptual knowledge is that new concepts and relationships can be created at will. Let's create a simple database to track books using `title` and `author`.

``` mermaid
flowchart LR
	philosophersstone([Harry Potter and the Philosopher's Stone]) --is--> book --is--> concept
	jkrowling[J.K. Rowling] --is--> author --is--> concept
	philosophersstone -.author.-> jkrowling
```

The whole thing can be thrown together in five minutes, but it can easily scale to thousands of books and hundreds of authors. You might have to deal with issues like having two authors or two books with the same name, but the `equals` relationship for each can show the difference between them.

## Breaking large concepts into smaller ones
Many concepts grow so big that people invent types or categories to break it apart into smaller pieces. We'll use `type` since it's shorter than `category`. Since a `type` always has a larger thing it's part of, we'll create a new relationship for this using `of`, like `this is a type of {this larger thing}`.

For an example, let's start to categorize our books into fantasy, science fiction, nonfiction, etc.

``` mermaid
flowchart LR
	philosophersstone([Harry Potter and the Philosopher's Stone]) --is--> book --is--> concept
	type --is--> concept
	philosophersstone -.type.-> fantasy --is--> type
	fantasy -.of.-> book
	jkrowling[J.K. Rowling] --is--> author --is--> concept
	philosophersstone -.author.-> jkrowling
```

Now our book database is more organized and easier to search. That approach can be used to organize nearly anything, from types of food.

## Grouping similar things together
We commonly group similar things together. Let's create a group of things and add something to that group. Like `type`, all of the things might be part of a bigger thing.

For example, we want to track our favorite books.

``` mermaid
flowchart LR
	philosophersstone([Harry Potter and the Philosopher's Stone]) --is--> book --is--> concept
	philosophersstone -.in.-> favoritebooks[my favorite books] --is--> group --is--> concept
	favoritebooks -.of.-> book
```

## Concept libraries
It should be possible to create libraries of concepts that people can easily import to kickstart a new knowledge structure, and expand it as needed. A person just starting out could pull in the conceptual knowledge system, and libraries for note taking, books, and movies. Later they could extend their knowledge with libraries of other things.

Since each library would link out to relevant sources of truth, everyone using that library would automatically have compatible knowledge structures.

A core library of concepts has been started at https://github.com/digitalreplica/conceptual-knowledge-core.

## Comparing two knowledge structures
It should be straightforward to compare two knowledge structures with overlapping relationships to create new ways of looking at knowledge. Let's look at Alice and Bob again.

``` mermaid
flowchart LR
	subgraph internet
		bookwikipedia(book - Wikipedia)
		cookingwikipedia(cooking - Wikipedia)
		rockclimbingwikipedia([rock climbing - Wikipedia])
		balletwikipedia([ballet - Wikipedia])
	end
	subgraph Alice
		balletalice(ballet) <--equals--> balletwikipedia
		bookalice(book) <--equals--> bookwikipedia
		cookingalice(cooking) <--equals--> cookingwikipedia
	end
	subgraph Bob
		bookbob(book) <--equals--> bookwikipedia
		cookingbob(cooking) <--equals--> cookingwikipedia
		rockclimbingbob(rockclimbing) <--equals--> rockclimbingwikipedia
	end
```

It's pretty easy to see they share a common interest in books and cooking, but each like other things. Let's look even deeper.

``` mermaid
flowchart LR
	subgraph internet
		bookwikipedia(book - Wikipedia)
		jkrowlinggoodreads(J.K. Rowling - Goodreads)
		philosophersstonegoodreads([Harry Potter and the Philosopher's Stone - Goodreads])
	end
	subgraph Alice
		philosophersstonealice([Harry Potter and the Philosopher's Stone]) --is--> bookalice(book) <--equals--> bookwikipedia
		philosophersstonealice <--equals--> philosophersstonegoodreads
		philosophersstonealice -.author.-> jkrowlingalice
		jkrowlingalice(J.K. Rowling) <--equals--> jkrowlinggoodreads
	end
	subgraph Bob
		philosophersstonebob([Harry Potter and the Philosopher's Stone]) --is--> bookbob(book) <--equals--> bookwikipedia
		philosophersstonebob <--equals--> philosophersstonegoodreads
		philosophersstonebob -.author.-> jkrowlingbob
		jkrowlingbob(J.K. Rowling) <--equals--> jkrowlinggoodreads
	end
```

The diagram is messier, but shows not only that they both like books, but show authors and books that they have in common. If they used a common system of rating books, it could also tell them which books they both like.

These are the types of comparisons that conceptual knowledge is trying to make possible.

# Implementation
Conceptual knowledge uses [markdown | Wikipedia](https://en.wikipedia.org/wiki/Markdown) to store knowledge. Relationships are added at the top of each file using [inline fields](https://blacksmithgu.github.io/obsidian-dataview/annotation/add-metadata/#inline-fields) with either a [markdown link](https://help.obsidian.md/How+to/Format+your+notes#External+links) to external concepts, or a [wikilink](https://help.obsidian.md/Linking+notes+and+files/Internal+links) to internal concepts. The inline field method allows the links to be clickable, while also letting applications query the fields.

Here's an example from our book.

**Harry Potter and the Philosopher’s Stone**
```
is_a:: [[book]]
type:: [[fantasy]]
author:: [[J.K. Rowling]]
equals:: [Harry Potter and the Philosopher’s Stone | Goodreads](https://www.goodreads.com/book/show/72193.Harry_Potter_and_the_Philosopher_s_Stone)
in:: [[my favorite books]]
```

That small amount of information, plus your notes, is everything you need to summarize your knowledge of the book. It lets you find related things easily, and expand later if desired.

Concepts are even smaller, since they typically only have relationships without any notes

**book**
```
is_a:: [[concept]]
equals:: [book | Wikipedia](https://en.wikipedia.org/wiki/Book
```

## Non-concept fields
Conceptual knowledge plays nicely with other fields that aren't concept-related. Modern markdown applications allow for frontmatter and inline fields. So if you wanted to add an `isbn` field for your books, it's as simple as:

```
---
isbn: 12345
---
```
or

```
isbn:: 12345
```

Then your knowledge system becomes mini databases of all the different types of things you know about.

# Finding information

## With concepts
The concept structure makes it much more intuitive information. You can start with the concept itself, following [backlinks](https://help.obsidian.md/Plugins/Backlinks) through your concepts, types and groupings until you narrow them down to what you're looking for. It's a self-reinforcing system. If something isn't where you expected to find it, then you can add a few more links to fill in that expectation for next time, or tweak names of things to match.

## Querying information
The structure in inherently query friendly. To find a book you read last month, you can start with the book concept, then sort the backlinks by date. Or you can start by the type of book, or author.

# Notes
The conceptual knowledge format makes structured data really easy, but it can also work for unstructured notes as well. This is where the `from` relationship really shines. Here is a simple structure for programming notes.

``` mermaid
flowchart LR
	programmingnotes[programming notes] --is--> note --is--> concept
	programmingnotes[programming notes] -.from.-> programming --is--> concept
```

Here's a more elaborate set of notes.

``` mermaid
flowchart LR
	pythonnotes[python notes] --is--> note --is--> concept
	pythonnotes[python notes] -.from.-> python --is--> programminglanguage[programming language] --is--> concept
	programminglanguage[programming language] -.from.-> programming --is--> concept
```

## Difference between notes and concepts
In general, concepts are things you know so well, you don't need to write notes about them. They serve as anchor points for your notes.
