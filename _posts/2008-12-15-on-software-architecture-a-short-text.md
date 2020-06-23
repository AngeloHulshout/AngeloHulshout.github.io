---
layout: post
title: Software architecture - a short text
categories: [architecture, software engineering]
type: post
published: true
author: Angelo Hulshout
---


Here's a transcript of an e-mail I sent to one of my students, who asked input
for a presentation on the topic 'Why do we need software architecture'. It may
be a no-brainer to some, irrelevant or uninteresting to others, but I feel
this is a nice summary to use as a starting point for explaining the need for
architecture.

> Hello X,
>
>I'll start with a short answer, otherwise you end up with a book. Feel free to
ask additional questions when necessary.
>
>First of all, we are very capable of building things, including software,
without architecture. However, often this means that these things are either
reasonably simple in nature. If they are not simple, they can still be build
without architecture, but in that case we're bound to find out they are
lacking in quality in certain areas. These quality areas can be for example  
>
>  * maintainability: it's hard to extend something that has been build up piece by piece without thinking about structure). Extending such programs is difficult, if possible at all, and subject to lots of trial-and-error excercises  
>
>  * reliability: software build without a plan is often (not always) build with a focus on functionality. In those cases, error handling, robustness tend to be second class citizens, resulting in unreliable solutions. A good example are so called 'friendly user' applications: applications that work only if the user knows what the application expects and sticks to that order. There's no error handling in case a user makes a mistake there. Quite a few old Unix scripts and command line programs suffer from this problem.
>
>These are just two examples of quality aspects that are part of an
architecture, which cannot be added _after_ the application has been build.  
Architecture deals with the structure of a (software) system, in terms of it
's decomposition into elements and the way these elements are connected and
co-operate. This structure is, as the examples above show, determined not only
by the functionality of the system, but also by so-called -ilities or quality
attributes.  
In real life, this implies that we need to think about these aspects, which in
turn are determined by the needs of the environments in which the system is
build, produced and used. Finding out the key needs of those environments, and
translating them into quality requirements and a proper design for a
(software) system is what is software architecture is about.  
The amount of environmental needs introduced by stakeholders from the
different environments, the amount of quality aspects they translate into -
including functionality - and the infinite solution space makes software
development into something complex, and software architecture tries to deal
with this complexity.  
It should be noted however, that software architecture is a discipline with
many faces. Some people go for what the agile community calls 'BDUF, or Big
Design Up Front' - resulting in large models and big documents. Others go for
the opposite, following Scrum and eXtreme Programming to the maximum extend -
without much documentation. In both cases, architecture plays a role though,
because both approaches take into account the needs of the different
evironments the system goes through in it's life cycle (conception,
development, production, use, …).
>
>Best regards,
>
>Angelo


