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

### Results
Altitude and Height:

![](https://github.com/mlmarteja/Lab-3---Regression/blob/9beb753390aec2ff1ed1c8585ffc183f98c22892/AltAndHeight.PNG width="400" height="350")


Rain and Height:

<img src=https://github.com/mlmarteja/Lab-3---Regression/blob/7533e661d3b53f0aa6628865ad6f6118821fb0b6/RainAndHeight.PNG width="400" height="350" />


Site and Height:


<img src=https://github.com/mlmarteja/Lab-3---Regression/blob/7533e661d3b53f0aa6628865ad6f6118821fb0b6/SiteAndHeight.PNG width="400" height="350" />


Temperature and Height:

<img src=https://github.com/mlmarteja/Lab-3---Regression/blob/7533e661d3b53f0aa6628865ad6f6118821fb0b6/TempAndHeight.PNG width="400" height="350" />

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
