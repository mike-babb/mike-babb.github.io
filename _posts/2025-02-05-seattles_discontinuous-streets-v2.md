---
layout: post
title: "Seattle's Discontinuous Streets: version 2"
date: 2025-02-05
categories: geospatial analysis, street network, GeoPandas, NetworkX, webmap
---

# Visualizing Street Discontinuities: v2.0
I just [updated](https://github.com/mike-babb/seattle_streets) my project on identifying and visualizing Seattle's discontinuous street network. See this [page](https://mike-babb.github.io/blog/2025/01/01/seattles-discontinuous-streets) for version 1.0.

[SEE THIS PAGE FOR AN INTERACTIVE MAP OF THE ADDED STREETS](/media/discontinuous_streets_vtwo.html)

The major change in version 2.0 is that I added the connections between city sectors. For example, there are now connections between W GALER ST and GALER ST and connections between GALER ST and E GALER ST.  
<img src="https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_12_overall_v2.png" alt="overall" width="500" height="443"/>  

In the image above, the blue lines are the connections between sectors. The connections across the various salt and fresh water bodies really stands out and really emphasize the quasi-grid structure as seen in Seattle's streets. That being said, Galer is probably a little hard to see in that image, so here it is by itself.  
<img src="https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_11_galer_v2.png" alt="overall" width="500" height="150"/>  

I'll update this post with more information about how I created the interconnections and some of the others features in version 2.0. But for now, I am going to finish this beer at [The Sloop](https://theslooptavern.com/), commit some code and these words, and make my way home.