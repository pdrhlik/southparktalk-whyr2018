---
title       : GOING DOWN TO SOUTH PARK
subtitle    : to make some tidytext analysis
author      : Patrik Drhlík
job         : freelance data scientist
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
logo		: boys.png
--- #southparkbg
<!-- South Park backgound intro slide -->

---

## Web scraping and R packages

<img src="assets/img/fandom.png" style="width: 10%" />
[South Park episode transcripts](https://southpark.wikia.com/wiki/Portal:Scripts)

<img src="assets/img/imdb.svg" style="width: 10%" />
[IMDB South Park episode ratings](https://www.imdb.com/title/tt0121955/episodes)

Main R packages: [tidyverse](https://www.tidyverse.org/),
[tidytext](https://www.tidytextmining.com/),
[southparkr](https://github.com/pdrhlik/southparkr)

<img src="assets/img/tidyverse.png" style="width: 10%" />
<img src="assets/img/tidytextmining.png" style="width: 10%" />
<img src="assets/img/southparkme.png" style="width: 15%" />

<img src="assets/img/griefer.png" style="position: absolute; right: 10px; bottom: 50px;" />

---

## Glimpse at the data




```
## Observations: 312,767
## Variables: 16
## $ season                <fct> Season Thirteen, Season One, Season Sixt...
## $ season_number         <int> 13, 1, 16, 5, 15, 3, 11, 9, 13, 3, 21, 8...
## $ season_episode_number <dbl> 7, 10, 14, 10, 10, 4, 1, 2, 5, 15, 6, 1,...
## $ episode               <fct> Fatbeard, Damien, Obama Wins!, How to Ea...
## $ episode_number        <int> 188, 10, 237, 75, 219, 35, 154, 127, 186...
## $ character             <chr> "cartman", "stan", "kyle", "jonesy", "mr...
## $ year                  <int> 2009, 1997, 2012, 2001, 2011, 1999, 2007...
## $ line_number           <int> 63817, 4528, 76451, 31001, 72011, 16346,...
## $ word                  <chr> "hey", "bubye", "program", "wrong", "gen...
## $ word_stem             <chr> "hei", "buby", "program", "wrong", "gene...
## $ swear_word            <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE...
## $ episode_name          <chr> "Fatbeard", "Damien", "Obama Wins!", "Ho...
## $ air_date              <date> 2009-04-22, 1998-02-04, 2012-11-07, 200...
## $ user_rating           <dbl> 8.2, 8.1, 7.5, 8.1, 7.6, 6.7, 8.8, 8.8, ...
## $ user_votes            <dbl> 1578, 1703, 1156, 1488, 1229, 1546, 2356...
## $ score                 <int> NA, NA, NA, -2, 2, NA, NA, NA, NA, NA, N...
```

---

## Basic statistics about the show

<div class="basic-stats-table">
<table class="table" style="margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;display: none;"> figures </th>
   <th style="text-align:left;display: none;"> text </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 21 </td>
   <td style="text-align:left;"> Number of seasons </td>
  </tr>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 287 </td>
   <td style="text-align:left;"> Number of episodes </td>
  </tr>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 914 475 </td>
   <td style="text-align:left;"> Number of words </td>
  </tr>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 312 767 </td>
   <td style="text-align:left;"> No stopwords (a, the, this, ...) </td>
  </tr>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 6 170 </td>
   <td style="text-align:left;"> Number of swear words </td>
  </tr>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 1.97 </td>
   <td style="text-align:left;"> % of swear words </td>
  </tr>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 34.2 </td>
   <td style="text-align:left;"> % used for analysis </td>
  </tr>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 4 403 </td>
   <td style="text-align:left;"> Number of characters </td>
  </tr>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 8.14 </td>
   <td style="text-align:left;"> Mean IMDB rating </td>
  </tr>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 9.6 </td>
   <td style="text-align:left;"> Scott Tenorman Must Die (S05E04) </td>
  </tr>
  <tr>
   <td style="text-align:left;font-family: southpark;"> 6.3 </td>
   <td style="text-align:left;"> A Million Little Fibers (S10E05) </td>
  </tr>
</tbody>
</table>
</div>

<img src="assets/img/mrgarrison.png" style="position: absolute; right: 10px; bottom: 50px;" />

---

## How much who talks?

<img src="assets/fig/unnamed-chunk-4-1.png" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" style="display: block; margin: auto;" />

---

## Most used words by characters

<img src="assets/fig/unnamed-chunk-5-1.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" style="display: block; margin: auto;" />

---

## Overall swear word ratio

<img src="assets/fig/unnamed-chunk-6-1.png" title="plot of chunk unnamed-chunk-6" alt="plot of chunk unnamed-chunk-6" style="display: block; margin: auto;" />

---

## Character swear word ratio

<img src="assets/fig/unnamed-chunk-7-1.png" title="plot of chunk unnamed-chunk-7" alt="plot of chunk unnamed-chunk-7" style="display: block; margin: auto;" />

---

## Overall sentiment analysis

<img src="assets/fig/unnamed-chunk-8-1.png" title="plot of chunk unnamed-chunk-8" alt="plot of chunk unnamed-chunk-8" style="display: block; margin: auto;" />

---

## Character sentiment analysis

<img src="assets/fig/unnamed-chunk-9-1.png" title="plot of chunk unnamed-chunk-9" alt="plot of chunk unnamed-chunk-9" style="display: block; margin: auto;" />

---

## Episode popularity

<img src="assets/fig/unnamed-chunk-10-1.png" title="plot of chunk unnamed-chunk-10" alt="plot of chunk unnamed-chunk-10" style="display: block; margin: auto;" />

--- #naughty-episodes

## Are naughty episodes more popular?

<img src="assets/fig/unnamed-chunk-11-1.png" title="plot of chunk unnamed-chunk-11" alt="plot of chunk unnamed-chunk-11" style="display: block; margin: auto;" />

--- #mysterion

## So who's the naughtiest character?

<img src="assets/img/mysterion.png" style="position: absolute; width: 35%; left: 30%;" />

---

## It's Kenny!

<img src="assets/img/kenny.png" style="position: absolute; width: 35%; left: 30%;" />

---

![plot of chunk unnamed-chunk-12](assets/fig/unnamed-chunk-12-1.png)

---

## Contact
<img src="assets/img/linkedin.png" width="32px" />
[https://www.linkedin.com/in/patrik-drhlik/](https://www.linkedin.com/in/patrik-drhlik/)

<img src="assets/img/github.png" width="32px" />
[https://github.com/pdrhlik](https://github.com/pdrhlik)

<img src="assets/img/twitter.png" width="32px" />
[@PatrioScraper](https://twitter.com/PatrioScraper)

<img src="assets/img/mail.png" width="32px" />
[patrik.drhlik@gmail.com](mailto:patrik.drhlik@gmail.com)

<img src="assets/img/blog.png" width="32px" />
[https://www.patrio.blog](https://www.patrio.blog)

<img src="assets/img/southparkme-contact.png" class="avatar-contact" />
