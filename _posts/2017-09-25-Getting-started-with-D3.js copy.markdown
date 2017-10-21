---
layout: post
title: Getting started with D3.js
comments: true
---

An introduction to data visualization with the mighty D3.js.

<img class="no-shadow" alt="D3.js logo" src="/Front/assets/img/4/D3.png" style="width: 30%; height: auto; display: block; margin: 0 auto;"/>

In this tutorial, we will go through the following.

1. What is D3?
2. Why would you use D3?
3. Shapes, Helpers and Scales in D3
4. Creating a scatter plot in D3


### **1. What is D3?**

Data Driven Documents (or D3) is a powerful javascript library for building data visualizations using the common web standards like HTML, Canvas and SVG. D3 allows you to bind data to the DOM and then apply data-driven transformations to the document like CSS properties and SVGs.

D3.js was created by [Mike Bostock](https://bost.ocks.org/mike/), Vadim Ogievetsky and Jeff Heer in early 2011. It is a massive javascript library and actively managed by Mike Bostock on [GitHub](https://github.com/d3/d3).

<hr>

### **2. Why would you use D3?**

**I. Make data driven decisions**

Visualizations help businesses filter the noise and see the trend in the data. D3.js is more than just a charting library, it provides a variety of visualization tools including both static and interactive to see the data the way you want to. 

**II. Dynamic and data-bound**

D3 lets you bind data to the [DOM](https://css-tricks.com/dom/), and so the visualization changes along with the data.

**III. Manipulating SVGs**

D3 visualizations are based on SVGs, an XML-based text format to describe how the image should appear.
A line, circle and rectangle in SVG are shown below.

```html
<svg>
<line x1="40" y1="20" x2="40" y2="160" style="stroke-width: 1; stroke: black;"/>
<circle cx="100" cy="80" r="20" fill="green" />
<rect x="140" y="25" width="30" height="200" fill="red" />
</svg>
```
<svg>
<line x1="40" y1="20" x2="40" y2="160" style="stroke-width: 1; stroke: black;"/>
<circle cx="100" cy="80" r="20" fill="green" />
<rect x="140" y="25" width="30" height="200" fill="red" />
</svg>

SVGs are vector-based so they can be scaled without any loss of quality or pixelation. More information about other SVG elements can be found [here](https://developer.mozilla.org/en-US/docs/Web/SVG/Element).

**IV. Lots of examples**

D3 has thousands of examples to take inspiration from, right from simple bar graphs to complex [Voronoi](https://en.wikipedia.org/wiki/Voronoi_diagram) diagrams. 

<img alt="Voronoi" src="/Front/assets/img/4/voronoi.png" style="width: 90%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;">Voronoi diagram, source: http://christophermanning.org/gists/1734663/</p>

More examples can be viewed in the D3 [gallery](https://github.com/d3/d3/wiki/Gallery).

**V. Open-source!**

D3 is an open-source library and its source code can be found on [GitHub](https://github.com/d3/d3). It is one of the **most-starred** and **most-forked** repos on GitHub and contributed to by hundreds of developers. It also supports wrappers for other javascript libraries such as React and Leaflet, as built by other developers. 


<img class="no-shadow" alt="Open source" src="https://media.giphy.com/media/y5gweIjtEZ8d2/giphy.gif" style="width: 50%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Source: giphy.com</em></p>

<hr>

### **3. Shapes, Helpers and Scales in D3**

**I. Shapes**

As we saw above, creating individual shapes is quite tedious. Imagine drawing a scatter plot with hundreds of dots and aligning them with the axes! D3 takes care of the basic charting chores so that you can focus on the actual visualization. Before we jump into the scatter plot, let's recreate the shapes in D3.

First, we define an SVG element that will contain our shapes. The SVG element can be appended to any element in the DOM. Next, we add in the circle, rectangle and line.

```html
<!DOCTYPE html>
<html>
	<head>
		<title>Shapes in D3</title>
		<script src="https://d3js.org/d3.v4.min.js"></script>
	</head>
	<body>
	<div id="canvas"></div>
	<script>
	var canvas = d3.select("#canvas") // D3 uses a jQuery like selector
			.append("svg")
			.attr("height", 500)
			.attr("width", 500);
	var circle = canvas.append("circle") // Appending shape elements to the SVG element
			.attr("cx", 250)
			.attr("cy", 250)
			.attr("r", 100)
			.attr("fill", "red");
	var rectangle = canvas.append("rect")
			.attr("height", 500).attr("width", 100)
			.attr("fill", "blue")
			.attr("stroke", "blue")
			.attr("stroke-width", 2);
	var line = canvas.append("line")
			.attr("x1", 500).attr("y1", 0)
			.attr("x2", 500).attr("y2", 500)
			.attr("stroke-width", 2)
			.attr("stroke", "black");
	</script>
	</body>
</html>
```
Here is the result. If you try zooming in or out, notice that the quality of the image is not compromised.

<script src="https://d3js.org/d3.v4.min.js"></script>

<div id="canvas"></div>
<script>
		var canvas = d3.select("#canvas")
					.append("svg")
					.attr("height", 500)
					.attr("width", 500);
		var circle = canvas.append("circle")
					.attr("cx", 250)
					.attr("cy", 250)
					.attr("r", 100)
					.attr("fill", "red");
		var rectangle = canvas.append("rect")
						.attr("height", 500).attr("width", 100)
						.attr("fill", "blue")
						.attr("stroke", "blue")
						.attr("stroke-width", 2);
		var line = canvas.append("line")
					.attr("x1", 500).attr("y1", 0)
					.attr("x2", 500).attr("y2", 500)
					.attr("stroke-width", 2)
					.attr("stroke", "black");
</script>

**II. Helpers**

D3 comes with a bunch of helper functions so that you don't have to load [Lodash](https://lodash.com/) or [Underscore](http://underscorejs.org/).

```javascript
const data = [1, 2, 3, 4, 5];
const moreData = [[5, 20], [480, 90], [250, 50], [100, 33], [330, 95]];

d3.min(data); // 1

d3.max(moreData, function(d) { return d[0]; }); // 480

d3.max(moreData, function(d) { return d[1]; }); // 95

d3.extent(data); // [1, 5]
```

**III. Scales**

Scales are a vital part of any visualization and D3 comes with a variety of them (Linear, Log, Ordinal and others). D3 scales map the data-space (domain) to the pixel-space (range) and are heavily used for drawing axes. 

Going back to our Shapes and Helpers examples, if we want to visualize a scatter-plot of `moreData` on the `canvas` element, we can declare our scales as below.

```javascript
var xScale = d3.scaleLinear()
	.domain([0, d3.max(moreData, function(d) { return d[0]; })])
	.range([0, 500])
		
var yScale = d3.scaleLinear()
	.domain([0, d3.max(moreData, function(d) { return d[1]; })])
	.range([500, 0]) // SVG is y-down

```
Let's test our scales.

```javascript
console.log(xScale(0)); // 0
console.log(xScale(480)); // 500

console.log(yScale(0)); // 0
console.log(yScale(95)); // 500

// The intermediate values are mapped linearly between 0 and 500.

```
To create an axis, we just pass on our scale to the suitable axis function.

```javascript
var xAxis = d3.axisBottom(xScale);
```
More info about D3 scales can be found [here](https://github.com/d3/d3-scale).

<hr>

### **4. Creating a scatter plot in D3**

We are now ready to create our first (or 100th) scatter plot. First, let's create a `div` element that will contain our SVG plot.

```html
<div id="plot"></div>
```
Now, let's create our SVG element.

```javascript
const w = 500, h = 500, pad = 50; // // defining width and height of the SVG element; and a little padding for the plot
		
var svg = d3.select("#plot") // Select the plot element from the DOM
	.append("svg") // Append an SVG element to it
	.attr("height", h)
	.attr("width", w);
```
Some data to plot.

```javascript
// [x-coordinate, y-coordinate, radius]
const dataset = [[5, 20, 30], [480, 90, 20], [250, 50, 100], [100, 33, 40], [330, 85, 60]];
```

Create the scales and axes.

```javascript
// Scales
var xScale = d3.scaleLinear() // For the X axis
	.domain([0, d3.max(dataset, function(d) { return d[0]; })])
	.range([pad, w - pad]);
		
var yScale = d3.scaleLinear() // For the Y axis
	.domain([0, d3.max(dataset, function(d) { return d[1]; })])
	.range([h - pad, pad]);
		
var rScale = d3.scaleLinear() // Custom scale for the radii
	.domain([0, d3.max(dataset, function(d) { return d[2]; })])
	.range([1, 30]); // Custom range, change it to see the effects!
	
// Axes
var xAxis = d3.axisBottom(xScale); // handy axes for any orientation
var yAxis = d3.axisLeft(yScale);
```
Plotting the data. 

```javascript
var circ = svg.selectAll("circle") // Returns ALL matching elements
	.data(dataset) // Bind data to DOM
	.enter() // Add one circle per such data point
	.append("circle")
	.attr("cx", function(d) { return xScale(d[0]); })
	.attr("cy", function(d) { return yScale(d[1]); })
	.attr("r", function(d) { return rScale(d[2]); })
	.attr("fill", "blue").attr("opacity", 0.5);
```
The above block contains the crux of D3. Let's break it down.

We know that the scatter plot will essentially be a set of circles. Their location and radius will depend upon the `dataset` that we defined above. So we want **one circle per data point**. D3 achieves this goal in the following three steps.

`svg.selectAll("circle")`: Returns all matching elements, even though they haven't been created yet.

`.data(dataset)`: Binds each of the circles from above to a data point (DOM - Data binding).

`.enter()`: Add a circle per data point.

Great, now let's add our axes to finish it all.

```javascript
//X axis
svg.append("g") // Creates a group
	.attr("class", "axis") // adding a CSS class for styling
	.attr("transform", "translate(0," + (h - pad) + ")") 
	.call(xAxis);
	
//Y axis	
svg.append("g")
	.attr("class", "axis")
	.attr("transform", "translate(" + pad +", 0)")
	.call(yAxis);
```
The transformations above are done to translate the axes to origin. And here is the CSS class.

```css
.axis {
fill: none;
stroke: black;
shape-rendering: crispEdges;
}
```
The final product.

<style>
			.axis path, .axis line {
    			fill: none;
    			stroke: black;
    			shape-rendering: crispEdges;
			}
</style>

<div id="plot"></div>

<script>
		
var dataset = [[5, 20, 30], [480, 90, 20], [250, 50, 100], [100, 33, 40], [330, 85, 60]];
		
		
var w = 500, h = 500, pad = 50;
		
var svg = d3.select("#plot")
					.append("svg")
					.attr("height", h)
					.attr("width", w);
		
var xScale = d3.scaleLinear()
			.domain([0, d3.max(dataset, function(d) { return d[0]; })])
			.range([pad, w - pad]);
		
		
var yScale = d3.scaleLinear()
			.domain([0, d3.max(dataset, function(d) { return d[1]; })])
			.range([h - pad, pad]);
		
var rScale = d3.scaleLinear()
			.domain([0, d3.max(dataset, function(d) { return d[2]; })])
			.range([1, 30]);
		
var xAxis = d3.axisBottom(xScale);
var yAxis = d3.axisLeft(yScale);
						
		
var circ = svg.selectAll("circle")
			.data(dataset)
			.enter()
			.append("circle")
				.attr("cx", function(d) { return xScale(d[0]); })
				.attr("cy", function(d) { return yScale(d[1]); })
				.attr("r", function(d) { return rScale(d[2]); })
				.attr("fill", "blue").attr("opacity", 0.5);
		
		
		svg.append("g")
			.attr("class", "axis")
			.attr("transform", "translate(0," + (h - pad) + ")")
			.call(xAxis)
		
		svg.append("g")
			.attr("class", "axis")
			.attr("transform", "translate(" + pad +", 0)")
			.call(yAxis)
		
</script>

As you add more points to `dataset`, the plot will automatically reflect it. 

<hr>

### **Furthermore**

Hope you liked this brief intro to D3. Here are a few helpful resources,

* https://github.com/d3/d3/wiki/gallery
* https://bl.ocks.org/mbostock
* https://square.github.io/intro-to-d3/

And an amazing Game of Thrones [visualization](https://mimno.github.io/showcase/project2/got/) to conclude.