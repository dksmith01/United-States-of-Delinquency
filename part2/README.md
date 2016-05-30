## Prosper.com Loan Performance by State, 2005-2014
## 
 
This is a continuation of [The United States of Deliquency, Part
1](http://bit.ly/usd-part1), which is a visualization of Prosper.com's loan
performance data by state from 2005-2014. The slopegraph implemented in Part 1
does not show the relative importance of each state as to its contribution to
the overall national average. By employing a cartogram, the sizes of the states
can be scaled by Loan Count or other metric to illustrate how a particular state
compares with others. Also, the cartogram gives us an opportunity to use colors
for scaling along another variable, such as the loan default rate.

This project builds on the work of [Shawn
Allen](http://secularproducts.com/work/), whose [USA
topogram](https://github.com/shawnbot/topogram) is a reference project for many
internet cartographers. [D3.js](http://d3js.org) does much of the heavy lifting.

[Cartogram.js](./cartogram.js) is a JavaScript implementation of an [algoritm to construct continuous area
cartograms](http://lambert.nico.free.fr/tp/biblio/Dougeniketal1985.pdf), by
James A. Dougenik, Nicholas R. Chrisman and Duane R. Niemeyer, ©1985 by the
Association of American Geographers. It relies heavily on the work of [Mike
Bostock](https://bost.ocks.org/mike/), including
[d3](http://github.com/mbostock/d3) for rendering and
[TopoJSON](http://github.com/mbostock/topojson) for both writing and reading
topological JSON geodata. It uses segmented topology, which distorts the shapes more fluidly than the original.

The [included
example](https://github.com/shawnbot/d3-cartogram/blob/master/index.html)
combines TopoJSON-encoded and boundaries of the United States from [Natural
Earth](http://www.naturalearthdata.com/downloads/110m-cultural-vectors/) with Prosper.com lending data and US Census population data to scale the state sizes and colors accordingly.


