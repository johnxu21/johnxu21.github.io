---
layout: page
title: Projects
permalink: /evol/projects/
---


<a href="/evol/projects/" target="_self"><img src="/images/logo.jpeg" alt="Evol Logo" style="width:450px;height:174px;" align="right"></a> <br><br>


# EVOL Research Projects
Below are some of our current and past projects<br> <br>




# Current Projects

### PaReco

<table>

<tr>
<td>  
	
<p align="justify" style="max-width:800px">

Re-using whole repositories as a starting point for new projects is often done by maintaining a variant fork parallel to the original.
      However, the common artifacts between both are not always kept up to date.
      As a result, patches are not optimally integrated across the two repositories, which may lead to sub-optimal maintenance between the variant and the original project.
      A bug existing in both repositories can be patched in one but not the other (we see this as a missed opportunity) or it can be manually patched in both probably by different developers (we see this as effort duplication).
      In this paper we present a tool (named  PaReco) which relies on clone detection to mine cases of missed opportunity and effort duplication from a pool of patches.
      We analyzed 364 (source->target) variant pairs with 8,323 patches resulting in a curated dataset containing 1,116 cases of effort duplication and 1,008 cases of missed opportunities.
      We achieve a precision of 91%, recall of 80%, accuracy of 88%, and F1-score of 85%.
      Furthermore, we investigated the time interval between patches and found out that, on average, missed patches in the target variants have been introduced in the source variants 52 weeks earlier.
      Consequently, PaReco can be used to manage variability in ``time'' by automatically identifying interesting patches in later project releases to be backported to supported earlier releases.</p>
</td>
	<td > <a href="/images/fse_image.jpeg" target="_blank"><img src="/images/fse_image.jpeg" alt="FSE 2022" style="width:300px;height:165px;" align="right"></a></td>

</tr>

</table>


### Variant Forks - Motivations and Impediments

<table>

<tr>
<td>  
	
<p align="justify" style="max-width:800px">

Social coding platforms centered around git provide explicit facilities to share code between projects: 
forks, pull requests, cherry-picking, to name but a few. Variant forks are an interesting phenomenon in that respect, 
as they permit different projects to co-exist peacefully yet explicitly acknowledge the common ancestry. 
Several researchers analyzed forking practices on open source platforms and observed that variant forks get 
created frequently. 
However, little is known about the motivations for launching such a variant fork. Is it mainly technical 
(e.g., diverging features), governance (e.g., diverging interests), legal (e.g., diverging licenses), 
or do other factors come into play? We report the results of an exploratory qualitative analysis on the 
motivations behind creating and maintaining variant forks. We surveyed 105 maintainers of different active 
open-source variant projects hosted on GitHub. Our study extends previous findings, identifying several 
fine-grained common motivations for launching a variant fork and listing concrete impediments for 
maintaining the co-existing projects.
</p>
</td>
	<td > <a href="/images/sankey.jpeg" target="_blank"><img src="/images/sankey.jpeg" alt="SANER2022" style="width:300px;height:104px;" align="right"></a></td>

</tr>

</table>

### Reuse and Maintenance Practices among Divergent Forks

<table>

<tr>
<td>  
	
<p align="justify" style="max-width:800px">

With the rise of social coding platforms that rely on distributed version control systems, software reuse 
is also on the rise. Many software developers leverage this reuse by creating variants through forking, 
to account for different customer needs, markets, or environments. Forked variants then form a so-called 
software family; they share a common code base and are maintained in parallel by same or different 
developers. As such, software families can easily arise within software ecosystems, which are large 
collections of interdependent software components maintained by communities of collaborating contributors. 
However, little is known about the existence and characteristics of such families within ecosystems, 
especially about their maintenance practices. Improving our empirical understanding of such families 
will help build better tools for maintaining and evolving such families. We empirically explore 
maintenance practices in such fork-based software families within ecosystems of open-source software. 
Our focus is on three of the largest software ecosystems existence today: Android, .NET, and JavaScript. 
We identify and analyze software families that are maintained together and that exist both on the official 
distribution platform (Google play, nuget, and npm) as well as on GitHub , allowing us to analyze reuse 
practices in depth. We mine and identify 38 software families, 526 software families, and 8,837 software 
families from the ecosystems of Android, .NET, and JavaScript, to study their characteristics and 
code-propagation practices. We provide scripts for analyzing code integration within our families. 
Interestingly, our results show that there is little code integration across the studied software 
families from the three ecosystems. Our studied families also show that techniques of direct integration 
using git outside of GitHub is more commonly used than GitHub pull requests. Overall, we hope to raise 
awareness about the existence of software families within larger ecosystems of software, calling for 
further research and better tools support to effectively maintain and evolve them.
</p>
</td>
	<td > <a href="/images/emse2020.jpeg" target="_blank"><img src="/images/emse2020.jpeg" alt="EMSE 2022" style="width:300px;height:127px;" align="right"></a></td>

</tr>

</table>

