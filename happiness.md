---
output:
  html_document:
    keep_md: true 
---
Finding Happiness
========================================================




#### <br>
This dataset was obtained <a href="https://www.kaggle.com/unsdsn/world-happiness">here</a>. 

"The World Happiness Report is a landmark survey of the state of global happiness. The first report was published in 2012, the second in 2013, the third in 2015, and the fourth in the 2016 Update." "...The report continues to gain global recognition as governments, organizations and civil society increasingly use happiness indicators to inform their policy-making decisions. Leading experts across fields – economics, psychology, survey analysis, national statistics, health, public policy and more – describe how measurements of well-being can be used effectively to assess the progress of nations. The reports review the state of happiness in the world today and show how the new science of happiness explains personal and national variations in happiness." 

"The happiness scores and rankings use data from the Gallup World Poll. The scores are based on answers to the main life evaluation question asked in the poll. This question, known as the Cantril ladder, asks respondents to think of a ladder with the best possible life for them being a 10 and the worst possible life being a 0 and to rate their own current lives on that scale. The scores are from nationally representative samples for the years 2013-2016 and use the Gallup weights to make the estimates representative. The columns following the happiness score estimate the extent to which each of six factors – economic production, social support, life expectancy, freedom, absence of corruption, and generosity – contribute to making life evaluations higher in each country than they are in Dystopia, a hypothetical country that has values equal to the world’s lowest national averages for each of the six factors. They have no impact on the total score reported for each country, but they do explain why some countries rank higher than others."

Per <a href="http://worldhappiness.report/wp-content/uploads/sites/2/2016/03/HR-V1_web.pdf">their document</a>, here are the measures of each factors:

- <b>GDP per capita</b>

- <b>Healthy years of life expectancy</b>

- <b>Social support </b><br>
“If you were in trouble, do you have relatives or friends you can count on to help you whenever you need them, or not?” 

- <b>Trust</b> <br>
As measured by a perceived absence of corruption in government and business, perceptions of corruption are the average of binary answers to two GWP questions: “Is corruption widespread throughout the government or not” and “Is corruption widespread within businesses or not?” Where data for government corruption are missing, the perception of business corruption is used as the overall corruption-perception measure.

- <b>Freedom to make life decisions</b><br>
“Are you satisfied or dissatisfied with your freedom to choose what you do with your life?”

- <b>Generosity </b><br>
“Have you donated money to a charity in the past month?” on GDP per capita.

#### <br>
## Univariate Plots Section
<p><br><p>
#### <br>
#### Taking a peek

```
## Observations: 157
## Variables: 13
## $ Country                       <fct> Denmark, Switzerland, Iceland, N...
## $ Region                        <fct> Western Europe, Western Europe, ...
## $ Happiness.Rank                <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 1...
## $ Happiness.Score               <dbl> 7.526, 7.509, 7.501, 7.498, 7.41...
## $ Lower.Confidence.Interval     <dbl> 7.460, 7.428, 7.333, 7.421, 7.35...
## $ Upper.Confidence.Interval     <dbl> 7.592, 7.590, 7.669, 7.575, 7.47...
## $ Economy..GDP.per.Capita.      <dbl> 1.44178, 1.52733, 1.42666, 1.577...
## $ Family                        <dbl> 1.16374, 1.14524, 1.18326, 1.126...
## $ Health..Life.Expectancy.      <dbl> 0.79504, 0.86303, 0.86733, 0.795...
## $ Freedom                       <dbl> 0.57941, 0.58557, 0.56624, 0.596...
## $ Trust..Government.Corruption. <dbl> 0.44453, 0.41203, 0.14975, 0.357...
## $ Generosity                    <dbl> 0.36171, 0.28083, 0.47678, 0.378...
## $ Dystopia.Residual             <dbl> 2.73939, 2.69463, 2.83137, 2.664...
```
#### <br>
#### Cleaning up a little...
First, I'm removing the periods in the column names. I'm also replacing some of the long names for clarity.


```
##  [1] "Country"                 "Region"                 
##  [3] "HappinessRank"           "HappinessScore"         
##  [5] "LowerConfidenceInterval" "UpperConfidenceInterval"
##  [7] "GDP"                     "SocialSupport"          
##  [9] "LifeExpectancy"          "Freedom"                
## [11] "TrustForGovernment"      "Generosity"             
## [13] "DystopiaResidual"
```

####<br>
#### Summary


