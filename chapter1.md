---
title: 'Load data and preparation'
description: 'Chapter description goes here.'
---

## Load data

```yaml
type: NormalExercise
key: 2bafef99a3
lang: r
xp: 100
skills: 1
```

In a first step, we look at the dataset "Schooling" which is already loaded from the package "Ecdat".

`@instructions`
Use the head() function, to see the first lines of the dataset

`@hint`


`@pre_exercise_code`
```{r}
set.seed(123456)
Schooling <- read.csv("http://assets.datacamp.com/production/repositories/4057/datasets/ac9460776cedb41072c2431250011c31148b0d61/Schooling.csv")
```

`@sample_code`
```{r}
head()
```

`@solution`
```{r}
head(Schooling)
```

`@sct`
```{r}

```

---

## Data preparation 1

```yaml
type: NormalExercise
key: 76f8ad6c1e
xp: 100
```

We now want to generate new variables and modify existing ones.

`@instructions`
Generate new variables for the square and a third order term of ed76 and exp76.
Append those four new variables to the dataset Schooling. You may do this in one step

`@hint`


`@pre_exercise_code`
```{r}
set.seed(123456)
Schooling <- read.csv("http://assets.datacamp.com/production/repositories/4057/datasets/ac9460776cedb41072c2431250011c31148b0d61/Schooling.csv")
```

`@sample_code`
```{r}
Schooling$ed76_2 <- ()^2
Schooling$ed76_3 <-
Schooling$exp76_2 <- 
Schooling$exp76_3 <- 
```

`@solution`
```{r}
Schooling$ed76_2 <- (Schooling$ed76)^2
Schooling$ed76_3 <- (Schooling$ed76)^3
Schooling$exp76_2 <- (Schooling$exp76)^2
Schooling$exp76_3 <- (Schooling$exp76)^3
```

`@sct`
```{r}

```

---

## Data preparation 2

```yaml
type: NormalExercise
key: 42caf1b942
xp: 100
```

Some variables are saved as factors containing levels "yes" and "no". We want to change those.

`@instructions`
Convert the variables black, nearc4a, nearc4b, south66, south76, sinmom14, enroll76 and smsa76 to factor variables which have levels 1 and 0.
Replace the existing variables in the dataset Schooling by these new variables.

`@hint`


`@pre_exercise_code`
```{r}
set.seed(123456)
Schooling <- read.csv("http://assets.datacamp.com/production/repositories/4057/datasets/ac9460776cedb41072c2431250011c31148b0d61/Schooling.csv")
Schooling$ed76_2 <- (Schooling$ed76)^2
Schooling$ed76_3 <- (Schooling$ed76)^3
Schooling$exp76_2 <- (Schooling$exp76)^2
Schooling$exp76_3 <- (Schooling$exp76)^3
```

`@sample_code`
```{r}
Schooling$var <- as.factor(as.numeric(Schooling$var) - 1)
```

`@solution`
```{r}
Schooling$black <- as.factor(as.numeric(Schooling$black)-1)
Schooling$nearc4a <- as.factor(as.numeric(Schooling$nearc4a)-1)
Schooling$nearc4b <- as.factor(as.numeric(Schooling$nearc4b)-1)
Schooling$south66 <- as.factor(as.numeric(Schooling$south66)-1)
Schooling$south76 <- as.factor(as.numeric(Schooling$south76)-1)
Schooling$sinmom14 <- as.factor(as.numeric(Schooling$sinmom14)-1)
Schooling$enroll76 <- as.factor(as.numeric(Schooling$enroll76)-1)
Schooling$smsa76 <- as.factor(as.numeric(Schooling$smsa76)-1)
```

`@sct`
```{r}

```
