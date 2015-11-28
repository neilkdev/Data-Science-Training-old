#D3 Technical Course - Part 1


##D3
>D3.js is a JavaScript library for manipulating documents based on data. D3 helps you bring data to life using HTML, SVG, and CSS. D3’s emphasis on web standards gives you the full capabilities of modern browsers without tying yourself to a proprietary framework, combining powerful visualization components and a data-driven approach to DOM manipulation.
*http://d3js.org/*






##HTML



##CSS



##Javascript Basics

###Starting off 
- Open the Javascript Console in Google Chrome
- Open index.html in your text editor
- In Terminal/PC Console, Change to the directory with index.html
- Type in: python -m SimpleHTTPServer
- Then in a broswer, go to http://localhost:8000/index.html
- You should see a white page with some text 

###Handy Javascript Console Tricks
- Control+l clear your command screen
- The style section allows you to easily change formatting
- Open the Javascript console by hitting command+option+i
- You can use the javascript console like a calculator 
- You can see what you last entered by hitting UP

---

###Variables
In D3, as well as in most programming langauges, setting variables is very important functionality. It allows you to build upon a just a few configurations so your code scales and adjusts. In D3, a lot of what you'll write are variables, so that if you want to, say, adjust the size of your visualization, you can modify just a main width and height, which will then update the rest of the visualization (the size of the margins, the axes, the values in your visualization). In Javascript, which D3 is built on 


In Javascript, we can set integers to variable and treat them like integers. The difference in javascript is we have to explicitly state that they are variables, or "var." Arrays can also be variables, like var Data = [1,2,3,4,5];


Let's make a few variables:

```
1. Make a variable called numerator, equal to 99
2. Make a variable called denominator, equal to 100
3. Make a variable called percent, equal to the numerator divided by the denominator
4. Make a dataset called dataset, equal to five random numbers 
```

---

### Functions ###
We can use functions to modify our variables, and there are primarily two types of functions:

#### Named Funcitons ####
```javascript
function myFunction(x) { return x * 2; } 
```
Try entering a value into myFunction()
  
#### Unnamed Functions ####
```javascript
(function(x) { return x * 2; })(2);
```
- aka IIFE (Immediately Invoked Function Expression)
- Unnamed functions are most commonly used as part of a chain, so something like:

```javascript
var data = [1,2,3,4,5]

data.map( function(x) { return x * 2;} );
```
*This will be very important in D3, as we will often make functions on the fly. The difference in D3 is that we won't necessarily nest the function within a map() function.*

---

You can filter datasets with functions
```javascript
var data = [1,2,3,4,5]

data.filter( function(x) { return x * 2 == 2;} );


or 


var data = [1,2,3,4,5]

data.filter( function(x) { if(x * 2 == 2) {return x;}} );
```


You can also map datasets with functions
```javascript
var data = [1,2,3,4,5]

data.map( function(x) { return x * 2 == 2; } );


or 


var data = [1,2,3,4,5]

data.map( function(x) { if(x * 2 == 2) { return x; } } );
```
*Notice the difference in what those two return - the latter is what is more commonly used in D3*

---

Let's make a few functions: 

```
1. Make a function that adds 3 to any input
2. Make a function that divides by three to any input
3. Make a function that determines if numbers in a dataset are less than 4
4. Make a function that determines if numbers in a dataset are even
```
*Hint - in Javascript, the modular operator (%) returns division remainder.*



