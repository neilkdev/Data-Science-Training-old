#Javascript Basics

###Starting off 
- Using the javascript console on Google Chrome
- Download the index.html file
- You can also pull up what you last entered, using the UP button
- Start a HTTP server on your computer by going into terminal and into the directory with index.html
- Type in: python -m SimpleHTTPServer
- Then in a broswer, go to http://localhost:8000/index.html
- You should see a white page with some text 

###Handy Javascript Console Tricks
- Control+l clear your command screen
- The style section allows you to easily change formatting
- Open the Javascript console by hitting command+option+i
- You can use the javascript console like a calculator 


---

### Variables ###
Like python, we can set integers to variable and treat them like integers. The difference in javascript is we have to explicitly state that they are variables, or "var." Arrays can also be variables, like var Data = [1,2,3,4,5];


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



