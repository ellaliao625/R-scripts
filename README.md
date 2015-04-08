ST 552 homework5 questions

(c) 
t1 <- summary(fit)$coef["money", 3]
nreps <- 1000
tstat <- rep(0, nreps)
set.seed(123)
for (i in 1:nreps){
  fit2 <- lm(happy ~ sample(money) + sex + love + work , data = happy)
  tstat[i] <- summary(fit2)$coef["sample(money)", 3]
}

mean(abs(tstat) > abs(t1))

(d)
hist(tstat, freq = FALSE, main = "Histogram of t-statistics")

(e)
grid <- seq(-3, 3, length = 300)
df <- fit$df.residual
hist(tstat, freq = FALSE)
lines(grid, dt(grid, df), type = "l")

