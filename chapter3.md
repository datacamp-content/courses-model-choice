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

---

## Model Estimation

```yaml
type: NormalExercise
key: ae528fe9c9
xp: 100
```



`@instructions`
Estimate the three models only using the training sample.

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
model3      <- lm(wage76 ~ ed76 + ed76_3 + exp76 + exp76_2 + exp76_3 + black + 
               nearc4a + south76 + momed + enroll76 + smsa76, data=Schooling)



```

`@sample_code`
```{r}
model1_train      <- lm(wage76~ed76+black, data=)
model2_train      <- lm(wage76~ed76+black+exp76+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+famed+enroll76+smsa76, data=)
model3_train      <- lm(wage76~ed76+ed76_3+exp76+exp76_2+exp76_3 black+nearc4a+south76+momed+enroll76+smsa76,data=)
```

`@solution`
```{r}
model1_train      <- lm(wage76~ed76+black, data=train)
model2_train      <- lm(wage76~ed76+black+exp76+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+famed+enroll76+smsa76, data=train)
model3_train      <- lm(wage76~ed76+ed76_3+exp76+exp76_2+exp76_3 black+nearc4a+south76+momed+enroll76+smsa76,data=train)
```

`@sct`
```{r}

```

---

## Fitted Values

```yaml
type: NormalExercise
key: 7747da1089
xp: 100
```



`@instructions`
Use the predict() function to get the fitted values for the test sample using the estimated parameters for the three models.

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
model3      <- lm(wage76 ~ ed76 + ed76_3 + exp76 + exp76_2 + exp76_3 + black + 
               nearc4a + south76 + momed + enroll76 + smsa76, data=Schooling)

Schooling$obs <- 1:nrow(Schooling)
obs_train <- sort(sample(Schooling$obs, 2/3*nrow(Schooling)))
Schooling$train <- Schooling$obs %in% obs_train
train <- Schooling[Schooling$train==TRUE,]
test  <- Schooling[Schooling$train==FALSE,]

model1_train      <- lm(wage76~ed76+black, data=train)
model2_train      <- lm(wage76~ed76+black+iqscore+exp76+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+famed+kww+enroll76+smsa76, data=train)
model3_train      <- lm(wage76~ed76+ed76_3+exp76+exp76_2+exp76_3 black+nearc4a+south76+momed+enroll76+smsa76,data=train)
```

`@sample_code`
```{r}
yhat1 <- predict(, newdata=)	
yhat2 <- predict(, newdata=)	
yhat3 <- predict(, newdata=)	
```

`@solution`
```{r}
yhat1 <- predict(model1_train, newdata=test)	
yhat2 <- predict(model2_train, newdata=test)	
yhat3 <- predict(model3_train, newdata=test)	
```

`@sct`
```{r}

```

---

## Mean Squared Error

```yaml
type: NormalExercise
key: b84715536e
xp: 100
```



`@instructions`
First, generate a variable Ytest only containing the wages for the test sample.
Second, regress the squared difference of Ytest and yhat on a constant for every model.
Third, extract the coefficient of the intercept and its standard deviation. 
Note: In the solution, all these steps are done within one line. 
Finally, list all the MSE errors.

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
model3      <- lm(wage76 ~ ed76 + ed76_3 + exp76 + exp76_2 + exp76_3 + black + 
               nearc4a + south76 + momed + enroll76 + smsa76, data=Schooling)

Schooling$obs <- 1:nrow(Schooling)
obs_train <- sort(sample(Schooling$obs, 2/3*nrow(Schooling)))
Schooling$train <- Schooling$obs %in% obs_train
train <- Schooling[Schooling$train==TRUE,]
test  <- Schooling[Schooling$train==FALSE,]

model1_train      <- lm(wage76~ed76+black, data=train)
model2_train      <- lm(wage76~ed76+black+iqscore+exp76+nearc4a+nearc4b+south66+south76+sinmom14+daded+momed+famed+kww+enroll76+smsa76, data=train)
model3_train      <- lm(wage76~ed76+ed76_3+exp76+exp76_2+exp76_3 black+nearc4a+south76+momed+enroll76+smsa76,data=train)

yhat1 <- predict(model1_train, newdata=test)	
yhat2 <- predict(model2_train, newdata=test)	
yhat3 <- predict(model3_train, newdata=test)	
```

`@sample_code`
```{r}
model1_MSE <- summary(lm(()^2~1))$
model2_MSE <- summary(lm(()^2~1))$
model3_MSE <- summary(lm(()^2~1))$
model1_MSE
model2_MSE
model3_MSE
```

`@solution`
```{r}
model1_MSE <- summary(lm((Ytest-yhat1)^2~1))$coef[1:2]	
model2_MSE <- summary(lm((Ytest-yhat2)^2~1))$coef[1:2]	
model3_MSE <- summary(lm((Ytest-yhat3)^2~1))$coef[1:2]	
model1_MSE
model2_MSE
model3_MSE
```

`@sct`
```{r}

```

---

## Mean Squared Error 2

```yaml
type: PureMultipleChoiceExercise
key: 13afdabe1f
xp: 50
```

Which one of the models has the lowest MSE?

`@hint`


`@possible_answers`
1. Model 1
2. Model 2
3. [Model 3]

`@feedback`
1. Unfortunately not.
2. Unfortunately not.
3. Yes! This model does not use irrelevant regressors and has thus the best fit on the data. Further, it has the lowest standard deviation.
