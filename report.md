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
  ![Fig.2 Histograms of the prices by fuel type](histograms_prices.png "Histograms prices by fuelType")  
  We can see on these histograms that our customers have bought quite a good number of hybrids.  
fuelType  |  Count
-------   |  -----
Petrol    |  4087
Hybrid    |  2043
Diesel    |  503
Other     |  105  

The petrol cars are the first fuel type of cars our customers bought, however the hybrids are the second type of cars our customers bought even though they are more expensive than the Diesels.

## **What kind of cars our customers bought?**  
Model       |   Diesel | Hybrid | Other | Petrol
--------    |  ------- | ------ | ----- | -----                                                         
Auris       |       42 |    498 |     1 |    171
Avensis     |       76 |      0 |     0 |     39
Aygo        |        0 |      0 |    59 |   1902
C-HR        |        0 |    352 |     7 |    120
Camry       |        0 |     11 |     0 |      0
Corolla     |        1 |    181 |     2 |     83
GT86        |        0 |      0 |     0 |     73
Hilux       |       86 |      0 |     0 |      0
IQ          |        0 |      0 |     0 |      8
Land Cruiser|       51 |      0 |     0 |      0
PROACE VERSO |      15 |      0 |     0 |      0
Prius       |        0 |    214 |    18 |      0
RAV4        |      180 |    230 |     5 |     58
Supra       |        0 |      0 |     1 |     11
Urban Cruiser |      1 |      0 |     0 |      3
Verso       |       29 |      0 |     2 |     83
Verso-S     |        0 |      0 |     0 |      3
Yaris       |       22 |    557 |    10 |   1533

To simplify the analysis I have distributed all our models to 6 categories:  
- city_small              
- compact Sedan/family        
- compact SUV              
- mid-size/large family car  
- large SUV/profesional  
- sport                

model_genre                |  Count  
-----------                |  -----
city_small                 |  4091
compact Sedan/family       |  1213
compact SUV                |   956
mid-size/large family car  |   240
large SUV/profesional      |   152
sport                      |    85  

this way we can see our customers preferred to buy very small cars better suited for the cities.  

Kind of cars               | Freq among the Hybrids  |  Freq among the Petrols
------------               | ----------------------  |  -------------
compact Sedan/family       |  0.437102               |  0.062653
compact SUV                |  0.284875               |  0.044298
city_small                 |  0.272638               |  0.842633
mid-size/large family car  |  0.005384               |  0.029858
sport                      |  0.000000               |  0.020558
large SUV/profesional      |  0.000000               |  0.000000  

While the customers who preferred to buy a petrol car largely chose a city car (84%), the customers who decided to invest in a hybrid car turned their choice towards a compact sedan car (43.7%). Importantly, only 6% of our customers who bought a petrol car chose a Sedan kind of car and 4% chose a compact SUV while 28.5% of the customers who bought a Hybrid chose a compact SUV. It is important to note that hybrids have the advantage to combine the classic petrol fuel and electrivity. Hence, they can achieve long distances with much less fuel consumptions. Furthermore, some of these cars go with an auto-charge (and not a plug-in system) of the electric motor. This is a huge advantage over both the e-cars and the petrol cars. therefore this characeristic can easily convince a customer ready to invest a bit more in a car.  

# **Focus on the comparison between Petrol and Hybrids**  
## **Do the hybrids SUVs and sedans have a higher mpg than the petrol cars of the same kind?**  

![Comparison of mpg distribution of both Sedan and SUV cars between hybrids and petrol cars](histogram_mpg_comparison.png "mpg distribution SUV and sedan")  

We can see here what would confirm my first thought (see above): the hybird customers who bought a sedan or suv car chose a higher mpg car. 

fuelType   |    Count     |   mean     |    std     |   min  | 25%  | 50%  | 75%  |  max
--------   |   --------   |   -------  |  -----     | ----   | ---- | ---- | ---- | ----
Hybrid     |  1475.0      | 73.919932  | 20.054551  | 49.6   | 68.8 | 74.3 | 78.5 | 235.0
Petrol     |  437.0       | 47.454920  | 8.229537   |  6.0   | 41.5 | 47.1 | 52.3 |  78.5  

