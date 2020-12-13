---
layout: post
title: The Closed Loop
type: post
published: true
comments: true
---

![Photo by Lars Kienle on Unsplash](https://miro.medium.com/max/1400/1*0Rlb9pV2Vx7YfEs3FlEPRQ.jpeg)

In software engineering, and specifically in software architecture, we spend a lot of time talking about patterns, architectural styles and other rules and guidelines. Over the past 25 years, and before, a lot of books and articles have been written about those, covering all aspects of software engineering. All of this is very useful, but it can also be overwhelming and sometimes appear quite complex. That's why every once in a while, I enjoy going back to very basic principles. Basic, as in simple, effective, and often so obvious that they often get overlooked.
Recently, during discussions of the sofware architecture for a new project, I came across one of these principles again. One that is so obvious, and yet so often overlooked in software design: the closed loop.

The closed loop is a principle that is very common in in electrical engineering, and specifically in control systems. In such systems an actuator, e.g. a motor, is given an input signal. That is supposed to trigger a certain action that results in an output signal. Part of that output signal is fed back to the component that generated the input signal, to ensure the system is behaving as expected.
Depending on the type of actuator, it may be needed to add a sensor to detect the action and provide the output and thus also the feedback signal, but the principle stays the same. In the case of the motor that starts moving on an input signal, the feedback could for example come from a motion sensor that detects movement on whatever the motor is supposed to drive.
In software, and cerainly in larger systems, I see the results of the lack of such closed loops. All to often we trigger an action, set something in motion and never check the result. This leads to unexpected behaviour - not just in control applications, but also in web applications, or even (the tax agency will love this) in book keeping software. This, while all it takes is following one simple rule in design and implementaition:
Close the loop: trigger an action, and verify whether it is executed correctly.

Some very simple examples from different application domains:
Signal the start of a motor: verify it is moving by checking the output of a motion sensor or cycle counter
Trigger a database transaction: check the result of the commit (Yes, I know it's obvious, so why do so many applications skip this check?!)
Stop a process: verify it is no longer running after a specified timeout (even Microsoft Teams forgets to do this - just try switching between accounts a few time)
Send a message on a message queue: check the result of the queueing function, and design your protocol to return an ACKnowledge message to be returned

It's basic, it's simple and feels like an open door, but as said, I keep running into violations of this very basic principle. The excuse is often: yes, but we tested every possible situation. That's wrong - no manual test, nor any automated (unit) test framework will ever cover every situation until the day the software becomes end of life. Don't fool yourself!
And now I'm curious to who shares this experience. Would you care to have a look at your own last project and let me know in the comments if you are convinced that you closed every loop?