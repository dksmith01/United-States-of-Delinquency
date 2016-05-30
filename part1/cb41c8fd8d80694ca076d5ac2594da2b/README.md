
## Summary
## 
The goal with this visualization is to create a fun, interactive graphic to help
a user discover how well his or her state compares to other states with respect
to paying back its Prosper.com loans, given the average income in that state.
One would think that high incomes correlate with low default rates, but that is
not always the case. With this visualization, users control the narrative, by
easily comparing state incomes, loan default rates, and the interplay between
the two.

## Design
## 
### Data
### 
* The Prosper data is a transformation of a raw Prosper dataset from 2005-2014,
containing 113K records and 81 variables 
  + The transformation first filtered the raw data down to about 34K records for loans whose entire loan origination
vintage had fully matured 
  + The final transformation consists of 51 states and their loan performance statistics for the 34K records 
  + The "expected" value for the percentage of non-performing loans in a state given its mean income is the
result of a linear regression of the weighted average income for each state

### Chart Type
### 
The idea to use a slope graph for this visualization came from the cover of
[Albert Cairo](http://albertocairo.com/)'s book, [The Functional
Art](http://www.thefunctionalart.com/). 

I also consulted Andy Kriebel's [analysis](http://vizwiz.blogspot.com/2013/01/alberto-cairo-three-steps-to-
become.html) of Dr. Cairo's iterative process. 

Charlie Park's discussion about Slopegraphs, [Part 1](http://charliepark.org/slopegraphs/) and [Part
2](http://charliepark.org/a-slopegraph-update/), helped convince me to go with a
slopegraph. In particular, it was his discussion of the [National Geographic
Magazine Life-Expectancy
Chart](http://charliepark.org/images/slopegraphs/natgeo.jpg) led me to believe
that a slopegraph was the right choice despite having different scales on either
side. The alternative would have been to use a scatter-plot with a linear
regression line, or a geographical encoding, which wouldn't have illustrated the
differences between the states as effectively.

Two drawbacks to using a slopegraph in this case: 
* Slopegraphs are best when using one scale versus two. 
* It is difficult to show the relative weightings of large states, like CA, versus smaller states, like WY, on the national average. I thought about using a thicker line for CA, ultimately thought it would be a
distraction.

### Visual Encodings
### 
* Vertical position on the left and right axis indicates how each state ranks in
average income and loan default rate. 
* Grey lines indicate all states' inactive
lines to give context for any active lines or the National Average. 
* The persistent black horizontal line gives the National Average and anchors the two
scales on either axis around one central line. The scale on the left has to
adjust to become smaller to allow for the considerable variance of the actual
loan default rates found in the data, while keeping the average line perfectly
horizontal. 
* The blue or red on slope lines and on the right state menu on
mouseover indicate "repaying" vs. "defaulting" states. This allows for further
user discovery and investigation, as well as obviating the need for a legend. *
The slope of a line, up or down, indicates how well a state is overperforming or
underperforming on its default rate given its average income 
* Text on the left and right axis appears to show the average income and loan default rate,
respectively, when a particular state is highlighted 
* Text is persistent on the left and right axes at the minimum, maximum, and National Average locations (the
persistence of the National Average came from Alberto Cairo's feedback). This
contextually-appearing text helps keep the level of "ink" to a minimum. 
* Based on feedback that I received, I included tick marks on each axis, to make it
clear that they use different scales and provide more context.

### Layout
### 
* I went with a vertical layout for the slopegraph and the right menu, even
though the overall orientation of a bl.ocks.org page and a gist is horizontal. I
can control the height of the graphic through parameters at the top of the draw
function. + A horizontal slopegraph felt too awkward + Also, I could lead the
user left to right from the background to the graphic, allowing me to introduce
the story before he or she plays with the interactive graphic. 
* Despite the feedback that I got from Alberto Cairo about the states menu, I chose to leave
it in one column. To address his concern about scrolling, I just chose to make
the graphic a little shorter vertically. 
* I tuned the axis titles based on user feedback to make them more prominent, improve the language ("Loan Default Rate"
vs. "Non-Performing Loan Pct"), and include units. 
* The text section on the left gives the user a brief explanation for how to use the graphic to explore
how his or her state compares to the rest of the country. It also explains how
the data was generated, as mentioned by the users who supplied me with feedback.

## Feedback
## 
####Alberto Cairo said via email: 
####
* I am always nervous when I see dual-axis charts (including my own slopegraph!)
My main suggestion would be to make it very clear for people that the scales are
indeed different, perhaps by showing tick marks --notice that I did this in the
chart in the cover of The Functional Art. 
* Also, I would make the average label on either end of the black line visible at all times, not on hover over state. 
* Finally, I'd split the states into two columns, to avoid scrolling. Perhaps you
can make columns for responsible vs non-responsible states?

## Resources
## 
### Credits
### 
The idea to use a slope graph for this visualization came from the cover of
[Albert Cairo](http://albertocairo.com/)'s book, [The Functional
Art](http://www.thefunctionalart.com/).

I benefitted from Andy Kriebel's
[analysis](http://vizwiz.blogspot.com/2013/01/alberto-cairo-three-steps-to-
become.html) of Dr. Cairo's iterative process.

Charlie Park's discussion about Slopegraphs, [Part
1](http://charliepark.org/slopegraphs/) and [Part
2](http://charliepark.org/a-slopegraph-update/), helped convince me to go with a
slopegraph. In particular, it was his discussion of the [National Geographic
Magazine Life-Expectancy
Chart](http://charliepark.org/images/slopegraphs/natgeo.jpg) led me to believe
that a slopegraph was the right choice despite having different scales on either
side.

Cole Nussbaumer Knauflic also helped me get a better handle on [how to use
slopegraphs](http://www.storytellingwithdata.com/blog/2014/03/more-on-
slopegraphs).

I may not have been able to start coding the D3 visualization without a boost
from Chris Viau, whose "[Basic Reusable
Slopegraph](http://bl.ocks.org/biovisualize/4348024)" served as the launching
point for my code.

### Other Sources
### 
* Stephen Few's [discussion](http://www.perceptualedge.com/articles/visual_business_intelligence
/dual-scaled_axes.pdf) of dual-scale axes 
* [Help with bringing SVG elements to the front](http://bl.ocks.org/eesur/4e0a69d57d3bfc8a82c2) 
* [Help with data binding](https://square.github.io/intro-to-d3/data-binding/) 
* [Help understanding selectAll](http://knowledgestockpile.blogspot.com/2012/01/understanding-
selectall-data-enter.html) 
* [Basic shapes in D3.js](https://www.dashingd3js.com/svg-basic-shapes-and-d3js) 
* [Help summing totals](http://stackoverflow.com/questions/24964746/csv-to-d3-summing-over-
values-for-multiple-links) 
* [Mike Bostock's choropleth when I was considering a geographic form factor](http://bl.ocks.org/mbostock/4060606)

