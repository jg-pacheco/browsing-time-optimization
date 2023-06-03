# Netflix Users Browsing Time Optimization

## Executive Summary

As Netflix users often experience choice overload, which leads to decision paralysis whenever
they browse too long for shows to watch on Netflix, we conducted a series of experiments to
minimize the users browsing time. In this project, we aim to reduce the browsing time on the
Netflix homepage by analyzing the effects of four factors: Tile Size, Match Score, Preview
Length, and Preview Type. Through testing, we found that Tile Size has no significant impact
on browsing time and that the best results were achieved using teaser/trailer for Preview Type.
Further experimentation using the Central Composite Design (CCD) method resulted in
identifying the optimal factor combination, with a Match Score of 73%, a Preview Length of
75 seconds, and a Preview Type of Teaser/Trailer, which reaches the lowest browsing time of
10.16 minutes.


## Introduction

The project presents a problem inspired by an online experiment performed by Netflix to grow

its business. Users browse for content on Netflix’s homepage, categorized into different

subcategories. One of the categories,“ Top picks for,” presents recommended content tailored
to a specific user. As Netflix users get overwhelmed by the number of choices offered to them,
they experience decision paralysis, which potentially causes users to lose interest and leave
Netflix not watching anything at all.

To solve this problem, a series of experiments were conducted to analyze the factors that
influence the browsing time of a user so that the factors can be optimized to improve the
browsing experience and help users land on their desired content as soon as possible while also
preserving the user engagement on their streaming platform. As part of this project, four factors
(Tile Size, Preview Length, Preview Type, and Match Score) are explored.

We perform experiments to evaluate the significance of the four design factors aiming to arrive
at an optimal combination of the design factors to observe the least browsing time.

We focus on Tile Size and Preview Type first, as they have less number of levels, while using
the whole range for the rest of the design factors. We leverage linear statistical models and
CCD-based response surface methodology design experiments to filter out non-significant
factors and reach an optimum combination. For each experiment, the relevant design factors
are set, and response data against each of the conditions is collected with the help of a web-
based response surface simulator.


## Experiments

We have a total of four factors to experiment with in our dataset. In this dataset, our response
variable is the Browsing Time that Netflix users spend when choosing what to watch, and we
have four design factors that we could experiment with, namely Match Score, Preview Length,
Tile Size, and Preview Type. Their region of operability is summarized as follows:

```
Factor            Region of Operability     Default Value
```
```
Tile Size         [0.1,0.5]                 0
```
```
Match Score       [0,100]                   95
```
```
Preview Length    [30,120]                  75
```
```
Preview Type      [TT,AC]                   TT
```
### Experiment 1: Investigating the Effect of Tile Size and Preview Type on Browsing Time
The first experiment's objective was to investigate the effect of the tile size and preview type
on the browsing time. For this experiment, the variable Match Score and Preview Length are
kept at default values, only the factor Tile Size varies from 0.1 to 0.5, and Preview Type is
chosen alternatively between TT and AC. Our metric of interest is the average browsing time,
and the experiment units are each Netflix user simulated by the web-based simulator. The
response variable is Browse Time for each viewer. The experiment unit is the viewer on the
website. A linear regression model is applied to the data using browsing time as the response
variable and the interaction between Tile Size and Preview Type as the predictor variable to
examine the significance of the interaction effect. The impact of main effects of Tile Size and
Preview Type is determined by analyzing the coefficients of the predictor variable.

Based on the coefficients table, the p-value of the t-test for the significance of Tile Size is quite
large, indicating that we can reject the null hypothesis and conclude that Tile Size is not
significant in our analysis. To further confirm this conclusion, we also conducted a partial F-
test. The p-value obtained from this test also supports our initial conclusion. Hence, we will
not include Tile Size in our subsequent optimization efforts. Another observation is that since
the coefficient of 'C(type)[T.TT]' is negative, it suggests that the TT preview type might lead
to shorter browsing time compared to other preview types, which we will further investigate.

### Experiment 2: Performing Central Composite Designs (CCD) on TT surface
From the first experiment, we would like to investigate the design factor further. Preview type
has a significant influence on the response variable Browse Time. So, eliminating a level for
design factor early can help reduce the conditions later in the experimentation journey. The
objective of the second experiment is to determine the significance of Preview Length and
Match Score and identify the optimal combination of these parameters on the TT response
surface. Because of the importance of Preview Type, we will conduct a CCD analysis at both
levels, starting with the TT surface, where Preview Type is set to TT. We start by considering
a full range of possible values for Preview Length (30 - 120 sec) and Match Score (0 - 100)
design factors. To find optimal values of these factors, a follow-up two-factor central
composite design was run to fit a second-order response surface model. The experiment intends
to perform axial conditions with $a = \sqrt{2}$. In the interest of defining experimental conditions
with practically convenient levels, they opted for $a$ as close to $\sqrt{2}$ as possible, yielding the
Preview Length and Match Score.
Contour plots of the fitted response surface are shown in the figure below.

The coefficients table shows that both Preview Length and Match Score are significant. The
stationary point for this second-order model is located (in coded units) at X 1 = - 4.5156 and
X 2 = 3.4678. In natural units, this corresponds to the Preview Length of - 60.4668 and Match
Score of 171.3736.
The optimal values of design factors Preview Length and Match Score fall outside the range of
the accepted values for this experimental design. This is likely due to the model unable to
capture the underlying relationship between the factors and the response, and the CCD method
doesn’t perform well in a large region. As we narrow the optimum level for the Preview type,
we repeat the CCD experiment with a shorter range of values and hence a smaller region for
the rest of the design factors. Since it is impossible to comment if a Preview type of TT leads
to an optimal condition based on a single experiment, we will repeat the experiment with a
Preview Type of AC and compare the results to determine which level minimizes browsing
time more effectively.

