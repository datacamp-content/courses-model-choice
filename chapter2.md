---
title: 'First Linear Models'
description: ""
---

## Insert exercise title here

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
