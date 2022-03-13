---
layout: post
title: "Finding anagrams"
date: 2022-02-24
categories: words, text analysis, python, numpy, ETL, data visualization
usemathjax: true
---

# Discovering relationships between words
How can we can discover and formalize relationships between words? For example, how can we determine that the words 'emit', 'item', 'mite', and 'time' are anagrams? That is, the letters in each of those words in this group can be rearranged to spell a different word. How many word groups are there? Further more, how can we determine that some of the letters in the word 'terminator' can be used to spell 'emit' (or 'item', or 'mite', or 'time', or other words)? 

The [finding anagrams workshop](https://github.com/mike-babb/finding_anagrams) accomplishes two tasks:
- Finding exact anagrams: the valid combinations of letters in the 'emit' word group
- Discovering and formalizing from/to word relationships: the word 'emit' can be spelled using letters in the word 'terminator'.

The workshop presents the tasks as an Extract-Transform-Load pipeline using python, pandas, numpy, and SQLite. Briefly, python and pandas is used to import, shape, and peform some intial processing on a list of approximately 236K words. Pandas is used to find the exact anagrams. Next, the list of words are represented as a matrix and NumPy is used to perform many matrix calculations to discover and formalize the from/to word relationships. Key to this portion of the process is how much pre-processing the user wants to perform. Without any preprocessing, the discovery and formalization process takes about 120 minutes. With a moderate amount of preprocessing, the from/to discovery and formalization process takes a little over 2 minutes. The differences in processing times make use of carefully constructed matrix operations that are possible through NumPy. 

Once the word relationships are discovered and formalized, the data are stored in a SQLite database. Using python, several indices are added to various database tables to showcase performance. Finally, an R script is included to showcase how to query a SQLite database and produce graphics visualizing differences in processing time.

I'll describe this process in more detail in this blog post at a later date in time. For now, I'll refer readers to the [PowerPoint included in the github repo](https://github.com/mike-babb/finding_anagrams/blob/main/Finding%20Anagrams%20v2.0.pptx?raw=true) that describes the various python and numpy techniques used. 

