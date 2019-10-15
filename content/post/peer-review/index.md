---
title: 'Peer Review is Broken: Editor Version!'
subtitle: 'Nowhere to go :rocket:'
summary: 
authors:
- admin
tags: ["replication", "reproducible research", "peer review", "quasi-experiments"]
categories:
date: "2019-10-15T00:00:00Z"
lastmod: "2019-10-15T00:00:00Z"
featured: false
markup: mmark
draft: true

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  placement: 1
  caption: 'Image credit: [**XKCD**](https://xkcd.com/2025/)'
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
## I.

This week I saw an interesting [paper](http://www.nber.org/papers/w26364) published by NBER by D. Mark Anderson, Kyutaro Matsuzawa, and Joseph J. Sabia (an ungated version is posted on Anderson's [website](http://www.dmarkanderson.com/AMS_Marriage_Equality_Teen_Suicide_Attempts_October_3_2019v3.pdf)) about the impact of marriage equality laws on youth suicide risk. 

Obviously, this paper is interesting in it's own right: Marriage equality laws may have plausible impacts on mental health, especially among marginalized populations, and Anderson et al. also argue that there could be some potential negative consequences for mental health due to political backlash. Thus designing a study to evaluate the impact of legislation on youth suicide piqued my interest.

As it turns out, it seems that Anderson et al. also had *their* interest piqued by a previous paper on this topic, which was published in *JAMA Pediatrics*. They start by 

> A recent article published by Raifman et al. (2017) produces the first empirical evidence on the relationship between SSM legalization and youth mental health. Using data from the State Youth Risk Behavior Surveys (YRBS) for the period 1999-2015, Raifman et al. (2017) find that legalization is associated with a 0.6 percentage-point (7 percent) decline in self-reported suicide attempts among all high school students, and a 4 percentage-point (14 percent) decline in suicide attempts among those who identified as LGBQ relative to suicide attempts among heterosexual-identifying youth.

Hey...wait a minute...something seems familiar here...Oh yeah! I know that paper! In fact, I *reviewed* the Raifman (2017) paper for *JAMA Pediatrics* a couple of years ago:

![](jp-email.png)

Well. This is indeed interesting. Let's see where it goes...

> While there is much to admire about the pioneering efforts of Raifman et al. (2017), we believe their conclusions deserve closer scrutiny for a number of reasons...

Ohhhh, now I think I see what's going on. They make a few arguments regarding limitations of the Raifman paper, which I think can be read for free [here](https://jamanetwork.com/journals/jamapediatrics/fullarticle/2604258)

## II.
Next, they try and replicate the findings of Raifman et al. (2017). I won't digress too much here, except to say that it may come as little surprise to anyone that *JAMA Pediatrics* does not require (or ask) authors to post either datasets or code that would help to facilitate straightforward computational replication. However, the data are public and the design is relatively straightforward, and Raifman et al. were pretty clear about what they did. Here is what Anderson et al. found when they tried to replicate:

> In column (1) of Table 3, we attempt to replicate the original findings of Raifman et al. (2017). Following Raifman et al. (2017), we estimate equation (1), adjusting standard errors for clustering at the state-by-grade level and weighting regressions using the State YRBS-provided sampling weights. As discussed above, clustering at the state-by-grade level may lead to standard errors that are too small and the State YRBS weights are not designed to be comparable across states or even within states over time. Based on this specification, we find that SSM laws are associated with a 0.66 percentage point decrease in suicide attempts among U.S. high school students. This estimate is statistically distinguishable from zero at the 5 percent level and is nearly identical to the estimate reported in Raifman et al. (2017).

*Nearly identical* estimates seems pretty great, and of course this really helps Anderson et al. make their case for how other kinds of choices may have impacted the Raifman et al. results. 

Now here is the part that got me going:

> In column (2), we correct the standard errors by adjusting them for clustering them at the level of policy variation (i.e., the state). This adjustment results in a 56 percent increase in the estimated standard error, rendering the estimate statistically indistinguishable from zero at conventional levels.

So, they find that the standard errors are sensitive to whether they are clustered at the state vs. the state-grade level. In terms of point estimates and 95% confidence intervals, here are those estimates from Anderson et al.:

| Level of clustering | Estimate (percentage points)  | 95%CI |
| ------------- | ------------- | ------------- | 
| State, grade | -0.66 | -1.2, -0.1  |
| State | -0.66  | -1.5, 0.2  |

Now, there is, of course, a larger discussion to be had about how we should feel about the difference between those two estimates. Anderson et al. focus on the new results being "statistically indistiguishingable" from the zero. If one wanted to, one could obtain the analogous [p-values](https://www.bmj.com/content/343/bmj.d2304) for these estimates, and I'm sure readers won't be surprised where that would lead. 


In fact, I tried to login to the JAMA Pediatrics site to retrieve my review and see how the paper was handled, and there is not only no record of my review, they don't even have me in the system as a peer reviewer!

![](jp-gone.png)

What the hell kind of clown show is going on here?!

At the risk of revealing both my parts of the review and, in retrospect, things I wish I might have said, I'll just highlight a couple of points I made in my review on October 6:

> 10. p9. “We estimated linear models rather than logit models due to their unbiased estimation properties with fixed effects analyses. We accounted for the complex survey design of the YRBSS by using Taylor series linearization to estimate standard errors.” I don't have a big problem with using a linear probability model, but stickler's might ask the authors to at least see whether similar results would be obtained using logistic models with marginal effects (does not have to be reported, but if these are different, it should be further investigated). However, it is obvious that the standard error for such a model is wrong, which is why these models must use robust/sandwich type standard errors (see Angrist/Pischke's book or Cameron/Miller J Hum Res on this). I guess my question is whether the Taylor series standard errors also account for heteroskedasticity as would the sandwich type errors?

This was primarily about needing to use a robust standard error for their model, which (I am pretty sure) must be done if you want to use a linear model instead of logistic for a binary outcome. I tried to give them and will note only in passing that the first version of the manuscript

> 11. More importantly, do the Taylor series standard errors adjust for clustering and potential serial correlation by state? I think they do, but this is an important issue in DD analysis (see the Bertrand paper already cited). I see now in the footnote to Table 2 that SEs were clustered “school and by classroom.” Cameron and Miller (J Hum Res 2015) discuss this situation in particular: “At the minimum, one should cluster at the level of the primary sampling unit though often there is reason to cluster at a broader level, such as clustering on state if regressors and errors are correlated within state.” Because it seems very likely that in the YRBS data for suicide attempts errors are correlated within state and, at a minimum, the authors should also cluster standard errors at the state level in a sensitivity analysis, though my preference would be to do this for the main analysis.


Now my first instinct is to feel.



What **does** frustrate me is that I made this exact same argument in my review and told the authors that they should be clustering at the state level rather than the state-class level. 

This is where I now start to feel frustrated as a peer reviewer. One of the primary

## III.
The purpose of this post isn't to comment specifically about the substantive. On one hand, I can see this as a good example of a well-designed replication paper. Anderson et al. found "much to admire" in Raifman et al. (2017), but also believed the results deserved to be further interrogated. Plus, they attempt to *advance* the evidence further by including more post-treatment data and taking advantage of a new potential source of exogenous variation. All good. 

It's also important to say that NBER papers are *not* peer-reviewed and I'm sure Anderson et al.'s paper will also benefit from the scrutiny of the peer review process. I just hope that the peer reviewers who use their limited time to provide this crucial activity, **free-of-charge**, have their reports faithfully considered by editors when making judgements about the paper's merits. 



[Research waste](https://www.thelancet.com/series/research) is a huge problem in biomedical research, and of course one 



My question, for all you counterfactualists out there, is what do you think *would* have happened to this paper had the authors clustered the standard errors at the state level?




