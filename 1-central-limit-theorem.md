---
layout: page
title: Central Limit The Explained
nav_title: Central Limit Theorem
step: 1
---

Central Limit Theorem (CLT) is a statistical theory stating that given a sufficiently large sample size from a population with a finite level of variance, the mean of all samples from the same population will be approximately equal to the mean of the population.

## Working with Real time data

To explain the concepts of Central limit Theorem i am taking a dataset from <a href="https://www.kaggle.com/mehdidag/black-friday" target="_blank">here</a>

In this dataset we have 537577 data points, and below is the distribution plot of the prices of the iterms.

<img alt="distribution of data" src="../public/img/centeral_dist.JPG" width=400 class='image_cent'>

## Getting samples

To demonistrate the cetral limit Theorem, lets do a simple experiment by collecting few samples from the data and for each sample calculate its mean.

the bellow image shows the distribution of the those means

<img alt="means of sample distribution" src="../public/img/centeral_dist2.PNG" width=400 class='image_cent'>

if you have observed the above image, i have plotted 6 distributions, the left top is generated with 100 samples and each sample of size of 50, for each sample i have calculated mean and plotted a <a href='https://en.wikipedia.org/wiki/Kernel_density_estimation1'>kde plot</a>, the blue line shows the mean of sample means i.e `mean(100 sample means)` and the red line is drawn at the population mean. the remaining other plots were also generated in the similar fashion.

> if we can observe the thrid row distribution plots, we can say that the larger the sample size, the more it looks like Gaussian

<img alt="means of sample distribution" src="../public/img/centeral_dist3.PNG" class='img-nice'>

I have just tabulated all the values so that we can have a better look at the numbers and relate to our experiment. In the above table P_mean is Population mean, P_std is Population standard deviation, and <font color='red'>\(n\)</font> is the number of elements in each sample.

> <strong>Observations:</strong> If you check the above stats, we can observe the distribution of sample means, is having mean <font color='red'>\(\mu_{x} \approx \mu\)</font> and <font color='red'>\(\sigma_{x}\approx \frac{\sigma}{\sqrt{n}}\)</font>


<strong>Central Limit Theorem says: </strong>
<ul style="font-family:'Georgia';font-size:18px" >
<li>
The sampling distribution of the sample mean <font color='red'>\(\overline{X}\)</font>  is approximately normally distributed with mean <font color='red'>\(\mu\)</font> and standard deviation <font color='red'>\(\frac{\sigma}{\sqrt{n}}\)</font>. if the original distributions are non-normal.
</li>
<br>
<li>
The larger the sample size <font color='red'>\(n\)</font> is, the more normally distributed the sampling distribution will be and the more tightly it will converge about the true population mean <font color='red'>\(\mu\)</font>.
</li>
<br>
<li>
The sampling distribution of the sample mean <font color='red'>\(\overline{X}\)</font> is exactly normally distributed with mean <font color='red'>\(\mu\)</font> and standard deviation <font color='red'>\(\frac{\sigma}{\sqrt{n}}\)</font> if the original distributions are normal.</li>
</ul>

><strong>Note</strong>: here <font color='red'>\(\overline{x}\)</font> is the mean of single sample,  <font color='red'>\(\mu_{x}\)</font> is the mean of the sampling distribution of the sample mean and <font color='red'>\(\mu\)</font> is the population mean

## Population Mean Confidence Intervals for Larger Samples
<ol>
<li>Consider the poplulation mean is <font color='red'>\(\mu\)</font>, and suppose you have taken a sample and calculated its mean as <font color='red'>\(\overline{x}\)</font></li>
<li>Often for a given population we don't know what is the values of <font color='red'>\(\mu\)</font></li>
<li> Here we try to esitmate the <font color="#67E3FC"> <i>unknown</i> <font color='red'>\(\mu\)</font> </font>with the help of <font color="#67E3FC"> known value <font color='red'>\(\overline{x}\)</font> </font> </li>
</ol>

__<strong>Q: Here “Why do we need a sample mean to calculate the population mean? why can't we directly calcualte the mean of the population?” </strong>__

