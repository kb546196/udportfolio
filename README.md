Changes made to optimize

For index.html

>Inlined the style.css
>Added a media query to print.css
>Inlined perfmatters.js javascript
>Add an async to the google analytics javascript to prevent render blocking
>Minimised the image pizzeria.jpg
>Removed the web fonts 


For views/js/main.js for pizza.html
>Amended the ChangePizzaSize function simplifying the for loop in function 
>Amended the updatePositions function - taking the scrollTop outside the loop to prevent FSL
>Amended the function creating the sliding Pizzas. - Moving height / width into css, adding formula to ensure only neccessary amount of pizzas are generated dependent on screen size
>Optimized the pizzeria.jpg image to load certain image dependent on screen size

