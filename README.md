# Using exponential distribution to fit car intervals and others

<p align="center">
  <img src="penny lane tr.gif" alt="penny lane centered">
</p>

These exercises demonstrate how to fit an exponential distribution to a variety of real-world intervals. For example, we can study the time between cars passing at different spots on a street, the interval between beer sips in a pub, or, in a more serious context, the time between crimes in a particular city or country. The exponential distribution models the probability of the time (or distance, or any other measured unit) until the next event occurs in a Poisson process, where events happen continuously, independently, and at a constant average rate, λ (lambda). A key feature of the exponential distribution is its memoryless property: the probability of an event occurring in the future does not depend on how much time has already passed. This makes it particularly useful for modeling rare or catastrophic events, such as meteorite impacts, volcanic eruptions, terrorist attacks, or similar events where each occurrence is independent of the previous one.
As a first exercise, we fit an exponential distribution to the intervals (in seconds) between cars passing by. The methodology is simple: look out the window and record the time between each vehicle for about an hour — enough to see whether the observed data roughly follows the exponential shape.

Using this model, we can ask questions such as:
	•	What is the probability that the next car passes in less than 90 seconds?
	•	What is the probability that the next car takes more than 90 seconds to pass?
	•	Similarly, what is the probability of a sex crime occurring within the next 10 days?

In R, we can use the functions dexp() to evaluate the density, pexp() to compute cumulative probabilities, and rexp() to generate random exponential values for simulation. Notably, the empirical cumulative distribution function (ECDF) approaches the concept of pexp() as it assigns an accumulated probability to each observed value, providing an intuitive link between observed data and probabilistic modeling.

<p align="center">
  λ = 1/mean(interval)</p>
<p align="center">


<img src="https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.gifmania.co.uk%2FVehicles-Animated-Gifs%2FAnimated-Cars%2FSports-Cars%2FRed-Porsche-911-54536.gif&f=1&nofb=1" alt="car">
</p>

<p align="center">
<img src="https://github.com/norberello/lecture-images-and-clips/blob/main/21-22/taxy%20city%20wide.gif?raw=true" alt="Girl in a jacket">
  <p align="center">

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
  <img src="machist violence.png" alt="penny lane centered"
       >
</p>  

<p align="center">
  <img src="ecdf and pexp crime.png" alt="penny lane centered"
       width=500>
</p>  
