## Website Performance Optimization portfolio project

This is a project from the [Udacity Front-End Web Developer Nanodegree](https://www.udacity.com/course/front-end-web-developer-nanodegree--nd001), with the aim to optimize this online portfolio for speed. In particular, optimize the critical rendering path and make this page render as quickly as possible 

## Getting started
The code for the "before" website can be found [here](https://github.com/udacity/frontend-nanodegree-mobile-portfolio)

While the optimized portfolio with my changes can be found [here](https://github.com/kb546196/udportfolio) 


To compare sites:

1. Clone the before and after repo on to your local machine:
```
git clone https://github.com/kb546196/udportfolio.git
git clone https://github.com/udacity/frontend-nanodegree-mobile-portfolio.git
```

2. Navigate to the root directory of each project and start a web server
(use different ports for each site):
```
$ python -m SimpleHTTPServer 8080
$ python -m SimpleHTTPServer 8090
```

3.  Tunnel local web servers to the internet using ngrok. Further Instructions are on the [ngrok website](https://ngrok.com/docs#expose)


## Website Performance Optimizations: The changes I made

###Part 1: Optimize PageSpeed Insights score for ```index.html```

 PageSpeed Insights gave the original index.html scores of 27/100 for mobile and 30/100 for desktop, with the following recommended changes: 

* Should Fix:
	* Optimize images
	* Eliminate render-blocking JavaScript and CSS in above-the-fold content

* Consider Fixing:
	* Leverage browser caching
	* Reduce server response time
	* Enable compression
	* Minify HTML


####Changes I made to ```index.html```

1. Optimize images: 
    * Minimised the image pizzeria.jpg and renamed pizzeria_small.jpg
2. To eliminate render-blocking JS & CSS:
    * Minimised and inlined the css from ```style.css```
    * Added a _print_ media query to ```print.css```, so it does not block rendering for desktop and mobile
    * Minimised and inlined javascript ```perfmatters.js```
    * Add _async_ to the google analytics javascript to prevent render blocking
    * Removed the web fonts 

The effect of these changes is much better PageSpeed Score 95/91 on mobile/ desktop. 


###Part 2: Optimize Frames per Second in ```pizza.html```

This task had two criteria 

a. Optimizations made to ```views/js/main.js``` make ```views/pizza.html``` render with a consistent frame-rate at 60fps when scrolling.

b. Time to resize pizzas is less than 5 ms using the pizza size slider on the views/pizza.html page. Resize time is shown in the browser developer tools.


#### Part 2a: ```Pizza.html``` render with a consistent frame-rate at 60fps when scrolling.


*	In ```views/js/main.js``` the function ```updatePositions``` was causing Forced reflow when scrolling.  

 	* To change this I amended the function - taking  scrollTop outside the loop to prevent FSL. 
 
* The frame-rate was also reduced by too many sliding pizzas being created in the background, which  were all updated when there was scrolling. 

	* So I altered the function which created the sliding Pizzas, adding formula to ensure only neccessary amount of pizzas are generated dependent on screen size. I also moved height and width out of the function and into css to make it more efficent.




#### Part 2b: Time to resize pizzas is less than 5 ms using the pizza size slider

* The ```ChangePizzaSize``` function was causing the Forced Synchronous Layout
	* Removed ```determineDx```, instead using percentages in ```sizeSwitcher ``` function
	* Simplified the for loop in the function, moving the newwidth var to outise the loop to prevent FSL


More notes about the changes in  ```views/js/main.js```. 



- - - - 

Also, it should be noted, that at times when I was stuck the [Udacity forums](https://discussions.udacity.com/c/nd001-website-optimization/website-optimization-project) were a vital resource


