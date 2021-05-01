# fitting-exponential-car-intervals

<center><img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi.pinimg.com%2Foriginals%2F34%2F9b%2Fdc%2F349bdce7fbcc03eb560ccd0ace5c1437.gif&f=1&nofb=1" alt="penny lane centered"> </center>

Fitting exponential distribution to observed car intervals at a given street. The exponential distribution is the probability distribution of the time (or space!!) between two events in a Poisson process, where the events occur continuously and independently at a constant rate λ. We want to fit a exponential distribution to the interval of time between cars passing. Just looked over the window and started counting time between vehicles passing by for about an hour (enough to see if the data collected follows the exponential shape). What is the probability of the next car passing in less than 90 seconds? What is the probability of the next car lasting more than 90 seconds?

`λ = 1 / interval`

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

Excelent explanations here:
<https://r-coder.com/exponential-distribution-r/>

What about counting people until type A shows up? Would that follow an exponential distribution?

<center>
<font size="5">Instead of time (or distance), let's count the number of persons until type A shows up in two different locations. Can this be characterized with exponential distributions? What type A person is will remain secret. </font>
<p class="aligncenter">
    <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimg.pngio.com%2Fmassive-crush-pt-1-all-saints-youth-ministry-people-walking-png-gif-302_170.gif&f=1&nofb=1" alt="centered image" />
</p></center>
