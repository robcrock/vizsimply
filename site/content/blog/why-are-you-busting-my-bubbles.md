+++
title = "Why Are You Busting My Bubbles"
date = "2018-04-26T14:25:44+08:00"
tags = ["theme"]
categories = ["starting"]
banner = "img/banners/banner-1.jpg"
+++

MakeoverMonday was an especially special event this week as the digital gathered together at the Tableau Customer Conference for a live makeover in Vegas. As you can imagine this is an exciting opportunity to meet fellow #MakeoverMonday regulars and newbies in real life, but also a challenge yourself to create something presentable within an hour while Andy and Eva looking over your shoulder.

![](/img/post-9/from-the-stage.png)

Personally, I would rather spend days wondering how I am going to visualize the dataset of the week, play with the numbers a bit and iterate far longer than any sane person.

In an attempt to test my pain tolerance, I presented what was cobbled together within the time constraint. My work was less than polished, but worse yet… I presented packed bubbles #gasp

The audience quickly let me know my chart choice was a big no no. Unfortunately I hadn’t realized my mistake prior to ascending the stage stairs to what was sure to be a roast. Instead of defending the chart type I tried to explain what lead me these blocks of bubbles.

## How did I come up with bubbles?

The viz started as a heat map, because I wanted to test a theory. Will a heat map show that the States are getting fatter over time?

![](/img/post-9/heat map.png)

The heat map is somewhat helpful, but doesn’t quite capture my story. Another problem I had with the squares is how to abstract away the individual states.

Imagine looking a music festival from the sky. I wanted to get a sense of which obesity / year combos were most common in the way crowds around a stage indicate who’s music is most popular. Don’t ask me why. We only had an hour to come up with something!

![](/img/post-9/concert.png)

To try and visualize the differences between the obesity / year combos better than hues, [Ivett Kovacs](https://twitter.com/IvettAlexa) and I changed the colored squares for circles of blue sized by State count.

![](/img/post-9/big-blue-circles.png)

This chart did a better job showing the trend toward a fatter America, but we still don’t get a good sense for how many states fall within each intersection.

In an attempt to show those counts like you might see is a unit chart I threw state onto the detail marks card to get a unit-esque chart. The only difference, which is the biggest downfall of bubble packs is unit charts units have meaningful positions.

![](/img/post-9/smaller-blue-circles.png)

Look, we only got an hour to make something meaningful and I put a lot of pressure on myself! How can you expect me to make good decisions?

## Why did my bubbles get burst?

After some reflection on my chart choice, multiple attempts at making the bubbles work and research on the chart type I have to admit… we shouldn’t go using this chart all willy nilly.

[Stephen Few](https://www.perceptualedge.com/blog/?p=2523) suggests the problems with packed bubbles stems from the fact position of marks on the screen as well as their position relative to one another is meaningless. But wait, there’s more.

If challenging comparisons was the only issue with packed bubble, we might write this chart debate off completely.

![](/img/post-9/circle pack.png)

The example above is more similar to the packed bubbles you’ll find most often and these are even more dangerous than my makeover!

Often we mess our designs up by doing too much. By sizing and coloring the bubbles above the author suggests users should make comparisons between bubbles and product categories. This may work in cases where the difference is extreme, but the areas of [circles are a challenge](https://guides.library.duke.edu/datavis/topten) to accurately compare.

If you aren’t comfortable saying which product type has the more products, then this chart clearly isn’t working.

## What can we learn from my bubbles being burst?

* Randomly positioning points on a screen is no way to make meaningful comparisons. There are reasons certain charts work better than others. Instead of making a bubble chart because you like bubbles, let the information your chart needs to communicate to your users dictate your design decisions.
* Comparing an area of one circle to another is serious cognitive calisthenics. If you do choose to use bubbles then I hope your measures are different enough to stand out like the IPO data below.

![](/img/post-9/nyt-graphic.png)

* Feedback, even when received on a stage in front of a large, live audience, is valuable. Seek it out. The Tableau community is always game to offer up their constructive criticism to help grow your data viz skills.
* Take your time. Heck, sleep on it if you’re feeling stuck or aren’t happy with your work. Often I wake up after working on a viz for hours with completely new designs in mind or solutions to hard problems. You’ll likely experience the same if you just give your mind a little more time.

---

To polish up the viz before submitting to #MakeoverMonday without fearing the bubble pack I cleaned up the story and added some highlight actions you can play with on [Tableau Public](https://public.tableau.com/views/MMWeek41/Update?:embed=y&:display_count=yes).

![](/img/post-9/final-viz.gif)

You can see how others visualized the data differently on the MakeoverMonday [site](http://www.makeovermonday.co.uk/week-41). You can pick up where I left off by downloading my original workbook from [Tableau Public](https://public.tableau.com/views/PeriodicTableMap_3/Dashboard1?:embed=y&:display_count=yes). Be warned there are more mistakes behind the scene you'll need to address to make an accurate visualization.

If you would like me to message you every couple weeks with juicy data viz knowledge, see what I am tweeting about by following [@robcrock](https://twitter.com/robcrock).
