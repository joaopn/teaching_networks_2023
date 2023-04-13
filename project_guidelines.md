# Project guideline

(based on [this guide](https://github.com/dgarcia-eu/FoundationsOfCSS-TUGraz/blob/master/Projects_Guidance/ProjectsGuide.md))

The course will be graded based on the development of a final course project. Projects can be developed in groups of **three people maximum**, or individually. The purpose of the project is to apply the insights and techniques developed during the course to the social media platform [Reddit](http://www.reddit.com). Projects should start from a research question, and be developed in a data-driven manner. While the main methods should involve the ones developed during the course, participants should think critically about their applicability and limitations. 

The timeline of the project deadlines can be found below. 

- Project registration: **11/Jun/23**
- Project presentations: likely second week of September, TBD
- Project report deadline: likely third week of September, TBD

You can get guidance for your project by [email appointment](mailto:joao.pinheiro-neto@uni-konstanz.de). 

The steps to do the course project are the following:

#### 1. Form a group and choose a topic
Groups up to 3 people are possible. While the deadline to register the project is quite far ahead, and after the book content has been presented, we recommend start thinking about it early. In particular, after the lectures on **May 10** and **May 17th** you should have an idea of the platform, and what is possible with the Reddit data.

#### 2. Project registration
Your group has to register your project as a **plain text** email to [joao.pinheiro-neto@uni-konstanz.de](mailto:joao.pinheiro-neto@uni-konstanz.de) by the mentioned deadline. A project registration is a short text that includes the following:

1) Project title
2) Names and email addresses of group members
3) Research question(s)
4) Planned data usage and analysis to address the questions

**Invest time on designing carefully your project registration:** once registered, you cannot change the research questions or project topic. You can later adapt steps in the planned data retrieval and analysis, but your final report has to argue why and justify the changes. The registration needs to be concise but detailed enough to allow a reader to judge if you followed those steps when reading the report.

#### 3. Submit the final report

Send a final report as a PDF document (max. 6 pages, min. font size 11pt) via email.
References do not count towards this 6-page limit. Projects can contain a link to a Github repository including the code and data to produce results, and additional figures or tables that can be referenced from the project report. Data 

Project reports should follow this structure:

1. Motivation: What question(s) do you seek to answer and why?
2. Data retrieval and cleaning: Explain the interfaces or resources you used to collect all data necessary for the project (pushshift dumps, API, Reddit API, etc). Explain what extra steps you utilized to clean the data, removing bad entries.
3. Data processing: Explain how you filtered data, normalized values, computed additional variables, etc.
4. Analysis: Perform statistical analyses and visualizations that assess the question(s).
5. Conclusion: Evaluate answers to the question and their reliability.
6. Critique: Identify limitations and alternative explanations for your results.

Plots should be correctly shown (named axes, visible scales) and writing has to be understandable. The motivation part is very important. Argue why your project is relevant and what we can learn about human behaviour on online platforms from it.

Be careful with statistics in the analysis part. Use the methods covered in the course to assess the uncertainty of your answers and comment on these results in the conclusion part. The critique part is essential. An important objective of this course is to develop a critical understanding of the opportunities and limitations of the data and methods we will use.

## Project grading

The grade for the project is composed of 50% for the presentation and 50% for the final report. Extra points (10%) are given when projects are based on open science principles (e.g. data and codes are available in a Github repository). **Projects do not need to report "positive results",** what is important is that you show how your have addressed your research questions, document any issues or deviations, and critically reflect on methods and results. 

## Examples of project topics

#### Replicating a previous paper

You can select a previous paper and take the same question and methods used in the paper. You don't need to do the exact same thing, but the question can be the same. Much of research on Reddit uses datasets that are much older and smaller than what we currently have access to, and thus your results may differ. This is a good thing!

A good source to start your search is the review paper [The Anatomy of Reddit: An Overview of Academic Research](https://arxiv.org/abs/1810.10881). A good companion practical guide is [New Data Sources in Social Science Research: Things to Know Before Working With Reddit Data](https://journals.sagepub.com/doi/abs/10.1177/0894439319893305). Another useful resource is this meta-analysis of Reddit papers: [Studying Reddit: A Systematic Overview of Disciplines, Approaches, Methods, and Ethics](https://doi.org/10.1177/20563051211019004). Below a list of data-driven papers that in principle can be reproduced:

- [From Reddit to Wall Street: The Role of Committed Minorities in Financial Collective Action](http:/arxiv.org/abs/2107.07361) (2021)
	- Analysis of wallstreetbets during the GME short squeeze.

- [Identifying Social Roles in Reddit Using Network Structure](https://doi.org/10.1145/2567948.2579231) (2014)
	- Claims the existence of social roles such as "answer people" within Reddit
	- Claims that users usually keep to one community

- [No Echo in the Chambers of Political Interactions on Reddit’](https://doi.org/10.1038/s41598-021-81531-x) (2021)
	- Claims that political interactions on Reddit do not occur in echo chambers.

- [Political Bias and Factualness in News Sharing across More than 100,000 Online Communities](https://arxiv.org/abs/2102.08537) (2021)
	- Analyses factualness of link-sharing across many subreddits. Claims that "bad content" is concentrated on an extremely small fraction of communities.

- [Evolution of Reddit: From the Front Page of the Internet to a Self-referential Community?](https://arxiv.org/abs/1402.1386) (2014)
	- Claims that Reddit is increasingly self-referential.

**If your group decides to replicate one of the papers above, drop me an email so we can coordinate to not have multiple groups doing the same paper.**

#### Idea basket

Due to the way Reddit is structured, interesting research questions can be tackled at different scales: users, posts and subreddits. Below are some examples of questions at those scales:
- Do users mostly keep to one subreddit, or contribute to many? How does that vary in different thematic corners of Reddit?
- In some particular community/topic you possess expert knowledge in, how do interaction networks and discussion tree structure differ from that of other, bigger subreddits? Do these differences make sense in light of the specifics of the topic?
- Interactions on Reddit are known to be mostly anonymous. Is that true in small subreddits? How does the community structure of user networks in small subreddits looks like? 
- How the statistics of the discussion tree structure varies between subreddits? Can it be related to the content of the subreddit? (ref. to the lecture on May 24th, Detecting inorganic dynamics in Social Media). 


## Frequently asked questions

- **Can we change the question or project topic?**
Only before you register your project. Your project registration has to include your question and you cannot change it afterwards. If you have problems regarding methods or data, you should document that in your project report, but not change the question because of that.

- **What if some dataset or method turns out to work differently than we planned?**
This can always happen and there is no problem with changing some plans about the data retrieval or analysis, as long as you document these well in your report and argue about the changes. What you cannot change is the question and motivation of your project or do arbitrary, unjustified changes to the plan.

- **What if we don't get "nice" results or don't fit our expectations?**
As long as you followed your plan, the particular results that you get will not factor into the grade. If you get a negative result or a surprising answer, comment on that in the conclusion section and reflect on it in your critique section. Follow our recommendations and feedback during the course and comment on them in your report if some reason you couldn't follow them.