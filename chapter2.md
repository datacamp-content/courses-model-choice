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
set.seed(123456)
Schooling <- read.csv("http://assets.datacamp.com/production/repositories/4057/datasets/ac9460776cedb41072c2431250011c31148b0d61/Schooling.csv")
Schooling$ed76_2 <- (Schooling$ed76)^2
Schooling$ed76_3 <- (Schooling$ed76)^3
Schooling$exp76_2 <- (Schooling$exp76)^2
Schooling$exp76_3 <- (Schooling$exp76)^3

Schooling$black <- as.factor(as.numeric(Schooling$black)-1)
Schooling$nearc4a <- as.factor(as.numeric(Schooling$nearc4a)-1)
Schooling$nearc4b <- as.factor(as.numeric(Schooling$nearc4b)-1)
Schooling$south66 <- as.factor(as.numeric(Schooling$south66)-1)
Schooling$south76 <- as.factor(as.numeric(Schooling$south76)-1)
Schooling$sinmom14 <- as.factor(as.numeric(Schooling$sinmom14)-1)
Schooling$enroll76 <- as.factor(as.numeric(Schooling$enroll76)-1)
Schooling$smsa76 <- as.factor(as.numeric(Schooling$smsa76)-1)
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
set.seed(123456)
Schooling <- read.csv("http://assets.datacamp.com/production/repositories/4057/datasets/ac9460776cedb41072c2431250011c31148b0d61/Schooling.csv")
Schooling$ed76_2 <- (Schooling$ed76)^2
Schooling$ed76_3 <- (Schooling$ed76)^3
Schooling$exp76_2 <- (Schooling$exp76)^2
Schooling$exp76_3 <- (Schooling$exp76)^3

Schooling$black <- as.factor(as.numeric(Schooling$black)-1)
Schooling$nearc4a <- as.factor(as.numeric(Schooling$nearc4a)-1)
Schooling$nearc4b <- as.factor(as.numeric(Schooling$nearc4b)-1)
Schooling$south66 <- as.factor(as.numeric(Schooling$south66)-1)
Schooling$south76 <- as.factor(as.numeric(Schooling$south76)-1)
Schooling$sinmom14 <- as.factor(as.numeric(Schooling$sinmom14)-1)
Schooling$enroll76 <- as.factor(as.numeric(Schooling$enroll76)-1)
Schooling$smsa76 <- as.factor(as.numeric(Schooling$smsa76)-1)

model1      <- lm(wage76~ed76+black, data=Schooling)
sum_model1  <- summary(model1)
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
1. wrong
2. [right]
3. unclear

`@feedback`
1. Unfortunately not.
2. Yes, you are right. A higher number of regressors mechanically increases the R2.
3. Unfortunately not.

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
1. [wrong]
2. right
3. unclear

`@feedback`
1. Yes, you are right. The adjusted R2 decreases if irrelevant regressors are included.
2. Unfortunately not.
3. Unfortunately not.

---

## Calculate the R2

```yaml
type: NormalExercise
key: 0f17f63b8a
xp: 100
```



`@instructions`
Calculate the R2 for both models. Note that the R2 is saved in the summary object we saved up front.

`@hint`
The R2 is saved as r.squared, it can thus be extracted by …$r.squared.