After applying a Mann-Whitney U test on the two fuel types, I can conlcude that the mpg of the compact SUV and sedan hybrid cars bought is significantly higher than the petrol cars of the same kinds.  

## **Why would our customers largely prefer to buy a small city petrol car?**
This question is perhaps the most relevant. Indeed, concerning the e-cars (not the hybrids), one would instinctively think that a first purchase would balance more toward an affordable small e-car.  
Furthermore the small city cars were our best sellers (60% of our total sales in the past 6 months).  

![Price distribution in small petrol and hybrid cars](two_price_distrib_small_cars.png "Price distribution in small city cars")  

fuelType  |  count  |  mean   |  std    |    min   |   25%   | 50%  | 75%  |  max
-------   |  -----  |  ----   |  -----  |  ------- |  -----  | ---- | ---- | ----
Hybrid    |  557.0  | 12148.4991 | 1827.110 | 7495.0 | 10890.0 | 12070.0 | 13450.0 | 18868  
Petrol    |3443.0 |  8816.1333 | 2358.942 | 950.0 | 7197.5 | 8695.0 | 10290.0 | 25995.0   

Although clearly the city petrol cars are cheaper than the hybrids of the same kind, we can see that the price range of the hybrids overlaps with the upper price range of the petrol cars. Hence, the people who bought the petrol cars at the same price as the hybrids must have got a reason for that.  
Therefore I'm going to look at the pattern of these "expensive" small petrol cars. If any pattern I find are not different from the one observed with the small hybrids, we can use this argument to convince our futur customers to switch to an electric car.  

  I selected the IQR of the hybrids to restrict the small petrol cars to the right tail of their price distribution.  
  Furthermore, I removed the right tail of the price distribution from the small hybrid cars.  
  Here is the general summary statistics of the different numeric variables.  

-   **Small hybrids**  

Stat method |year | price  |  mileage  | tax   | mpg | engineSize
--------    |---- | ------ |  -------  | ----- | --- | ----------
count | 419 |419  | 419    |  419      |419  | 419  
mean  | 2015.88 |11393.01 | 27925.86 |  25.07| 80.53 | 1.49   
std   | 1.38| 1343.01 | 14886 |52.91 | 4.43 | 0.10   
min   | 2012| 7495 | 2563 | 0.00 | 67.30 | 0.00   
25%   | 2015| 10492| 17028.50 | 0.00 |76.30 | 1.50   
50%   | 2016| 11595| 25054.00 | 0.00 |78.00 | 1.50
75%   | 2017| 12500| 35951.50 | 0.00 |86.00 | 1.50
max   | 2019| 13450| 83288.00 |140.00|86.00 | 1.50  

- **Small expensive petrol cars**  

Stat method |year | price  |  mileage  | tax   | mpg | engineSize
--------    |---- | ------ |  -------  | ----- | --- | ----------
count  | 546 | 546| 546 | 546 | 546  | 546
mean   | 2018.45 | 11803.82 | 8822.09| 138.78 | 52.44 | 1.43
std    | 0.81 | 651.04 | 6367.91 | 27.74 | 5.48 | 0.16
min    |2016 | 10890 | 3.00 | 0.00 |47.10 | 1.00
25%    |2018 | 11202.50 | 4223.50 | 145.00 | 47.90 | 1.50 
50%    |2019 | 11810.50 | 7808.00 | 145.00 | 47.90 | 1.50 
75%    |2019 | 12250.00 | 11842.50| 145.00 | 57.70 | 1.50 
max    |2020 | 13400.00 | 39066.00| 150.00 | 86.00 | 1.50  

By looking at the summary statistic, we can see several differences. For example, the petrol clients were enclined to buy younger cars than the hybrid clients. The age correlates with the lower mileage. However, while the engine size does not seem to be different between hybrids and petrol cars (median = 1.5L), the median tax was much higher for the petrol cars than for the hybrids. This could be an advantage for the hybrids. The customers are willing to pay a tax for a relatively expensive small-city car as long as the car is almost brand new, while the customers who bought an hybrid didn't mind to buy an older car for their tax efficiency.  
Now I needd to confirm this statement using statistical tests.


