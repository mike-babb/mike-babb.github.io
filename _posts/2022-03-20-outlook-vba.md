---
layout: post
title: "Outlook and VBA"
date: 2022-03-20
categories: microsoft, outlook, vba, automating
usemathjax: true
---

# Still VBA?
This is an exploratory post. In a nutshell, I need to automate some processes in Outlook. I know I can do that with Visual Basic for Applications (VBA). And I have. As a matter of fact, VBA was the first programming language I learned. So, in that regard, I've been using VBA for close to 20 years! I was tasked with automating some processes in ArcMap. I think it was version 8.3. Python, while on the scene, wasn't the most robust. And the GIS shop I was interning with built custom applications using VBA. So I learned VBA. A year or two later I learned that the Microsoft Office Applications have a built in VBA editors (Alt+F11, anyone?). These are usually called macros. While bad guys the world over have used macros to compromise computers and run malicious code, I have used these macros to extract data and apply formatting. 

Since then, I've learned a few more programming languages. And one constant between ALL of the programming languages I've used is that each programming language requires different way of thinking. Sometimes there are collisions between the design of one language and another. For example, I sometimes think ESRI, seeing the rise of python, ported the VBA object model to python. I say this without any confirmation, but because the ArcPy library is such a different way of working with python (it's *very* hierarchical) that it sometimes doesn't feel like python. But that's a different topic for a different time. 

With respect to automating outlook, I'd like to read all of my calendar entries and pipe them to a database. I've built this code before, it's currently on my hard drive (maybe in a git repo somewhere). But what database do I use? Well, SQLite would be nice, but that's a little more difficult than piping to an MS Access Database. That's right: we're using VBA with MS Access to read an outlook file and save the entries to Outlook! Why did I do this? The short answer is that it's the most straightforward. The longer answer is multifaceted: 
- I spend a lot of time in Outlook.
- Many times over the years, I have had to keep track of my hours.
- I dislike entering the same data in multiple spots.
- I desperately want to minimize the time I spend reporting my time.

So, 10-plus years ago I built a tool that reads my outlook calendar entries, parses the entries, and dumps the output to a database. From the database, I can then quickly generate an excel file to send to a client. Even better when I can build a form in MS Access and click one button to generate a report. So that's what I've done and over the years I've tweaked this codebase. 

I have no doubt there are other programs out there that do the same thing. Mostly likely web based, offer some proprietary technology, and come with steep subscription fees. The hell with that. 

My real innovation is that I can use VBA's limited string parsing library to format the data during extract. And the way this really plays out is the careful use of delimiters. I've found that nearly all of my time can be categorized as "category - activity." The category can be anything: a project, a class in college, a client, family, friends, or general to-do. The activity is something germane to each category. For example: prepare map of the Eastside development areas, write up chapter three notes, update slide deck for management presentation, buy a cake for mom, buy a cake for Tim, or take out the garbage. And outlook lets you segment your calendar into 15 minute chunks. This has always been an interesting way to think about time, my work, and what I engage with on each day. 

## Opening a database
I just opened my Access database and it looks like my code still works. 

The cool part about the outlook - database pipeline that I built is that I can import my calendar entries, my email, my tasks, my contacts, and my notes.

According to my DB, I have about 1.8K appointments defined. It takes a little less than a minute to import the appointments. 

The downside is that it's slow. Such is VBA. Is there something faster? A different language? Probably. Is it my ten year old code? More than likely. Could I query the server in a more direct manner? Still unclear.








