---
layout: post
title: Software design - is it differnt from architecture, and why do we need it?
type: post
published: true
comments: true
---
This is the first article in a series that covers the contents of a training I developed (and taught) for over 7 years now. The training covers software design, using the Domain Driven Design approach as it’s basis. Why I chose Domain Driven Design is explained in a seperate article.

At the start of this first article of the series, I have to thank Ewald de Bruijn and Peter Schipperen who have provided a lot of help in developing and teeaching this material over the past 7+ years.

##An example
So, what are we talking about when we talk about software design? Let’s start by looking at an example of a software development problem.
Quite some years ago, I had a colleague who was working on software for a weighbridge system for a transport company. This is a relatively simple system, where a truck drives onto a weighbridge, it’s weight is determined, and a ticket with the weight is printed and handed to the driver.

![Weighbridge overview](https://dev-to-uploads.s3.amazonaws.com/i/9ngh429xlbn76r8vu27o.png)

The main actors on this system are the operator, who is responsible for weighing the truck, and the truck driver, who is driving the truck on and off the weigbridge, and gets handed the ticket before driving off.
The whole flow related to the picture above is described as follows:

*Trucks drive onto the weighing bridge. The operator checks the weight and prints a ticket with the weight. After receiving the ticket, the driver drives the truck of the weighing bridge so that the next truck can come in.*

The software for this system consisted of 4 main packages

* User interface
* Printer Queue
* BridgeInterface
* Printer Driver

![Weigbridge packages](https://dev-to-uploads.s3.amazonaws.com/i/bipqx81p0610ipru1x4g.png)

The customer of this simple software application asked to extend the text driven user interface with a simple menu to replace hand type commands, and a reporting function to get an overview of the weighings of the past 4 hours.
This turned out to be a small problem, because the controller board had only 2kb of memory left and we needed 20kb for the software change. Yes kb, this was the 1990s, when a 1 megabyte RAM module still cost around 200 euros.

![Weighbridge classes](https://dev-to-uploads.s3.amazonaws.com/i/gfj7508l6khmsbws27xq.png)

Looking at the software, which is abstracted in the diagram below, my colleague wondered what could done to reduce the amount of memory used by the existing application. It took a little bit of thinking and discussion, but in the end the solution was very simple.

Looking at the usage scenario, it’s pretty obvious that the printer queue has no purpose here. At any point in time there is only one print job in progress, since no truck can enter the weigh bridge before the one on there receives its ticket and drives off. So removing the queue and the related software easily solved the memory problem.
This is an example of how easy it is for a designer to thinking in solutions, which isn’t a bad thing in itself, but at the same time loose track of what is really needed. It pays off to keep in mind who you develop the software for, your stakeholders, and what problem they try to solve.

This is one of many pitfalls in software design, all of which are avoidable as long as we are aware of them and apply the best practises for avoiding them.

##Design
To clarify that a bit further, let’s have a look at what software design actually is. There are many definitions, but the one that works best for me is the following:

*“Software design is the process of defining software structure and the related behaviour that satisfy both functional and non-functional requirements of our stakeholders”*

That definition covers, for me, the most important aspect of software design.

First of all, design is a process, more than (what is commonly assumed) the outcome of a process — ‘the design’. ‘The design’ is never finished, that’s what is most important to realise here: during creation of the software, the design will change due to new requirements, new insights. 

After creation, there will again be requirements that lead to more changes. As such, the process is more important than the result. In fact, there is nothing that can be called the results, all so called resulting designs are intermediate designs at best. I put that a bit black and white, but in essence it’s true.
If we do want to talk about the result — and of course we do — I talk about the design model, which is an abstraction of the software solution expressed in tables, text or (preferably) diagrams that help software developers to create software that covers the issues addressed during design.

Second, design should cover both structure and behaviour of the solution. A block diagram, class diagram, package diagram by itself is NOT the design model of the software. It has to be clear how the software behaves, if only because the days of simple, sequential mainframe or BASIC programs has long past. Most modern software systems handle data streams and events, and deal with things happening in specific order, or in parallel. If that behaviour is not matched to the structure, there is no design model that will help us implement the actual software.

Third, the functional requirements provide little need for explanation. Of course, every software solution has to provide the functionality required by it’s users. However, we have to make sure that we cover the required functions, but also the necessary functionality to deal with errors of any kind that may realistically occur.

That brings us to the fourth and final element. We have to deal with non-functional requirements, or quality attributes. These cover what some people call the ‘-ilities’ even though not all of them have a name that ends in ‘-ility’: functionality, reliability, usability, robustness, fault tolerance and so on. The notion of dealing with errors as described above shows that functionality and quality attributes (fault tolerance in this case) go hand in hand, and practise shows that this goes for any combination of quality attributes.
In the end, in our design process and the resulting design model, we will cover choices that allow the resulting solution to balance all quality attributes that are relevant for the system at hand.

##Architecture
So, now that we know what software design is, how does it differ from software architecture?

Well, let’s start with the definition of architecture as given by the IEEE 42010 recommended practise for architecture description:

*“Architecture is the fundamental organisation of a system embodied in its components, their relationship to each other and to the environment, and the principles guiding its design and evolution.”*

In essence, despite the heavier wording, this is not so different from design. The main difference is that in larger systems, an architecture defines the overall structure of a software system, including guidelines for more detailed design work within that structure.
This is mainly put in place to translate higher level requirements, sometimes (almost) on the meta level that the designs of all parts of the system must adhere to.

As an example:

A large company has a software system that has been developed over a period of more than 20 years. It covers millions of lines of code, and in order to keep things manageable, their lead architects have set up a basic structure and a set of guidelines that should be followed by all designers when extending or modifying the system:

* The software is divided into layers, where higher layers are further removed from the underlying hardware than lower layers — say the highest layer is the user interface, while the lowest is at the device driver level
* Within each layer, they defined building blocks, because the layers are cross cutting across serveral functional areas (which are orthogonal to the layers)
* Within the building blocks, which may be quite large, they defined the concept of components, which are small, dedicated software pieces
* Layers, building blocks and components have well defined, managed interfaces
* Each layer, building block and component has an owner, typically an architect or a senior software engineer
* Modifications to the interfaces cannot be made without consent of the owner, and this is actively managed through authorisations on the version control system

![Layers example](https://dev-to-uploads.s3.amazonaws.com/i/h37z7neqfb0pdus7c6um.png)

Of course, this is a very simple example, in modern architectures there are much more complex rules and guidelines than this. Just think of the security related guidelines that (should) apply to systems that manage our personal data and/or are connected to the internet. It’s those guidelines that are prescribed by the architecture, and that are to be followed in the designs that detail the parts of the architecture.

On a closing note, I’d like to stress that architecture and design are both needed to develop proper software that stands the test of time and quality. In the past 20 years, I’ve seen a lot of people trying to without either one of the two, and the results are not exactly positive. Doing architecture, and doing design does not necessarily mean you have to do a lot of paper work. It’s mainly about setting up structural and behavioural rules for your solution, a framework that matches your needs and those of your customer. In follow up articles, I’ll elaborate on that — combining 25 years of working on software and systems architectures with the ideas of Domain Driven Design.


