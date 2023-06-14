# Description

[Joao Neto](http://joaopn.github.io), 2023.

Welcome to the online materials for Network Science of Online Interactions at the University of Konstanz.

The course introduces Network Science as a means to analyze social networks at scale. It focuses on both the fundamentals of network analysis, and its application to social media. It aims to offer tools to understand how internet communities operate, and how users in those communities organize and interact. The platform Reddit will be primarily used as case study to develop theoretical and practical understanding of network analysis of online behavior and interaction structures.

Course materials will be based primarily on the book [“A First Course in Network Science”](https://cambridgeuniversitypress.github.io/FirstCourseNetworkScience/) by Menczer et al. In parallel to that, we'll have shorter talks touching on important topics that are useful for project development. 

# Location

The course will be held online on Zoom every Wednesday and Friday at 13h30. The link was sent by email, [message me](mailto:joao.pinheiro-neto@uni-konstanz.de) if you didn't get it.

# Course grading

The course is graded based on the final research project. It is split as
- 50% from the presentation
- 50% from a written report
- 10% extra by developing the project on Github,  publishing a notebook that can generate the figures shown in the report.

Check the project guide document for more details.

# Deadlines

- Project registration: **11/Jun/23**
- Project presentations: likely second week of September, TBD
- Project report deadline: likely third week of September, TBD

# Course content

**Fridays**: lectures following the book [“A First Course in Network Science” by Menczer et al](https://cambridgeuniversitypress.github.io/FirstCourseNetworkScience/).

**Wednesdays**: Discussion of selected book exercises + ~30 min presentation on a related topic.

**[Exercise sessions Youtube playlist](https://www.youtube.com/playlist?list=PLOOsHDVUMKcbUSzkXRJPQPXVjGW3zk_Nl)**

- **Fri, Apr 14:** [Chapter 0 - Introduction](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_0.pdf)

- **Wed, Apr 19:** [Python coding tools](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_0_exercises.pdf)

- **Fri, Apr 21:** [Chapter 1 - Network Elements](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_1.pdf)

- **Wed, Apr 26:** [Scientific Computing](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_1_exercises.pdf) - [(VIDEO)](https://www.youtube.com/watch?v=iWawqGdUZEc)

- **Fri, Apr 28:** [Chapter 2 - Small Worlds](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_2.pdf) 

- **Wed, May 3:** [Data gathering](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_2_exercises.pdf) - [(VIDEO)](https://www.youtube.com/watch?v=mkRa6Nrggtg)

- **Fri, May 5:** [Chapter 3 - Hubs](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_3.pdf)

- **Wed, May 10:** [A primer on Reddit part I + Power-law tutorial](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_3_exercises.pdf) - Notebooks: [Ex. 3.19](https://github.com/joaopn/teaching_networks_2023/blob/main/notebooks/exercise_3_19.ipynb), [Power-laws](https://github.com/joaopn/teaching_networks_2023/blob/main/notebooks/powerlaw_examples.ipynb)

- **Fri, May 12:** [Chapter 4 - Directions and Weights](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_4.pdf)

- **Wed, May 17:** [A primer on Reddit part II](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_4_exercises.pdf) - [(VIDEO)](https://www.youtube.com/watch?v=U9g06dTqRFA), [(Notebook)](https://github.com/joaopn/teaching_networks_2023/blob/main/notebooks/exercise_4.ipynb)

- **Fri, May 19:** SKIPPED

- **Wed, May 24:** [Chapter 5 - Network Models](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_5.pdf) - [(VIDEO)](https://www.youtube.com/watch?v=T43KzPnDURU), [(NOTEBOOK)](https://github.com/joaopn/teaching_networks_2023/blob/main/notebooks/chapter_5.ipynb) [(EXERCISES)](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_5_exercises.pdf), [(EXERCISES NOTEBOOK)](https://github.com/joaopn/teaching_networks_2023/blob/main/notebooks/exercises_5.ipynb)

- **Fri, May 26:** [Chapter 6 - Communities](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_6.pdf)

- **Wed, May 31:** [Descriptive vs Inference methods + Inorganic Communities on Reddit](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_6_exercises.pdf) - [(VIDEO)](https://www.youtube.com/watch?v=NBIc4rlz914), Exercises: [6.18](https://github.com/joaopn/teaching_networks_2023/blob/main/notebooks/exercise_6_18.ipynb), [6.20](https://github.com/joaopn/teaching_networks_2023/blob/main/notebooks/exercise_6_20.ipynb), [6.22](https://github.com/joaopn/teaching_networks_2023/blob/main/notebooks/exercise_6_22.ipynb)

- **Fri, Jun 2:** [Chapter 7 - Dynamics](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_7.pdf)

- **Wed, Jun 14:** [Handling large datasets/databases](https://github.com/joaopn/teaching_networks_2023/raw/main/lectures/lecture_7_exercises.pdf) - [(VIDEO)](https://www.youtube.com/watch?v=T-4elOUSAYM), [(EXERCISES NOTEBOOK)](https://github.com/joaopn/teaching_networks_2023/blob/main/notebooks/exercise_7_19.ipynb)

- **Fri, Jun 16:** Critical Phenomena on Networks

- **Wed, Jun 21:** Sampling bias and social media data

- **Fri, Jun 23:** Polarization Dynamics on Networks

- **Wed, Jun 28:** Depolarization mechanisms

- **Fri, Jun 30:** Scaling laws and Inequality in Social Media

- **Jul 5 and Jul 7**: free, can be used if needed.

# Resources

- Reddit full dataset (updated monthly): [Link](https://files.pushshift.io/reddit/)
- Reddit dataset separated by subreddit (top 20k subreddits, up to 12/2022): [Link](https://academictorrents.com/details/c398a571976c78d346c325bd75c47b82edf6124e)
- Package to analyze heavy-tailed distributions: [powerlaw](https://github.com/jeffalstott/powerlaw)
- [Podcast] Mason Porter on Community Detection and Data Topology: [Youtube](https://www.youtube.com/watch?v=mkh3oX3fRXk)
- [Talk] Opinion Models and Social Influence on Networks Mason Porter Department of Mathematics, UCLA: [Youtube](https://www.youtube.com/watch?v=pYXf1-_4ozo)