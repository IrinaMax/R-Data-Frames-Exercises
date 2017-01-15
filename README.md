#   R-Data-Exercises
   Polishing skills with Udemy. It's easy and fun and remind me there are a lof of methods in R to write code. 
   I like nice easy instructor and I may do course for girls who wanted to learn R  and try Statistical 
   Analysis with my favorite tool on the most of the powerfull language in Math and Data Science.
    
    ##Ex 1: Recreate the following dataframe by creating vectors and 
    ##using the data.frame function:
    ## I did 2 methods: a and df
     Age <- c(22,25,26)
     Weight <- c(150, 165, 120)
     Sex <- c("M", "M", "F")
     Name <- c("Sam", "Frank", "Ami")

     a <- cbind.data.frame( Age, Weight, Sex)
     row.names(a)<- c("Sam", "Frank", "Ami")
     a
     d <- data.frame(row.names =Name, Age, Weight, Sex )
     d
    ##Ex2.Check if mtcars is a dataframe using is.data.frame()
     is.data.frame(mtcars)
    ##Ex3.Use as.data.frame() to convert a matrix into a dataframe:
     mat <- matrix(1:25, nrow=5)
     mat <- as.data.frame(mat)
     mat
    ## Ex 4: Set the built-in data frame mtcars as a variable df. 
    ## We'll use this df variable for the rest of the exercises.
       df <- mtcars
    ## Ex 5: Display the first 6 rows of df
      head(mtcars)
    ## Ex 6: What is the average mpg value for all the cars?
      avg <- mean(df$mpg)
      avg
    ##Ex 7: Select the rows where all cars have 6 cylinders (cyl column)
      mtcars[mtcars$cyl==6, ]
    ##Ex 8: Select the columns am,gear, and carb.
      df(df$am, df$gear, df$carb)
      df[ , c("am", "gear", "carb")]
    ##Ex 9: Create a new column called performance, which is calculated by hp/wt.
      perfomence <- c(df$hp/df$wt)
      cbind(df, perfomence) 
    ##or method 2 
      df$perfomence <- df$hp/df$wt
    ##Ex 9: Your performance column will have several decimal place precision.
    ##Figure out how to use round() (check help(round)) to reduce this accuracy to only 
    ##2 decimal places.
    ##round(x, digits = 0)
     df$perfomence <- round(df$perfomence, digits = 2)
     head(df)
    ##Ex 10: What is the average mpg for cars that have more than 100 hp 
    ##AND a wt value of more than 2.5.
      avg.mpg <- mean(df$mpg[ (df$hp>100) & (df$wt>2.5)])
      avg.mpg
    ##method 2
      mean(subset( df, df$hp>100 & df$wt>2.5)$mpg)

    ##Ex 11: What is the mpg of the Hornet Sportabout?
      df[["Hornet Sportabout","mpg"]] 
      
