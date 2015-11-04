
![http://quantnet.wiwi.hu-berlin.de/style/banner.png](http://quantnet.wiwi.hu-berlin.de/style/banner.png)

## ![qlogo](http://quantnet.wiwi.hu-berlin.de/graphics/quantlogo.png) **Git2Q3-Collaboration**


### Collaboration Timeline
![Picture1](collaboration_timeline.png)

```yaml
Name of QuantLet : MVAghadatail

Published in : Applied Multivariate Statistical Analysis

Description : 'Plots four probability density functions 
(top) and four tails (bottom) in comparison of the NIG, 
the Laplace, the Cauchy and the Gauss distribution'

Keywords : 
- pdf
- cauchy
- gaussian
- laplace
- distribution
- tail
- heavy-tailed
- multivariate
- probability
- density
- plot
- graphical representation

See also : 
- MVAghdis
- MVAghdistail

Author : Wolfgang K. Haerdle

Submitted : Sun, January 29 2012 by Dedy Dwi Prastyo

```


![Picture1](distribution comparison.png)
![Picture1](Tail comparison.png)


```R

# clear variables and close windows
rm(list = ls(all = TRUE))
graphics.off()

# install and load packages
libraries = c("VGAM", "fBasics")
lapply(libraries, function(x) if (!(x %in% installed.packages())) {
    install.packages(x)
})
lapply(libraries, library, quietly = TRUE, character.only = TRUE)

# Graphical comparison of the NIG distribution and normal distribution
xx = seq(-6, 6, by = 0.1)
plot(xx, dlaplace(xx, location = 0, scale = 1), type = "c", ylab = "Y", xlab = "X", 
    col = "black", lwd = 1, cex.lab = 2, cex.axis = 2)
lines(xx, dnig(xx, alpha = 1, beta = 0, delta = 1, mu = 0), type = "l", col = "green", 
    lwd = 3)
lines(xx, dcauchy(xx, 0, 1), type = "p", ylim = c(0, 0.4), ylab = "Y", xlab = "X", 
    col = "blue", lwd = 1)
lines(seq(-6, 6, 0.01), dnorm(seq(-6, 6, 0.01)), type = "l", col = "red", lwd = 2)
legend(x = 2, y = 0.4, legend = c("Laplace", "NIG", "Cauchy", "Gaussian"), pch = c(20, 
    20, 20, 20), col = c("black", "green", "blue", "red"), bty = "n")
title("Distribution comparison")

dev.new()
plot(xx, dnig(xx, alpha = 1, beta = 0, delta = 1, mu = 0), ylim = c(0, 0.02), xlim = c(-5, 
    -4), type = "l", ylab = "Y", xlab = "X", col = "green", lwd = 3, cex.lab = 2, 
    cex.axis = 2)
lines(xx, dlaplace(xx, location = 0, scale = 1), type = "c", col = "black", lwd = 1)
lines(xx, dcauchy(xx, 0, 1), type = "p", col = "blue", lwd = 1)
lines(seq(-6, 6, 0.02), dnorm(seq(-6, 6, 0.02)), type = "l", col = "red", lwd = 3)
legend(x = -4.5, y = 0.014, legend = c("NIG", "Laplace", "Cauchy", "Gaussian"), pch = c(20, 
    20, 20, 20), col = c("green", "black", "blue", "red"), bty = "n")
title("Tail comparison")

```
