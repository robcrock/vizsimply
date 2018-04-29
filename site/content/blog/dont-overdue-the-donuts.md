+++
title = "Don't Over Do the Donuts"
date = "2015-06-24T13:50:46+02:00"
tags = ["Chart Type"]
categories = ["Makeover"]
banner = "img/banners/banner-1.jpg"
+++

## WHAT'S A LIFT?
A lift is my way improving a visualization by isolating one feature that hinders our perception in some way. Data visualization is complex, but that doesn't mean there aren't informed approaches anyone can take to make more accessible visualizations. I hope by sharing these bite-size improvements we can learn how to avoid common missteps and better defend our design decisions.

## LET'S GET AFTER IT!
[Week 39](http://www.nielsen.com/content/dam/nielsenglobal/eu/docs/pdf/Global%20Ingredient%20and%20Out-of-Home%20Dining%20Trends%20Report%20FINAL%20(1).pdf) of Makeover Monday had us makeover a chart type I have started noticing more and more in the wild. Pies have been around for a [couple centuries](https://research.tableau.com/sites/default/files/Skau-EuroVis-2016.pdf). Donuts are a newer breed. Now I’m starting to see these nested donuts.

![](http://localhost:3000/img/post-11/original-viz.png)

My guess is that we have the Apple Watch fitness tracker to thank for their sudden surge in popularity, but don’t quote me on that. Apple is a brand with design clout other organizations will only achieve in their dreams. If they can use nested donuts, then I guess it is okay for me to do so too, right?

![](http://localhost:3000/img/post-11/apple-watch.png)

No! In this case, more donuts aren’t better. Whenever you visualize data, you want to do so accurately and efficiently. Nesting means each donut will be different sizes. Therefore, two complete donuts will be different sizes even though their values are equal.

To say the same thing differently; let’s look at five nested arcs that are all 48% complete. I have added a couple features to the nested arcs below to make them easier to read.

![](http://localhost:3000/img/post-11/arc-length-comparison.png)

While each arc does line up with the central angle, some arcs have to stretch farther than others. Here is what the same arcs look like without the helpful decoration.

![](http://localhost:3000/img/post-11/just-arcs.png)

See how those outer rings bear more visual weight than the inner rings? This means those outer rings get an unfair advantage over the inner rings purely because of the chart choice. None of the values are different.

Can you imagine how frustrating it would be to defend your orange rings' widget sales when you know the numbers are equal while all the audience can think of is how much larger the other rings are? Yes, size matters in data viz.

Are we any better off with bars?

![](http://localhost:3000/img/post-11/straight-lines.png)

Yes, by unbending those radial bars we allow each bar to share an x-axis, common baseline and stretch no more or less than their neighbors. Not only that, but straight bars are easier for our minds to interpret than arc-length or angle, which is what our brains use to make sense of donut charts.

![](http://localhost:3000/img/post-11/arc-length.png)

## WALK IT OFF
You can see the fully lifted [viz](https://public.tableau.com/views/Barsarebetter/Barsarebetter?:embed=y&:display_count=yes&publish=yes) on Tableau Public. This wasn’t my week 39 Makeover Monday submission. You can peak at that [here](https://public.tableau.com/profile/robert.crocker#!/vizhome/workspace_0/workspace). The example below simply illustrates how bars are (usually) better when they aren’t bent.

![](http://localhost:3000/img/post-11/final-viz.png)

Hopefully you learned a thing or two from this quick lift. If you have a chart in need of a lift, get in touch. You can drop me a line at [robert@vizsimply.com](mailto:robert@vizsimply.com) to share your struggles. I would love to help!