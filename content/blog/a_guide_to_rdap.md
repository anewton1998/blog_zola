+++
title = "A Guide to the Registration Data Access Protocol (RDAP)"
date = "2024-08-11"
tags = [ "RDAP", "Whois", "Domains", "IPs" ]
draft = false
+++

Earlier this year I heard Simon Fernandez, a cybersecurity researcher, give a talk on his paper
["WHOIS Right? An Analysis of WHOIS and RDAP Consistency"](https://pam2024.cs.northwestern.edu/pdfs/paper-89.pdf).

During his talk, he made an aside about the scattershot nature of the RDAP specifications and how hard it
can be for one person to know where everything is documented. And it is a problem because he is not the only
one to notice it.

Around that time I stumbled upon [mdbook](https://github.com/rust-lang/mdBook), which is the tool used to
publish many of those fantastic [Rust webbooks](https://doc.rust-lang.org/book/). mdbook is actually an ecosystem
of open source software designed to make the publication of webbooks easier.

And so, wala! Introducing a free, open source webbook on RDAP, _**[A Guide to the Registration Data Access Protocol](https://rdap.rcode3.com)**_. 

It not only covers the specifications, but also has a quick reference to all the relevant RFCs and IANA registries
and a list of all known RDAP software. Plus, it's a living document, can grow with time and need, and anybody can
contribute to it.

I hope this helps all the future researchers, users, and developers who want to learn this rather esoteric topic,
one that is likely to become more important as the [Whois sunset](https://en.wikipedia.org/wiki/WHOIS#:~:text=The%20date%20for%20WHOIS%20Sunset,set%20as%2028%20January%202025.)
approaches.
