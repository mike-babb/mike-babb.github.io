---
layout: post
title: "Word relationships: Found even faster"
date: 2025-05-19
categories: NumPy, tHe MaTrIx, data visualization, anagrams
---

I implemented a few new techniques to see if I could decrease the processing time in my finding word relationships project. See the [README.md](https://github.com/mike-babb/finding_anagrams?tab=readme-ov-file#update-may-10-2025) for more information and few new plots. The four techniques I tried were:
* Explicitly setting [NumPy data types](https://numpy.org/doc/stable/user/basics.types.html)
* moving operations to the GPU via [CuPy](https://cupy.dev/)
* Optimizing the creation of the search spaces
* Using [Numba's](https://numba.pydata.org/) just-in-time compilation techniques.

Of the four techniques, explicitly setting the NumPy data types was the only technique that reduced processing time. And did it ever! The time savings were incredible: some operations were twice as fast. By default, NumPy uses a 64-bit address for integers. In this project, no object needed a 64-bit address space. Some objects only needed an 8-bit address space while most needed a 32-bit address space. I implemented a slightly modified version of matrix-extraction technique `5`. On my newer computer, this process takes $35$ seconds to generate all $73$ million parent/child word relationship pairs. Wow! For comparison, on the same computer, matrix extraction technique `1` takes about 60 minutes. That's over 100 times faster!

The GPU didn't offer any speed up - unless the NumPy arrays were large: hundreds of thousands of rows by and thousands of columns. To that end, I include two demos showing *how* using the GPU can be faster: an implementation of [matrix extraction technique `1` on the GPU](https://github.com/mike-babb/finding_anagrams/blob/main/code/Exp_02_demo_cupy.ipynb) and using CuPy to [find all possible sub-matrices](https://github.com/mike-babb/finding_anagrams/blob/main/code/Exp_04_compute_sizes_of_all_search_spaces.ipynb). Optimizing the creation of the search spaces didn't offer any speed up because it traded decreases in one search space for increases in other. And using Numba wasn't any faster. However, I think this was because Numba is being tasked with working on small arrays that change frequently so any benefits from just-in-time compilation are lost. That being said, I would like to try Numba on other tasks. 

So, the ultimate take away from this exercise? Set your data types. I am still in a bit of disbelief at the time savings this very-modest-and-easy-to-implement change produced. Simply adding `dtype = np.int32` during array creation was all it took

I will add that this is most certainly comp sci 101, and I knew that using smaller address spaces were generally faster, I never thought they would be *that* much faster. I disregarded that idea, because I figured that any gains would be marginal. So let that be a lesson! Always check your assumptions and never be afraid to revisit something fundamental.  