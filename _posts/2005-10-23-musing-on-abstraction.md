---
layout: post
title: Musing on abstraction
categories: [architecture, software engineering]
type: post
published: true
author: Angelo Hulshout
---

The following is a musing on the concept of abstraction - I'll be refining it
over time…

A short while ago, I was involved in the creation of a product roadmap, and
budget discussions for the first year of implementing that roadmap. A
discussion that kept recurring in different settings during this process
focussed on a concept that been at the center of dicussions on software
engineering for years:

**Abstraction**

In another discussion around the same time, on Operating System Abstraction
Layers and Hardware Abstraction Layers (OSAL and HAL), the same topic popped
up, showing another set of examples of how people talk about, think about and
use abstraction. This triggered me to write the following short text about one
of the most dangerous concepts in software engineering…

Abstraction is one of the tools of the software architect - next to
generalisation, composition, and others. Within the architect's toolbox,
abstraction is one of the most dangerous tools. It's about as dangerous as
generalisation, but at least generalisation has some sort of negative sound to
it that warns people to apply it with a bit of care. Abstraction doesn't have
that sound to it, instead it is mostly seen as a way to simplify things and
make it easier to reason about certain problems.

As we know, dictionaries tend to describe the same word in different ways, but
most definitions of abstraction in our context as software and system
engineers can be translated into something like 'removing unnecessary detail
in order to create an understandable view of a problem'.

First of all, this way of regarding abstraction is correct, but while it is
intended to be applied in design of an architecture, it is often applied in
discussions around the design process. A good example of this I found in the
roadmapping and budget discussions, where management wanted to get initial
effort estimation for development of a new subsystem. The date set for that
product was set about two years in the future and initial feasibility studies
had not started at the time. As a result there were just as many opinions on
how to design the system as there were people involved in the estimation
discussions. The only way out in such a situation - given that management does
not take 'no estimation' for an answer - is by involuntarily applying
abstraction. The subsystem is subdivided into chunks, called hardware and
software and rough estimations based on functionality implemented in each of
these are made up and discussed.

A lot of things get lost in this process - including attention for the system
architecture, and it's spin-off, such as such as selection of a useable
(embedded) operating system.

When estimating software development efforts, engineers assume an operating
system to be present, so the selection and evaluation process - which does
take time and money - is not made part of the estimation. Luckily we noticed
this, but the risk of oversight is evident, given that an operating system was
in use for existing products (hey, it's there, so why bother selecting another
one).

**On reconsidering this - about a month after the initial posting, I must add
that there's another factor that is not helping us here. At estimation
meetings in the organisation I'm talking about, there's usually about 6
engineers involved in estimations, but often none of them brings or creates a few design figures as input for the meeting. Everything is done from the top of people's heads.**

Another example comes from an architecting assessment a longer while ago. A
company developed a product consisting of two carts, both involving a number
of electronical, mechanical and software parts. At some point, with cost
reduction on the bill of materials in mind, the software architect came up
with the idea to run all software, except for some communications related
stuff, on one processor, in one of the carts. Effectively, this meant that one
cart would get a better processor, and the other one would get a simple
microcontroller - with a slight reduction of material cost as a result. Since
the two carts were designed only for end user logistics purposes, and the two
were only used in conjunction, this looked workable.

What was not taken into account, because it was abstracted away, was the fact
that the product also had to be assembled and tested before delivery. This was
done at the manufacturing site, where the following problem occurred: one cart
was assembled in about half the time as the other one. Because only one of
them ran all software, both carts were needed for delivery testing. Because of
the difference in assembly time, a queue of carts developed at the test
center. This resulted in costly changes to the assembly lines, and less
manufacturing throughput.

Combined with the fact that the simple microcontroller was not powerful
enough, the anticipated material cost reduction turned out to be an over-all
cost increase. One could argue that this is not a matter of abstraction, but
of not taking into account the full scale of the problem. In a way, I think
this is still a form of abstraction, because abstraction leads to
simplification, and in this case, oversimplification of the problem statement.

Because of these examples, and a few others, I more and more getting to the
conclusion that we should be very careful when applying abstraction in our
work. Abstraction introduces the risk of oversimplification, and
oversimplification makes us miss the important details.



