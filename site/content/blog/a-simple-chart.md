+++
title = "A Simply Chart"
date = "2015-06-24T13:50:46+02:00"
tags = ["D3"]
categories = ["Side Project"]
banner = "img/banners/banner-1.jpg"
+++

This project was inspired by Andy Kirk's [Chart Maker Directory](http://chartmaker.visualisingdata.com/). Each post in this series will cover the basics of building chart a from Andy’s list with D3.

What better way to learn than by building a chart or… 49. We will start with the most widely used chart types and slowly explore the more esoteric. This way you're sure to get more utility out of these tutorials as well. Know that I’m also learning this library.

By covering the basic chart types first I should have enough experience with the library to stay on the weekly schedule I’m aiming for.

And no, we won’t be exploring the fancier aspects of the library. I know 😭

These tutorials are meant to help you understand the basics of what’s needed to create specific visualizations with D3, not nuances of JavaScript or how to add interactivity. I may add a supplementary post if as needed, but we are keeping them simple for now.

Each tutorial will follow a couple conventions you might not find in the several other “How to Build Chart Blah” with D3.

One is the [object-oriented](http://ejb.github.io/2017/08/09/a-better-way-to-structure-d3-code-es6-version.html) approach found in [Elliot Bentley’s](https://twitter.com/elliot_bentley) work. Elliot shares a way we can leverage the latest features of es6 to add structure to our code that makes it much easier to understand.

Another characteristic is that we won’t use abstract datasets. I will use actual datasets to make these concepts more relatable and easier to repurpose in your own work.

Lastly, we will be creating charts in line with what [Michelle Borkin](https://www.ccis.northeastern.edu/people/michelle-borkin/) has found to make visualizations more understandable. You can hear more of what she has to say on the topic in this [Data Stories](http://datastori.es/113-what-makes-a-visualization-memorable-with-michelle-borkin/#t=0:03.369) episode.

Those tips to follow are: add a good title, annotate the important things, label your axes, and pick appropriate visual encodings. I know these may seem like common sense, but they also aren’t free with D3. I’ll be taking you all the way to understandable D3 charts 🤓

## The charts

### Categorical

* Bar chart
* Clustered bar chart
* Bullet Chart
* Dot plot
* Connected dot plot
* Pictogram
* Bubble chart
* Radar chart
* Polar chart
* Box-and-whisker plot
* Univariate scatter plot
* Histogram
* Word cloud

### Hierarchical

* Pie chart
* Donut chart
* Waffle chart
* Stacked bar chart
* Waterfall chart
* Back-to-back bar chart
* Marimekko chart
* Treemap
* Venn diagram
* Dendrogram
* Sunburst chart

## Relational

* Scatter plot
* Bubble plot
* Parallel coordinates
* Heatmap
* Matrix chart
* Network diagram
* Chord diagram
* Sankey diagram

## Temporal

* Line chart
* Bump chart
* Slope graph
* Connected scatter plot
* Area chart
* Horizon chart
* Streamgraph
* Timeline
* Gantt chart
* Instance chart

### Spatial

* Choropleth map
* Isarithmic map
* Proportional symbol map
* Prism map
* Dot map
* Flow map
* Area cartogram
* Dorling cartogram
* Grid map