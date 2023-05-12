---
layout: post
title: "IRS State-To-State Migration, 1990 - 2020, v1.0"
date: 2023-05-11
categories: migration data
usemathjax: true
---

# Migration data
My [dissertation](https://mike-babb.github.io/cv/diss) used county-to-county migration data from the
[Internal Revenue Service](https://www.irs.gov/statistics/soi-tax-stats-migration-data). A few weeks ago I received a request asking for the state-to-state equivalent. Unfortunately, I did not have those data readily available. But! Having conducted research (and written a dissertation) using migration data from the IRS - albeit at a different scale - I am familiar with how those data are arranged and the effort, skill, and attention-to-detail needed to parse those data.

To that end, I am sharing a version 1.0 of the formatted state-to-state data. These data feature every single state-to-state in-migration and out-migration data file during the 1990 through 2020 time period. Be warned: this is very much a work-in-progress file. The files linked below do have all of the state-to-state flow records. To get to this point, I used python and pandas and a combination of regex and deduction to determine the metadata of each file. While this is very much a work-in-progress, I will make available the python files and the import spec files I wrote to parse all of these data.

Mostly what needs to be done for a version 2.0 is remove excess records and use the data to generate measures of internal consistency. An initial pass of generating internal consistent involves reading in all files for all 50 states and Washington DC an ensuring that the *same* number of files are read in for each state for each year and that the cross-year totals reflect those numbers. [This file](/assets/file_name_triage_2023_05_11.xlsx) reflects those tabulations. And this is a strength of pandas: the library can be used simultaneously to import data *and* generate metadata. That's awesome.

The IRS state-to-state migration data are downloaded in *.xls for years 1990 through 2019 and *.xlsx format for 2020. The row, and sometimes the column, that feature the state-to-state migration data is different, depending on the year of data. And sometimes it varies by file by year! But for now, here is version 1.0:

[Migration data](/assets/irs_state_to_state_1990_2020_v1.0.csv)
[Migration data metadata](/assets/irs_state_to_state_1990_2020_v1.0_metadata.csv)

Stay tuned for a version 2.0.

Addendum:
In between the request for the state-to-state migration data, and the timing of this post, the [2020-2021 migration data](https://www.irs.gov/statistics/soi-tax-stats-migration-data-2020-2021) were published. Wow!

