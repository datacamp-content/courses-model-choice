---
title: 'Chapter Title Here'
description: 'Chapter description goes here.'
---

## Load data and preparation

```yaml
type: NormalExercise
key: 2bafef99a3
lang: r
xp: 100
skills: 1
```

In a first step, we load the data and apply some changes to the variables.

`@instructions`
Load the dataset "Schooling" by using the data() function.

`@hint`
You have to type data("") where you place the name of the dataset in between the quotation marks. Type head(Schooling) to get a proper dataset (not a "promise").

`@pre_exercise_code`
```{r}
install.packages("Ecdat")
library(Ecdat)
```

`@sample_code`
```{r}

```

`@solution`
```{r}
data("Schooling")
head(Schooling)
```

`@sct`
```{r}

```
