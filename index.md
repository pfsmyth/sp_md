## Creating objects in R

> ### Objects vs. variables
>
> What are known as `objects` in `R` are known as `variables` in many other
> programming languages. Depending on the context, `object` and `variable` can
> have drastically different meanings. However, in this lesson, the two words
> are used synonymously. For more information see:
> [https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Objects](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Objects)




You can get output from R simply by typing math in the console:


~~~r
3 + 5
~~~




~~~
[1] 8
~~~




~~~r
12 / 7
~~~




~~~
[1] 1.714286
~~~


However, to do useful and interesting things, we need to assign _values_ to
_objects_. To create an object, we need to give it a name followed by the
assignment operator `<-`, and the value we want to give it:


~~~r
area_hectares <- 1.0
~~~


`<-` is the assignment operator. It assigns values on the right to objects on
the left. So, after executing `x <- 3`, the value of `x` is `3`. The arrow can
be read as 3 **is assigned the value of** `x`.  For historical reasons, you can also use `=`
for assignments, but not in every context. Because of the
[slight](http://blog.revolutionanalytics.com/2008/12/use-equals-or-arrow-for-assignment.html)
[differences](http://r.789695.n4.nabble.com/Is-there-any-difference-between-and-tp878594p878598.html)
in syntax, it is good practice to always use `<-` for assignments. If you search the Internet for help with R code, you will occasionally see examples using `=`, but the majority will use `<-`.>

In RStudio, typing <kbd>Alt</kbd> + <kbd>-</kbd> (push <kbd>Alt</kbd> at the
same time as the <kbd>-</kbd> key) will write `<- ` in a single keystroke in a
PC, while typing <kbd>Option</kbd> + <kbd>-</kbd> (push <kbd>Option</kbd> at the
same time as the <kbd>-</kbd> key) does the same in a Mac.

### Naming Objects

Objects can be given any name such as `x`, `current_temperature`, or
`subject_id`. You want your object names to be explicit and not too long. They
cannot start with a number (`2x` is not valid, but `x2` is). **R is case sensitive**
(e.g., `age` is different from `Age`). There are some names that
cannot be used because they are the names of fundamental functions in R (e.g.,
`if`, `else`, `for`, see
[here](https://stat.ethz.ch/R-manual/R-devel/library/base/html/Reserved.html)
for a complete list). In general, even if it's allowed, it's best to not use
other function names (e.g., `c`, `T`, `mean`, `data`, `df`, `weights`). If in
doubt, check the help to see if the name is already in use. It's also best to
avoid dots (`.`) within an object name as in `my.dataset`. There are many
functions in R with dots in their names for historical reasons, but because dots
have a special meaning in R (for methods) and other programming languages, it's
best to avoid them. It is also recommended to use nouns for object names, and
verbs for function names. It's important to be consistent in the styling of your
code (where you put spaces, how you name objects, etc.). Using a consistent
coding style makes your code clearer to read for your future self and your
collaborators. In R, three popular style guides are
[Google's](https://google.github.io/styleguide/Rguide.xml), [Jean
Fan's](http://jef.works/R-style-guide/) and the
[tidyverse's](http://style.tidyverse.org/). The tidyverse's is very
comprehensive and may seem overwhelming at first. You can install the
[**`lintr`**](https://github.com/jimhester/lintr) package to automatically check
for issues in the styling of your code.



When assigning a value to an object, R does not print anything. You
can force R to print the value by using parentheses or by typing
the object name:


~~~r
area_hectares <- 1.0    # doesn't print anything
(area_hectares <- 1.0)  # putting parenthesis around the call prints the value of `area_hectares`
~~~




~~~
[1] 1
~~~




~~~r
area_hectares         # and so does typing the name of the object
~~~




~~~
[1] 1
~~~


Now that R has `area_hectares` in memory, we can do arithmetic with it. For
instance, we may want to convert this area into acres (area in acres is 2.47 times the area in hectares):


~~~r
2.47 * area_hectares
~~~


~~~
[1] 2.47
~~~


We can also change an object's value by assigning it a new one:


~~~r
area_hectares <- 2.5
2.47 * area_hectares
~~~


~~~
[1] 6.175
~~~


This means that assigning a value to one object does not change the values of
other objects  For example, let's store the plot's area in acres
in a new object, `area_acres`:


~~~r  
area_acres <- 2.47 * area_hectares
~~~


and then change `area_hectares` to 50.


~~~r
area_hectares <- 50
~~~



> ### Exercise
> 
> What do you think is the current content of the object `area_acres`? 123.5 or
> 6.175?
>

<details> 
<summary>
<b>Solution</b>  - click me</summary>

The value of `area_acres` is still 6.175 because you have not
re-run the line `area_acres <- 2.47 * area_hectares` since
changing the value of `area_hectares`.


<br>

```r
area_acres <- 2.47 * area_hectares
area_acres
```


</details>


## Comments

All programming languages allow the programmer to include comments in their code. To do this in R we use the `#` character.
Anything to the right of the `#` sign and up to the end of the line is treated as a comment and is ignored by R. You can start lines with comments
or include them after any code on the line.
