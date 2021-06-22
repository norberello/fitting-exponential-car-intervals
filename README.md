# Using exponential distribution to fit car intervals and others

<p align="center">
  <img src="penny lane tr.gif" alt="penny lane centered">
</p>

This exercise fits exponential distribution to several possibilities, for example observed car intervals across two given streets, this is: the number of seconds between cars at different spots, or the time between beer sips in a pub, or the same notion applied to something more serious, the interval between crimes in a particular country or city. The exponential distribution is the probability distribution of the time (or space, distance, or any other unit counted until an event occurs!!) between two events in a Poisson process, where the events occur continuously and independently at a constant rate labmda (λ). We want to fit a exponential distribution to the interval of time (in seconds) between cars passing as  first exercise. Simple methodology to gather data: just looked over the window and started counting time between vehicles passing by for about an hour (enough to see if the data collected follows the exponential shape). What is the probability of the next car passing in less than 90 seconds? What is the probability of the next car lasting more than 90 seconds? We can use the commands `dexp` and `pexp` to answer these questions, and `rexp` to generate random exponential values. Actually, the empirical cumulative distribution function (ecdp) approaches the notion of `pexp` as every value has an estimate of the accumulated probability.

<p align="center">
  $${
  \lambda = \frac{1}{\overline{interval}}}$$
</p>
<p align="center">

<p align="center">
  λ = 1/mean(interval)</p>
<p align="center">


<img src="https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.gifmania.co.uk%2FVehicles-Animated-Gifs%2FAnimated-Cars%2FSports-Cars%2FRed-Porsche-911-54536.gif&f=1&nofb=1" alt="car">
</p>

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
<font size="5">Instead of time (or distance), let's count the number of persons until type-A shows up in two different locations. Can this be characterized with exponential distributions? I will be also interested to model the interval of time until a person gets angry </font>
<p align="center">
    <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimg.pngio.com%2Fmassive-crush-pt-1-all-saints-youth-ministry-people-walking-png-gif-302_170.gif&f=1&nofb=1" alt="centered image" />
</p>

<img src="type A person.png" alt="exponential distribution of type A intervals">

<p align="center">
  <img src="https://unrealitymag.com/wp-content/uploads/2012/07/eZb0i.gif" alt="penny lane centered"
       width=650>
</p>  

<p align="center">
  <img src="ECDF and PEXP.png" alt="penny lane centered"
       width=500>
</p>      
  
  <p align="center">
  <img src="hmachist violence.png" alt="penny lane centered"
       width=650>
</p>  

<p align="center">
  <img src="ecdf and pexp crime.png" alt="penny lane centered"
       width=500>
</p>  
