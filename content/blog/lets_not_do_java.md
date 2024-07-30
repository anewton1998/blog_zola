+++
title = "Let's Not Do Java"
date = "2024-07-30"
tags = [ "Scala", "Rust", "Kotlin", "Java" ]
draft = false
+++

Eight years ago I wrote ["Java will be the New COBOL"](https://blog.rcode3.com/blog/is-java-the-new-cobol/),
but that may have been more pejorative than COBOL deserves.

In [Java is Becoming What COBOL Was - Will It Become What COBOL Is?](https://www.javacodegeeks.com/2018/06/java-becoming-cobol.html),
Mike Siemasz writes:

> Some involved in the COBOL project advocated for abandoning design efforts and starting anew. 
> Others criticized COBOL for its “semantic verbosity, its syntactical redundancy, and its overall 
> lack of linguistic elegance,” Kurt Beyer writes in his 2009 book, _Grace Hopper and the Invention 
> of the Information Age_. The most insolent critics suggested COBOL would fail simply because women 
> played a large role in its inception.
> 
> They were all wrong.
>
> Eventually pushing past its precarious, underdog position, COBOL blossomed into the standard 
> business programming language. Within its first decade, it was being used globally more than 
> any other programming language, and it has lived long past its anticipated expiration date, 
> being widely taught to new programmers throughout the ‘70s and ‘80s as a leading-edge technology, 
> being core to ‘90s computing as the world prepared for Y2K, and remaining essential today as the 
> underpinning of the world’s largest, most complex and most important applications.

Yeah.... maybe I should not be dunking on COBOL.

{{ image(src="/blog/lets_not_do_java/andrew_oliver_tweet.png", alt="Andrew Oliver Tweet", position="center")}}

Ok, that's not exactly what I meant either. In my post eight years ago, I used data to predict that Java
would soon start dying. Today, we have data that it is.

<!-- more -->

## The Indices

Java was long considered the most used and most popular programming language, dethroning C during the dot-com boom years.
However, the indexes that track such things now show a definite decline.
On every single one of them, Java is in decline... in some cases quite dramatically.

| Index                                                                         | Previous Date | Previous Position | Current Position |
| ----------------------------------------------------------------------------- | ------------- | ----------------- | ---------------- |
| [TIOBE index](https://www.tiobe.com/tiobe-index/)                             | 2016          | 1                 | 4                |
| [PYPL](https://pypl.github.io/PYPL.html)                                      | 2016          | 1                 | 2                |
| [Redmonk](https://redmonk.com/sogrady/2024/03/08/language-rankings-1-24/)     | 2016          | 2                 | 3                |
| [IEEE Spectrum](https://spectrum.ieee.org/the-top-programming-languages-2023) | 2016          | 1                 | 2                |
| GitHut / [GitHub Top 30 Programming Languages](https://innovationgraph.github.com/global-metrics/programming-languages) | 2016 | 1 | 5 |
| [Stack Overflow](https://survey.stackoverflow.co/2024/technology)             | 2018          | 3                 | 7                |
| [JetBrains Survey](https://www.jetbrains.com/lp/devecosystem-2023/languages/) | 2017          | 3                 | 5                |

Looking closer at the data, it gets worse. While Javascript was the main contender against Java eight years ago, today it is Python with
almost twice as much usage as Java. The Javascript to Java comparison was always an "oranges to apples" thing as neither filled the
same space, but that is not true when comparing Java to Python. That is, while Javascript was primarily used in browser applications where
Java was not viable, both Java and Python occupy the similar non-browser, runtime-required application space.

Adding insult to injury, there is also an interesting tidbit in the [JetBrains Survey](https://www.jetbrains.com/lp/devecosystem-2023/languages/).
Based on salary, it was found that both Scala and Kotlin developers are generally more highly paid than Java developers
despite all three languages running on the JVM... and many of the Scala and Kotlin applications using Java libraries.

{{ figure(src="/blog/lets_not_do_java/jetbrains_highest_paid_2023.png", alt="GitHub 2023", position="center", caption="JetBrains Highest Paid 2023") }}

You can find the index charts in the Notes and Asides section below.

# Conclusion: The Old and Busted

I once worked at Amazon (I mean, haven't we all at this point). It was during the industry's hiring frenzy circa 2021, and
in one year I ended up interviewing over 70 college graduates and interns. In that experience I noticed a trend: nearly every one of them
opted to do programming interviews in Python... Java was seldom the preference. And it was quite common to have new hires that had never
used Java at all, even in previous jobs or in academic classes.

That seems to match the programming indices mentioned above. That seems to match the industry trend. That seems to be the way things are going.

# Postscript: Poor Oracle Stewardship

Oracle purchased Sun Microsystems, the creator and steward of Java, in 2010. After the acquisition, Oracle sued Google a few months
later over Google's use of Java APIs but not any of Oracle's code. Google won the lawsuit 11 years later, but the episode
highlights Oracle's willingness to leverage its ownership of Java for profit in extreme ways.

Oracle began charging commercial licenses for its Java implementation in 2019, with continuing changes to the licensing terms in
2020, 2021, and 2023. That's right, if you use Oracle's Java you'll need lawyers and accountants to review some new Oracle profit scheme
nearly every year. There are, in fact, 
[companies that specialize in Java license consulting](https://redresscompliance.com/decoding-oracle-java-licensing-java-licensing-changes-2023/):

> In 2023, Oracle Java Licensing requires that organizations purchase a license for their entire employee population if even a 
> single employee or server has installed a licensable version of Java.

What's going on here? Well, Dave Kellog has [a great post](https://kellblog.com/2009/03/24/oracles-become-computer-associates-ca-2/) that begins:

> * I’ve become my parents,
> * SQL has become Cobol,
> * and Oracle has become CA

Go read [it](https://kellblog.com/2009/03/24/oracles-become-computer-associates-ca-2/), especially as it predates Oracle's acquisition of Java.

# Notes and Asides

## Rust Moves Up

In July 2024, Rust moved up from 17 to 14 in the [TIOBE Index](https://www.tiobe.com/tiobe-index/):

> This month, high-performance language Rust jumped from position #17 to position #13 in the 
> TIOBE index. This is an all time high for Rust. Gaining 4 positions might seem a small change, 
> but Rust has been "the talk of the town" the last couple of years without making much 
> progress in the TIOBE index. Rust is finally moving up.

And on the July 2024 PYPL index, Rust breaks into the top 10.

## The Index Charts

{{ figure(src="/blog/lets_not_do_java/tiobe_index_july_2024.png", alt="TIOBE July 2024", position="center", caption="TIOBE July 2024") }}

{{ figure(src="/blog/lets_not_do_java/pypl_july_2024.png", alt="PYPL July 2024", position="center", caption="PYPL July 2024") }}

{{ figure(src="/blog/lets_not_do_java/ieee_spectrum_2023.png", alt="IEEE Spectrum 2023", position="center", caption="IEEE Spectrum 2023") }}

{{ figure(src="/blog/lets_not_do_java/github_2023.png", alt="GitHub 2023", position="center", caption="GitHub 2023") }}

{{ figure(src="/blog/lets_not_do_java/stack_overflow_2024.png", alt="GitHub 2023", position="center", caption="Stack Overflow 2024") }}

{{ figure(src="/blog/lets_not_do_java/jetbrains_highest_paid_2023.png", alt="GitHub 2023", position="center", caption="JetBrains Highest Paid 2023") }}

## Indexes or Indices

As Liam Lynch would [say](https://youtu.be/Xz7_3n7xyDg?si=Qr6lZKQ_VWWeme5w), 
"Yeah, [whatever](https://stackoverflow.com/questions/1378781/proper-terminology-should-i-say-indexes-or-indices)!"
