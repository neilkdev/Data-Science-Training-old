#D3 Technical Course - Part 3

Now we're going to learn about transitions, events, margins & axes, then a few D3 examples so you'll know how they work.

--- 

###Transitions
Transitions are functions within the D3 library that allow for seamless transitions between changes in your D3. They're a great way to add more interaction to your visualization. 

Let's go back to index.html, and try adding some transitions while we make changes
```javascript
var dataset = [10,20,30,40];

var svg = d3.select("body").append("svg")
    .attr("width",700)
    .attr("height", 700);

var circles = svg.selectAll("circle");

circles.data(dataset)
    .enter().append("circle")
    .attr("r", function(d) { return d*2; })
    .attr("cx", function(d,i) { return (i + 1) *100; } )
    .attr("cy", function(d,i) { return (i + 1) *100; } )
    .attr("fill", function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
    })
    .style("fill-opacity", 0.7)
    .style("stroke-width",".2em")
    .style("stroke",function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
    }); 
```

Now let's add a trasition to the update:
```javascript
var dataset = [10,20,30,40];

var svg = d3.select("body").append("svg")
    .attr("width",700)
    .attr("height", 700);

var circles = svg.selectAll("circle");

circles.data(dataset)
    .enter().append("circle")
    .transition()
    .duration(2000)
    .attr("r", function(d) { return d*2; })
    .attr("cx", function(d,i) { return (i + 1) *100; } )
    .attr("cy", function(d,i) { return (i + 1) *100; } )
    .attr("fill", function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
    })
    .style("fill-opacity", 0.7)
    .style("stroke-width",".2em")
    .style("stroke",function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
    });
```

See what happened? 

Let's play with some of the transition parameters to change our transitions:
* ease()
* delay()
* duration()

```javascript
var newdata = [30,10,20,40];

d3.select("svg").selectAll("circle")
    .data(newdata)
    .transition()
    .duration(2000)
    .ease("elastic")
    .delay(200)
    .attr("r", function(d) { return d*2; })
    .attr("cx", function(d,i) { return (i + 1) *100; } )
    .attr("cy", function(d,i) { return (i + 1) *100; } )
    .attr("fill", function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
    })
    .style("fill-opacity", 0.7)
    .style("stroke-width",".2em")
    .style("stroke",function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
    });
```
* ease() // applies various time value ranges
* delay() // add a delay 
* duration() // say how long you want it to be

For more transition parameters, [check out the API](https://github.com/mbostock/d3/wiki/API-Reference#d3-core).

---
###Events
Because D3 is a Javascript framework, we can use the different [Javascript Events](http://www.w3schools.com/js/js_events.asp) to add interaction to our visualization.

Javascript Events are things that either user or the browser to does that affects HTML elements. Some common events are "onclick" or "onmouseover"

Let's go back to index.html and add this:
```javascript
function somethingCool() {
    d3.select(this)
        .style("color", "red");
  }

d3.select("p")
    .on("mouseover",somethingCool)
```
* What's going on here?
    * We defined the event function.
    * We specified where and when it should occur.

*How could we add this to our circles?
```javascript
function somethingCool() {
    d3.select(this)
        .style("fill", "red");
  }

d3.selectAll("circle")
    .on("mouseover",somethingCool)
```
That select(this) is important, as it says that we're doing it to just this matched element not all of them, even though we allowed any to be selected with the selectAll(). You can add transitions to this to make even cooler events:
```javascript
function somethingCool() {
    d3.select(this)
    .transition()
    .duration(5000)
    .ease("elastic")
    .delay(100)
        .style("fill", "black")
        .style("stroke-width","0em");
      
  }

d3.selectAll("circle")
    .on("mouseover",somethingCool)

```
We didn't cover this with transitions before, but you can chain transitions, which are fun to do with events:
```javascript
function somethingCool() {
    d3.select(this)
    .transition()
    .duration(2000)
    .ease("elastic")
    .delay(100)
        .style("fill", "black")
        .style("stroke-width","0em")
    .transition()
    .duration(2000)
    .ease("elastic")
    .style("fill", function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
         })
    .style("fill-opacity", 0.7)
    .style("stroke-width",".2em")
    .style("stroke",function(d) { if( d == '10' ) { return "red"; } 
                        else if( d == '20' ) { return "blue"; }
                        else if( d == '30' ) { return "green"; }
                        else if( d == '40' ) { return "orange"; }
        });
      
  }

d3.selectAll("circle")
    .on("mouseover",somethingCool)
```
Here's another one for fun:

```javascript
function somethingCool() {
    d3.select(this)
        .transition()
        .duration(2000)
        .ease("elastic")
        .delay(100)
        .attr("r", function(d) { return d*0.25; })
        .attr("cx", function(d,i) { return Math.random()*100; } )
        .attr("cy", function(d,i) { return Math.random()*100; } )
        .transition()
        .duration(2000)
        .ease("elastic")
        .attr("r", function(d) { return d*2; })
        .attr("cx", function(d,i) { return (i + 1) *100; } )
        .attr("cy", function(d,i) { return (i + 1) *100; } );
  }

d3.selectAll("circle")
    .on("mouseover",somethingCool)
```

---
###Margins, Axes, and Transform() 
For this, we'll be going through [Bostock's Margin](http://bl.ocks.org/mbostock/3019563) example. This is a great example to show:
- Why we use margins
- What < g > tags are used for
- How to make axes

Open up the axes.html file, and let's walk through each part. 

*Learn through removing things.*

*Think about the defaults.*

---
###First Example
We're now going to go through an example by Mike Bostock for a scatterplot visualization. In this example, we'll learn about pulling data from a file into a visualization.

Get the files [here](http://bl.ocks.org/mbostock/3887118).

---
###D3 Resources
Let's go through the [D3 Resource](/Resources.md) repository I set up and see what you have at your disposal.

##Final Challenge
Take [one](http://bl.ocks.org/mbostock/3887118) of [these](http://bl.ocks.org/mbostock/3885304) Bostock examples and use an [open source data set](https://nycopendata.socrata.com/) to make your own visualization.







