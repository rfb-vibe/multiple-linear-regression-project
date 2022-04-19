# Advising On Influences On Sale Price in King County, WA
 Using multiple linear regression modeling to analyze house sales in King County, WA


## Business Understanding
As the data scientist for Emerald City Realtors, a realty firm dedicated to affordable housing, I have been asked by our lead executives to analyze sales data from 2014-2015 in order to create a list of advice the realtors can provide to prospective homesellers about what they can do to increase the estimated value of their homes, and by what amount.

The stakeholders here are the lead executives of Emerald City Realtors who are seeking to solve a real-world problem: providing prospective homesellers of affordable homes advice on how to increase the estimated value of their home, and by what amount.

Data-informed recommendations based on data analysis will help lead executives accurately and confidently advise prospective homesellers within the affordable home market.


## Data Understanding
This project uses the King County House Sales dataset because Emerald City Realtors and its prospective homesellers are all based in King County. The dataset includes all data of single-family home sales from 2014-2015. The dataset itself can be found in `kc_house_data.csv` in the data folder of this GitHub repository along with the descriptions of the features, found in `column_names.md` Further information about the features can be found on the [King County Assessor Website](https://info.kingcounty.gov/assessor/esales/Glossary.aspx?type=r)


## Modeling
## Baseline Model

This is our extremely simple model we will use for comparison throughout our investigation on the features that may affect sale price and to what degree.

### Regression Results: Baseline Model

**Findings**
Our dependent, target variable is sale price and our explanatory, independent variable is square feet of living space (sqft_living). This model's performance is fine - it explains 39% of variance in the data.

The F-test measures the significance of the model relative to a model in which all coefficients are 0, i.e. relative to a model that says there is no correlation whatever between the predictors and the target. This model F-statistic has a p-value less than .05 and thus is statistically significant such that the sqft_living feature is statistically significant in predicting sale price.

The correlation coefficient of sqft_living has a p-value less that 0.05, so it is statistically signifcant. This measure indicates:

* For every one unit increase in sqft_living, the sale price increases 168.64 dollars

**Recommendation**

1. Increase square footage of the living area 

## Iterative Model 1: Considering Quantitative Home Features

To best advise the lead executives of Emerald City Realtors on actions prospectice homesellers can take to increase the estimated value of their home, and by what amount, this model will assess the quantitative features of a home: the number of bedrooms and bathrooms, the number of floors, and the square footage of the home, both living and basement. 

We are creating this model within the context of our problem, intending to improve the results of our baseline model by adding to the complexity of the features within the model. Focusing on the quantitative features keeps some consistency in the elements within the model.

### Regression Results: Quantitative Home Features Model

**Findings**
Our dependent, target variable is sale price and our explanatory, independent variables are bedrooms, bathrooms, sqft_living, sqft_basement, and floors. This model's performance is minimally better than the baseline - it explains 40% of variance in the data.

The F-test measures the significance of the model relative to a model in which all coefficients are 0, i.e. relative to a model that says there is no correlation whatever between the predictors and the target. This model F-statistic has a p-value less than .05 and thus is statistically significant such that all of these quantative features are statistically significant in predicting sale price.

The correlation coefficients for bedrooms, floors, sqft_living, and sqft_basement all have p-values less than 0.05, which indicates they are all statistically significant. This model shows the following:

* Holding all else constant, an increase in one bedroom unit decreases the price by 22,600 dollars
* Holding all else constant, an increase in one bathroom unit decreases the price by 2,495 dollars
* Holding all else constant, an increase in one sqft_living unit increases the price by 172.55 dollars
* Holding all else constant, an increase in one floor unit increases the price by 34,730 dollars
* Holding all else constant, an increase in one sqft_basement unit increases the price by 26.10 dollars

Before making recommendations, let's check the assumptions for this model and explore the utilization of a standardized scale for analysis.

### Apply Standardized Scaling

One note about this model we've been analyzing is that the features are not on the same scale. In other words, the values and coefficients of each feature cannot be compared apples-to-apples as it were. Applying a standard scaler gives us the opportunity to compare across features without considering the different scales of values.

**Findings**

The performance metrics of this model are the same as the previous quantitative model; what differs is that large coefficients tend to be more influential and we can make direct comparisons across features.

For example, holding everything else constant, adding an additional level to a home increases the sale price by 18,590 dollars, but an increase of one additional sqft of living space increases sale price by **133,900 dollars**.

**Recommendation**

If homesellers could change one quantitative feature of their home, we would recommend additional sqft of living space. This is a relevant recommendation because it is a possible solution to the problem of the project: advising prospective homesellers on what they can do to increase the sale price of their home.

## Iterative Model 2: Considering Qualitative Home Features

To best advise the lead executives of Emerald City Realtors on actions prospectice homesellers can take to increase the estimated value of their home, and by what amount, this model will assess the qualitative features of a home: the grade of the home (i.e., the construction quality of the home including materials and workmanship), the condition of the home (i.e., condition relative to the age and grade of the home), and renovation status. 

We are creating this model within the context of our problem, intending to improve the results of our baseline model by adding to the complexity of the features within the model. Focusing on the qualitative features keeps some consistency in the elements within the model and allows for direct comparison between degrees of characteristics.

### Regression Results: Qualitative Home Features Model

**Findings**

Our dependent, target variable is sale price and our explanatory, independent variables are qualitative features of a home, such as its grade, condition, or renovation status. This model's performance is a bit better than the baseline (39%), explaining 44.3% of variance in the data.

The F-test measures the significance of the model relative to a model in which all coefficients are 0, i.e. relative to a model that says there is no correlation whatever between the predictors and the target. This model F-statistic has a p-value less than .05 and thus is statistically significant such that all of these qualitative features are statistically significant in predicting sale price.

All of our features have statistically significant coefficients except Poor and Fair conditions and a Luxury grade, none of which have a statistically significant linear relationship to sale price.

The most influential features show the following impact on sale price:

* Increasing a home's condition from Good to Very Good increases the sale price by 9,950 dollars (meaning that all home items are well maintained, many having been overhauled and repaired)
* Renovating a home increases the sale price by **23,300 dollars**
* Improving a home's grade from Grade 9 (Better) to Grade 11 (Excellent) increases the sale price by **53,070 dollars** (meaning that the home has custom design features and higher quality finish work with added amenities of solid woods, bathroom fixtures and more luxurious options)

**Recommendations**

1. Advise potential homesellers to renovate their home, focusing on well-maintained home items, custom features, high quality finishes, and more luxurious options, which would increase the sale price by **76,370 dollars**

## Iterative Model 3: Considering Most Influential Home Features

To best advise the lead executives of Emerald City Realtors on actions prospectice homesellers can take to increase the estimated value of their home, and by what amount, this model will assess the most influential features from our previous two models (both the quantitative and qualitative models): square footage of living areas, Good and Very Good conditions of materials and workmanship quality, and Excellent grade (indicating custom design and luxurious finishes).

We are creating this model within the context of our problem, intending to improve the results of our baseline model by adding to the complexity of the features within the model. Focusing on the most influential home features keeps some consistency in the elements within the model and allows for direct comparison between degrees of characteristics.

### Regression Results: Most Influential Home Features Model

**Findings**

Our dependent, target variable is sale price and our explanatory, independent variables are the most influential features as measured by our previous models: sqft_living, Good and Very Good conditions, renovation status, Excellent( Grade 11), and number of floors.

This model's performance is a bit better than the baseline (39%), explaining 41.5% of the variance, which, while better than the baseline, does not perform as well as the full qualitative model.

The F-test measures the significance of the model relative to a model in which all coefficients are 0, i.e. relative to a model that says there is no correlation whatever between the predictors and the target. This model F-statistic has a p-value less than .05 and thus is statistically significant such that all of these qualitative features are statistically significant in predicting sale price.

All of our features have statistically significant coefficients indicating a linear relationship with sale price and have the following effect on sale price:

* Increasing a home's condition from Good to Very Good increases the sale price by 7,400 dollars
* Renovating a home increases the sale price by **17,880 dollars**
* Increasing the square footage of living area increases the sale price by **123,000 dollars**

**Recommendations**

1. Complete a renovation project to add square footage of living space to the home, which can increase the sale price of the home by **140,880 dollars**

## Iterative Model 4: Considering All Home Features

To best advise the lead executives of Emerald City Realtors on actions prospectice homesellers can take to increase the estimated value of their home, and by what amount, this model will assess all home features that homesellers can change or improve upon to increase the price of their home.

We are creating this model within the context of our problem, intending to improve the results of our baseline model by adding to the complexity of the features within the model. This model looks at all features homesellers have control over.

### Regression Results: All Home Features Model

**Findings**

Our dependent, target variable is sale price and our explanatory, independent variables are all home features that owners have the capacity to change in order to affect sale price, including square footage, bedrooms, grade, condition, and renovations.

This model performs better than our previous three models, with an adjusted R-squared of 50.3%.

All of our features have statistically significant coefficients except Poor and Fair conditions and Grade 12 (Luxury), neither of which have a statistically significant linear relationship to sale price. The coefficients demonstrate that:

* Increasing a home's condition from Fair to Good increases the sale price by **19,367 dollars**
* Increasing a home's condition from Good to Very Good increases the sale price by 8,840 dollars
* Renovating a home increases the sale price by **20,260 dollars**
* Increasing the square footage of living area by one unit increases the sale price by **65,920 dollars**

**Recommendations**

1. Complete a renovation project to add square footage of living space to the home, which can increase the sale price of the home by **140,880 dollars**


## Recommendations

Our final model, looking at all home features homesellers can control to improve the sale price of their home, performs the best when compared to the baseline model.

Based on the effect all these features have on sale price, Emerald City Realtors should recommend to prospective homesellers that they complete a renovation project to add square footage of living space to the home, which can increase the sale price of the home by 140,880 dollars.

If increasing the square footage of the home is impossible, we should recommend a renovation project that improves a home's condition from Fair to Good, which would increase the sale price of the home by 39,627 dollars.

## Conclusion
