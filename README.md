#Finding Happiness

<p><a href="https://github.com/emimimura/FindingHappiness/blob/master/2016.csv">Download dataset</a></p> 

<p>“The World Happiness Report is a landmark survey of the state of global 
happiness. The first report was published in 2012, the second in 2013, the third 
in 2015, and the fourth in the 2016 Update.”</p>

<p>“The happiness scores and rankings use data from the Gallup World Poll. The 
scores are based on answers to the main life evaluation question asked in the 
poll. This question, known as the Cantril ladder, asks respondents to think of 
a ladder with the best possible life for them being a 10 and the worst possible 
life being a 0 and to rate their own current lives on that scale. The scores are 
from nationally representative samples for the years 2013-2016 and use the 
Gallup weights to make the estimates representative.”</p>

<p>Per <a href="http://worldhappiness.report/wp-content/uploads/sites/2/2016/03/HR-V1_web.pdf">their document</a>, here are the measures of each factors:</p>

- <b>GDP per capita</b>

- <b>Healthy years of life expectancy</b>

- <b>Social support </b><br>
“If you were in trouble, do you have relatives or friends you can count on to 
help you whenever you need them, or not?” 

- <b>Trust</b> <br>
As measured by a perceived absence of corruption in government and business, 
perceptions of corruption are the average of binary answers to two GWP 
questions: “Is corruption widespread throughout the government or not” and 
“Is corruption widespread within businesses or not?” Where data for government 
corruption are missing, the perception of business corruption is used as the 
overall corruption-perception measure.

- <b>Freedom to make life decisions</b><br>
“Are you satisfied or dissatisfied with your freedom to choose what you do 
with your life?”

- <b>Generosity </b><br>
“Have you donated money to a charity in the past month?” on GDP per capita.

<p>I first assumed that happiness is affected mostly by social support and life 
expectancy. I've also thought people's feeling oppressed in life decision making 
could cause unhappiness. I've also read before that sense of helping others 
supposedly increases your happiness. </p>

<p>However, as I kept exploring each variable with another, I've come to a 
realization that I was quite wrong about a couple of things. One is that GDP by 
far had the strong correlation to happiness, followed by Life Expectancy and 
Social Support. And to my surprise, Freedom had not much to do with it compared 
to the first three factors. And when it comes to generosity, richer countries 
did not necessarily donate more to charity than poor countries, and that did not 
reflect their happiness. </p>

<p>The limitation of this analysis comes from the fact that the dataset only 
contains information of 2015. Using datas from other years would definitely help 
clarify stories. I also don't think the number of charitable donations really 
reflects people's generosity, since often times it is done for tax-related 
benefits and for political reasons. </p>

<p>According to the <a href="http://worldhappiness.report/faq/">report</a>, each 
country collected the survey from 1000 people. So if they have conducted this 
survey from 2014, they would have 3000 samples. Using datasets from the previous 
two years would be helpful to see the pattern along with what happened in 
the world each year. Additionally, if they have also collected more detailed data 
in the survey, such as people's genders, ages, and their incomes, we could dig 
deeper to what is truly affecting their happiness. </p>
