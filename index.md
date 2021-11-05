## Welcome Lab 3 - Regression

In this site, I will display the code that was written to illustrate Linear Regresstion with the use
data of the [PLant Height Data](https://docs.google.com/spreadsheets/d/1bTjiX7XfyHbT3Qx0Jgwor96Vze8POf5g6epJY8epX6Q/edit?usp=sharing).

This site will contain:
- **Scatter Plots**, as ways to visualize the data
- **Line of Best Fit**, explain what best means and how we calculate the line 
- **Standard Error**, what it is
- **R Squared**, what it is and what it can tell us about the Line of Best Fit


### Program Code

This code is written using python. 

Link: [here](https://github.com/mlmarteja/Lab-3---Regression/blob/master/Plant%20Height%20Data.ipynb).

[Download Now!](https://github.com/mlmarteja/Lab-3---Regression/files/7488389/PlantHeightData.zip)

```python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

##Rain, Altitude, Site Number
def main():
    plantData = pd.read_csv("PlantHeightData.csv", 
                            usecols = ['temp','height','alt','rain','site'])
    ##x and y data sets
    temp = np.array(plantData["temp"])
    height = np.array(plantData["height"])
    rain = np.array(plantData["rain"])
    alt = np.array(plantData["alt"])
    site = np.array(plantData["site"])
    
    ##temp and height 
    print("R-Squared of temp and height: " + str(round(RSquared(temp,height),4)))
    ScatterPlot(temp,height,"Temperature and Height")
    
    print("\n")
    
    ##rain and height
    print("R-Squared of rain and height: " + str(round(RSquared(rain,height),4)))
    ScatterPlot(rain,height,"Rain and Height")
    
    print("\n")
    
   ##alt and height
    print("R-Squared of altitude and height: " + str(round(RSquared(alt,height),4)))
    ScatterPlot(alt,height,"Altitude and Height")
    
    print("\n")
    
    ##site and height  
    print("R-Squared of site and height: " + str(RSquared(site,height)))
    ScatterPlot(site,height,"Site and Height")

##create scatter plot##
def ScatterPlot(data_x,data_y,title):
    plt.scatter(data_x,data_y)
    plt.title(title)
    plt.plot(data_x,data_y,'o')
    ##line of best fit
    m,b = np.polyfit(data_x,data_y,1)
    plt.plot(data_x, m*data_x + b)
    plt.show()


##r-squared##
def RSquared(xDataSet,yDataSet):
    correlation_matrix = np.corrcoef(xDataSet, yDataSet)
    correlation_xy = correlation_matrix[0,1]
    r_squared = correlation_xy**2
    return r_squared


##calling main##
main()
```

### Linear Regression
#### Scatter Plots

Scatter Plots a graph designedto show therealtionship between two variables. This is utilized to identify a linear relationship 
when analyzing simple regressions. With that, a sapptr plot is used to visually inspect data to see whether the dataset of x and
y are linearly related.

As seen in the results there are scatter plots that represnts altitude to height, rain to height, site to height, and temperature to height. Among all of the data, site to height has the most significant amount of variation. The scatter plot displays more outliers in the data. Whereas, rain to height shows less variation.



#### Line of Best Fit
The line of best fit is a line that goes trhough the scatter plot of data points. The line of best fit displays the corrolation of the data. The line can show a positive, negative, or even neutral-looking line. For example, the rain and height graph shows a positve line of best fit whereas altitude and height has a negative line of best fit.

These are the steps to find the line of best fit:
1. Calculate the mean of x and y values
2. calculate the slope.
3. Use the fomula y=mx+b to find the y intercept(b)


#### Standard Error and R Squared
Standard Error of regression is the avarage distance from the line of best fit to the data points on a scatter plot
Standard Error used to calculate R-Sqaured which is the goodness-of-fit measure for a linear regression mode. R-Sqaured is a value between 0 and 1. It meaures the strength of the relationship between the line of best fit and the dependent varaible. When R-sqaured is closer to 0%, this indicates that the line of best fit does not explain the spead of the data around the mean. When it is closer to 100%, it best explains all the variation around the mean.

For example, when R-Sqaured is 0.25 or 25%, the line of best fit accounts for 25% of the spread of data points.

To calculate the R-Sqaured of a dataset:
- Find the Standard error of the line which is the summation of the (y at i) - (line of best fit) 
- Find the Standard error of the y-mean which is the the summation of the (y at i) - (y-mean)
- R-squared = 1 - ((SE line of best fit)/(SE y-mean))

When looking at the Plant Height data, the rain to height data showed that the line of best fit accounts for 14% of the spead of data points, which is the largst amongts the other datasets. The R-Sqaured of site to height is the lowest. This value is closer to 0 which means that the line of best fit does not account for most of the data points.

### Results
#### Altitude and Height:


```
![AltAndHeight](https://user-images.githubusercontent.com/93753370/140563287-5de6ded0-37e7-483f-849d-84bee3d4a401.PNG)
```


#### Rain and Height:
```
![RainAndHeight](https://user-images.githubusercontent.com/93753370/140563288-eefa394b-d5e9-4baa-ac04-62c4f41dae9b.PNG)
```

#### Site and Height:

```
![SiteAndHeight](https://user-images.githubusercontent.com/93753370/140563289-6b54024d-028d-4f52-9357-cbd24f9e232d.PNG)
```

#### Temperature and Height:

```
![TempAndHeight](https://user-images.githubusercontent.com/93753370/140563290-29875d61-671c-4af0-9057-da5aee95d984.PNG)
```



