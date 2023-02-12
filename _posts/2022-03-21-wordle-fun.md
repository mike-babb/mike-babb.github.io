---
layout: post
title: "Wordle Fun"
date: 2022-03-24
categories: words, text analysis, python, numpy
usemathjax: true
---

# Wordle: so hot right now
Like most people, I am captivated by wordle. It's a fun exercise. Especially on a bus.
Because it's simple enough and working with a finite set of data, I wanted to programmatically explore the data space. So, two things came to mind:
- Is there a way to rank words in order to suggest the best starting word?
- Can I build a simple solver that suggests words given letters known to be in the word, the position, and letters not in the word?

[Yes and yes we can.](https://github.com/mike-babb/wordle_fun)

# V1.0
I use python, pandas, and NumPy to determine the top starting word and the solver. I make use of all five-letter words as found in the list of words in my [finding anagrams workshop.](https://github.com/mike-babb/finding_anagrams)

V1.0 is feature complete. Both the top starting word and solver work correctly. To determine the top starting word, I counted the occurence of each letter across all five-letter words in my list of 9,972 words. Each letter is then assigned this score. The score of each word is the sum of each letter's score in the word. The higher the score, the better the word is to use as a starter. Using this metric, 'raise' is the best word to start with. In addition, this metric is the quickest way to remove possible words. 

The five most common letters in five letter words are:
<br>
'a', 'e', 'r', 'i', 'o'
<br>
Four vowels and one consonant. Makes sense...
<br>
![frequency of letter occurence](/assets/letter_score.png)

The ten best starting words/word groups with five unique letters are:

1. ['aries', 'arise', 'raise', 'serai']
2. ['arose', 'oreas']
3. ['ariel']
4. ['leora']
5. ['erian', 'irena', 'reina']
6. ['arite', 'artie', 'irate', 'retia', 'tarie']
7. ['orate']
8. ['arles', 'arsle', 'laser', 'seral', 'slare']
9. ['anser', 'nares', 'rasen', 'snare']
10. ['aster', 'serta', 'stare', 'strae', 'tarse', 'teras']


# V2.0: TBD
Create a web-based interface to interact with the solver.
Solve edge cases. 




