# STAT615_Bok_Choy
Project location for the Bok Choy group of STAT615.

Slide Deck Link:
https://docs.google.com/presentation/d/1-hCwI2j32xos0VzeYPpAjl6eBAsjGcgYEgpmC-pNkuw/edit?usp=sharing 

Article Link:
https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0296906 

Professor's Notes:
 "Hedonic model" seems to mean just a multiple linear regression of price on other factors. They do a special method of adjusting for selection bias (i.e., only paintings sold have a hammer price). These are the steps: Fit a probit model with the binary indicator of whether the painting was sold as the response (this is encoded by NA in the hammerprice variable in the dataset). They use this to calculate a "inverse Mills ratio". They then include this inverse mills ratio as a covariate in the regression. E.g., if ⁠ am ⁠ is 1 if the observation is in the model and 0 if it is not in the model, then you can calculate an inverse mills ratio via: library(sampleSelection) data("mtcars") probit_out <- glm(am ~ wt, data = mtcars, family = binomial(link = "probit")) mr <- invMillsRatio(x = probit_out) mr$IMR1 You would then include that variable in the regression analysis. Of course, the probit model would have different covariates than wt. You can load dta data with the haven package: library(haven) dat <- read_dta("./bok_choy_dat.dta") For the progress report, I expect the output of the multiple linear regression results to match those in the paper. With you four, I think you can do it
