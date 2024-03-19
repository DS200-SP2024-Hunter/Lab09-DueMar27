# Lab Assignment 09, Due on [Canvas](https://psu.instructure.com/courses/2306358/assignments/16016386), Mar. 27 at 11:59pm
## What does the distribution of the sample mean look like when the population is skewed?

**On this and all labs for the rest of the semester: When you have a choice between the [datascience package](https://www.data8.org/datascience/) and the [pandas library](https://pandas.pydata.org/docs/), you are free to use either method to complete your work.**


The main objective of today's lab is to use python tools to understand and illustrate how a sample mean behaves for various sample sizes.

**Objective**:  Using the massive flights dataset from [Lab 6](https://github.com/DS200-SP2024-Hunter/Week06-DueFeb23), extract the column called AIR_TIME and then investigate the behavior of sample means for samples from this column of various sizes.  

**Your assignment** is as follows:

1. Repeat the steps in Lab 6 that create the giant `Table` object, called `flights`, with 5.8 million rows of data.  After this is done, we only need the column called `AIR_TIME` so reduce the `flights` object to just that column using this code:
```
flights = flights.select('AIR_TIME')
```

2. Delete the `AIR_TIME` values that equal `nan` (which means "not a number") using this code:
```
airtimes = np.array(flights.column('AIR_TIME')) # Create a np.array from the AIR_TIME column
airtimes = airtimes[~np.isnan(airtimes)] # Get rid of all nan entries using np.isnan 
airtimes = Table().with_column('AirTime', airtimes) # Put the modified array back into a Table
```

3. Use the `num_rows` method to find the number of observations in the `airtimes` dataset, then create a histogram of the data.  Your histogram should show that the dataset is skewed toward larger times.  Verify directly that the mean is larger than the median.

4. Use the `simulate_sample_mean` function from [Section 14.5](https://inferentialthinking.com/chapters/14/5/Variability_of_the_Sample_Mean.html) to generate a histogram of sample means from 10,000 samples of size _n_=1 from `AIR_TIME`.  What is the shape of the histogram?  Is this what you expected, and why? Explain your answers in a text box.

5. Now repeat step 4, including answering the questions, using _n_=5 and _n_=100.

6. In this case, we are sampling from a population that is entirely known to us.  Therefore, we can calculate the exact value of the population standard deviation.  Find this SD, then calculate the SD of sample means from steps 4 and 5 using the information in Section 14.5.2.  Summarize these values side by side next to the SDs of sample means that were measured in the simulations in steps 4 and 5.  (The values should be very close.  This comparison is similar to the SD comparison in Section 14.5.1.)

7. _(Optional, for an extra point):_ [Section 14.4.1](https://inferentialthinking.com/chapters/14/4/Central_Limit_Theorem.html) analyzes the net gain in roulette if the player bets on red.  Suppose you work for a casino.  If the casino has 400 people play roulette and bet on red each day, what is the probability that the casino loses money on these players that day?  Find a number of players, _n_, so that the probability of the casino losing money on a given day drops to about 1% and explain how you found this _n_. It's fine if you use simulation for this task to obtain an approximate answer.

8.  Finally, make sure that your Jupyter notebook only includes code and text that is relevant to this assignment.  For instance, if you have been completing this assignment by editing the original code from Chapter 4 or Lab 6, make sure to delete the material that isn't relevant before turning in your work.

When you've completed this, you should select "Print" from the File menu, then save to pdf using this option.  The pdf file that you create in this way is the file that you should upload to Canvas for grading.  We have found that if you can select the "A3" paper size from the advanced options, this seems to solve the problems that are sometimes encountered in this step.
