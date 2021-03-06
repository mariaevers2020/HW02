HW02\_B\_Graph-Mimic
================
Maria Evers

``` r
library("ggplot2")
library("magrittr") #so I can do some piping
data("diamonds")
data("mpg")
data("iris")
theme_set(theme_bw()) #I'll give you this one, you can set the theme individually for graphs
#or you can set the theme for all the graphs using theme_set()
#theme_bw() is best theme (IMO)

#for graph 3:
library("ggrepel")

```

## HW02 Part B

For this part of the HW, the goal is to try to recreate the graphs I
make from scratch. I will only provide the MD, not the actual code I
used to create it besides which data I use to create it. The rest will
be up to you.

Try for all 4, but if you are struggling don’t worry about it. Try your
best for each, if you don’t get everything that’s what the peer-review
is for. :smile:

### Graph 1

``` r
library("ggplot2")
library("magrittr")
data("diamonds")

#hint think about the *position* the bars are in...

ggplot(diamonds, aes( x = cut, color = clarity, fill = clarity)) +
  geom_bar(position = "dodge") +
  labs(x = "Diamond Cut", y = "Number of Diamonds") +
  labs(title = "My Diamond Collection", subtitle = "Boxplot representing the number of diamonds in my diamond collection by type of cut \n quality and clarity of diamond") +
  theme(plot.title = element_text(hjust = 0.5)) 
  
 
  ```

Using the diamonds dataset, make this graph:
![](HW02_B_Mimic_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

### Graph 2

``` r
data("iris")

ggplot(iris, aes(Sepal.Length, Petal.Length, color = Species, shape = Species)) +
  geom_point() + 
  geom_smooth(formula = y ~ x, color = "black") +
  facet_wrap(~ Species)

#This graph is the one I struggled the most with.  
```

Using the iris dataset, make this graph:

    ## `geom_smooth()` using formula 'y ~ x'

![](HW02_B_Mimic_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

### Graph 3

You’ll need the information in this first box to create the graph

``` r
data("mpg")
corvette <- mpg[mpg$model == "corvette",]
#install
library("ggrepel")
require("ggrepel") 
#useful for making text annotations better, hint hint
set.seed(42)

ggplot(corvette, aes(displ, hwy)) + 
  geom_point(data = mpg) +
  geom_point(data = corvette, color = "blue") + 
  labs(title = "Corvettes are a bit of an outlier") 

 # For the data labels, every code I tried produced an error, or ran but did not show up on the graph.  
  
  ```

Now using the mpg dataset and the corvette dataset, make this graph:

![](HW02_B_Mimic_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

There is a trick to getting the model and year to print off together.
`paste()` is a useful function for this, also pasting together parts of
file names and parts of urls together.

### Graph 4

``` r
data("mpg")

#hint for the coloring, colorbrewer and you can set palette colors and make your graphs colorblind friendly
library(RColorBrewer)
display.brewer.all(colorblindFriendly = T) #take a look at the colorblindfriendly options

ggplot(mpg, aes(cty, class, color = class)) + 
  geom_point(position = "jitter", alpha = 0.5) + 
  geom_boxplot(aes(group = class), alpha = 0.0, color = "black") +
  scale_color_brewer(palette = "Set2") + 
  labs(title = "Horizontal BoxPlot of City MPG and Car Class", x = "City MPG", y = "Car Class")

```

![](HW02_B_Mimic_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

The above graph lets you see some colobrlind friendly palettes. For the
graph below, I used Set2.

Now using the above mpg dataset, make this graph

![](HW02_B_Mimic_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->
