---
layout: page
title: Hypothesis testing Explained
nav_title: Hypothesis testing
step: 2
---

__What is Hypothesis testing?__

<font color='#67E3FC'>Ans: The process of using probability and statistics to set up an experimental situation and decide whether or not to reject the “status quo” hypothesis based on sample data is called hypothesis testing.</font>

Before getting into details of how Hypothesis testing works , let us get ourselfs familiar with some terminology related to Hypothesis testing

<ul>
    <li> <b> <font color='#67E3FC'> Null Hypothesis </font> </b>[\(H_0\)] :  It is the “status quo” or “prior belief” .It assumes that the observation is due to a chance factor.  The null hypothesis is assumed to be true unless proven otherwise.</li>
    <li>  <b> <font color='#67E3FC'> Alternative Hypothesis </font> </b>[\(H_1\)] :Contrary to the null hypothesis, the alternative hypothesis shows that observations are the result of a real effect.We reject the null hypothesis in favor of the alternative hypothesis only if there is convincing statistical evidence against \(H_0\). The alternative hypothesis is sometimes referred to as the research hypothesis.</li>
</ul>

<b> Example</b>:
<img src='https://i.imgur.com/MWHcJ0c.jpg' class='image_cent'>
Suppose we wanted to determine whether a coin was fair and balanced(<b>unbiased</b>). A <b>Null hypothesis</b> states that half the flips would result in Heads and half in Tails.This can mathematically be written as follows

$$ H_o: P(Head) = 0.5$$

Now the coin is tossed let's say 10 times and 7 Heads and 3 Tails are observed.Now <b>Alternative hypothesis</b> states that the coin is a <b>biased</b>  one as we did'nt observe equal number of Heads and Tails in our experiment.

$$ H_1: P(Head){\neq} 0.5$$

Now let's go back and visit our definition of \\(H_{0}\\) -<font style="font-family:'Georgia';font-size:18px">"It assumes that the observation is due to a chance factor"</font>.A chance factor is an influence that contributes randomly to each observation, and is unpredictable.
><font color='#ff9900'><i>In simple sense, Null hypothesis argues that prior belief ( P(Head)= 0.5 in this case) is true and the observations from experiment is due to some randomness and hence can be ignored.</i></font>

The definition of \\(H_1\\) says that -<font style="font-family:'Georgia';font-size:18px">"Contrary to the null hypothesis, the alternative hypothesis shows that observations are the result of a real effect"</font>.
>Therefore <font color='#99ff33'><i>alternative hypothesis argues that observations of the experiment are biased because the coin itself is a biased-coin and not due to some chance factor.</i></font>

Now that we are done with Null hypotheis and Alternate Hypothesis , let's move to the next terms


The two types of hypothesis tests, based on the alternative hypothesis  $ H_1$, are:
<ul>
    <li>
    <font color='#67E3FC'> Two-sided, or two-tailed, tests: </font>
    When you want to detect a difference on either side of the mean, the test is said to be two-tailed and takes the form \( H_1: μ{\neq} value\). The two-sided test for the above example can be given as follows, $$ H_1: P(Head){\neq} 0.5.$$ Graphically a two tailed test can be represented as
        <img src='https://i.imgur.com/r6jgJpv.gif' class='image_cent'>
    </li>
    <li>
    <font color='#67E3FC'> One-sided, or one-tailed, tests: </font>
    When you want to detect a difference on only one side of the mean, the test is said to be one-sided and takes the form \( H_1: μ < value\) or \( H_1: μ > value \). One sided test for the above problem can be given as $$ H_1: P(Head) > 0.5$$
   <img src='https://i.imgur.com/i4PhluQ.gif' class='image_cent'>
   $$ H_1: P(Head) < 0.5.$$
   <img src='https://i.imgur.com/YDZl9Rn.gif' class='image_cent'></li>
</ul>
> __Note:__  Since we are showing the plots of normal distribution, it didn't mean that hypothesis test only applicable for only normal distribution.

When an Hypothesis test is performed, we either have to reject Null hypothesis or fail to reject it. The possible errors that may occur are <br>
<img src='https://i.imgur.com/RMqB45E.png' class='image_cent'>

