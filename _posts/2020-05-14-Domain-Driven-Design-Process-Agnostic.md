---
layout: post
title: Domain Driven Design - Method and process agnostic
type: post
published: true
comments: true
---
This is the second article in a series that covers the contents of a training I developed (and taught) for over 7 years now. The training covers software design, using the Domain Driven Design approach as it’s basis.

## On processes, methods and methodologies
As every experienced software professional knows, every organisation, be it a multi national, a startup, a small business, or even an open source project, has its own way of working. Often you find a mix of methodologies and best practises that has developed over time into something specific for the organisation. 

What those exact mixes are is beyond the scope of this article, but let's say that in most organisations you find a bits of waterfall, agile or iterative processes, mixed with functional or object oriented design, some form of requirements engineering and bits of various testing methodologies. The exact combination is beyond this article (and different in every case) but I have to address it. It was one of the reasons I first got in touch with Domain Driven Design, DDD for short. When I was asked by a customer if I could set up a training for software designers, I was confronted with the question which design method to follow. All candidates for the training were working on projects for different companies, on secondment basis. The implicaiton of that was that, although my customer would love ot promote a specific design approach, the course participants would be stuck to the way of working of the project and organisation they were working for. 

In disussions with a fellow trainer working at my customer, we concluded that the work a software designer needs to do, and the deliverables coming out of it, should not be dictated by this company specific approach. Instead, they should always be more or less the same, even if not all steps would be executed always in the same order - i.e. in a waterfall or in iterations. the work and deliverables in the end should be roughly the same. That's why, after a short research into existing approaches to software development, we settled on Domain Driven Design. DDD covers every element that we consider important for making a software design, in terms of activities, deliverables and patterns, and it can be fit in with any development process, no matter how modern or archaic.

What these are? It's a short list:

* Problem analysis - identifying stakeholders, system context and requirements
* Creating models - of the problem and solution space
* Creating the design itself
* Combining specific problems with generic solutions - technology choices, design patterns, re-use etc.

The web site DDDCommunity.org summarized it in a way that made it easy for us to select DDD - it literally said at that time (in 2012):

 __"The premise of Domain Driven Design is twofold:
 * for most software projects, the primary focus should be on the domain and domain logic, and
* complex domain designs should be based on a model

Domain Driven Design is not a technology nor a methodology, it is a way of thinking and a set of priorities, aimed at accelerating software projects that have to deal with complicated domains."__

## So what are these domains DDD talks about?
Domain is a word with two meanings when talking about software development using DDD, as far as I'm concerned. It can either mean problem domain or solution domain. If you do things the right way, the two almost become one in the end, as we'll see later.

* Problem domain: the organisation, process, environment in which the software is going to be **used**
* Solution domain: the organisation, process, environment in wich the software is going to be **created**

When we start a project, the funny thing here is that, as software engineers, we know a lot about the solution domain, but often far less about the problem domain. 
Let me use myself as an example. in over 25 years in software engineering I learned over 15 programmming languages, countless frameworks and design patterns, and many different technologies relatd to software development. At the same time, when I started working on a project (that is now about to end) 3.5 years ago for setting up the software to control a petfood factory, I knew close to nothing about petfood manufacturing. 

