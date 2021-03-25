In 2014 FiveThirtyEight.com published an article entitled 
[How to Tell Someone's Age When All You Know Is Her Name](https://fivethirtyeight.com/features/how-to-tell-someones-age-when-all-you-know-is-her-name/), 
and I thought that it might be interesting to re-create the FiveThirtyEight analysis in Python (everyone needs a hobby). 
The article suggested that one might use the median age for a given name as a point estimate for age and also included 
plots of the median age for popular names, male and female, with bars showing the middle 50%. We'll take those plots as 
a goal for this notebook.

I would like to highlight two key aspects of this analysis. First of all, the data are already aggregated so that one cannot compute the 
median age by name and gender by a simple application of the built-in methods. However, this provides an opportunity to discuss GroupBy 
objects in pandas. GroupBy objects are explained by Wes McKinney in Chapter 9, *Data Aggregation and Group Operations,* of **Python for Data 
Analysis.** McKinney notes that this type of computation is commonly referred to as "split-apply-combine", a phrase that was coined by 
Hadley Wickham, the R language guru.

The second highlight is that the main data set has data about names given at birth, but we are interested in living Americans. So we need 
to join a dataset with survival rates to the name data. However, the survival rate data is given only for people born in years divisible 
by 10; so we need to interpolate the data. That's a good thing to know too!

The Python code here does not re-create the FiveThirtyEight article in full, but it should get you to a point where you could easily 
re-create every graphic in the article.