# Work with ggplot2 package

    ##install.packages('ggplot2')
    #install.packages('ggplot2movies')
    library(ggplot2)
    library(ggplot2movies)

    # Data & Aesthetics
    colnames(movies)
    head(movies)
    ## will use rating for Aestethis to make first plot
    pl <-ggplot(movies,aes(x=rating))
    print(pl+ geom_histogram())  # will give you the base histogram plot1
 ![1](https://cloud.githubusercontent.com/assets/16123495/21574788/6c7329a0-ceae-11e6-8e63-03fd706dd534.png)
 
     print(pl+ geom_histogram(binwidth = 0.1)) ## will show mor precise solution plot2
 ![2](https://cloud.githubusercontent.com/assets/16123495/21574790/73dff024-ceae-11e6-9f65-1126d01cc7c6.png)
 
     print(pl+ geom_histogram(binwidth = 0.1, color = "red")) # and add red countor plot3
 ![3](https://cloud.githubusercontent.com/assets/16123495/21574791/73e22f2e-ceae-11e6-8c86-4fe7fad24d82.png)
 
## Now we need to use Geometry
    pl2 <- pl + geom_histogram(binwidth = 0.1, color = 'red', fill= "pink", alpha = 0.4)
    print(pl2) ## plot 4
![4](https://cloud.githubusercontent.com/assets/16123495/21574792/73e36b3c-ceae-11e6-8dc6-8728de01e2af.png)

    pl3 <- pl + geom_histogram(binwidth = 0.1, color = 'red', fill= "pink", alpha = 0)
    print(pl3) ## plot 5  alfa shows the trancparancy
![5](https://cloud.githubusercontent.com/assets/16123495/21574793/73e42f54-ceae-11e6-81b7-7ef1e69fe5a3.png)
       
    pl4 <-pl2 + xlab('Movie Rating') + ylab('Count')
    print(pl4) ## plot6 with adding x and y names
 ![6](https://cloud.githubusercontent.com/assets/16123495/21574794/73e6d02e-ceae-11e6-9bba-5537e838e97a.png)

    pl5 <- pl + geom_histogram(binwidth = 0.1, aes(fill = ..count..))
    pl7 <-pl5 + xlab('Movie Rating') + ylab('Count') 
    print(pl7) ##plot7
    
![7](https://cloud.githubusercontent.com/assets/16123495/21574795/73eaabea-ceae-11e6-8f32-ec8294230a44.png)
   
    pl8 <-pl7 + xlab('Movie Rating') + ylab('Count') +theme(legend.position = "bottom")
    print(pl8 + ggtitle("MY TITLE")) ##plot8 with TITLE and lables
![8](https://cloud.githubusercontent.com/assets/16123495/21575087/187d3cde-ceb6-11e6-9ea9-42a04a678258.png)



## SCATERPLOTS
    library(ggplot2)
    df <- mtcars

## Data and aesthics
    pl_sc <- ggplot(df,aes(x=wt,y=mpg))
## GEOMETRY
    print(pl_sc + geom_point( alpha = 0.5, size = 5))    # alpha shows clarity 0:1, plot10
 ![10](https://cloud.githubusercontent.com/assets/16123495/21574797/73f56328-ceae-11e6-9465-7d499c7d9148.png)   
   
     print(pl_sc + geom_point(aes(size=hp)))    ## by horse power, plot11
 ![11](https://cloud.githubusercontent.com/assets/16123495/21574798/73f8a060-ceae-11e6-9c4c-72877db0dd45.png)     
     
     print(pl_sc + geom_point(aes(size = cyl)))  ## by cylinders, plot12
 ![12](https://cloud.githubusercontent.com/assets/16123495/21574799/73f9152c-ceae-11e6-8157-0d007172d136.png)    
     
     print(pl_sc + geom_point(aes(size = factor(cyl))))  ## plot13
 ![13](https://cloud.githubusercontent.com/assets/16123495/21574800/73fc1948-ceae-11e6-89b0-d601f896d3d9.png)    
     
     print(pl_sc + geom_point(aes(shape = factor(cyl)), size = 5))  ## plot14
 ![14](https://cloud.githubusercontent.com/assets/16123495/21574801/73fe0442-ceae-11e6-9e67-5d2f5e2affd2.png)    

     print(pl_sc + geom_point(aes(shape = factor(cyl)), size = 5, color = "#8470ff")) ##plot15
 ![15](https://cloud.githubusercontent.com/assets/16123495/21574802/7406bd26-ceae-11e6-93a0-c8e09b886d91.png)    
      
## Hex color picker, you can use any code to pick any color www.color-hex.com

    pl_sc2 <- pl_sc + geom_point(aes(color = hp, size=hp))
    print(pl_sc2)  ## plot16
![16](https://cloud.githubusercontent.com/assets/16123495/21574803/74094da2-ceae-11e6-82b4-da664af2ece0.png)
    
    pl_sc3 <-  pl_sc2 + scale_color_gradient(low = 'black', high = 'green')
    print(pl_sc3) ## plot17
![17](https://cloud.githubusercontent.com/assets/16123495/21574804/740c2040-ceae-11e6-8c12-6e8e1d8b7d4c.png)

## Barplots
    df <- mpg
    pl.b <- ggplot(df, aes(x=class))  # class is a catigorical data in DF
    print(pl.b + geom_bar())
    print(pl.b + geom_bar(color="red", fill="blue"))  # color shows the line around, you  not nessasary 
    print(pl.b + geom_bar(aes(fill=drv))) # will classify by color of class dvr 
    #  "dodge" will show staking = classify bars next to each other for easy to compare
    print(pl.b + geom_bar(aes(fill=drv), position = "dodge"))
    # "fill will show percentage% 
    print(pl.b + geom_bar(aes(fill=drv), position = "fill"))


## 2 Variables plot
    library(ggplot2)
    library(ggplot2movies)
    library(dplyr)

    pl <- ggplot(movies, aes(x=year,y=rating))
    pl2 <- pl + geom_bin2d()  ## pl1
    pl2 %>%print()
    #  pl1 <-( pl + geom_bin2d()) %>% print()  can work like this also

    pl3 <- pl2+ scale_fill_gradient(high='red', low = 'green')
    print(pl3)
 
    pl4 <- pl3 + geom_bin2d(binwidth=c(3,1))
    print(pl4)
 
    pl5 <- pl4+ scale_fill_gradient(high='red', low = 'blue')
    print(pl5)
    install.packages('hexbin')

    ##install.packages('stat_binhex')
    require('hexbin')
    pl <- ggplot(movies, aes(x=year, y=rating))
    pl6 <- pl + geom_hex()
    pl7 <- pl6+ scale_fill_gradient(high='red', low = 'blue')
    print(pl7)

    pl8 <- pl+ geom_density2d()
    print(pl8)
    gqplot(x=years, y=rating, data = df, geom = "density2d")