`@pre_exercise_code`
```{r}
set.seed(123456)
Schooling <- read.csv("http://assets.datacamp.com/production/repositories/4057/datasets/ac9460776cedb41072c2431250011c31148b0d61/Schooling.csv")
Schooling$ed76_2 <- (Schooling$ed76)^2
Schooling$ed76_3 <- (Schooling$ed76)^3
Schooling$exp76_2 <- (Schooling$exp76)^2
Schooling$exp76_3 <- (Schooling$exp76)^3

Schooling$black <- as.factor(as.numeric(Schooling$black)-1)
Schooling$nearc4a <- as.factor(as.numeric(Schooling$nearc4a)-1)
Schooling$nearc4b <- as.factor(as.numeric(Schooling$nearc4b)-1)
Schooling$south66 <- as.factor(as.numeric(Schooling$south66)-1)
Schooling$south76 <- as.factor(as.numeric(Schooling$south76)-1)
Schooling$sinmom14 <- as.factor(as.numeric(Schooling$sinmom14)-1)
Schooling$enroll76 <- as.factor(as.numeric(Schooling$enroll76)-1)
Schooling$smsa76 <- as.factor(as.numeric(Schooling$smsa76)-1)

model1      <- lm(wage76~ed76+black, data=Schooling)
sum_model1  <- summary(model1)
model2      <- lm(wage76~ed76+black+exp76+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+famed+enroll76+smsa76,data=Schooling)
sum_model2  <- summary(model2)
```

`@sample_code`
```{r}
model1r2 <- 
model2r2 <- 
```

`@solution`
```{r}
model1r2 <- sum_model1$r.squared
model2r2 <- sum_model2$r.squared
```

`@sct`
```{r}

```

---

## Calculate the adjusted R2

```yaml
type: NormalExercise
key: 6984fe58ff
xp: 100
```



`@instructions`
Calculate the adjusted R2 for both models. Note that the adjusted R2 is saved in the summary object we saved up front.

`@hint`
The adjusted R2 is saved as adj.r.squared, it can thus be extracted by …$adj.r.squared.

`@pre_exercise_code`
```{r}
set.seed(123456)
Schooling <- read.csv("http://assets.datacamp.com/production/repositories/4057/datasets/ac9460776cedb41072c2431250011c31148b0d61/Schooling.csv")
Schooling$ed76_2 <- (Schooling$ed76)^2
Schooling$ed76_3 <- (Schooling$ed76)^3
Schooling$exp76_2 <- (Schooling$exp76)^2
Schooling$exp76_3 <- (Schooling$exp76)^3

Schooling$black <- as.factor(as.numeric(Schooling$black)-1)
Schooling$nearc4a <- as.factor(as.numeric(Schooling$nearc4a)-1)
Schooling$nearc4b <- as.factor(as.numeric(Schooling$nearc4b)-1)
Schooling$south66 <- as.factor(as.numeric(Schooling$south66)-1)
Schooling$south76 <- as.factor(as.numeric(Schooling$south76)-1)
Schooling$sinmom14 <- as.factor(as.numeric(Schooling$sinmom14)-1)
Schooling$enroll76 <- as.factor(as.numeric(Schooling$enroll76)-1)
Schooling$smsa76 <- as.factor(as.numeric(Schooling$smsa76)-1)

model1      <- lm(wage76~ed76+black, data=Schooling)
sum_model1  <- summary(model1)
model2      <- lm(wage76~ed76+black+exp76+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+famed+enroll76+smsa76,data=Schooling)
sum_model2  <- summary(model2)

model1r2 <- sum_model1$r.squared
model2r2 <- sum_model2$r.squared
```

`@sample_code`
```{r}
model1adr2 <- 
model2adr2 <- 
```

`@solution`
```{r}
model1adr2 <- sum_model1$adj.r.squared
model2adr2 <- sum_model2$adj.r.squared
```

`@sct`
```{r}

```

---

## comparison R2

```yaml
type: NormalExercise
key: ad1c9490db
xp: 100
```



`@instructions`
List the R2 and the adjusted R2 for both models. Remember that you saved them by model1r2, model2r2, model2adr2 and model2adr2.

`@hint`