<ul>
    <li> <b> <font color='#67E3FC'> Type-I error: </font> </b>
      <ul>  <li> A Type I error occurs when the researcher rejects a null hypothesis when it is true.</li>
            <li>The probability of committing a Type I error is called the <b>significance level</b>.</li>
          <li>This probability is also called <b>alpha</b>, and is often denoted by <b>α</b>.</li> </ul>
        Type one error can be interpreted as-$$ α=P(Type\, I\, error)=P(Reject\, H_0 \,when\, H_0 \,is \,true)$$


   </li>
   <li>  <b> <font color='#67E3FC'> Type -II error: </font> </b>
    <ul> <li>A Type II error occurs when the researcher fails to reject a null hypothesis that is false.</li>
        <li> The probability of committing a Type II error is called <b>Beta</b>, and is often denoted by <b>β</b>.</li>
        <li>The probability of not committing a Type II error is called the <b>Power of the test</b>.</li></ul>
        Type two error can be interpreted as - $$ β=P(Type \,II \,error)=P(fail\, to \,reject\, H_0 \,when \,H_0 \,is \,actually\, false)$$
   </li>
</ul>

> __Note:__ We would like the probability of committing either one of these errors to be as small as possible. Unfortunately, decreasing the probability of committing one type of error only increases the probability of committing the other type of error. So our main focus of interest would be <b>Type I error</b>, i.e 𝛼


### __Significance level \\(\alpha\\)__
<font color='#67E3FC'>Graphically can we explain what Significance level means?</font>
The significance level determines how far our from the null hypothesis value we'll draw that line on the graph. To draw a significance level of 0.05, we need to shade the 5% of the distribution that is furthest away from the null hypothesis.
<img src='https://i.imgur.com/sLRb6Wu.png' class='image_cent'>

The shaded region is also called as <font color='red'> Critical region </font> and the if the sample mean falls into that region, we reject the Null Hypothesis \\(H_0\\) .<br>
<font color='#67E3FC'>What does a significance level of α = 0.05 mean? </font>It means that if \\(H_0\\) is actually true and the hypothesis test is repeated on different random samples of data from the same population, then we would expect \\(H_0\\) to be incorrectly rejected 5% of the time.

<h3>\(pValue\)</h3>
>P-values are the probability of obtaining an effect at least as extreme as the one in your sample data, assuming the truth of the null hypothesis.
$$ pValue=P(Occuring\ of observation | H_0\ is\ assumed\ to\ be\ true)$$

<h3> We fail to reject the null hypothesis \(H_0\) if \(p{Value> \alpha }\) and reject if  \(p{Value< \alpha }\).</h3>

<pre>
<font color='orange' size=5><b>The Misunderstood p Value </b></font>
<img src='https://imgs.xkcd.com/comics/null_hypothesis.png' class='image_cent' style="width:200px">
The p value is one of the most misunderstood quantities in psychological research. Even professional researchers misinterpret it, and it is not unusual for such misinterpretations to appear in statistics textbooks!

The most common misinterpretation is that the p value is the probability that the null hypothesis is true—that the sample result occurred by chance. For example, a misguided researcher might say that because the p value is .02, there is only a 2% chance that the result is due to chance and a 98% chance that it reflects a real relationship in the population.
But this is incorrect. The p value is really the probability of a result at least as extreme as the sample result if the null hypothesis were true. So a p value of .02 means that if the null hypothesis were true, a sample result this extreme would occur only 2% of the time.

You can avoid this misunderstanding by remembering that the p value is not the probability that any particular hypothesis is true or false. Instead, it is the probability of obtaining the sample result if the null hypothesis were true.
<font size=2>Credit: https://opentextbc.ca/researchmethods/chapter/understanding-null-hypothesis-testing/</font>
</pre>

### __ \(z-Score\)__
A z-score (aka, a standard score) indicates how many standard deviations an element is from the mean. A z-score can be calculated from the following formula.<font color='red'> $$z =\frac{(\overline{x}-\mu)}{\frac{\sigma}{\sqrt{n}}}$$</font>

Here is how to interpret z-scores.
<ul>

<li>A z-score less than 0 represents an element less than the mean.</li>
<li>A z-score greater than 0 represents an element greater than the mean.</li>
<li>A z-score equal to 0 represents an element equal to the mean.</li>
<li>A z-score equal to 1 represents an element that is 1 standard deviation greater than the mean; a z-score equal to 2, 2 standard deviations greater than the mean; etc.</li>
<li>A z-score equal to -1 represents an element that is 1 standard deviation less than the mean; a z-score equal to -2, 2 standard deviations less than the mean; etc.</li>
</ul>

Enough of theory , now let's jump into Hypothesis implementation with example

### Example 1
<img src='https://imgs.xkcd.com/comics/significant.png' class='image_cent'>
<font size=2>credit: https://xkcd.com/882/</font>

