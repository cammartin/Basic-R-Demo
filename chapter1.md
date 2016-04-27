---
title       : Insert the chapter title here
description : Insert the chapter description here
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf


--- type:NormalExercise lang:r xp:100 skills:1
## Cost of diamonds 

In this exercise, we will use the dataset diamonds within the ggplot2 package. Using a randomForest will attempt to predict the cost of a diamond using a some of the diamond characterists found in the dataset.

*** =instructions
- Load `ggplot2` into the environment.
- Assign `diamonds` dataset. 
- Check out the structure of diamonds.

*** =hint
- Use `str()` to see the structure of diamonds.
- Remember to assign the `diamonds` dataset.
 

*** =pre_exercise_code
```{r}
# Pre-load a package in the workspace

# You can prepare the data before the student starts:

# You can also clean up data so that it's not available in the student's workspace anymore:

```

*** =sample_code
```{r}
# Make ggplot2 available to use
#library(ggplot2)

# Make the dataset diamonds available to use
#diamonds <- diamonds

# Check out the structure of diamonds
#str(diamonds)
```

*** =solution
```{r}
# Make ggplot2 available to use
library(ggplot2)

# Make the dataset diamonds available to use
diamonds <- diamonds

# Check out the structure of diamonds
str(diamonds)

```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki
test_function("library",
              not_called_msg = "You didn't call `library()`!",
              incorrect_msg = "You didn't call `library(object = ...)` with the correct argument, `object`.")

# Test the object, diamonds
# Notice that we didn't define any feedback here, this will cause automatically 
# generated feedback to be given to the student in case of an incorrect submission
 test_object("diamonds")
 
 