<font color='#67E3FC'>
Ans: Suppose your population of interest is in Delhi, and you want to know the mean age of the population.
<ul>
<li>Due to lack of time, energy, and money, you cannot obtain the age of every person in Delhi.</li>
<li>You can select a sample (e.g. a simple random sample) and calculate the mean of that sample, <font color='red'>\(\overline{x}\)</font></li>
</ul>
</font>

<strong>Q: Then “Why don’t we just use the sample mean  <font color='red'>\(\overline{x}\)</font> to estimate the population mean <font color='red'>\(\mu\)</font>?” </strong>

<font color='#67E3FC'>
<ul>
<li>We can – but the sample mean <font color='red'>\(\overline{x}\)</font> may be quite different from the population mean <font color='red'>\(\mu\)</font>, even if we obtained the sample correctly.</li>

<li>In addition, a single number estimate by itself, such as <font color='red'>\(\overline{x}\)</font>, provides no information about the precision and reliability of the estimate with respect to the larger population. </li>

</ul>
</font>

<p style="font-family:'Georgia';font-size:18px" >
Statisticians use the sample statistic <font color='red'>\(\overline{x}\)</font> and the population(<font color='red'>\(\sigma\)</font>) or sample standard deviation to provide <font color="#67E3FC">an interval of plausible estimates</font> for the population parameter <font color='red'>\(\mu\)</font>. This interval is called a <font color="#67E3FC">confidence interval.</font>
</p>

> <strong>Definition:</strong> A confidence interval is an entire interval of plausible values for a population parameter, such as <font color='red'>\(\mu\)</font>, based on observations obtained from a random sample of size <font color='red'>\(n\)</font>.

### Let us answer a question
__What is the avarage money spent by Male population on black friday ?__

Before we know how to estimate that lets have a look at couple of concepts
### <a href='https://en.wikipedia.org/wiki/Standard_error'><font color='white'>Standard error</font></a>
<li>The standard error (SE) of a statistic (usually an estimate of a parameter) is the standard deviation of its sampling distribution or an estimate of that standard deviation.</li>
<li>If the parameter or the statistic is the mean, it is called the standard error of the mean (SEM). </li>
<li>The standard error of the mean (SEM) can be expressed as: </li>

$$\sigma_\overline{x}=\frac{\sigma}{\sqrt{n}}$$

Since the population standard deviation is seldom known, the standard error of the mean(SEM) is usually estimated as the sample standard deviation divided by the square root of the sample size (assuming statistical independence of the values in the sample).

$${\displaystyle {\sigma }_{\bar {x}}\ \approx {\frac {s}{\sqrt {n}}}} $$

### \(zScore\) and Confidence Levels:

<ul>
    <li>Let \(\alpha\) be a number between 0 and 1, and let 100 * (1 – \(\alpha\))% denote the confidence level.
    <br>For example,
        <ul>
        <li>if \(\alpha\) = 0.05, then the corresponding confidence level is 95%. </li>
        <li>If \(\alpha\)= 0.01, then the confidence level is 99%.</li>
        </ul>
    </li>
    <li>
        Suppose we have a standard normal distribution \(Z\). <br>Let \(z_\frac{\sigma}{2}\) denote a \(zScore\) with α/2 probability to its right. <br>Similarly let -\(z_\frac{\sigma}{2}\) denote a \(zScore\) with α/2 probability to its left.
    </li>
    <li> Example: <img src='https://i.imgur.com/mntg6h2.png' width=700>
        The value \(z_{0.10}\) is the positive z-score that has α/2 = 0.1 probability to its right. The desired \(zScore\) is 1.282. <br>The value \(-z_{0.25}\) is the negative z-score that has α/2 = 0.25 probability to its left. The
desired \(zScore\) is -0.6745.
    </li>
</ul>

~~~
# https://stackoverflow.com/a/20864883/4084039
import scipy.stats as st
print("zScore for 0.1 probability to right is",st.norm.ppf(1-0.10))
print("zScore for 0.25 probability to left is",st.norm.ppf(0.25))

zScore for 0.1 probability to right is 1.2815515655446004
zScore for 0.25 probability to left is -0.6744897501960817
~~~

