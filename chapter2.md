---
title: 'First Linear Models'
description: ""
---

## First Model

```yaml
type: NormalExercise
key: f9f0004f3a
xp: 100
```

Starting with a simple linear regression model.

`@instructions`
Regress wage76 on ed76 and black. 
Save the model and the summary of it.

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
model1 <- lm( ~ , data=Schooling)
sum_model1 <- 
```

`@solution`
```{r}
model1      <- lm(wage76~ed76+black, data=Schooling)
sum_model1  <- summary(model1)
```

`@sct`
```{r}

```

---

## Second Model

```yaml
type: NormalExercise
key: 6824c75950
xp: 100
```



`@instructions`
Regress wage76 on ed76, black, exp76, nearc4a, nearc4b, south66, south76, sinmom14, daded, momed, famed, enroll76 and smsa76.
Save the model and the summary of it.

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
model2      <- lm( ~, data=Schooling)
sum_model2  <- 
```

`@solution`
```{r}
model2      <- lm(wage76~ed76+black+exp76+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+famed+enroll76+smsa76,
                     data=Schooling)
sum_model2  <- summary(model2)
```

`@sct`
```{r}

```

---

## R2

```yaml
type: PureMultipleChoiceExercise
key: 4e408e19b0
xp: 50
```

A model with a higher number of regressors has always a higher R2.

`@hint`


`@possible_answers`
wrong
[right]
unclear

`@feedback`
Unfortunately not.
Yes, you are right.
Unfortunately not.

---

## Adjusted R2

```yaml
type: PureMultipleChoiceExercise
key: 90883cf28f
xp: 50
```

A model with a higher number of regressors has always a higher adjusted R2.

`@hint`


`@possible_answers`
[wrong]
right
unclear

`@feedback`
Yes, you are right.
Unfortunately not.
Unfortunately not.