```
##         Country                                Region   HappinessRank   
##  Afghanistan:  1   Sub-Saharan Africa             :38   Min.   :  1.00  
##  Albania    :  1   Central and Eastern Europe     :29   1st Qu.: 40.00  
##  Algeria    :  1   Latin America and Caribbean    :24   Median : 79.00  
##  Angola     :  1   Western Europe                 :21   Mean   : 78.98  
##  Argentina  :  1   Middle East and Northern Africa:19   3rd Qu.:118.00  
##  Armenia    :  1   Southeastern Asia              : 9   Max.   :157.00  
##  (Other)    :151   (Other)                        :17                   
##  HappinessScore  LowerConfidenceInterval UpperConfidenceInterval
##  Min.   :2.905   Min.   :2.732           Min.   :3.078          
##  1st Qu.:4.404   1st Qu.:4.327           1st Qu.:4.465          
##  Median :5.314   Median :5.237           Median :5.419          
##  Mean   :5.382   Mean   :5.282           Mean   :5.482          
##  3rd Qu.:6.269   3rd Qu.:6.154           3rd Qu.:6.434          
##  Max.   :7.526   Max.   :7.460           Max.   :7.669          
##                                                                 
##       GDP         SocialSupport    LifeExpectancy      Freedom      
##  Min.   :0.0000   Min.   :0.0000   Min.   :0.0000   Min.   :0.0000  
##  1st Qu.:0.6702   1st Qu.:0.6418   1st Qu.:0.3829   1st Qu.:0.2575  
##  Median :1.0278   Median :0.8414   Median :0.5966   Median :0.3975  
##  Mean   :0.9539   Mean   :0.7936   Mean   :0.5576   Mean   :0.3710  
##  3rd Qu.:1.2796   3rd Qu.:1.0215   3rd Qu.:0.7299   3rd Qu.:0.4845  
##  Max.   :1.8243   Max.   :1.1833   Max.   :0.9528   Max.   :0.6085  
##                                                                     
##  TrustForGovernment   Generosity     DystopiaResidual
##  Min.   :0.00000    Min.   :0.0000   Min.   :0.8179  
##  1st Qu.:0.06126    1st Qu.:0.1546   1st Qu.:2.0317  
##  Median :0.10547    Median :0.2225   Median :2.2907  
##  Mean   :0.13762    Mean   :0.2426   Mean   :2.3258  
##  3rd Qu.:0.17554    3rd Qu.:0.3119   3rd Qu.:2.6646  
##  Max.   :0.50521    Max.   :0.8197   Max.   :3.8377  
## 
```

<p><br></p>
This dataset consists of 13 variables and 157 observations. 
<p><br></p>

#### <br>
#### Seeing a distribution of each factor


```
##       Country         Region      variable value
## 1     Denmark Western Europe HappinessRank     1
## 2 Switzerland Western Europe HappinessRank     2
## 3     Iceland Western Europe HappinessRank     3
## 4      Norway Western Europe HappinessRank     4
## 5     Finland Western Europe HappinessRank     5
## 6      Canada  North America HappinessRank     6
```

![](happiness_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

<p><br></p>
I see Generosity and Dystopia Residual have a shape cloaser to normal distribution than other factors.
<p><br></p>

#### <br>
#### Which regions does the dataset use and how many countries are in each region?

```
## 
##       Australia and New Zealand      Central and Eastern Europe 
##                               2                              29 
##                    Eastern Asia     Latin America and Caribbean 
##                               6                              24 
## Middle East and Northern Africa                   North America 
##                              19                               2 
##               Southeastern Asia                   Southern Asia 
##                               9                               7 
##              Sub-Saharan Africa                  Western Europe 
##                              38                              21
```
<p><br></p>
Naturally, the number of countries in each region is quite spread out, so I'll keep that in mind when plotting.

Now I'll divide the class based on the quartiles and make a new column called "GDPClass".


```
## [1] very high very high very high very high very high very high
## Levels: very high high moderate low
```

<p><br><p>
Next, I'm going to divide the happiness scores into categories, and make a new column called "HappinessClass".


```
## [1] very high very high very high very high very high very high
## Levels: very high high moderate low
```


## Univariate Analysis
<p><br><p>
### What is the structure of your dataset?
The dataset has 13 variables for 157 countries to measure their happiness scores. The six factors that affect on the happiness scoare is: GDP, Family (Social Support), Health (Life Expectancy), Freedom, Trust, and Generosity. 

Happiness score goes from 0 (unhappy) to 10 (happy), and other factors increase when their numbers go up.

### What is/are the main feature(s) of interest in your dataset?
The main feature of interest is: What affect people's happiness? What has greater influence for happiness? My initial assumption is GDP doesn't necessary plays a big part in happiness — family support and health is. I've also read before that helping others makes you happy, so maybe generosity would be another big factor for happiness.

### What other features in the dataset do you think will help support your investigation into your feature(s) of interest?
Finding out each factor's correlation with others would be interesting, too. 

### Did you create any new variables from existing variables in the dataset?
I've created two categorical variables from the GDP and HappinessScore columns. 

### Of the features you investigated, were there any unusual distributions? Did you perform any operations on the data to tidy, adjust, or change the form of the data? If so, why did you do this?
I didn't see anything unusual in this data.

<p><br></p>
## Bivariate Plots Section
<p><br></p>
#### Regions and Happiness
![](happiness_files/figure-html/unnamed-chunk-8-1.png)<!-- -->

<p><br></p>
This shows Sub-Saharan Africa has the lowest median as well as the IQR. 
<p><br></p>

#### Relationship between Sosial Support and Life Expectancy
Is life expectancy related to social supportness? I will divide social support column into classes. 
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-9-1.png)<!-- -->

