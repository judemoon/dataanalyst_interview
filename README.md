# Interview Practice for Data Analyst Job 

July-August 2017, by Jude Moon

## Practice Overview
Employers use interviews to judge your readiness and fit for the job, which includes hearing about your skills and interest in the role. The interview is not a test or exam, but a conversation between you and the employer. Build your own strategies to be prepared come interview day. This project is one of many ways for you to practice!

### 1. Describe a data project you worked on recently.

The goal of my project is to use financial and email data from Enron - which comprised email and financial data of 146 people (records), most of which are senior management of Enron, to come up with a predictive model that could spot an individual as a "Person of Interest (POI). I use `scikit-learn` & various machine learning techniques to predict "Person fo Interest", detecting culpable person using both financial & email-data. 

First, I used scikit-learn `SelectKBest` to select best 10 influential features and used those featuers for all the upcoming algorithm. After feature engineering & using `SelectKBest`, I then scaled all features using `min-max scalers` so we can prevent data not to have several of magnitudes difference . Next, I use parameter tuning in order to improve the fit on the test set, there're multiple parameters can be tuned for logistic regression. 

Next, I use validation techniques to make sure our model generalizes with the remaining part of the dataset. In detail, I split the data into 3:1 ratio & create 1000 trials. Main reason why I'd create too many trials since the dataset is very small and with small number of trials, the data might be bias. Finally, I evaluate the mdel using `precision` & `recall` rather than `accuracy` since if everyone is flagged as Person of Interest, the accuracy would be 100% and shows irrelevant data.

### 2. You are given a ten piece box of chocolate truffles. You know based on the label that six of the pieces have an orange cream filling and four of the pieces have a coconut filling. If you were to eat four pieces in a row, what is the probability that the first two pieces you eat have an orange cream filling and the last two have a coconut filling?

* Probability of 1st and 2nd choices to be orange: $\frac{6}{10} * \frac{5}{9}$
* Probability of 3rd and 4th choice to be coconut: \frac{4}{8} * \frac{3}{7}
* Total Probability:  \frac{6}{10} * \frac{5}{9} * \frac{4}{8} * \frac{3}{7} = 0.0714

### Follow up question: If you were given an identical box of chocolates and again eat four pieces in a row, what is the probability that exactly two contain coconut filling?



Within first 4 pieces of box of chocolates, there're 14 combinations, assuming each combinations have similar probability
```
Example:
Combination 1: Orange, Orange, Orange, Coconut 
Combination 2: Orange, Coconut, Coconut, Orange
Combination 3: Orange, Coconut, Coconut, Coconut
Combination 4: Coconut, Coconut, Coconut, Coconut
....
Combination 14.

Within those 14 combinations, there're 6 combinations have exactly 2 coconuts

Therefore, we have P(exactly 2 coconuts in 14 combinations) = 6/14 = 42.857%
```

### 3. Construct a query to find the top 5 states with the highest number of active users. Include the number for each state in the query result.

```
SELECT state, SUM(active)
from users
GROUP BY state
ORDER BY SUM(active) DESC
LIMIT 5
```

> Define a function `first_unique` that takes a string as input and returns the first non-repeated (unique) character in the input string. If there are no unique characters return None. Note: Your code should be in Python.

```
from collections import defaultdict
def first_unique(word):
    '''initiate defaultdict for count'''   
    counts = defaultdict(int)
    ''' create empty list'''
    l = []
    '''loop through each character in a string'''
    for c in word:
        counts[c] += 1
        '''if there's first unique character, append them to list'''
        if counts[c] == 1:
            l.append(c)
    ''' if list only contains 1 character, return the result'''        
    for c in l:
        if counts[c] == 1:
            return c
    ''' otherwise, return "None"" '''
    return "None"
```

### 4. What are underfitting and overfitting in the context of Machine Learning? How might you balance them?

Let's say we attend a symphony and want to get the clearest, most faithful sound possible. So we buy a extremely-sensitive microphone and hearing aid to pick up all the sounds in the auditorium.
Then we start "overfitting," hearing the noise on top of the symphony. We hear our neighbors moving in their seats, the musicians turning their pages or even sneezing of the audiences afar.
When we're at a concert, there's both the symphony and the random noise. Fitting a perfect model is only listening to the symphony. Over-fitting is when you hear more noise then you need to, and underfitting is the quality of the symphony sound is not as amazing as it should be since all the goodness of the symphony is not fully capture by a bad microphone.

To balance overfitting, we can go for simpler model with fewer parameters to tune & remove the parameters that add little improvement to the result. The other method is to use cross validation, splitting the data into 3:1 or 4:1 ratio and conduct multiple trials (if the dataset is too small).

### 5. If you were to start your data analyst position today, what would be your goals a year from now?

Job I want to apply to : https://careers-uber.icims.com/jobs/13612/global-data-analyst%2c-singapore/job?mobile=false&width=1048&height=500&bga=true&needsRedirect=false&jan1offset=420&jun1offset=420

Within the Uber sphere, my goal is to become technically sufficient in SQL & Python, matching with Uber needs as a Global Data Analyst. 

Within the first 3 months, my goal are:

1. Understand nuts and bolts of every single database scheme in Uber, especially Uber Asia Pacific.
2. Have a clear knowledge of every Uber metrics/KPIs needed to operate in Asia Pacific.
3. Ability to do fundamental data analysis task for Uber (A/B testing, statistical inference,etc.)

Within one year, my goal are:

1. Code fluently in Python to develop new innovative metrics to track for Uber.
2. Query database cold & create new assumptions/hypothesis and test it. For example: I'd suspect Uber customers are increasingly parents (doesn't have time to pick-up children & use Uber for alternative to school-bus) so I'd collect data & conduct a statistical test to test if this is true, and how could we target those new emerging segment.
3. Develop new data product (an internal platform for Uber drivers or Uber data team).E.g an automate tool to calculate A/B testing result & experiement (split the data & conduct statistical analysis automatically with a few click of a button).