# Test whether the function str is called with the correct argument, object
# If it is not called, print something informative
# If it is called, but called incorrectly, print something else
 test_function("str", args = "object", 
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")


# It's always smart to include the following line of code at the end of your SCTs
# It will check whether executing the student's code resulted in an error, 
# and if so, will cause the exercise to fail
test_error()

# Final message the student will see upon completing the exercise
success_msg("Good work!")
```

--- type:NormalExercise lang:r xp:100 skills:1
## Cost of diamonds 2

In the last exercise, you saw a dataset about diamonds. In this exercise, we will look at the same dataset in a different way!

The package ggplot and the dataset diamonds are available in the workspace.

*** =instructions
- Check out the structure of diamonds, but use `summary()` this time.
- Use `head()` show the columns names and the first few rows of the dataset.

*** =hint
- Use 'summary()' to see the structure of diamonds.
- Use 'head()' to display the column names and the first few rows of the dataset.

*** =pre_exercise_code
```{r}
library(ggplot2)
diamonds <- diamonds
```

*** =sample_code
```{r}
# Check out the structure of diamonds
#summary(diamonds)

# Display the column names and first few rows of the data set
#head(diamonds)
```

*** =solution
```{r}
# Check out the structure of diamonds
summary(diamonds)

# Display the column names and first few rows of the data set
head(diamonds)
```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

# Test whether the function summary is called with the correct argument, object
# If it is not called, print something informative
# If it is called, but called incorrectly, print something else
 test_function("summary", args = "object", 
              not_called_msg = "You didn't call `summary()`!",
              incorrect_msg = "You didn't call `summary(object = ...)` with the correct argument, `object`.")

#test_function("head", 
#              not_called_msg = "You didn't call `head()`!",
#              incorrect_msg = "You didn't call `head(object = ...)` with the correct argument, `object`.")
test_output_contains("head(diamonds)", incorrect_msg = "Something is wrong with `head()`. Take another look at the instruction.")
test_student_typed("head(diamonds)", not_typed_msg = "Something is wrong with `head()`. Take another look at the instruction.")


# It's always smart to include the following line of code at the end of your SCTs
# It will check whether executing the student's code resulted in an error, 
# and if so, will cause the exercise to fail
test_error()

# Final message the student will see upon completing the exercise
success_msg("Good work!")
```

--- type:NormalExercise lang:r xp:100 skills:1
## Cost of diamonds 3

In the previous exercise, we looked at the stucture of the data, but now let's look at some graphs of the data. 

The diamonds dataset and ggplot2 are available in the workspace.

*** =instructions
- Create two histograms from the diamond dataset. 
- Have the first histogram count the diamonds in terms of their price.
- Have the second histogram count the diamonds in terms of carat size. 


*** =hint
- Add `qplot` to render the graphs.


*** =pre_exercise_code
```{r}
# Pre-load a package in the workspace
library(ggplot2)
diamonds <- diamonds
```

*** =sample_code
```{r}
# Create a histogram of the price of the diamonds in the dataset
#(price, data=diamonds, geom="histogram", bins = 20)

# Create a histogram of the carat sizes of the diamonds in the dataset
#(carat, data=diamonds, geom="histogram", bins = 20)
```

*** =solution
```{r}
# Create a histogram of the price of the diamonds in the dataset
qplot(price, data=diamonds, geom="histogram", bins = 20)

# Create a histogram of the carat sizes of the diamonds in the dataset
qplot(carat, data=diamonds, geom="histogram", bins = 20)
```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

# Test whether the function str is called with the correct argument, object
# If it is not called, print something informative
# If it is called, but called incorrectly, print something else
test_function("qplot", args = c("data", "geom", "bins"),
              not_called_msg = "You didn't call `qplot()`!",
              incorrect_msg = "You didn't call `qplot(data = ...,geom = ..., bins= ...)` with the correct argument, `data = ...,geom = ..., bins= ...`.")

test_student_typed("qplot(price, data=diamonds, geom='histogram', bins = 20)", not_typed_msg = "Something is wrong with your qplot. Take another look at the instruction.")

test_student_typed("qplot(carat, data=diamonds, geom='histogram', bins = 20)", not_typed_msg = "Something is wrong with your qplot. Take another look at the instruction.")

# It's always smart to include the following line of code at the end of your SCTs
# It will check whether executing the student's code resulted in an error, 
# and if so, will cause the exercise to fail
test_error()

# Final message the student will see upon completing the exercise
success_msg("Good work!")
```

--- type:NormalExercise lang:r xp:100 skills:1
## Cost of diamonds 4


*** =instructions
- Create a series of facet_grid ggplots with the price on the y axis, carat size on the x axis and the cut as the color.
- Because there are two variables use `ggplot` with the `geom_point` extension.
- Use the diamond clarity as the variable to separate the data into subplots.
- Create new column categorical `price_level`
- Remove old `price`column
- Create `qplot` histogram for new `price_level` column


*** =hint
- Use `ggplot` for the first instruction.


*** =pre_exercise_code
```{r}
# Pre-load a package in the workspace
library(ggplot2)
diamonds <- diamonds
```

*** =sample_code
```{r}
# The dataset diamonds and the ggplot2 package are available in your workspace.

# Display the column names.
#names(diamonds)

# Create a series of facet_grid ggplots.
#ggplot(diamonds, aes(x=carat, y=price, color=cut)) + geom_point() + facet_grid(color ~ clarity)

# Create a column price_level.
#diamonds$price_level <- as.numeric(cut(diamonds$price, seq(from = 0, to = 50000, by = 4000)))

# Show that you have successfully added the price_level column.
#names(diamonds)

# We won't need the price column anymore, remove it from the dataset.
#diamonds$price <- NULL

# Show that you have successfully removed the price_level column.
#names(diamonds)

# Find the maximum price level and make a histogram using `qplot` and price_level 
#max(diamonds$)
#(price_level, data=diamonds, geom="histogram", bins = 5)

```

*** =solution
```{r}
# The dataset diamonds and the ggplot2 package are available in your workspace.

# Display the column names.
names(diamonds)

# Create a series of facet_grid ggplots.
ggplot(diamonds, aes(x=carat, y=price, color=cut)) + geom_point() + facet_grid(color ~ clarity)

# Create a column price_level.
diamonds$price_level <- as.numeric(cut(diamonds$price, seq(from = 0, to = 50000, by = 4000)))

# Show that you have successfully added the price_level column.
names(diamonds)

# We won't need the price column anymore, remove it from the dataset.
diamonds$price <- NULL

# Show that you have successfully removed the price_level column.
names(diamonds)

# Find the maximum price level and make a histogram using `qplot` and price_level 
max(diamonds$price_level)
qplot(price_level, data=diamonds, geom='histogram', bins = 5)
```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

# Test whether the function str is called with the correct argument, object
# If it is not called, print something informative
# If it is called, but called incorrectly, print something else
# first instruction
test_student_typed("names(diamonds)", not_typed_msg = "Did you forget to check the column names? Take another look at the instruction.")
test_output_contains("names(diamonds)", incorrect_msg = "Did you forget to check the column names? Take another look at the instruction.")

# second instruction
test_output_contains("ggplot(diamonds, aes(x=carat, y=price, color=cut)) + geom_point() + facet_grid(color ~ clarity)", incorrect_msg = "Take a look at your code for the facet plot.")
test_function("ggplot")

# third instruction
test_student_typed("diamonds$price_level", not_typed_msg = "Did you forget to add price_level column? Take another look at the instruction.")
test_output_contains("diamonds$price_level <- as.numeric(cut(diamonds$price, seq(from = 0, to = 50000, by = 4000)))", incorrect_msg = "Did you forget to add price_level column? Take another look at the instruction.")

# fourth instruction
test_student_typed("names(diamonds)", not_typed_msg = "Did you forget to check the column names? Take another look at the instruction.")
test_output_contains("names(diamonds)", incorrect_msg = "Did you forget to check the column names? Take another look at the instruction.")

# fifth instruction
test_student_typed("diamonds$price <- NULL", not_typed_msg = "Did you forget to remove the price column? Take another look at the instruction.")
test_output_contains("diamonds$price <- NULL", incorrect_msg = "Did you forget to remove the price column? Take another look at the instruction.")

# sixth instruction
test_student_typed("names(diamonds)", not_typed_msg = "Did you forget to check the column names? Take another look at the instruction.")
test_output_contains("names(diamonds)", incorrect_msg = "Did you forget to check the column names? Take another look at the instruction.")

# seventh instruction
test_student_typed("max(diamonds$price_level)", not_typed_msg = "Did you forget to check the max price_level? Take another look at the instruction.")
test_output_contains("max(diamonds$price_level)", incorrect_msg = "Did you forget to check the max price_level? Take another look at the instruction.")

# eigth instruction
test_output_contains("qplot(price_level, data=diamonds, geom='histogram', bins = 5)", incorrect_msg = "Take a look at your code for the facet plot.")
test_function("qplot")

# It's always smart to include the following line of code at the end of your SCTs
# It will check whether executing the student's code resulted in an error, 
# and if so, will cause the exercise to fail
test_error()

# Final message the student will see upon completing the exercise
success_msg("Good work!")
```

--- type:NormalExercise lang:r xp:100 skills:1
## Diamonds 5

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
# Pre-load a package in the workspace
library(ggplot2)
diamonds <- diamonds
diamonds$price_level <- as.numeric(cut(diamonds$price,seq(from = 0, to = 50000, by = 4000)))
diamonds$price <- NULL


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
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

# Test whether the function str is called with the correct argument, object
# If it is not called, print something informative
# If it is called, but called incorrectly, print something else
test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

# Test the object, good_movies
# Notice that we didn't define any feedback here, this will cause automatically 
# generated feedback to be given to the student in case of an incorrect submission
test_object("good_movies")

# Test whether the student correctly used plot()
# Again, we use the automatically generated feedback here
test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

# Alternativeley, you can use test_function() like this
# test_function("plot", args = c("x", "y", "col"))

# It's always smart to include the following line of code at the end of your SCTs
# It will check whether executing the student's code resulted in an error, 
# and if so, will cause the exercise to fail
test_error()

# Final message the student will see upon completing the exercise
success_msg("Good work!")
```

--- type:NormalExercise lang:r xp:100 skills:1
## Diamonds 6

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
# Pre-load a package in the workspace
library(MindOnStats)

# You can prepare the data before the student starts:
data(Movies)
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"),c("Genre", "Rating", "Run")]

# You can also clean up data so that it's not available in the student's workspace anymore:
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
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

# Test whether the function str is called with the correct argument, object
# If it is not called, print something informative
# If it is called, but called incorrectly, print something else
test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

# Test the object, good_movies
# Notice that we didn't define any feedback here, this will cause automatically 
# generated feedback to be given to the student in case of an incorrect submission
test_object("good_movies")

# Test whether the student correctly used plot()
# Again, we use the automatically generated feedback here
test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

# Alternativeley, you can use test_function() like this
# test_function("plot", args = c("x", "y", "col"))

# It's always smart to include the following line of code at the end of your SCTs
# It will check whether executing the student's code resulted in an error, 
# and if so, will cause the exercise to fail
test_error()

# Final message the student will see upon completing the exercise
success_msg("Good work!")
```

--- type:NormalExercise lang:r xp:100 skills:1
## Diamonds 7

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
# Pre-load a package in the workspace
library(MindOnStats)

# You can prepare the data before the student starts:
data(Movies)
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"),c("Genre", "Rating", "Run")]

# You can also clean up data so that it's not available in the student's workspace anymore:
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
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

# Test whether the function str is called with the correct argument, object
# If it is not called, print something informative
# If it is called, but called incorrectly, print something else
test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

# Test the object, good_movies
# Notice that we didn't define any feedback here, this will cause automatically 
# generated feedback to be given to the student in case of an incorrect submission
test_object("good_movies")

# Test whether the student correctly used plot()
# Again, we use the automatically generated feedback here
test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

# Alternativeley, you can use test_function() like this
# test_function("plot", args = c("x", "y", "col"))

# It's always smart to include the following line of code at the end of your SCTs
# It will check whether executing the student's code resulted in an error, 
# and if so, will cause the exercise to fail
test_error()

# Final message the student will see upon completing the exercise
success_msg("Good work!")
```