<p><br></p>
Also based on each region:
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-10-1.png)<!-- -->

<p><br></p>
Not so much, although it does get dense towards upper right, the correlation is pretty weak. People in Sub-Saharan African region are definitely suffering though, compared to the rest of the world...
<p><br></p>

#### Relationship between Sosial Support and GDP

![](happiness_files/figure-html/unnamed-chunk-11-1.png)<!-- -->

<p><br></p>
There seems to be some positive relationship between GDP and Social Support. And the density increases positively as well.
<p><br></p>

#### Relationship between LifeExpectancy and GDP

![](happiness_files/figure-html/unnamed-chunk-12-1.png)<!-- -->

<p><br></p>
Stronger correlation here. 
<p><br></p>

#### Relationship between Freedom and Trust for Government

![](happiness_files/figure-html/unnamed-chunk-13-1.png)<!-- -->

<p><br></p>
 I don't see a strong correlation here, although it's not negative. Whether the freedom score is low or high, the majority of the trust seem to stay below 0.2. 
<p><br></p>

#### Distribution of factors and Happiness Class

![](happiness_files/figure-html/unnamed-chunk-14-1.png)<!-- -->

<p><br></p>
I can clearly see the distributions shifting from high to low, as the happiness goes from high to low.
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-15-1.png)<!-- -->

<p><br></p>
The distribution of very high happiness has smaller variance, while as the happiness score goes down, the variance increases. 
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-16-1.png)<!-- -->

<p><br></p>
Although less obvious, the shift of distribution does exist based on the happiness categories.
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-17-1.png)<!-- -->

<p><br></p>
Variance is bigger in Freedom in all distributions.
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-18-1.png)<!-- -->

<p><br></p>
Since the happiess countries' distributino is so spread out, and the second happiess class has as low trust for their government as the least happy countries, this confirms that the trust for government doesn't have much to do with happiness.
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-19-1.png)<!-- -->

<p><br></p>
This also confirms the less role of generosity in happiness. By the way, who is it in the "low" class who also appear to be the most generous, anyway? 
<p><br></p>


```
##   Country            Region HappinessRank HappinessScore
## 1 Myanmar Southeastern Asia           119          4.395
##   LowerConfidenceInterval UpperConfidenceInterval     GDP SocialSupport
## 1                   4.327                   4.463 0.34112       0.69981
##   LifeExpectancy Freedom TrustForGovernment Generosity DystopiaResidual
## 1         0.3988 0.42692            0.20243    0.81971          1.50655
##   GDPClass HappinessClass
## 1      low            low
```

<p><br></p>
Myanmar! 
Now, I just want to see the same plots in density.
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-21-1.png)<!-- -->

![](happiness_files/figure-html/unnamed-chunk-22-1.png)<!-- -->

![](happiness_files/figure-html/unnamed-chunk-23-1.png)<!-- -->

![](happiness_files/figure-html/unnamed-chunk-24-1.png)<!-- -->

![](happiness_files/figure-html/unnamed-chunk-25-1.png)<!-- -->

![](happiness_files/figure-html/unnamed-chunk-26-1.png)<!-- -->

<p><br></p>
Yep... So GDP can be a big factor that contributes to happiness. 
Generosity and Trust for Government, on the other hand, not so much. 
What is obvious for the other factors (e.i. Life Expectancy, Social Support, and Freedom), is that although 'high', 'moderate', 'low' classes have a lot of overlaps, the 'very high' class clearly stands out. 
<p><br></p>

#### Correlation Solution

