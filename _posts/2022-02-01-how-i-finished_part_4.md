---
layout: post
title: "How I Finished - part 4"
date: 2022-02-01
categories: dissertation advice
---

# On technology
Through an iterative and experimental process, I settled on a set of software and technology practices that helped me finish. Technolocy and software that got out of my way and helped me create helped me the most and in this post I describe the ways I made that happen. 

## Use software that helps
### _Pick software and create a digital eco-system that helps you work._
Was any one piece of software that I used particularly outstanding? Not really. But they all helped. For example, I used Microsoft OneNote for my dissertation journal because I can access it from my computer, iPhone, iPad, and from a browser. This helped make my dissertation journal more available and ready if I needed to get a bunch of anxious or scattered thoughts out of my head. That being said, I also bought a nice notebook and a [4-color pen](https://uni-pens.com/product/jetstream-4and1/). Somedays I wrote my dissertation journal out by hand and multi-colored doodles.

While software can help, beware of the "new-tool" or the "perfect-tool" trap. There will always be a new tool. It might be better. It might be worse. But all tools are equally worthless if they are not used. Pick one. If you don't like it, chances are you can port your work to a new tool. But, you have to pick one and keep going. I've definitely lost a lot of time investing in some new software because I thought it would solve all of my problems. Certainly, my dissertation journal helped me solved a lot of my problems. But that was a technique and an action - not OneNote specifically. I could have written my journal in MS Excel, or MS Word, or MS Access, or in a plain text editor. It was the action that help me finish.

There is a great deal of revision in a dissertation, including how you work. Iterate! Keep what helps you work and jettison what doesn't. 

The technology and the interfaces I used for my dissertation:
- Programming, analysis, and data storage
    - [R](https://cran.r-project.org/) and [RStudio](https://www.rstudio.com/): statistical programming and visualization.
    - [Python](https://www.python.org/): general programming and data processing.
        - [pycharm](https://www.jetbrains.com/pycharm/) --> [sublime text](https://www.sublimetext.com/) --> [jupyter notebook](https://www.anaconda.com/)
    - [SQLite](https://www.sqlite.org/index.html) and [SQLiteStudio](https://sqlitestudio.pl/): powerful open-source database platform and database management interface.
    - [MS Excel](https://www.microsoft.com/en-us/microsoft-365/excel): spreadsheets.
- Writing, communciation, and information management
    - [MS Word](https://www.microsoft.com/en-us/microsoft-365/word): Word processing.
    - [MS Powerpoint](https://www.microsoft.com/en-us/microsoft-365/powerpoint): Presentation software.
    - [OneNote](https://www.microsoft.com/en-us/microsoft-365/onenote/digital-note-taking-app/): Note taking software.
    - [LaTex](https://www.latex-project.org/) through [overleaf](https://www.overleaf.com/project): Document prepartion and type seting.
    - [Zotero](https://www.zotero.org/): Citation and reference management.
    - [Papership](https://apps.apple.com/app/papership/id631980748): iOS app for reading pdfs.
- Text editing, file replication, and utilities
    - [Notepad ++](https://notepad-plus-plus.org/downloads/): Text editor. 
    - [VS Code](https://code.visualstudio.com/): Text editor.
        - With VS Code I can edit and write python, R, sql, LaTex, and general notes. Integrates with git. VS Code is *VERY* useful.
    - [synctoy](https://en.wikipedia.org/wiki/SyncToy): File synchronization.
    - [robocopy](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy): Command-line utility for file replication.
    - [Git](https://github.com/): Software and manuscript versioning.

## Make starting each day a little easier
### _Have your computer open up your key programs right at boot up._

I have the following programs load when I turn on my computer:
- MS Word - so I can write my dissertation.
- MS Outlook - so I can respond to anything time sensitive, but I would close it shortly after.
- Firefox - so I can gather citations or launch a jupyter notebook.
- Zotero - so I can manage references and insert citations into my manuscript.
- RStudio - for analysis and visualization.

These five programs were key components to the work involved in my dissertation. (I would have made OneNote open at startup, but it works a little differently than other MS Office products.) Yes, in reality, I saved only five mouse clicks, but it was one less hurdle. Especially so with MS Word. It's already open, let's write a little in my dissertation, yeah?

## Use git
### _Version your code, version your manuscript._

I use git for both my dissertation code and my dissertation manuscript. I love checking in code. And major versions of chapters. I pay $4 a month for private repositories. I have no doubt that student plans exist. But again, now is not the time to cheap out. (I cannot remember the last time I paid less than $4 for a latte.) Git also lets you build webpages. Like this one! And you can start building a portfolio. And you can reover your work. Git has certainly saved me a time or two. 

## File backup and redundancy
### _Set up a backup plan for your code and your manuscript._

Make sure at least some portion of your backup plan is automatic. I try to practice "disposable computing". I've had my laptop since 2012. It's been all over the US and on three continents. I'd be sad if I were to lose or irepreprably damage my laptop. Because of my backup plan, I'd be back up and running in a few hours and minus a thousand dollars. As a result, the laptop is disposable at any time. 

My backup plan involved two external hard drives, a server on my university's campus (which is itself backed up nightly), Google Drive, Microsoft One Drive, Dropbox, and Git. In this backup schema, my most recent backup is never more than one hour old. This is out of convenience as I do not like working from Google Drive / Microsoft One Drive / Dropbox. I find those services to be too machine depenedent, stingy with storage space, and uppity if there isn't an active internet connection. And if I'm working from one service, I can't work from another. So, why pick any one cloud-based storage service when I can use all three as a backup?

TThe code for my dissertation and my dissertation manuscript is backed up to 7 different places. Yes, seven. Each at different sync periods. Some of the backup frequency is manual, and some is automated. When my computer is on, [once an hour every hour](https://docs.microsoft.com/en-us/windows/win32/taskschd/task-scheduler-start-page), a simple [batch file](https://en.wikipedia.org/wiki/Batch_file) is called that, using robocopy replicates my dissertation code and disertation manuscript to Google Drive, Microsoft One Drive, and Dropbox. I commit my code throughout the week and I commit my manuscript less frequently. Only my code and my manuscript is backed up every hour. It's the smallest storage-size wise of this project but the most sensitive. The data might take a few hours to create, but I can't create the data without the code.

I have two solid-state hard drives in my laptop. The OS and programs are on one internal hard drive (C:) and my code/data/manuscripts are on a seperate internal hard drive in my laptop (H:). Under this implementation, the laptop is replacable and I can easily swap the H drive to another computer should my laptop fail. 

I have nearly a terabyte of data on my H: drive and that is manually replicated tio two external hard drives. While my dissertation code and manuscript is never more than an hour old, my data backups are older. 

I use synctoy to maintain parity between local and remote resources and I use robocopy for replicating data. (SyncToy is no longer supported by Microsoft so I will be looking for a replacement.) In a recent release of robocopy, multithreaded copying was introduced which has dramatically reduced copy times.