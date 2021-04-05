# fitting-exponential-car-intervals
Fitting exponential distribution to observed car intervals at a given street. The exponential distribution is the probability distribution of the time (or space!) between two events in a Poisson process, where the events occur continuously and independently at a constant rate λ. We want to fit a exponential distribution to the interval of time between cars passing.

$λ = 1/mean(interval)$

<img src="https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.gifmania.co.uk%2FVehicles-Animated-Gifs%2FAnimated-Cars%2FSports-Cars%2FRed-Porsche-911-54536.gif&f=1&nofb=1" alt="car">

```{r,echo=TRUE}
car<-c(10,35,10,35,49,10,3,31,6,22,0.5,9,34,17,11,52,49,10,3,
       28,5,53,58,19,2,128,40,43,6,7,12,41,29,12,126,
       18,15,47,43,65,41,5,1,13,6,20.7,70,59,35,34,23,1,25,
       7,1,72,3,17,30,28,84,13,42,2,33,9,197,99,46,8,21,
       56)
```
```
par(mfrow=c(1,2))
par(mai=rep(0.5, 4))
layout(matrix(c(1,2,3,3), ncol = 2, byrow = TRUE))

hist(car,breaks = 10,prob=T,main = "observed distribution")
mean.int<-mean(car)
abline(v=mean.int,col="red",lty=3)#vertical line = mean interval

sim.int<-rexp(1000,1/mean.int)
hist(sim.int,breaks=10,prob=T,main="simulated distribution")
abline(v=mean.int,col="red",lty=3)


car.int <- seq(0, 200, by = 1)
prob.int <- dexp(car.int, rate = 1/1/mean.int)  
plot(car.int,prob.int,main="theoretical distribution",
     type="l",lwd=2,col="red",xlab="interval between cars")
```
<img src="three figures.png" alt="3 figures">

