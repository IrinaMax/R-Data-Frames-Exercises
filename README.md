#   R-Data-Frames-Exercises
   Polishilg skills with Udemy. It's easy and fun and remind me there are a lof of methods in R to write code. 
   I like nice easy instructor and I may do course for girls who wanted to learn R  and try statistical 
   Analysis with most of the powerull language in Math.
    
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
    ## Ex 9: Create a new column called performance, which is calculated by hp/wt.
      perfomence <- c(df$hp/df$wt)
      cbind(df, perfomence) 
    ## or method 2 
      df$perfomence <- df$hp/df$wt
   ##Ex 10: Your performance column will have several decimal place precision.
   ##Figure out how to use round() (check help(round)) to reduce this accuracy to only 
   ## 2 decimal places.

   ##round(x, digits = 0)
      df$perfomence <- round(df$perfomence, digits = 2)
      head(df)
   ##Ex 10: What is the average mpg for cars that have more than 100 hp 
   ## AND a wt value of more than 2.5.

      avg.mpg <- mean(df$mpg[ (df$hp>100) & (df$wt>2.5)])
      avg.mpg
   ## method 2
      mean(subset( df, df$hp>100 & df$wt>2.5)$mpg)

   ##Ex 11: What is the mpg of the Hornet Sportabout?
      df[["Hornet Sportabout","mpg"]] 

