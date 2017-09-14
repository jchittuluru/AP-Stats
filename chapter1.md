---
title       : Chapter 3 
description : Examining Relationships through Scatterplots, Correlation, and Least-Squares Regression
attachments : 
  slides_link : https://drive.google.com/open?id=0BzCPikTu8tqYNkdESE9qMy1XWFE&authuser=0

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:4c580e84bc
## Describing a Scatterplot: Direction

Have a look at the plot that showed up in the viewer to the right. How would you describe its direction?

*** =instructions
- Positive Association
- Negative Association
- No Association

*** =hint
Have a look at the plot; what kind of slope would a line drawn through the points have?

*** =pre_exercise_code
```{r}
# The pre exercise code runs code to initialize the user's workspace.
# You can use it to load packages, initialize datasets and draw a plot in the viewer

boats = c(498, 513, 512, 526, 559, 585, 614, 645, 675, 711, 719)
manatees = c(16, 24, 20, 15, 34, 33, 33, 39, 43, 50, 47)
plot(boats,manatees, ylab = "Manatee Deaths", xlab = "Thousands of Registered Boats")

```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "Please try again :)"
msg_success <- "Correct, the number of manatee deaths increases with powerboat registrations."
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad, msg_bad))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:cebccefc02
## More movies

In the previous exercise, you saw a dataset about movies. In this exercise, we'll have a look at yet another dataset about movies!

A dataset with a selection of movies, `movie_selection`, is available in the workspace.

*** =instructions
- Check out the structure of `movie_selection`.
- Select movies with a rating of 5 or higher. Assign the result to `good_movies`.
- Use `plot()` to  plot `good_movies$Run` on the x-axis, `good_movies$Rating` on the y-axis and set `col` to `good_movies$Genre`.

*** =hint
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`.

*** =pre_exercise_code
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code
load(url("https://s3.amazonaws.com/assets.datacamp.com/course/teach/movies.RData"))
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"), c("Genre", "Rating", "Run")]

# Clean up the environment
rm(Movies)
```

*** =sample_code
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection


# Select movies that have a rating of 5 or higher: good_movies


# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre

```

*** =solution
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

test_object("good_movies")

test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

test_error()

success_msg("Good work!")
```



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:3487dbbbc7
## Problem 3.1 (a)

Given the relationship between the amount of time that a student spends studying for her test and the grade that she receives, her study time should be considered...

*** =instructions
 
- a response variable
- an unrelated variable
- an explanatory variable

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}

msg_bad <- "Please try again :)"
msg_success <- "Correct!"
test_mc(correct = 3, feedback_msgs = c(msg_bad, msg_bad, msg_success))

```



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:eff633f5c7
## Problem 3.1 (b)


Problem 3.1 (b)


*** =instructions
Given the relationship between a person's height and weight, a person's weight should be considered... 

-a response variable
-an unrelated variable
-an explanatory variable

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}

msg_bad <- "Please try again :)"
msg_success <- "Correct!"
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad, msg_bad))

```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:8f2d929d1a
## Problem 3.1 (c)


Problem 3.1 (c)


*** =instructions
Given the relationship between the amount of yearly rainfall and the yield of a crop, the amount of rainfall should be considered... 

-a response variable
-an unrelated variable
-an explanatory variable

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}

msg_bad <- "Please try again :)"
msg_success <- "Correct!"
test_mc(correct = 3, feedback_msgs = c(msg_bad, msg_bad, msg_success))

```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1192cdf79b
## Problem 3.1 (d)


Problem 3.1 (d)


*** =instructions
Given the relationship between a person's grade in statistics and a person's grade in French, a person's grade in statistics should be considered... 

-a response variable
-an unrelated variable
-an explanatory variable

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}

msg_bad <- "Please try again :)"
msg_success <- "Correct!"
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad))

```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:d79416bc14
## Problem 3.1 (e)


Problem 3.1 (e)


*** =instructions
Given the relationship between a father's occupational class and his son's occupational class, his son's occupational class should be considered... 

-a response variable
-an unrelated variable
-an explanatory variable

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}

msg_bad <- "Please try again :)"
msg_success <- "Correct!"
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad, msg_bad))

```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:648ac92014
## Problem 3.3

Problem 3.3


*** =instructions
There may be a gender gap in the US with regard to political preference, with women tending to prefer the Democrat Party to the Republican Party. If a statistician conducts a study that asks voters whether they prefer to vote Democrat or Republican, which variable in this study is explanatory, and which is response? Further, are these variables catagorical or quantititative?

-Explanatory: Party Preference, Response: Gender, Variables are Categorical
-Explanatory: Gender, Response: Party Preference, Variables are Categorical
-Explanatory: Party Preference, Response: Gender, Variables are Quantitative
-Explanatory: Gender, Response: Party Preference, Variables are Quantitative

*** =hint
Is gender affecting voter preference, or is voter preference causing people to adopt a different gender? Also, are there any numerical values involved above?

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
msg_bad <- "Please try again :)"
msg_success <- "Correct!"
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad))

```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:df2a3ff1c0
## Problem 3.7 (a)

Problem 3.7 (a)


*** =instructions
If a study investigates the relationship between the number of jet skis in use and the number of jet ski accidents, the explanatory variable is...

-the number of jet skis in use
-the number of jet ski accidents


*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}

msg_bad <- "Please try again :)"
msg_success <- "Correct!"
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad))

```



--- type:NormalExercise lang:r xp:100 skills:1 key:95c4609ede
## Problem 3.7 (b)


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}

```

*** =solution
```{r}

```

*** =sct
```{r}

```
