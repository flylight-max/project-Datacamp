                 # **Defining best argument to launch a second hand e-car sale**

# **Abstract**
The marketing team would like to setup a campaign to sale e-cars. By 2030 only zero emission new cars will be on the market. Although this does not concern yet the second hand car, we need to be one step ahead and taste the water.  
To see what our customers trends are, I've been given the last 6 months cars sold. Although we haven't sold e-cars we do have a good dataset of hybrid cars. I used the hybrid cars sold as my point of comparison with the other types of cars.  

# **Overall comparison**
Here are the different variables I had in hand:  

Column    |    Non-Null Count | Dtype  
  ------    |    -------------- |   -----  
  model  |    6738 non-null  |  object 
  year   |    6738 non-null  |  int64  
  price  |    6738 non-null  |  int64  
  transmission | 6738 non-null |  object 
  mileage |   6738 non-null | int64  
  fuelType |  6738 non-null  |  object 
  tax    |    6738 non-null  |  int64  
  mpg    |    6738 non-null  |  float64
  engineSize  |  6738 non-null  | float64

## **What was the range of prices?**
To visualise the distribution of prices among the different fuel types, I used a violin plot.  
![Fig.1 Distribution of the prices by fuel type](price_distributions.png "Violin plot of the price by fuel tape")  
We can see that hybrids are more expensive. The median (white line) is higher in the hybrids but we will need to do a statistical test to be certain.
However, what this graph is also showing is that there are two populations of price among the hybrids while the distribution is much more homogene among the petrol car
despite the presence of exceptionnally high value cars.

  Because of the presence of these 2 populations in the Hybrid groups, I won't be using parametric test. 
  I am using first Kruskal Wallis test to test whether there are significant differences between the fuel types.
  Using Kruskal wallis there is at least one significant difference of the price distribution.