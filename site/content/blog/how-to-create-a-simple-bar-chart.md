+++
title = "How to Create a Simple Bar Chart"
date = "2018-04-26T14:26:46+08:00"
tags = ["theme"]
categories = ["starting"]
banner = "img/banners/banner-1.jpg"
+++

If you are new to the Simple Chart series and would like to get some clarity on what this is about please go check out the [intro](https://vizsimply.com/blog/2018/3/2/a-simple-chart).

Otherwise, move right along to this simple bar chart walkthrough.

---

This is what your bar chart should look like when you are done.

![](http://localhost:3000/img/post-10/final-chart.png)

One of the old faithful chart types. Bar charts do a great job comparing different categories to one another along a shared axis.

The best thing about bar charts, especially when they are sorted, is how easy they make it for us to compare one category to another. Length is a preattentive attribute our minds leverage well.

## What shape does d3 use to create bars?

When visualizing data with D3 you have to think about the shape you are trying to create. In the case of this horizontal bar chart we need to create a rectangle.

In the world of SVGs, which is a common way D3 draws shapes on our screens, rectangles are called rects. Rects are defined by four attributes: x, y, height and width.

### Rect attributes

* x attribute defines the left position of the rectangle (e.g. x="50" places the rectangle 50 px from the left margin)
* y attribute defines the top position of the rectangle (e.g. y="20" places the rectangle 20 px from the top margin)
* Height stretches your rect along the x-axis
* Width stretches your rect along the y-axisWhat format should our data be in?

## What format should our data be in?

Anyone who has tried visualizing data knows the shape of you data matters. D3 is no different. Thankfully the data structure needed to build a bar chart is easy to come by.

To build a basic bar chart we will want a dataset with one column of categories and one column values. Your data should be aggregated to point where each value is the total value for that row. Each categories will be an individual bar and the values will set the length.

The dataset for this example is from [Week 8 of Makeover Monday](https://data.world/makeovermonday/2018w8-where-does-your-medicine-come-from). To get the subset of the MakeoverMonday dataset I used to build the bar chart simply download the [gist](https://gist.githubusercontent.com/robcrock/245c45015de34207d79dbafdde27b8fd/raw/0f1f51abbe39a7e2a4a65e07ace25ed7305e32c7/data.csv).

![](http://localhost:3000/img/post-10/data-table.png)

To avoid Makeover Monday getting on to me I have to mention the importance of referencing the dataset you are using. Whenever possible link back to the original source.

This practice keeps us honest and allows others interested in the topic to add their own flair. This data has been made available by [TradeMap.org](https://www.trademap.org/Country_SelProduct_TS.aspx?nvpm=1%7C%7C%7C%7C%7C3004%7C%7C%7C4%7C1%7C1%7C2%7C2%7C1%7C2%7C1%7C1).

## What files do we need create this chart in D3?

Honestly, we could put our code in one HTML file and be done with it, but since we are working with different file types I like to separate them to avoid confusion.

You can download a started folder I put together from [Github](https://github.com/robcrock/simple_chart_boilerplate).

![](http://localhost:3000/img/post-10/repository.png)

We are almost ready to start coding, I promise.

All you need to do now is fire up a local webserver in the same folder you put those files you just downloaded from Github.

No idea what I am talking about? This [post](http://jasonwatmore.com/post/2016/06/22/nodejs-setup-simple-http-server-local-web-server) will walk you through installing the node http server on your machine so you can keep coding along. You could also install the Liver Server extension code for VisualStudio Code. Here is a little [demo video](https://www.youtube.com/watch?v=_4TraiVJDe0) showing off their cool setup 🤓

Once up and running you should see a window similar to the one below.

![](http://localhost:3000/img/post-10/first-look.png)

## Is it time to code?

Oh, yeah! We’ll break this approach down into two steps. The data manipulation and [DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction) manipulation.

The data manipulation step is the part of the process where we transform our data into a structure suitable for D3 and the specific chart we are trying to create.

The DOM manipulation step is where we edit the elements that make up what you see on your screen. If you have been doing any frontend development then you are familiar with the DOM, otherwise you might want to read this post by MDN.

### Data Manipulation

Now that your environment is up and running we can add our data to the mix. To do this, go back to that gist I mentioned earlier and copy the data into the empty data.csv you downloaded from Github.

Now let’s log our data to to see what we are working with.

![](http://localhost:3000/img/post-10/first-log.png)

To open the beloved console you can read use the [Keyboard Shortcut](https://developers.google.com/web/tools/chrome-devtools/shortcuts) Reference table below.

![](http://localhost:3000/img/post-10/keyboard-shortcuts.png)

We can see that our data is being served to the browser. Now we need to coerce those export value into numbers. We can tell that they aren’t in numbers yet because they are the same color as the exporters, which are clearly text. In JavaScript nomenclature, we call text [Strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String).

We can coerce our strings to numbers by looping through each row and using the plus sign or [Unary Operator](https://www.wikiwand.com/en/Unary_operation) if you want to sound fancy AF. We can also use the partseInt function. There are at least a couple ways to skin about everything when it comes to coding.

```
data.forEach(row => {
  row.exports = +row.exports
})
```

Now we see our red text turn has turn blue. Numbers always come through as blue in the console, which means this data can be used in our bar chart.

![](http://localhost:3000/img/post-10/second-log.png)

The last thing we need to address is sorting.

D3 doesn't automagically do anything for us. If we want our bars to be sorted, then we need to sort our data before creating the bars.

We do this with a sort method that’s available to every JavaScript array.

```
data.sort((a, b) => a.exports - b.exports);
```

The sort method still looks very mysterious. I’ll avoid confusing you with my explanation of how it works. You can read all about it on [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort).

Your data manipulation code should now look like…

```
d3.csv('data.csv').then(data => {

  data.forEach(row => {
    row.exports = parseInt(row.exports);
  });

  data.sort((a, b) => a.exports - b.exports);

  createChart(data);
});
```

### DOM Manipulation

With data manipulation out of the way we can start manipulating the DOM. This is carried out in a function we have conveniently called createChart.

```
function createChart(data) {

  const chart = new Chart({
    element: document.querySelector('body'),
    data: data,
    title: "Who made the most on medicine exports in 2016?",
    subtitle: "The top 25 are listed below."
  });

}
```

This function instantiates a new Chart class. All we have to specify is the place we want to put our chart, data we’ll use to build our chart and a couple titles.

### What is our Chart class doing?

Classes are special functions that take one constructor method that’s called every time the class is instantiated as well as instance methods that are available to the class. There is a lot to classes. I would recommend reviewing this article, [Understanding JavaScript](https://css-tricks.com/understanding-javascript-constructors/) Constructors, if you are interested in diving deeper.

In the case of our bar chart, the constructor assigns the properties of the object passed in to variables the instance methods can use inside the class.

```
constructor(opts) {

  this.element = opts.element;
  this.data = opts.data;
  this.title = opts.title;
  this.subtitle = opts.subtitle;

  this.draw();

}
```

Since the constructor function is called every time a new class is initiated we will have a function called draw in our constructor function that fires off every other function we need in order to build our bar chart.

### The draw function

Along with executing the other instance methods the draw function defines the space we want our chart to take up on the screen.

```
draw() {

  // Create the parent SVG
  this.width = 960;
  this.height = 600;
  this.margin = { top: 70, right: 20, bottom: 50, left: 225 };

  // Give your title and axes some space
  this.innerHeight = this.height - (this.margin.top + this.margin.bottom);
  this.innerWidth = this.width - (this.margin.right + this.margin.left);

  const svg = d3.select(this.element).append('svg');

  svg
    .attr('width', this.width)
    .attr('height', this.height);

  this.plot = svg.append('g')
    .attr('transform', `translate(${this.margin.left},${this.margin.top})`);

  // Call the necessary functions
  this.createScales();
  this.addAxes();
  this.addTitles();
  this.addChart();
}
```

Notice that we changed the width, height and margin for this bar chart.

```
this.width = 960;
this.height = 600;
this.margin = { top: 70, right: 20, bottom: 50, left: 225 };
```

Once the height and width of our SVG has been defined and we appended a g element that’s positioned just so, then the draw function can start to execute the other methods.

```
this.createScales();
this.addAxes();
this.addTitles();
this.addChart();
```

### Create the scales

The next piece of this D3 puzzle are scales. According to [Swizec Telle](https://swizec.com/)r, they are one of the [3 keys to making D3 easier to learn](https://swizec.com/blog/3-key-insights-make-d3-js-easy-learn/swizec/8179), so let's pay attention 😳

```
createScales() {
  // We set the domain to zero to make sure our bars
  // always start at zero. We don't want to truncate.
  this.xScale = d3.scaleLinear()
    .domain([0, d3.max(this.data, d => d.exports)])
    .range([0, this.innerWidth]);

  // Range relates to pixels
  // Domain relates to data

  this.yBand = d3.scaleBand()
    .paddingInner(0.1)
    .domain(this.data.map(d => d.exporter))
    .rangeRound([this.innerHeight, 0]);

}
```

This won’t render anything on your screen, so don’t get too excited, but DO get excited. The functions will be used later to place pixels on your screen in just the right place.

Our horizontal bar chart needs an x-axis that relates to exports and rows for each of our exporters.

Let’s start by breaking down the xScale function responsible for translating our exports into our bar length:

```
this.xScale = d3.scaleLinear()
    .domain([0, d3.max(this.data, d => d.exports)])
    .range([0, this.innerWidth]);
```

Since our exports are straightforward quantities, we will work the [scaleLinear](https://github.com/d3/d3-scale#linear-scales).

The scaleLinear function needs a domain and range.

When you’re first starting out it’s important to think about how the domain and range relate to one another. It takes some time before this is intuitive. When you create scales with D3 you are essentially creating a function that translates data to coordinates on your screen.

The first element of the array passed into the domain will map to the first element of the range array and similarly for the second element of the domain and range arrays.

To get a row for each exporter we'll use one of D3s ordinal scales, scaleBand. If we want to evenly distribute points along our y-axis, then we would use scalePoint, but we are after bars here so we’ll focus on [bands](https://github.com/d3/d3-scale#band-scales).

![](http://localhost:3000/img/post-10/scale-bands.png)

Side note, the bandwidth value will come in handy later, when we want to set a width for our bars.

```
this.yBand = d3.scaleBand()
   .paddingInner(0.1)
   .domain(this.data.map(d => d.exporter))
   .rangeRound([this.innerHeight, 0]);
```

The syntax is almost the same, with the exception of paddingInner. paddingInner represents the ratio of each band that is reserved for white space. Here we have set paddingInner to .1, meaning we want to allocate 10% of each band to spacing.

### Time to generate axes

This phase won’t win you any data visualization awards, but you will starting seeing much more chart like things on your screen.

![](http://localhost:3000/img/post-10/no-css.png)

Here’s the code…

```
addAxes() {
    // Create axises to be called later
    const xAxis = d3.axisBottom()
      .scale(this.xScale);

    const yAxis = d3.axisLeft()
      .scale(this.yBand);

    // Custom format to clean up tick formattin
    const siFormat = d3.format(".2s");
    const customTickFormat = function (d) {
      return siFormat(d).replace("G", "B");
    };

    // Call those axis generators
    this.plot.append("g")
      .attr("class", "x axis")
      .attr("transform", `translate(0, ${this.innerHeight})`)
      .call(
      xAxis
        .ticks(10)
        .tickSize(-this.innerHeight)
        .tickFormat(customTickFormat));

    // Add y-axis ticks
    this.plot.append("g")
      .attr("class", "y axis")
      .attr("transform", 'translate(0, 0)')
      .call(yAxis);
  }
```

[Axes](https://www.pshrmn.com/tutorials/d3/axes/) are an example of a generator. No, not the kind that keep your refrigerator running when the power goes out.

D3 generators save you hours of work by perfectly positioning tick marks, lines, text and drawing paths. While the default aren’t the most beautiful, they are easily styled.

Why don’t we apply some styles? With a little CSS...

![](http://localhost:3000/img/post-10/with-css.png)

Better, no? A little less jail cell like.

To get these styles in your visualization just add this CSS to your style.css file.

```

/* General */
text {
  font-family: roboto;
}

/* Axes */
path {
  stroke: none;
}
.y.axis text {
  font-size: 14px;
}
.y.axis line {
  display: none;
}
.x.axis text {
  font-size: 12px;
  fill: #333333;
}
.x.axis line {
  stroke-width: 1;
  stroke: #D3D3D3;
  shape-rendering: crispEdges;
}

/* Titles */
.chart.subtitle {
  font-size: 16px;
}
.chart.title {
  font-size: 32px;
}
.x.axis.title {
  font-size: 12px;
  fill: #D3D3D3;
  text-anchor: end;
}

/* Shapes */
rect {
  fill: #3399CC;
}

```

Now back to the JavaScript code.

```
const xAxis = d3.axisBottom()
  .scale(this.xScale);

const yAxis = d3.axisLeft()
  .scale(this.yBand);
```

Here we use axisBottom and axisLeft and pass in those scales we created earlier.

The orientation specifies which side of the of the lower end of your range you would like the ticks and text to to be placed.

Now let's get a little more complicated.

```
// Custom format to clean up tick formattin
const siFormat = d3.format(".2s");
const customTickFormat = function (d) {
  return siFormat(d).replace("G", "B");
};

// Call those axis generators
this.plot.append("g")
  .attr("class", "x axis")
  .attr("transform", `translate(0, ${this.innerHeight})`)
  .call(
  xAxis
    .ticks(10)
    .tickSize(-this.innerHeight)
    .tickFormat(customTickFormat));

// Add y-axis ticks
this.plot.append("g")
  .attr("class", "y axis")
  .attr("transform", 'translate(0, 0)')
  .call(yAxis);
}
```

In this section we append a g element to group both our x and y axes.

The x axis tick text needs special treatment thanks to the unfortunately combination of funny [SI-Formatting](https://www.wikiwand.com/en/International_System_of_Units) and massive amount of money these countries make on drugs.

SI Units are the default D3 formatting of the tick text. While they may not be handy when formatting currency they are an internationally recognized system of units. Possibly the farthest thing from funny 😐 But yay solid standards 🙌

Most of your charts won’t require you to adjust units like this, but at least we know how it’s done for the next time.

Here’s a table that does a better job expressing how we have found ourselves needing to replace a G with a B.

![](http://localhost:3000/img/post-10/si-prefixes.png)

Notice that the SI name for 1,000,000,000 is Giga and the symbol is G.

When we call our axis generators they get busy creating paths and lines and text to provide the context we would expect from such chart elements. The [cusomtFormat](https://stackoverflow.com/questions/40774677/d3-formatting-tick-value-to-show-b-billion-instead-of-g-giga) function just needs to be fed into the tickFormat function, so that the “G” can be replaced with the more relevant “B”.

The y-axis is much more standard. In fact, I don't think y-axes get any simpler.

```
// Add y-axis ticks
this.plot.append("g")
  .attr("class", "y axis")
  .call(yAxis);
```

### Time to adjust our titles

![](http://localhost:3000/img/post-10/titles.png)

No chart is complete without descriptive text explaining what the heck you are looking at. Cole, of storytelling with data would recommend using a takeaway title. These takeaway titles are meant to tell you just that, what should I “takeaway” from seeing this visualization.

You will notice that I didn’t subscribe to this convention. It's nothing against takeaway titles, I simply wanted to do something different. Feel free to modify the code to your liking.

Just a few more lines of code and you are there.

```
addTitles() {
  // Add chart title
  this.plot.append('text')
    .attr("class", "chart title")
    .attr('x', 0)
    .attr('y', -30)
    .text(this.title);

  // Add chart subtitle
  this.plot.append('text')
    .attr("class", "chart subtitle")
    .attr('x', 0)
    .attr('y', -5)
    .text(this.subtitle);

  // Add x-axis title
  this.plot.append('text')
    .attr("class", "x axis title")
    .attr('x', this.innerWidth)
    .attr('y', this.innerHeight + 30)
    .text("EXPORTS (USD)");
}
```

### Time to create our bars

![](http://localhost:3000/img/post-10/final-chart.png)

Boom 💥

Here's what that code looks like.

```
addChart() {
  this.plot.selectAll(".bar")
    .data(this.data)
    .enter().append("rect")
    .attr('class', "bar")
    .attr("x", 0)
    .attr("y", d => this.yBand(d.exporter))
    .attr("width", d => this.xScale(d.exports))
    .attr("height", this.yBand.bandwidth());
}
```

In D3 speak we made an empty selection of a class bar, indicated by the “.bar”, that we will bind to our data. Our data being an array of 25 elements means we have 25 empty selections with the class of bar.

Then we create an enter selection. An SVG rect is created for each element of the enter selection and appended to the DOM. We all make sure to class each rect as “bar” to match our the empty selection made earlier.

Their x position is set to 0 to give us that nice shared axis that make bar charts so powerful. Read more about why bar chart MUST have a zero baseline [here](http://www.storytellingwithdata.com/blog/2012/09/bar-charts-must-have-zero-baseline).

The yBand scale is used to place our bars in the correct position along the y-axis. The width uses our xScale. The height is set using that hand bandwidth property I mentioned earlier.

I told you that property would come in handy 😎

The full repository we completed code can be found [here](https://github.com/robcrock/a_simple_bar_chart).