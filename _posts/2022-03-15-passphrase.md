---
layout: post
title: "Passphrase generator"
date: 2022-03-15
categories: passwords, python, EFF, word list
usemathjax: true
---

# Horse batteries
On any given day I am creating a new account. Whenever I do, I prompted by Firefox with a password. It's totes random! But it's hard to remember. So I decided to build a [passphrase generator](https://github.com/mike-babb/passphrase) using python. 

The generator uses python, pandas, and numpy to read in the [EFF's large word list](https://www.eff.org/files/2016/07/18/eff_large_wordlist.txt) to create a passphrase consisting of five words. (The EFF has an informative article on the [list of words](https://www.eff.org/deeplinks/2016/07/new-wordlists-random-passphrases).) In addition, randomly selected characters are capitalized and numbers and special characters are also inserted. 

There is a jupyter notebook version of the code and a python file as well. I included a windows batch file to show how the code can be called from the command line and the output piped to the clipboard. Note that the batchfile activates an anconda environment to run the python code. 