`@pre_exercise_code`
```{r}
set.seed(123456)
Schooling <- read.csv("http://assets.datacamp.com/production/repositories/4057/datasets/ac9460776cedb41072c2431250011c31148b0d61/Schooling.csv")
Schooling$ed76_2 <- (Schooling$ed76)^2
Schooling$ed76_3 <- (Schooling$ed76)^3
Schooling$exp76_2 <- (Schooling$exp76)^2
Schooling$exp76_3 <- (Schooling$exp76)^3

Schooling$black <- as.factor(as.numeric(Schooling$black)-1)
Schooling$nearc4a <- as.factor(as.numeric(Schooling$nearc4a)-1)
Schooling$nearc4b <- as.factor(as.numeric(Schooling$nearc4b)-1)
Schooling$south66 <- as.factor(as.numeric(Schooling$south66)-1)
Schooling$south76 <- as.factor(as.numeric(Schooling$south76)-1)
Schooling$sinmom14 <- as.factor(as.numeric(Schooling$sinmom14)-1)
Schooling$enroll76 <- as.factor(as.numeric(Schooling$enroll76)-1)
Schooling$smsa76 <- as.factor(as.numeric(Schooling$smsa76)-1)

model1      <- lm(wage76~ed76+black, data=Schooling)
sum_model1  <- summary(model1)
model2      <- lm(wage76~ed76+black+exp76+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+famed+enroll76+smsa76,data=Schooling)
sum_model2  <- summary(model2)

model1r2 <- sum_model1$r.squared
model2r2 <- sum_model2$r.squared
model1adr2 <- sum_model1$adj.r.squared
model2adr2 <- sum_model2$adj.r.squared
```

`@sample_code`
```{r}

```

`@solution`
```{r}
model1r2
model2r2
model1adr2 
model2adr2 
```

`@sct`
```{r}

```

---

## AIC and BIC

```yaml
type: NormalExercise
key: e901bb74ff
xp: 100
```

There are other ways to measure the fit of a model than using the R2 and the adjusted R2. 
The Akaike and the Bayesian Information Criterion are such measures.

`@instructions`
Compute the AIC and BIC for both models. Use the functions AIC() and BIC() and list them.

`@hint`


`@pre_exercise_code`
```{r}
set.seed(123456)
Schooling <- read.csv("http://assets.datacamp.com/production/repositories/4057/datasets/ac9460776cedb41072c2431250011c31148b0d61/Schooling.csv")
Schooling$ed76_2 <- (Schooling$ed76)^2
Schooling$ed76_3 <- (Schooling$ed76)^3
Schooling$exp76_2 <- (Schooling$exp76)^2
Schooling$exp76_3 <- (Schooling$exp76)^3

Schooling$black <- as.factor(as.numeric(Schooling$black)-1)
Schooling$nearc4a <- as.factor(as.numeric(Schooling$nearc4a)-1)
Schooling$nearc4b <- as.factor(as.numeric(Schooling$nearc4b)-1)
Schooling$south66 <- as.factor(as.numeric(Schooling$south66)-1)
Schooling$south76 <- as.factor(as.numeric(Schooling$south76)-1)
Schooling$sinmom14 <- as.factor(as.numeric(Schooling$sinmom14)-1)
Schooling$enroll76 <- as.factor(as.numeric(Schooling$enroll76)-1)
Schooling$smsa76 <- as.factor(as.numeric(Schooling$smsa76)-1)

model1      <- lm(wage76~ed76+black, data=Schooling)
sum_model1  <- summary(model1)
model2      <- lm(wage76~ed76+black+exp76+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+famed+enroll76+smsa76,data=Schooling)
sum_model2  <- summary(model2)

model1_r2 <- sum_model1$r.squared
model2_r2 <- sum_model2$r.squared
model1_adr2 <- sum_model1$adj.r.squared
model2_adr2 <- sum_model2$adj.r.squared
```

`@sample_code`
```{r}
model1_AIC <- 
model1_BIC <- 
model2_AIC <- 
model2_BIC <- 
```

`@solution`
```{r}
model1_AIC <- AIC(model1)
model1_BIC <- BIC(model1)
model2_AIC <- AIC(model2)
model2_BIC <- BIC(model2)
model1_AIC
model1_BIC
model2_AIC
model2_BIC

```

`@sct`
```{r}

```

---

## Best model by AIC 1

