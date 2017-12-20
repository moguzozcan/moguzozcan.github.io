---
layout: post
title: "Git filter-branch experience"
date: 2017-12-20
---

In our project, two of our collegues mistakenly pushed big files into our repository. One of them was a huge debian package, which was
around 750 MB size and one jar file which was around 50 MB size. So, our .git folder was around 1 GB size. Although we delete those files
by in those branches and pushed again, they stay in the .git folder to keep history. They do not exist in any of the braches now, but git
stores them for backup under ".git\objects" folder. So, I've made some search to overcome this problem and I found out series of commands 
I need to run. Firstly, I needed to find which 



https://help.github.com/articles/removing-sensitive-data-from-a-repository/
