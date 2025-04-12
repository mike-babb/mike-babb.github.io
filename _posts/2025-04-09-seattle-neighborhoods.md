---
layout: post
title: "Seattle's neighborhoods"
date: 2025-04-09
categories: Leaflet, webmap, local data, socio-spatial boundaries
---

For quite some time I've wanted a web map those shows the boundaries of Seattle's neighborhoods

[SEATTLE NEIGHBORHOOD WEBMAP](https://mike-babb.github.io/media/seattle_nhoods/neighborhood_map.html)

Over the course of my journeys through the City of Seattle, I was curious as to what neighborhood I was in. By and large, I know the general boundaries of most neighborhoods (`Ballard`, `Fremont`, `Downtown`, `Pioneer Square`, etc.) But what are the exact boundaries? Is my mental-map correct? Often, we know what area we're in when navigating socio-culturally produced space, but those borders and boundaries between spaces are fuzzy. While the large neighborhoods (magenta) contain the smaller neighborhoods (green), the larger districts are not always meaningful. For the most part, the smaller neighborhoods conform to my mental map of the "neighborhood boundaries". Some boundaries are different than what I thought. For example, I thought the southern boundary of the `Greenwood` neighborhood was further north: N 85TH ST as opposed to N 75TH ST. `Lower Queen Anne` extends further south. And what I think of as `Capitol Hill` is actually a neighborhood called `Stevens` and `Capitol Hill` is a district. There is no `Central District`, but there is a `Central Area`. However, both the large district file and the small neighborhood file feature alternate names, when available, for the large districts and the small neighborhoods. And those can be viewed by clicking on the labels. For example, clicking on the label for `Minor` shows the alternate names of `Central District` and `Squire Park`. Clicking on the label for the `North Central` district shows the names for the neighborhoods and the alternate names. Finally, some of the larger districts have the same name as the smaller neighborhoods. `Interbay`, `University of Washington`, and `Seward Park`, for example. 


For example, where is `Frelard`? (And how is it pronounced?) Most people would probably say it's a place in between `Fremont` and `Ballard` as `Fremont` and `Ballard` share a boundary. But, as always, geo-social spatial data tell multiple stories. According to the map linked to above, there is no `Frelard` neighborhod. What would be the `Frelard` area is the `West Woodland` neighborhood. Most of the boundaries made sense.



What I found most interesting is the large districts (in Magenta) and the smaller neighborhoods (in Green). 

Both datasets come from the City of Seattle:
[Large Districts](https://data-seattlecitygis.opendata.arcgis.com/datasets/SeattleCityGIS::neighborhood-map-atlas-districts/about)
[Small Neighborhoods](https://data-seattlecitygis.opendata.arcgis.com/datasets/SeattleCityGIS::neighborhood-map-atlas-neighborhoods/about)


Modest descriptions aside, what about the provenance of these boundaries? The two links above provide some information. Both the district and the neighborhood boundaries originate from the [Seattle City Clerk's Office Geographic Indexing Atlas](https://clerk.seattle.gov/~maps/nmaps/fullcity.htm). This [passage](https://data-seattlecitygis.opendata.arcgis.com/datasets/SeattleCityGIS::neighborhood-map-atlas-districts/about)describes the origin and purpose of the boundaries: 
> The original atlas is designed for subject indexing of legislation, photographs, and other documents and is an unofficial delineation of neighborhood boundaries used by the City Clerks Office. Sources for this atlas and the neighborhood names used in it include a 1980 neighborhood map produced by the Department of Community Development, Seattle Public Library indexes, a 1984-1986 Neighborhood Profiles feature series in the Seattle Post-Intelligencer, numerous parks, land use and transportation planning studies, and records in the Seattle Municipal Archives. Many of the neighborhood names are traditional names whose meaning has changed over the years, and others derive from subdivision names or elementary school attendance areas.

This [page from the City Clerk](https://clerk.seattle.gov/~maps/nmaps/aboutnm.htm) specifically answers this *Frequently Asked Question*:
> Q: Why doesn't this map show my neighborhood correctly?
>
> A: There is no one "correct" Seattle neighborhood map. Representation of neighborhoods in this atlas can never meet all expectations for several reasons:
> * Different City departments and non-City entities define neighborhoods differently based on many factors;
> * Familiar neighborhood boundaries and City planning areas and names change over time;
> * The records being indexed using this atlas date from the 1800's to present, and so no one set of boundaries and names will ever perfectly match all records; and,
> * At any point in time there may be many conceptions of what defines a neigbhorhood and how it is named. 



















