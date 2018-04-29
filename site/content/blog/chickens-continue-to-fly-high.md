+++
title = "Chickens Continue to Fly High"
date = "2018-04-26T14:23:20+08:00"
tags = ["theme"]
categories = ["starting"]
banner = "img/banners/banner-1.jpg"
+++

![](http://localhost:3000/post5-original-chart.png)

## What works

* Lines are clearly differentiated
* It is intuitive

## What could be improved

* I’ll work on the title
* Remove the legend (test for color blindness)
* Right align the y-axis labels
* Remove vertical grid line
* Add full years
* Add annotations at points where lines intersect
* Research proper x-axis / y-axis ratios

![](http://localhost:3000/post5-chart-makeover.png)

## A few fun tips

1. Spectrum

![](http://localhost:3000/post5-spectrum.gif)

I use [Spectrum](https://chrome.google.com/webstore/detail/spectrum/ofclemegkcmilinpcimpjkfhjfgmhieb) to test for colorblindness.

You can see the original colors work well, buuut I decided to go with some different colors anyway. Notice how I said, "I decided". My color choice is totally subjective. Without colors that more clearly associated with the categories in our dataset, it's all free-range (pun intended) less those colors that make it hard for others with color vision limitations.

While most colors are free to use, notice what happens when the low-contrast option is selected. Those grid lines become a bit pointless, hey? There's your justification to remove the background color. Every choice is a design choice in data visualization.

2. ColorZilla

![](http://localhost:3000/post5-colorzilla.gif)

My favorite tool to use top pick pretty colors is [ColorZilla](https://chrome.google.com/webstore/detail/colorzilla/bhlhnicpbhignbdhedgjhgdocnmhomnp). Regardless of the tool you use, ColorZilla makes it super simple to grab those HEX codes your visualization tools needs for custom colors.

3. The golden ratio

![](http://localhost:3000/post5-colorzilla.golden-ratio.png)

In order to make my visualization (technically) beautiful the dimensions need to be just perfect 👌 [Visua.ly](https://visual.ly/community/presentation/business/golden-ratio-design) has a good slide deck you can run through to learn more about the golden ratio if you are into that sorta superficial stuff.

No, seriously, the reason I use this ratio in my line charts, besides the beauty, is to avoid skewing the data.

An x-axis that is too long will shrink the slope of your lines making spikes seem less severe. Create an x-axis that isn't wide enough (too narrow) might make your audience think the rise or fall you are presenting is more drastic than it should seem.

## Outro

That's it for this week.

Let me know what you learned from reading this on Twitter [@robcrock](https://twitter.com/robcrock)

Maybe you want to collaborate? I could be into that. Say hi at [rob@robcrock.com](mailto:rob@robcrock.com)