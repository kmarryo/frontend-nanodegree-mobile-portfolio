# Website Performance Optimization portfolio project

This project is containing work to improve the speed of a page. On one hand it was the goal to get a better Google PageSpeed rank, on the other hand it was necessary to get to 60 fps while scrolling or resizing the pizzas in the views/pizza.html file.

## Running this application

1. Download this project via github (clone or download)
2. Open a browser and visit localhost:8080 or you can simply open the index.html straight in your browser window

OR

To just look at the final result you can visit my[GitHub Pages-Site](https://kmarryo.github.io/frontend-nanodegree-mobile-portfolio/)

## Improvements made to speed up the Website

### Increasing PageSpeed
- Crop too large images and minify them using tinypng.com
- Inline CSS: Because the style.css file wasn´t much code, I completely inlined the css within a `<style>`-Tag and minified it
- Using WebFont-Loader JS at the very bottom of the page to load the Google Webfonts asynchronously
- Load Google Analytics asynchronously

### Reach 60 fps in views/pizza.html
All of the changes coming up were made in the views/js/main.js file.
#### `function updatePositions()`
I reduced the number of variables and calculations inside the for-loop. Therefore: 
- The scrolling position of the user is now stored in the variable scrollTop outside the loop.
- The phase-calculation is now outsourced into a function. The function takes a parameter called "modulo", which gets the `i % 5` as parameter when called inside the for-loop
#### `Reducing number of pizzas created`
It was unnecessary to create a fixed number of 200 pizzas on the screen, so I reduced this number. But instead of a fixed number it is now calculating the needed number of pizzas based on the screen height.

#### `function resizePizzas()`
- I replaced the whole determineDx function, which wasn´t needed and produced a lot of unnecessary calculations. Instead:
    - All pizza containers are now stored in the pizzaContainer variable.
    - `function sizeSwitcher(size)` now returns the numbers of the new size of the pizzas (in percent)
    - Inside the `resizePizzas()` function, the `sizeSwitcher(size)` function is called. Its value is stored inside the newWidth variable. This variable is then used for all of the pizzaContainers via the for-loop.