```yaml
type: NormalExercise
key: a8c677a2c6
xp: 100
```

So far, we have computed the AIC and BIC for just two models. However, we may consider a lot of models to find the best one. 
Thus, we now want to find the best regressors for wage76. The step() function will allow us to stepwise include regressors, either by forward or backward procedures.

`@instructions`
Use the step() function to regress wage76 on ed76, ed76_2, ed76_3, exp76, exp76_2, exp76_3, black, nearc4a, nearc4b, south66, south76, sinmom14, daded, momed, famed, enroll76 and smsa76.
First, use the forward procedure. Second, do the same exercise with the backward procedure. Do the included regressors differ?
Finally, save the model which achieved the lowest AIC as model3.

`@hint`


`@pre_exercise_code`
```{r}
set.seed(123456)
Schooling <- read.csv("http://assets.datacamp.com/production/repositories/4057/datasets/ac9460776cedb41072c2431250011c31148b0d61/Schooling.csv")
Schooling$ed76_2 <- (Schooling$ed76)^2
Schooling$ed76_3 <- (Schooling$ed76)^3
Schooling$exp76_2 <- (Schooling$exp76)^2
Schooling$exp76_3 <- (Schooling$exp76)^3

Schooling$black <- as.factor(as.numeric(Schooling$black)-1)
Schooling$nearc4a <- as.factor(as.numeric(Schooling$nearc4a)-1)
Schooling$nearc4b <- as.factor(as.numeric(Schooling$nearc4b)-1)
Schooling$south66 <- as.factor(as.numeric(Schooling$south66)-1)
Schooling$south76 <- as.factor(as.numeric(Schooling$south76)-1)
Schooling$sinmom14 <- as.factor(as.numeric(Schooling$sinmom14)-1)
Schooling$enroll76 <- as.factor(as.numeric(Schooling$enroll76)-1)
Schooling$smsa76 <- as.factor(as.numeric(Schooling$smsa76)-1)

model1      <- lm(wage76~ed76+black, data=Schooling)
sum_model1  <- summary(model1)
model2      <- lm(wage76~ed76+black+exp76+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+famed+enroll76+smsa76,data=Schooling)
sum_model2  <- summary(model2)

```

`@sample_code`
```{r}
attach(Schooling)
model3for   <- step(lm(wage76~1), wage76 ~ ed76+ed76_2+ed76_3+exp76+exp76_2+exp76_3+
                 black+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+
                 famed+enroll76+smsa76, direction = "")

model3back  <- step(lm(wage76 ~ (ed76+ed76_2+ed76_3+exp76+exp76_2+exp76_3+
                 black+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+
                 famed+enroll76+smsa76)), direction = "")

model3      <- lm(wage76 ~ , data=Schooling)
detach(Schooling)
```

`@solution`
```{r}
attach(Schooling)
model3for   <- step(lm(wage76~1), wage76 ~ ed76+ed76_2+ed76_3+exp76+exp76_2+exp76_3+
                 black+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+
                 famed+enroll76+smsa76 ,direction = "forward")

model3back  <- step(lm(wage76 ~ (ed76+ed76_2+ed76_3+exp76+exp76_2+exp76_3+
                 black+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+
                 famed+enroll76+smsa76)) ,direction = "backward")

model3      <- lm(wage76 ~ed76+ed76_3+exp76+exp76_2+exp76_3+black+nearc4a+south76+momed+enroll76+smsa76,data=Schooling)
detach(Schooling)
```

`@sct`
```{r}

```

---

## Best model by AIC 2

```yaml
type: PureMultipleChoiceExercise
key: 88873e9859
xp: 50
```

Which variable was included in the final model according to the backward procedure but not in the analogue model according to the forward procedure?

`@hint`


`@possible_answers`
1. smsa76
2. south66
3. [ed76_3]

`@feedback`
1. Unfortunately not.
2. Unfortunately not.
3. Yes, you are right. This implies that it depends which procedure we choose. A clearly undesirable feature.