```
## 
## 	Pearson's product-moment correlation
## 
## data:  Happiness$GDP and Happiness$HappinessScore
## t = 16.059, df = 155, p-value < 2.2e-16
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.7232138 0.8426452
## sample estimates:
##      cor 
## 0.790322
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  Happiness$LifeExpectancy and Happiness$HappinessScore
## t = 14.806, df = 155, p-value < 2.2e-16
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.6916693 0.8233164
## sample estimates:
##       cor 
## 0.7653843
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  Happiness$SocialSupport and Happiness$HappinessScore
## t = 13.667, df = 155, p-value < 2.2e-16
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.6589122 0.8029161
## sample estimates:
##       cor 
## 0.7392516
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  Happiness$Freedom and Happiness$HappinessScore
## t = 8.5659, df = 155, p-value = 1.005e-14
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.4501564 0.6644688
## sample estimates:
##       cor 
## 0.5668267
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  Happiness$TrustForGovernment and Happiness$HappinessScore
## t = 5.4665, df = 155, p-value = 1.798e-07
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.2618860 0.5255732
## sample estimates:
##       cor 
## 0.4020322
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  Happiness$Generosity and Happiness$HappinessScore
## t = 1.9772, df = 155, p-value = 0.04979
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.0002149396 0.3059687867
## sample estimates:
##       cor 
## 0.1568478
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  Happiness$LifeExpectancy and Happiness$GDP
## t = 19.048, df = 155, p-value < 2.2e-16
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.7831075 0.8785171
## sample estimates:
##       cor 
## 0.8370672
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  Happiness$LifeExpectancy and Happiness$SocialSupport
## t = 9.0593, df = 155, p-value = 5.358e-16
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.4755681 0.6821467
## sample estimates:
##       cor 
## 0.5883768
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  Happiness$GDP and Happiness$SocialSupport
## t = 11.222, df = 155, p-value < 2.2e-16
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.5729946 0.7477565
## sample estimates:
##       cor 
## 0.6695397
```

<p><br><p>
These numbers confirm my plots: Stronger correlations between happiness with GDP, Life Expectancy, and Social Support. The strongest correlation of all is between Life Expecancy and GDP.
<p><br><p>

#### Comparing rankings of factors
Another way I'd like to explore this data is to compare waves of each variable. How much of each factor score does it affect the happiness ranking? 

![](happiness_files/figure-html/unnamed-chunk-28-1.png)<!-- -->

This plot shows some factors display more obvious, negative correlation to happiness than the other. However, I can see that some countries have higher GDP, for example, than the countries happier than them, and it would be interesting to see what are causing those results.
<p><br><p>


## Bivariate Analysis
<p><br><p>
### Talk about some of the relationships you observed in this part of the investigation. How did the feature(s) of interest vary with other features in the dataset?
First, I've observed relationships between Happiness Score and each factor, as well as relationships in some of the factors. The variance between the happy regions and unhappy ones are pretty obvious, and I wanted to see what factors were contributing to that result. 

After deviding the happiness into categories, I've compared the distributions of the factors. 

### Did you observe any interesting relationships between the other features (not the main feature(s) of interest)?
It was interesting to see there wasn't a strong relationship between Freedom and Trust for Government. 

### What was the strongest relationship you found?
After comparing the density of factors in each happiness class, I saw that the GDP had the strongest division in happiness, while Generosity and Trust for Government displayed weak relationships with happiness: Being happy does not mean more generous, and perception of government corruption does not seem to affect happiness much either. The correlation coefficients also backed up this theory.

<p><br></p>

## Multivariate Plots Section
<p><br></p>
#### Happiness and GDP, based on region
![](happiness_files/figure-html/unnamed-chunk-29-1.png)<!-- -->

<p><br></p>
I see that GDP may have a strong influence on the score of happiness: the higher the GDP, the higher their happiness scores tend to be, and the highest and lowest points tend to be grouped by regions, while the midsection is rather scattered in color.
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-30-1.png)<!-- -->

<p><br></p>
Here, the correlation doesn't seem to be as strong as the GDP-Happiness plot, but I can still see a positive correlation. Countries with high GDPs seem to also have stronger social support.
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-31-1.png)<!-- -->

<p><br></p>
Positive correlation with similar region patterns to the previous two plots, also region-wide seperation seems to be there.
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-32-1.png)<!-- -->

<p><br></p>
Hmm, this seems pretty scattered. although I still see the same regions colors on the top right corner, the rest of the group doesn't seem to tell me anything: Some countries have high sense of freedom, but not high happiness scores. Colors of regions also seem to be more scattered.
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-33-1.png)<!-- -->

