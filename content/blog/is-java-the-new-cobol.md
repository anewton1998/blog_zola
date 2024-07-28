+++
title = "Java will be the New COBOL"
date = "2016-05-25"
tags = [ "JAVA", "COBOL" ]
+++

We can continue to debate this, but Java will be the new COBOL.

The "Java is the new COBOL" debate has been going on for about 10 years now.
And it's not just theoretical. There are companies catering to what they sense
is a shifting mindset in the enterprise programming world -- a mindset that starts with a premise
many of us would probably find unfamiliar: its time to switch from COBOL to Java.

If you want to know what I'm talking about, do a Google search for ["Java for COBOL programmers"](http://lmgtfy.com/?q=Java+for+COBOL+programmers).
You'll find lot's of resources for the COBOL programmer to learn Java. That highlights
two things: 1) there are still quite a few COBOL programmers out there (stunning, right?),
and 2) there is interest in moving them to Java, a language many of the cool kids
now find passé.

<!-- more -->

## The Scope of COBOL Today

COBOL is an old, old programming language, surfacing sometime around the cooling of the Earth's crust, as the legend has been passed down from generation to generation around the evening campfire. So to say that there are still COBOL programmers can be surprizing.

So how many are there? [Umm](https://www.quora.com/How-many-COBOL-programmers-are-left-in-the-US)...

> An estimated 2 million people in the world are currently working in COBOL; rough estimates put the US figure at around 20,000 people

Of course, there's no source for that, but the other stats seem to indicate there's a lot, *A LOT*, of [COBOL still running around out there](http://www.javaworld.com/article/2077835/guess-who-s-learning-cobol-.html):

> Some 75% of the world's businesses data is still processed in Cobol, and about 90% of all financial transactions are in Cobol, according to Arunn Ramadoss, head of the academic connections program at Micro Focus International PLC, which provides software to help modernize Cobol applications.

Surprizing? Given that there is so much COBOL out there and this
aging language's aging practitioners aren't getting any younger, some might say **ALARMING**. [Ritika Trikha](http://blog.hackerrank.com/the-inevitable-return-of-cobol/) is predicting an impending COBOL gap:

> But what’s not emphasized often enough is there’s a slowly increasing gap between the number of massive institutions relying on COBOL and its relevancy among programmers today.

And that maybe true if the law of supply and demand can be applied to COBOL programs needing COBOL programmers, as ITWorld has proclaimed: ["College students who learn COBOL make more money"](http://www.itworld.com/article/2694378/college-students-learning-cobol-make-more-money.html).

## Out: COBOL. In: Java

One might conclude, given everything I noted above, that COBOL is the new COBOL... or maybe that Java cannot be the new COBOL because COBOL is still king. But looking at the trends, Java may not be the new COBOL now, but it will be one day.

Here's one way to think about it. COBOL is what it is today because of the millions of man-hours that went into creating what we now call legacy business applications. Just think what hundreds-of-millions of man-hours of Java coding on today's business applications will yield 30 years from now?

I say hundreds-of-millions because for the last decade or so Java has been (and continues to be) the most popular language in the world:

1. Java's dominance on the [TIOBE Index](http://www.tiobe.com/tiobe_index) goes back to 2006.
2. It currently ranks #1 on the [PYPL](http://pypl.github.io/PYPL.html) Index.
3. On both of the Javascript-biased* rankings, [RedMonk](http://redmonk.com/sogrady/2016/02/19/language-rankings-1-16/) and [GitHut](http://githut.info/), it ranks #2.
4. It ranks #1 on [IEEE Spectrum](http://spectrum.ieee.org/static/interactive-the-top-programming-languages)'s rankings.

There are probably an order of magnitude more Java programmers now than there were COBOL programmers back in the day. And therefore the man-hours being put into code are far greater.

But numbers don't tell the whole story. COBOL's dominance didn't come from being the best programming language of the day but from targeting the average programmer. Rockstar programmers never fell for COBOL, but the vast majority of coders are not rockstars; they're more like Karaoke singers.

The same is true of Java today. It isn't elegant like Ruby, and it doesn't have the same level of functional ease like Elixir. But your average programmer tends to make a mess out of dynamic languages and is certainly not prepared to handle functional paradigms.

So where COBOL was geared toward report generation of fixed record manipulation and report generation, the big tasks of the mainframe era, Java (and importantly, its many frameworks) is geared toward the middle-tier problem of manipulating relational databases on behalf of a GUI (be it web, mobile or a REST endpoint).

As [C2.COM](http://c2.com/cgi/wiki?JavaIsTheNewCobol) puts it:

> Is Java the new Cobol? A good argument can be made that yes, it is. Considering the billions of lines of Cobol code that have been (or still are) in production; that observation should in no way be considered a slur. Java has succeeded in the marketplace (partially) because it is a language of its time; not one behind the times - or ahead of them.

## \*Notes and Asides

**Javascript-biased Indexes)** I say that RedMonk and GitHut language rankings are biased towards Javascript because they are based on GitHub code repository measurements, making them biased for two reasons.

First, as RedMonk points out, Javascript is used in the HTML of many of other projects where another language is really the dominant focus. So this inflates Javascript project and lines-of-code counts.

Second, the popularity of GitHub Pages likely inflates the Javascript numbers. Since all GitHub Pages are all GitHub repositories, any GitHub Pages site that might be about some other subject (take this blog for instance) would include Javascript files and thus inflate the counts.

**The Mind Boggles with the Confluence of Javascript and COBOL)** While we are on the topics of Javascript and COBOL, [this article at Ars Technica](http://arstechnica.com/information-technology/2016/05/who-put-this-javascript-in-my-cobol-node-cobol-thats-who/) on COBOL for Node.JS and vice-versa is interesting.
