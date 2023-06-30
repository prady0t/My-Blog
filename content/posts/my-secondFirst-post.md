---
title: "Status Report"
date: 2023-06-30T12:42:28+05:30

---

# What am I working on?

___
*This blog was created by the collaborative efforts of, my long dead writer spirit, the usual insomnia and some mixed tech experiences.* 

*I was going through the internet (surfing the web in Latin) when I came across personal blogs websites created by people, where they wrote pretty intreating stuff. At first I was sure it's not my thing, like writing soo much for whom?
Whose gonna read your your distilled liquid-gold of content that was curated as a result of your hours and hours of intense failures just to make a stupid calculator work! (Well that's not what I thought in my head I just framed it like that, I don't think self contradicting statements. Or do I?)*
___

```py
print("Hello World!")
```
So yes a formal intro. Let me write down things that I'm currently working on, that way I'll be compelled to finish every time I read this blog. 

### ***1. Go:*** 

I started learning Go because I wanted to contribute to some cool cloud native projects. I came across cloud native when I was fiddling around public GitHub repos. I was looking for projects that matches my tech stack (C++ only at that time) and also tickles my fancy, it became more and more difficult as most of the c++ projects were pretty overwhelming to start with.

 It was long overdue that I  start learning new technology as it was already beginning of my 4th sem of college. Right when I was at the brink of my existential crisis, I came across cloud native (a cool senior guy introduced me to Docker and Kubernetes)  it was not that appealing at the start, but gradually as I started learning, I started getting more and more involved with it. Wait, why am talking in past tense? I'm currently learning cloud native tech but I'll elaborate more on that later in this post.

`tl;dr ` -> Since most of the cloud native, CNCF projects are written in Go, I started learning Go.

I made a quiz game yesterday that comes with a timer for every time you start it, using channels and goroutine (yeah it's that recent). I'm currently working on making a URL shortener. All these projects are parts of an online free course called `Gophercises`: https://gophercises.com/ 

### ***2. Sympy:*** 

I came across this awesome python library called Sympy. It's a library for symbolic mathematical calculations. It's soo powerful, you can literally do fourier transforms in python by just using some predefined functions. It's 100% python codebase is really well modulated and organized with sufficient examples and useful documentations.

I started contributing to it. I was basically looking around, researching over an issue some dude opened, when I found out another major bug! Sympy was not able to tell weather a number is a transcendental number or not. It can do so for algebraic, rational, irrational etc. but due to some reason it just wont work for transcendental predicates. So I opened a new issue, maintainers commented on it, I brainstormed my way to find the solution and voilà, I did successfully found out the missing implementation and an improper import. So I made a PR and now I'm currently waiting for it to get merged.

Since I was new in Sympy, I made lot of mistakes along the way like adding unnecessary indents, incomplete test cases, failed CI tasks etc. so  currently working on fixing these things.

### ***3. Kubernetes:*** 

I started learning Docker and Kubernetes earlier this month. I've worked up on the basics and fundamentals. I watched videos of  "Tech world with Nana" and "Kunal Kushwaha", these peeps are very helpful while learning cloud native. 

Currently I've thought of starting to contribute to `kyverno` project, it's a CNCF sandbox project. It's basically a policy checker for kubernetes manifest files. It's really interesting and beginner friendly. I've started reading it's docs, i'll set it up locally soon for usage and development.

One thing that really needs to be get done with is setting up a cloud instance (on AWS most probably). I've been using kubernetes until now locally using minikube, which provides a single node cluster. Now it's really the time I get my hands dirty with multiple running clusters. 

### ***4. GSSoC:***

Girl Script Summer of Code. It's an open source event for beginners. I was really interested at the beginning, but now I find it a bit sketchy. Like you have to open an issue, it will be assigned to you and you'll have to work on it. People are working on random, most irrelevant things there and there are a lot of spamy PR's to get on top of the leader-board. So I decided to not take it seriously. Although I did work on one of their projects on web scraping and added functionality to scrape articles from Hacker News. It was kinda cool.

---

That's about it. Coming month, I'm trying to get more involved with CNCF community and find good projects there. LFX mentorship's fall term's applications will open in August. I really hope I make it to LFX this time as last time my application was rejected.

 I've also decided to write these status reports every month's end so that I can keep a track of my progress (given if there's any).

![Alt text](/static/moo.png)