> <strong>Note:</strong> the data we have in hand might not included all the purchases that are made, and assume we have given the whole population standard deviation as 5051

~~~
# we are taking a sample of male persons and calculating their mean
data_male = np.array(df[df['Gender']=='M']['Purchase'].values)
samples = random.sample(range(0, data_male.shape[0]), 100)
print("the mean of money spent by sample set of 100 persons :",data_male[samples].mean())
print("Given that the we have population standard deviation : 5051")
print("From central limit theorem we can say that, the std of sampling distribution of the sample mean is \u03C3/\u221An :", 5051/10)

the mean of money spent by sample set of 100 persons : 10474.31
Given that the we have population standard deviation : 5051
From central limit theorem we can say that, the std of sampling distribution of the sample mean is σ/√n : 505.1
~~~

<img src='https://i.imgur.com/vXSIeng.jpg' class='image_cent'>

We know that in normal distribution, given a data point there is \(95\) probability that it will be within the range [ <font color='red'>\(\mu-2\sigma\)</font>, <font color='red'>\(\mu+2\sigma\)</font>]

<ul>
    <li>The sampling distribution of the sample means is a normal distribution</li>
    <li>Any sample mean we take <font color='red'>\(\overline{x}\)</font> it is 95% probability that it will be within the range [ <font color='red'>\(\mu_{x}-2\sigma_{x}\)</font>, <font color='red'>\(\mu_{x}+2\sigma_{x}\)</font>] \(i.e.\) for every 100 sample means typically 95 of them are in this range [ <font color='red'>\(\mu_{x}-2\sigma_{x}\)</font>, <font color='red'>\(\mu_{x}+2\sigma_{x}\)</font>]</li>
    <li>It is similar to that for any sample mean we take <font color='red'>\(\overline{x}\)</font> it is 95% probability that the range [ <font color='red'>\(\overline{x}-2\sigma_{x}\)</font>, <font color='red'>\(\overline{x}+2\sigma_{x}\)</font>] will contain distribution mean <font color='red'>\(\mu_{x} [\approx \mu]\)</font>.
    </li>
</ul>


__Choose the best interpretation of a 95% confidence interval for the population mean μ?__ <br>
<font color='#67E3FC'><b>Option 1:</b></font> If repeated random samples were taken and the 95% confidence interval was computed for each sample, 95% of the intervals would contain the population mean.
<font color='#67E3FC'><b>Option 2:</b></font> The probability that the population mean μ is in the confidence interval is 0.95
<font color='#67E3FC'><b>Option 3:</b></font> 95% of the population distribution is contained in the confidence interval.
<br><br>
<font color='green'><b>Answer:</b></font> The correct answer is <font color='green'><b>Option 1</b></font> please check the above 3 points, <font color='#67E3FC'><b>Option 2</b></font> is incorrect because it places the probability on μ, instead of on the confidence interval. <font color='#67E3FC'><b>Option 3</b></font> is incorrect since the confidence interval for the population mean is built using sample means and not values from the population distribution. Using population distribution values would give us a confidence interval that is wider than the one for the population mean.

<font size='3'>From the above equations Let us construct an intravel [<font color='red'>\(\overline{x}\)- 2*505.1, \(\overline{x}\)+2*505.1</font>] = [<font color='red'> \(\overline{x}\)- 2*\(\frac{\sigma}{\sqrt{n}}\), \(\overline{x}\)+2*\(\frac{\sigma}{\sqrt{n}}\)</font>]</font>

<img src='../public/img/centeral_dist4.PNG' width=600 class='image_cent'>

In the above figure, the red line show the sample mean <font color='red'>\(\overline{x}\)</font> and the two green lines shows [<font color='red'> \(\overline{x}\)- 2*\(\frac{\sigma}{\sqrt{n}}\), \(\overline{x}\)+2*\(\frac{\sigma}{\sqrt{n}}\)</font>]

>__Note:__ We have a big Assumption that, we know the population standard deviation as 5051.

## Confidence interval when don't have knowldge about population standard deviation

