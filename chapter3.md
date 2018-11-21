---
title: 'Model Validation '
description: ""
---

## Training vs. Test sample

```yaml
type: NormalExercise
key: 5a8134de13
xp: 100
```

In a next step, we want to measure how good our three models perform. This is achieved by a validation method: First, we split our data into a training (2/3) and test sample (1/3). 
Second, we estimate the model parameters only using the training sample. 
Then, we predict the fitted values using the test sample and compute the mean squared error to judge which one performed best.
Note that usually, when we do model validation we do not fix the regressors up front. However, in this case here we want to test how the models from the previous section perform.

`@instructions`
Append a variable "obs" to the dataset which indexes the row of the observations.
Use the function sample() to draw randomly 2/3 of the data. 
Append a variable "train" to the dataset which is equal to "TRUE" if the observation is in the training dataset and "FALSE" otherwise.

`@hint`


`@pre_exercise_code`
```{r}
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
model3      <- lm(wage76 ~ ed76 + ed76_3 + exp76 + exp76_2 + exp76_3 + black + 
               nearc4a + south76 + momed + enroll76 + smsa76, data=Schooling)
```

`@sample_code`
```{r}
Schooling$obs <- 1:nrow()
obs_train <- sort(sample(Schooling$, 2/3*nrow()))
Schooling$train <- Schooling$obs %in% obs_train
train <- 
test  <- 
```

`@solution`
```{r}
Schooling$obs <- 1:nrow(Schooling)
obs_train <- sort(sample(Schooling$obs, 2/3*nrow(Schooling)))
Schooling$train <- Schooling$obs %in% obs_train
train <- Schooling[Schooling$train==TRUE,]
test  <- Schooling[Schooling$train==FALSE,]
```

`@sct`
```{r}

```