That changed a lot over the past 3.5 years, thanks in part to DDD. We used ideas from DDD (remember it's a way of thinking and not a methodoloy?) to clarify terminology, to set up functional descriptions, do design work, and now I not only know how the software works, but I can also explain how we get from raw chicken, cranberries, bone meal and barley to your dogs favourite food.

So what is so magical about DDD here? Well, plain and simple it comes down to is this. At the core of Domain Driven Design is a *model* - the *domain model*. It is a model of the problem domain, expressed in whatever notation you want. I use a derivative of UML often, but text or blocks-and-lines are equally possible. This model, and that's where the dark magic happens, is defined in such a way that eventually, you can implement it in code. So that means, your problem domain *model* becomes part of the software solution.

At the same time, working on the model, which in DDD is something you should do together with your customer as much as possible, builds up a common understanding of the problem, and later on the solution, with anyone involved. That means, you understand the problem customer and user are dealing with, and they understand your solution. Not that they can write software, but it is clear to them what you are creating and why - even in the externally invisible parts.

And to top it of, the terminology used in the model becomse a shared language between customers and engineer. When a customer or a user wants a change, he can express that in terms of the model, and similarly an engineer can explain a change being made using the same. This is what DDD refers to as the *Ubiquitous Language*.

# Example of what it looks like
The diagram below shows something from a first talk I had with the customer of the petfood factory 3.5 years ago. The terminology changed a bit in later talks, but this represents what a customer can tell you.

At a factory, new material comes in Trucks. Each truck has a load of material, which it has picked up at a certain origin. A lot is referred to as a Lot. Lots and origins are identifiable, because in case of problems (e.g. material contamination) all materials and products in which they are used need to be traced and dealt with. There are a lot of traceability related requirements that are serviced by making this things identifiable. Upon delivery, the truck dumps its load into an intake pit, and from there it is transferred to silos.

![Objects](https://dev-to-uploads.s3.amazonaws.com/i/yheqs50qo35varm8akzz.png)

This diagram is an object diagram, which contains very limited information. To add more information, what I usually do, is transform it into a class diagram after constructing it together with the customer, and keep only the parts that will be relevant in the software later on. This is what is shown in the class diagram below. In this case, the truck is not relevant in the software, it is an external entity passing by, while it's load is referred to as a lot and there is no need to keep both. Similarly, the intake pit is just a physical location where material passes by, that we are not really interested in. 
Purists may say that you have to keep these things anyway, but for me this is a matter of being practical.

![Classes](https://dev-to-uploads.s3.amazonaws.com/i/e4s5wjfcnjoyyjqq1lxl.png)

# DDD itself in a domain model
As an exercise in my trainings, I often ask trainees to look at Domain Driven Design itself, and create a basic domain model for it. This often results in something that resembles the diagram below.

![DDD Domain Model](https://dev-to-uploads.s3.amazonaws.com/i/ncy3cfv5wf363xjdrhpr.png)

I have no software based on this one, but one day I may put it into a wizard that guides newbies through the steps. Who knows...

# And how do you fit DDD into any process or method?
That of course is the main question - how does this fit in with any process or method that a company uses? The clue is in the four elements of the design activity we mentioned earlier:

* Problem analysis
* Creating models
* Creating the design itself
* Combining specific problems with generic solutions

As depicted in the diagram below, we can do DDD in an iterative way. The Problem Analysis is basically performed in interviews with stakeholder experts (customer, end user, representative), and captured in the domain model. The domain model is then extended with items from the solution domain into a design model, which is the basis for implementation. Finally the implementation gets tested, evaluated and used as input for further stakeholder talks. 

![DDD iterations](https://dev-to-uploads.s3.amazonaws.com/i/azkdkndxx2lsceb4asy1.png)

Now, only if someone would implement a pure top to bottom waterfall approach, this would be impossible to fit into their way of working. In an interative (Agile optional) approach this will fit in seamlessly, in a more waterfall like appraoch, there still is a feedback cycle somewhere that can be used to do this - and if not on project scale it can still be done on team scale or even between two or three developers and a stakeholde representative in some form. 

That basically explains how DDD ended up being the basis of my design training, but also of my own work since 2012. More in follow up articles.

[Register for my newsletter here](http://eepurl.com/g1oOaD) to be kept up to date with my articles and trainings, and interesting references to what else is going on in the field of software engineering.


## References
1. Domain Driven Design - Eric Evans, ISBN 0-321-12521-5 Addision Wesley 2003
2. Implementing Domain Driven Design - Vauhgn Vernon, ISBN 978-0321834577 Addison Wesley 2013
3. DDD Community web site: [https://dddcommunity.org](https://dddcommunity.org)