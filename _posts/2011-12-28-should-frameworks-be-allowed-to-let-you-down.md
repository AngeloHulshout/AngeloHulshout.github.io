---
layout: post
title: Should Frameworks be allowed to let you down?
categories: [abstraction, architecture, code generation, software engineering,vision]
type: post
published: true
author: Angelo Hulshout
---

Ever since I came across [WebDsl](http://www.webdsl.org "Webdsl"), almost
three years ago, I've been wanting to use it for at least one of the web sites
I maintain (four at the moment, with a fifth underway). However, since so far
I've relied on the services provided by hosting providers, I've been stuck in
the world of [MySql](http://www.mysql.com) and [PHP](http://www.php.net),
where as [WebDsl](http://www.webdsl.org) targets
[Java](http://www.oracle.com/technetwork/java/index.html) and
[Seam](http://www.seamframework.org/) platforms. A mismatch if ever there was
one. During [CodeGeneration 2009](http://www.codegeneration.net/cg2009) I
asked [Eelco Visser](http://www.eelcovisser.org) whether there were plans for
extending [WebDsl](http://www.webdsl.org) into the [PHP](http://www.php.net)
domain. He indicated that there were
[ideas](http://webdsl.org/singlepage/ProjectIdeas), but no concrete plans. Up
till now, that is how things stayed - the project's focus was more on
extending the language and providing [proper development tool
support](http://webdsl.org/selectpage/Download/WebDSLplugin) then switching to
different platforms.

So, after fiddling around with various tools, including
[MetaEdit+](http://www. metacase.com), [MPS](http://www.jetbrains.com/mps) and
[XText](http://www.xtext.org), and always ending up doing things the old
fashioned way, simply because I didn't have the time (or rather take the time)
to develop a proper solution I decided that maybe I should finally look into
developing that [PHP](http://www.php.net) backend for
[WebDsl](http://www.webdsl.org) myself. Of course, nothing comes for free, and
my time is very limited, so I will be investigating the feasibility first,
before starting. [Danny
Groenewegen](http://swerl.tudelft.nl/bin/view/Main/DannyGroenewegen) and
[Eelco Visser](http://www.eelcovisser.org) helped me on my way today, by
providing some initially ideas on how to attack the implementation side, and
by pointing me to an interesting short research paper they wrote: [When
frameworks let you
down...](http://researchr.org/publication/GroenewegenHKV08-DSM)

In this paper, they indicate that the [WebDsl](http://www.webdsl.org) DSL was
built as a very thin wrapper around [Seam](http://www.seamframework.org/),
They continue to explain how this made it difficult on one hand to keep the
DSL in sync with the framework (they wanted more and different things than
Seam could provide out of the box). On the other hand, because the concepts
supported by [Seam](http://www.seamframework.org/) show through in the
[WebDsl](http://www.webdsl.org) DSL in certain points, it may also be not-so-
trivial to replace the target platform with e.g. the [PHP](http://www.php.net)
[CodeIgniter](http://www.codeigniter.com) framework which I would like to see
supported. Come to think of it, things might get worse if I would add
something like [qooxdoo](http://www.qooxdoo.org) or [ExtJS
4](http://www.sencha.com/products/extjs/) for the user interface.

So, in the next few days, I'll have a thread running in the back of my head,
thinking through these issues and defining the steps to be taken. In fact,
even if my time is limited, I might just be able to spark the development of a
very useful extension to [WebDsl](http://www.webdsl.org), that would bring
both this tool and the benefits of model driven software development to the
far-from-small domain of [PHP](http://www.php.net) based web sites (I haven't
found any up to date statistics, but at least [Google
Insight](http://www.google.com/insights/search/#q=%22web%20programming%22&date=1%2F2011%2012m&cmpt=q)
indicates that PHP is the most searched for web programming language - for
what it's worth).

I'll keep you posted on further developments in this area, shortly.









