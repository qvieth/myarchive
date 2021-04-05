# intro to hypothesis testing in statistics

-   DIFFERENT CLAIMS => DIFFERENT DISTRIBUTION
- are under the cure : p-value, \alpha
-   REJECT THE NULL HYPOTHESIS
-   TEST STATISTICS Z (when talk about normal distrbution)
-   22 degree of freedoms => 23 samples
-   newton law of gravity is just simply version - einstein's gravity is space-time
-   https://www.youtube.com/watch?v=VK-rnA3-41c

-   hypothesis : a claim
    -   null hypothesis : H_0 - currently accepted value for a param
    -   alternative hypothesis : H_a - also called research hypothesis, involves the claim to be tested
    -   H_0 and H_a are mathematical opposites

*   possible outcomes of this test :
    -   reject null hypothesis H_0
    -   fail to reject null hypothesis H_0

-   how to determine whether to reject them or not?

    -   use something called **test statistic**
        -   calculated from sample data and used to decide
    -   ex : sample 50 bars
        -   get avg val the mass of the bars
        -   calculate test statistic
        -   then use test statistic to determine
            -   is the data that you have
            -   statistically significant enough
            -   to reject this null hypothesis
        *   need a concrete way to determine wheter :
            -   a test statistic is too high or too low
            -   and when you reject that null hypothesis and when you don't
        -   => confident level : variable `C` - 95%, 99%
            -   how confident are we in our decision
        -   => significant level : `\alpha` = 1 - C
        -   both confident level and significant level tell you the same thing :
            -   how sure are you that you're making the right decision or not
            -   H_0 what we currently think is true
            -   H_a is what we propose to be true
            -   the only way we can resolve this is either we reject the null hypothesis or we fail to reject if
            -   it's very similar to how courts work

-   https://www.youtube.com/watch?v=_Qlxt0HmuOo : continue

    -   H_0 : p >= 0.6
    -   H_a : p < 0.6 - the way we do the test depends on this `<` symbol
    -   \alpha = 0.02

-   https://www.youtube.com/watch?v=KLnGOL_AUgA : p-value
    -   IMPORTANT VIDEO WITH THE GRPAH : REWATCH
-   test statistic : Z = frac{x-bar - \mu}{s/sqrt{n}}
-   purpose of p-values : to know where to reject that null hypothesis

*   p-value :
    -   probability of obtaining a sample "more extreme"
    -   than the ones observed in your data, assuming H_0 is true
    -   area under the curve to the right or left of the distribution with 0 in the middle

-   left-tail test - right tail test :
    -   image of normal distribution with 0(null) in the middle

*   https://www.youtube.com/watch?v=5FmxvmlOmfA

-   **conclusion of p-test** :
    -   if p <= \alpha => reject H_0
    -   if p > \alpha => fail to reject H_0

*   think : why do people do hypothesis testing :
    -   if there's an established null hypothesis in some factory
    -   that the candy bars come out of certain lengths
    -   and i come in the door and i think by looking
    -   and i think that null hypothesis is wrong
    -   so i propose a new hypothesis we call alternate hypothesis or research hypothesis
    -   so i propose that and i go to the meeting and say
    -   look guys, the candy bar machine doesn't work
    -   they're making the candy bars too long
    -   okay well, the way we've done all of the problems so far is
    -   i've specified a level of significant which you can think of
    -   as a level of confidence i've said a 95% confidence
    -   i want to see if reject this null hypothesis or not
    -   i've said for every problem :
        -   when i reject a null hypothesis or fail to reject a null hypothesis
        -   it's only vaid at that level of significance
        -   you set the level of significance, can set too low or too high
        -   every time i move the goal line, when i change the level of significance
        -   i'm moving the threshold point, so that **my data is staying fixed**
        -   i may end up in the rejection region or accept region
*   think of Z come from data, we try to move

*   https://www.youtube.com/watch?v=KTFm7El1NBs :
*   independent sample
*   dependent sample
*   hypothesis testing - means

    -   large => n > 30
    -   independent - 2 groups not conn
    -   2 means : 2 groups of people
    -   H_0 : \mu_1 <= \mu2
    -   H_a : \mu_1 > \mu2
    -   H_a : < left tail, > right tail, != 2 tail
    -   reject or failed to reject based on p-value
    -   test statistic : Z : what governs hypothesis testing involving 2 population means with large(n>30) samples
    -   n>30 we can use normal distribution (central limit theorem)

*   https://www.youtube.com/watch?v=80YzzIm8NK8 : hypothesis testing for means & large sample, part 1
*   T-distribution : looks bellshape, the exact shape of it depends on **degrees of freedom** (n-1)
*   shape of tdistribution become normal as sample goes large
*   because distribution approaches normal distribution when you have large(>30) number of samples

-   as far as the hypothesis testing itself the actual method is basically exactly the same as what we've doing before :
    1. lockdown the rejection regions
    2. calculate the test statistics
    3. see where test statistic falls
    4. determine if reject or fail to reject

*   all of these stuff is really the same, the concept is really the same
*   DIFFERENT CLAIMS => DIFFERENT DISTRIBUTION
* T distribution totally change shape depending on the degrees of freedom that you have
* if i have a 15 degree of freedom problem which means 16 samples
* or if i have another problem that's 22 degree of freedoms => 23 samples
* then those 2 are gonna look bell-shaped but their shape of the curve will be different than the other
* because the changing nature of T-distribution depend on the number of samples
* i have to go find  those rejection region
* but now we're into the realm of large samples it's always going to be greater than 30 samples
* and i'm always gonna use a normal distribution
* **a normal distribution is much simpler because it never changes**
* doesn't matter if i have 32 samples or 49 samples or 1000 samples
* i'm gonna use that normal distribution for all of these problems
* so these problem are get a little bit simpler :
    * i don't have to go find these rejection regions for every single problem
    * because that distribution doesn't change for every problem
* Z distribution : area to the left
* T distribution : are to the right