<p><br></p>
Majority seem to lack their trust in their government, regardless of their happiness. 
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-34-1.png)<!-- -->

<p><br></p>
When it comes to generosity, regardless of the region there is no relationship with happiness.
<p><br></p>


<p><br></p>
#### Relationship between Trust and Freedom, based on region
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-35-1.png)<!-- -->

<p><br></p>
This is interesting. More freedom does not seem to mean more trust in their government. Now I want to find out how countries scoring the minimum and maximum score in each factor measure in their happiness score. 
<p><br></p>

#### Generosity and Happiness,based on GDP Class
Now, I want to see if GDP would affect people's generousity, and therefore happines. I'll compare the relationship between "Generosity" and "Happiness Score" based on "GDP Class".
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-36-1.png)<!-- -->

<p><br></p>
This tells me that higher the GDP does not mean they are more generous, even though it could mean happier. How about social support? 
<p><br></p>

#### SocialSupport and Happiness, based on GDP Class
What is the relationship betwen social supportness and GDP class, and their happiness?
<p><br></p>

![](happiness_files/figure-html/unnamed-chunk-37-1.png)<!-- -->

<p><br></p>
This tells me the higher GDP classes have more social support from the family, and also scoring higher happiness score.
<p><br></p>

#### Life Expectancy and Happiness, based on GDP Class

![](happiness_files/figure-html/unnamed-chunk-38-1.png)<!-- -->

<p><br></p>
This meets my expectations... the higher the GDP, the higher the life expectancy, and happier. 
<p><br></p>

## Multivariate Analysis

### Talk about some of the relationships you observed in this part of the investigation. Were there features that strengthened each other in terms of looking at your feature(s) of interest?
Bivariate plots with stronger correlations also seem to be correlated with regions, when grouped by it. When looking at the Happiness Score with Social Support based on GDP class, and then with Life Expectancy based on GDP class, the seperation seemed to be easier to recognized.

### Were there any interesting or surprising interactions between features?
To me it was interesting to see a relationship between GDP and Social Support, resulting in happiness, while GDP and Life Expectancy seem to have causation more ovious (<a herf="https://blog.euromonitor.com/2014/03/economic-growth-and-life-expectancy-do-wealthier-countries-live-longer.html">reference</a>). I don't see the direct cause and effect between them, and it would be interesting to dig deeper on this subject.

------

## Final Plots and Summary
<p><br><p>
### Plot One
![](happiness_files/figure-html/Plot_One-1.png)<!-- -->

### Description One
When grouped by regions, the gap between the happy and unhappy countries are evident. Middle Eastern and Norther African countries have big variances. 
<p><br><p>

### Plot Two
![](happiness_files/figure-html/Plot_Two-1.png)<!-- -->

### Description Two
GDP shows the strongeset difference in happiness out of all factors.
The happiest group sticks out in the crowd of GDP, and the shift of the groups is clear in GDP. As the GDP number increases, the happier the people.
<p><br><p>

### Plot Three
![](happiness_files/figure-html/unnamed-chunk-39-1.png)<!-- -->

![](happiness_files/figure-html/unnamed-chunk-40-1.png)<!-- -->

### Description Three
Positive (and stronger than other factors) correlations in both plots indicating as the GDP class goes higher, more social support people have, life expectancy increases, and happier they are. 
<p><br><p>
------

## Reflection

I first assumed that happiness is affected mostly by social support and life expectancy. I've also thought feeling oppressed in life decision making could also cause unhappiness. I've also read before that sense of helping others also helps your happiness. 

However, as I kept exploring each variable with another, I've come to realize that I was quite wrong about a couple of things. One is that GDP by far had the strong correlation to happiness, followed by Life Expectancy and Social Support. And to my surprise, Freedom had not much to do with it compared to the first three factors. And when it comes to generosity, richer countries did not necessary donate more to charity than poor countries, and that did not reflect their happiness. 

The limitation of this analysis comes from the fact that the dataset only contains information of 2015. Using datas from other years would definitely help clarify stories in this dataset. Also, I don't think the number of charitable donations really reflects people's generosity, since often times it is done for tax-related benefits and for political reasons. 

According to the <a href="http://worldhappiness.report/faq/">report</a>, each country collected the survey from 1000 people. So if they have conducted this survey from 2014, they would have 3000 samples. Using datasets from the previous two years would be interesting to see the pattern along with what happened in the world each year. In addition, if they have also collected more detailed data in the survey, such as gender, age, and their income, we can dig deeper to what is affecting their happiness. 

<p><br><p>
<p><br><p>