### Experiment 3: Perform Central Composite Designs (CCD) on AC surface
In the third experiment, we determine the most efficient combination of parameters on the AC
response surface. For this experiment, we used the same Match Score and Preview Length
levels as experiment 2, but this time we changed the level of Browsing Time to Actual Content.
We start by considering a full range of possible values for Preview Length (30 - 120 sec) and
Match Score (0 - 100) design factors. To determine the optimal values for the factors, we
conducted a follow-up two-factor central composite design (CCD) to fit a second-order
response surface model. The experiment utilized axial conditions with a value of $a = \sqrt{2}$. To
define practical experimental conditions, the value of $a$ was chosen to be as close to $\sqrt{2}$ as
possible, resulting in the Preview Length and Match Score values.
Contour plots of the fitted response surface are shown in the figure below.


The stationary point for this second-order model is located (in coded units) at X 1 = - 14.
and X 2 = 9.3044. In natural units, this corresponds to a Preview Length of -366.9622 and a
Match Score of 375.6545. We noticed that the optimal values for Preview Length and Match
Score lie outside the acceptable range for the factors. This is likely due to the relationship
between the factors needing to be fully captured by the model and the response and CCD
method not performing well over a large region. Thus, we will repeat CCD in a smaller region.
We also observe that using the same levels, having Preview Type equal to Teaser/Trailer
reduces Browsing Time more than Actual Content, so we proceed with Preview Type set to
Trailer/Teaser.

### Experiment 4: Perform Central Composite Designs (CCD) on TT surface (small range)
The response surface for the Preview Length and Match Score factors was analyzed for all
possible combinations of the two Preview Type levels. The results indicate that a more
miniature Browse Time can be expected on the TT surface compared to the AC surface.
Therefore, the next step is to conduct a CCD on the TT surface to optimize the response. Based
on the results of experiment 2, the CCD will be performed in a smaller region.

Hence, in the fourth experiment, we would investigate the optimum combination of Preview
Length and Match Score on the TT response surface. Experiment 2 suggested that the optimal
Preview Length is somewhere in the vicinity of 65 seconds, and the optimal Match Score is
somewhere in the vicinity of 75. To find the optimal values of these factors, a follow-up two-
factor central composite design was run to fit a second-order response surface model. The
experiment intends to perform axial conditions with $a = \sqrt{2}$. In the interest of defining
experimental conditions with practically convenient levels, they opted for $a$ as close to $\sqrt{2}$ as
possible, yielding the Preview Length and Match Score.

Contour plots of the fitted response surface are shown in the figure below.


The stationary point for this second-order model is located (in coded units) at X 1 = 9.4116 and
X 2 = - 3.4072. In natural units, this corresponds to the Preview Length of 159.1165 and Match
Score of 40.9272. The optimal value of Preview Length falls outside the range of the
experimental design; likely, the model being used needs to accurately capture the underlying
relationship between the factors and the response, and the CCD method needs to perform better
in a large region. So, we will do CCD one more time in a smaller region based on this
experiment.

### Experiment 5: Perform Central Composite Designs (CCD) on TT surface (tighter range)
The last experiment objective is still to determine the optimum combination of Preview
Length and Match Score on the TT response surface. According to the contour plots of
experiment 4, the optimal Preview Length is estimated to be around 75 seconds, and the
optimal Match Score is calculated to be around 70%. A follow-up CCD will be conducted in
a smaller region to ensure optimal combinations fall within the allowed range.

To determine the optimal values for the factors, a follow-up two-factor CCD was conducted to
fit a second-order response surface model. The experiment utilized axial conditions with a
value of $a = \sqrt{2}$. To define practical experimental conditions, the value of "a" was chosen to
be as close to $\sqrt{2}$ as possible, resulting in the Preview Length and Match Score values.

Contour plots of the fitted response surface are shown in the figure below.

The stationary point for this second-order model is located (in coded units) at X 1 = - 0.1365 and
X 2 = 0.6978. In natural units, this corresponds to the Preview Length of 74.6347 and Match
Score of 73.4890. The predicted Browse Time at this point is 10.1488, with a 95% prediction
interval of (9.9964, 10.3012). However, to comply with the requirement that the Preview
Length must be a multiple of 5 and the Match Score must be an integer, a slightly less optimal
but more practically feasible combination would be a Preview Length of 75 seconds and a
Match Score of 73. At this point, the predicted Browse Time is 10.1646, with a 95% prediction
interval of (10.0022, 10.3270).


## Conclusion

After conducting five experiments, we determined that the optimal settings to minimize
Browse Time are a Preview Length of 75, a Match Score of 73, and a Preview Type of TT. We
found that Tile Size has no impact on Browse Time, so we did not include it in our final
configuration. Our predicted Browse Time is 10.1646, with a 95% prediction interval of
(10.0022, 10.3270).

While five conditions were used to find and prove that Tile Size is insignificant, more
conditions would be ideal for providing stronger evidence. Additionally, we conducted CCD
experiments on different Preview Type surfaces directly. It would be beneficial to perform
screening experiments to identify which factors are significant. However, our approach was
still acceptable with only four factors. We also initially conducted CCD on a large region. Still,
it would be more efficient to use the steepest ascent/descent method to narrow the search region
before using CCD. However, this method would require a more significant number of
conditions. We are open to exploring other techniques and welcome feedback to improve our
optimization of Browse Time.