we know the the cofidenance interval [<font color='red'> \(\overline{x}\)- 2*\(\frac{\sigma}{\sqrt{n}}\), \(\overline{x}\)+2*\(\frac{\sigma}{\sqrt{n}}\)</font>] when we know the popuplation standard deviation. If you observe here we estimating population mean with sample mean (from above pdf plots, the sample mean is almost close to population mean)

<strong>Can we do the similar estimation of population stadard deviation using sample stadard deviation?</strong>
Answer: Yes, We can estimate it

SE is used is to make confidence intervals of the unknown population mean. If the sampling distribution is normally distributed, the sample mean, the standard error, and the quantiles of the normal distribution can be used to calculate confidence intervals for the true population mean.

The following expressions can be used to calculate the upper and lower \(95%\) confidence limits
<font color='white'>
\({\text{upper 95%  limit}{\displaystyle ={\bar {x}}+{\text{SE}}\times 1.96}}\) <br>
\({\text{lower 95%  limit}{\displaystyle ={\bar {x}}-{\text{SE}}\times 1.96}}\) <br>
</font>

<font color='white'>\({\displaystyle {\bar {x}}}\) is equal to the sample mean, an estimation to population mean
SE is equal to the standard error for the sample mean, <br>
1.96 is the 0.975 quantile of the normal distribution <br>
</font>
<br>
<strong> But why we have taken 0.975 quantile?</strong> <br>
<font>
Answer: as we need the confidence level of 95%, the \({\alpha}\) value will be 0.05, so \(\frac{\alpha}{2}=0.025\)
As we know <br><br>
\({\text{Upper 95%  limit}{\displaystyle ={\bar {x}}+{\text{SE}}\times z_\frac{\alpha}{2}}} = {\bar{x}}+{\text{SE}} \times z_{0.025}  = {\bar{x}}+{\text{SE}} \times 1.96 \) <br>
\({\text{Lower 95%  limit}{\displaystyle ={\bar {x}}-{\text{SE}}\times z_\frac{\alpha}{2}}} = {\bar{x}}-{\text{SE}} \times z_{0.025}= {\bar{x}}-{\text{SE}} \times 1.96 \)

</font>

<font >From the above equations we can construct an intravel  [<font color='red'> \(\overline{x}\)- 2*\(\frac{s}{\sqrt{n}}\), \(\overline{x}\)+2*\(\frac{s}{\sqrt{n}}\)</font>]</font>

<img src='../public/img/centeral_dist5.PNG' width=600 class='image_cent'>

__Conclusion: Finding Confidenace interval of population mean__
<ul>
    <li>Case 1: Knowing Population Standard Deviation <font color='red'> \({\sigma}\) </font>
    <ol>
        <li>Get a sample with decent size(<font color='red'>\(n\)</font>) from population and caculate its mean <font color='red'> \(\overline{x}\)</font></li>
        <li>Report confidence intravel as [<font color='red'> \(\overline{x}\)- 2*\(\frac{\sigma}{\sqrt{n}}\), \(\overline{x}\)+2*\(\frac{\sigma}{\sqrt{n}}\)</font>]</li>
    </ol>
</li>
<li>Case 2: Without Knowing Population Standard Deviation
    <ol>
        <li>Get a sample with decent size(<font color='red'>\(n\)</font>) from population and caculate its mean <font color='red'> \(\overline{x}\)</font></li>
        <li>Calculate the sample std <font color='red'>s</font> and find the The standard error of mean or <font color='red' > SE mean </font>as  <font color='red'>\(\frac{s}{\sqrt{n}}\)</font>.</li>
        <li>report confidence intravel as[<font color='red'> \(\overline{x}\)- 2*\(\frac{s}{\sqrt{n}}\), \(\overline{x}\)+2*\(\frac{s}{\sqrt{n}}\)</font>] or [<font color='red'> \(\overline{x}\)- 2*\(SE mean\), \(\overline{x}\)+2*\(SE mean\)</font>]</li>
    </ol>
</li>
</ul>


<div class="pagination">
  <a class="pagination-item older" href="{{ site.baseurl }}">&laquo; Introduction</a>
  <a class="pagination-item newer" href="{{ site.baseurl }}2-hypothesis-testing">2 hypothesis Testing &raquo;</a>
</div>