### Example 2
<font color='#ff9900'>A survey shows that the average black friday sales of male is much higher ($500) when compared to that of female. A company which is planning for it's black friday sales want to know if this is true and hence wanted to take data from samples of different sizes such as 100,500,1000 from the population and note their black friday spending details.The company wants to know if there is really any difference in spending or it is just by chance. Can you help the company come to a conclusion on this with the help of data provided about different samples?</font>

<ol>
    <li> <b>Stating Null Hypothesis and Alternate Hypothesis</b>
        <ul>
            <li><font color='brown'> Null Hypothesis \(H_0\)</font>:The average spending of male and female is same i.e, \(\mu_m= \mu_f\) </li>
            <li><font color='brown'> Alternative Hypothesis \(H_a\)</font>: The average spending of male is greater than that of female, i.e, \(\mu_m > \mu_f \) </li>
        </ul>
    </li>
    <li> <b>Choosing significance level</b>
        <ul>
            <li>As it was not mentioned in the problem we are taking the standard significance level <font color='brown'> \(\alpha=0.15\)</font></li>
        </ul>
    </li>
    <li> <b>Setting up Test Statistic</b>
        <ul>
           <li><font color='brown'>How do we decide whether or not to reject the null hypothesis H0 ?</font>
               <br>a. we start by determining a test statistic with our sample data</li>
           <li><font color='brown'>What is test statistic?</font>
               <br>a. It is the evidence that we look for, to prove our null hypothesis
               <br>b. The most natural choice for a test statistic of the difference in population mean is the difference in sample mean \(\mu_m-\mu_f\).</li>
        </ul>
    </li>
    <li> <b>Calculating the P-value using Permutation test</b>
        <br>Refer- https://www.appliedaicourse.com/course/applied-ai-course-online/lessons/resampling-and-permutation-test-3/
        <ul>
            <li><font color='brown'>Q: Assuming that  \(H_0\)  is true, what’s the probability of obtaining \(\mu_m -  \mu_f \) = \(diff_{100}\) for the random sample of 100 data points each?</font></li>
        </ul>
    </li>
</ol>
~~~
def calculate_p_value(sample1, sample2, alpha):
    #Step 1- calculate the difference between samples

    difference_between_sample_means = mean(sample1)-mean(sample2)

    #Step 2- Permuatation test

    #Step 2.1 Merge the sameples
    difference=[]
    total_sample = list(sample1)
    total_sample.extend(sample2)
    total_sample = np.array(total_sample)

    #Step 2.2 Sampling the data for 1000 times
    for i in range(0,1000):
        #Step 2.3 Picking 100 random numbers
        samples = random.sample(range(0, len(total_sample)), 100)

        #Step 2.4 First 50 random numbers are taken as set 1
        set1 = total_sample[samples[:50]].mean()

        #Step 2.5 Next 50 random numbers are taken as set 2
        set2 = total_sample[samples[50:]].mean()

        #Step 2.6 Taking the differnce between the two sets
        difference.append(set1 - set2)

    #Step3- Sort and count the number of values greater than the threshold

    difference.sort()
    count = sum(((i > diff) and (i>0)) for i in difference)
    pValue = count/len(difference)
    print("% of values > than the difference",diff," =",pValue*100,"%")
    print("The pValue=",pValue,"and P(Reject H0 when H0 is true)=",alpha)
    if pValue>alpha:
        print("We fail to reject the null hypothesis")
    else:
        print("We can reject the null hypothesis")

  print('_'*50)
  return difference
  ========================
  For Sample Size:  200
  The average spendings 100 male = 9881.62
  The average spendings 100 female= 7703.87
  The difference between mean of male and female spendings = 2177.750
  Percentage of values greater than the difference 2177.750  = 0.8 %
  The pValue =  0.008 and the P(Reject H0 when H0 is true)= 0.15
  We can reject the null hypothesis
~~~

<img src='https://i.imgur.com/lZx4Jt2.png' class='image_cent' style="width:650px">

in the above plot, when we take the sample size 100 we are getting `pValue =  0.008`, for sample size 500 we are getting `pValue = 0.161` and for the sample size 1000 we are having  `pValue = 0.289`

If we reject the null hypothesis, we do not prove the alternative hypothesis is true. We merely state there is sufficient evidence to reject the null hypothesis.
If we fail to reject the null hypothesis, we do not prove the null hypothesis is true. We merely state there is not sufficient evidence to reject the null hypothesis.
Unfortunately, whatever the decision, there is always a chance we made an error!
