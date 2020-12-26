---
title: "Phyllotaxis"
author: "Harsh Trivedi"
date: "24/12/2020"
output: md_document
---



## This is my exact lineup on "Phyllotaxis"


```{r library(ggplot2)}
 t <- seq(0, 2*pi, length.out = 50)
 x<-cos(t)
 y<-sin(t)
 df<-data.frame(t,x,y)
 ggplot(df,aes(x,y))+geom_path()

```

## Creating a circular data

For further data
```{r }
# Working with Golden Angle 
#(Here we chage the base of t as variable and then multiply to get the factor in our main variables of x and y)
# Define the number of points
points<-500
```

```{r}
 angle<-pi*(3-sqrt(5))
# Define the Golden Angle
 t <- (1:points) * angle
 x <- sin(t)
 y <-cos(t)
 df <- data.frame(t, x, y)
 # Make a scatter plot of points in a spiral
 p <- ggplot(df, aes(x*t, y*t))
 p + geom_point()
```

```{r}
# Make a scatter plot of points in a spiral and remove some plot components
p <- ggplot(df, aes(x*t, y*t))
p + geom_point() + theme_void()
```
```{r}
p <- ggplot(df, aes(x*t, y*t))
p + geom_point(colour="lightblue",size =0.8,alpha=1.8)+theme_void()
```
# As you see we don't get the exact spiral we want but rather the straight line connection beetween the points.

```{r}
p + geom_path(colour="lightblue",size =0.8,alpha=1.8,lineend="round",linejoin="mitre")+coord_fixed()+theme_void()
```
## Just a shape creation using different method.
# Coming Back
```{r}
p <- ggplot(df, aes(x*t, y*t))
X<-p +  geom_point(mapping =aes(size = t),color = "yellow",shape = 17,size=8,alpha=0.5)
X
```
```{r}
X + theme(panel.background = element_rect("magenta4"))
```
# To remove the indicators and get a better image we use other parameters.
```{r}
# shape of the points, and the background color
p <- ggplot(df, aes(x*t, y*t))
p +  geom_point(mapping =aes(size = t),color = "yellow",shape = 17,size=8,alpha=0.5)+theme(panel.background = element_rect(fill="darkmagenta"),
        panel.grid=element_blank(),
        axis.ticks=element_blank(),
        axis.title=element_blank(),
        axis.text=element_blank(),legend.position ="none")
```

## As seen we cannot use theme_void here as it will clear the previous commands and make the BG color as white / turn it blank.

```{r}
#Changing the angle
angle <- 0.25
points <- 1000

t <- (1:points)*angle
x <- sin(t)
y <- cos(t)
df <- data.frame(t, x, y)

p <- ggplot(df, aes(x*t, y*t))
p +   geom_point(mapping =aes(size = t),color = "yellow",shape = 17,size=8,alpha=0.5)+theme(panel.background = element_rect(fill="darkmagenta"),
        panel.grid=element_blank(),
        axis.ticks=element_blank(),
        axis.title=element_blank(),
        axis.text=element_blank(),legend.position ="none")
```
```{r}
#Be ready for the beeest one

# Change the values of angle and points
angle <- 13*pi/180
points <- 2000

t <- (1:points)*angle
x <- sin(t)
y <- cos(t)
df <- data.frame(t, x, y)

# Adjust the plot parameters to create the magenta flower
p <- ggplot(df, aes(x*t, y*t))
p + geom_point(size = 80, alpha = 0.1,shape = 1,color ="magenta4")+
  theme_void()
```

#let's make it more interesting
```{r}
# Change the values of angle and points
angle <- 13*pi/180
points <- 5000

t <- (1:points)*angle
x <- sin(t)
y <- cos(t)
df <- data.frame(t, x, y)

# Adjust the plot parameters to create the magenta flower
p <- ggplot(df, aes(x*t, y*t))
p + geom_point(size = 8, alpha = 0.5,shape = 3,color ="tomato")+
  theme_void()
```