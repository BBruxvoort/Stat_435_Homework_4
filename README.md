# Stat_435_Homework_4

1) In order to maximize sales, items within grocery stores are strategically placed to
draw customer attention. This exercise examines one type of item—breakfast cereal.
Typically, in large grocery stores, boxes of cereal are placed on sets of shelves located
on one side of the aisle. By placing particular boxes of cereals on specific shelves,
grocery stores may better attract customers to them. To investigate this further, a
random sample of size 10 was taken from each of four shelves at a Dillons grocery store
in Manhattan, KS. These data are given in the cereal_dillons.csv file. The response
variable is the shelf number, which is numbered from bottom (1) to top (4), and the
explanatory variables are the sugar, fat, and sodium content of the cereals. Using
these data, complete the following:
(a) The explanatory variables need to be re-formatted before proceeding further.
First, divide each explanatory variable by its serving size to account for the
different serving sizes among the cereals. Second, re-scale each variable to be
190 Analysis of Categorical Data with R
within 0 and 1.12 Below is code we use to re-format the data after the data file
is read into an object named cereal:
stand01 <- function ( x ) { ( x - min ( x ) ) /( max ( x ) - min ( x ) ) }
cereal2 <- data . frame ( Shelf = cereal$Shelf , sugar =
stand01 ( x = cereal$sugar_g / cereal$size_g ) , fat =
stand01 ( x = cereal$fat_g / cereal$size_g ) , sodium =
stand01 ( x = cereal$sodium_mg / cereal$size_g ) )
(b) Construct side-by-side box plots with dot plots overlaid for each of the explana-
tory variables. Below is code that can be used for plots involving sugar:
boxplot ( formula = sugar ~ Shelf , data = cereal2 , ylab =
" Sugar " , xlab = " Shelf " , pars = list ( outpch = NA ) )
stripchart ( x = cereal2$sugar ~ cereal2$Shelf , lwd = 2 , col
= " red " , method = " jitter " , vertical = TRUE , pch = 1 ,
add = TRUE )
Also, construct a parallel coordinates plot for the explanatory variables and the
shelf number. Discuss if possible content differences exist among the shelves.
(c) The response has values of 1, 2, 3, and 4. Under what setting would it be desir-
able to take into account ordinality. Do you think this occurs here?
(d) Estimate a multinomial regression model with linear forms of the sugar, fat, and
sodium variables. Perform LRTs to examine the importance of each explanatory
variable.
(e) Show that there are no significant interactions among the explanatory variables
(including an interaction among all three variables).
(f) Kellogg’s Apple Jacks (http://www.applejacks.com) is a cereal marketed to-
ward children. For a serving size of 28 grams, its sugar content is 12 grams, fat
content is 0.5 grams, and sodium content is 130 milligrams. Estimate the shelf
probabilities for Apple Jacks.
(g) Construct a plot similar to Figure 3.3 where the estimated probability for a shelf
is on the y-axis and the sugar content is on the x-axis. Use the mean overall fat
and sodium content as the corresponding variable values in the model. Interpret
the plot with respect to sugar content.
(h) Estimate odds ratios and calculate corresponding confidence intervals for each
explanatory variable. Relate your interpretations back to the plots constructed
for this exercise.
