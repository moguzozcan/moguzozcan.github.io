---
layout: post
title: "Git filter-branch experience"
date: 2017-12-20
---

In our project, two of our collegues mistakenly pushed big files into our repository. One of them was a huge debian package, which was
around 750 MB size and one jar file which was around 50 MB size. So, our .git folder was around 1 GB size. Although we delete those files
by in those branches and pushed again, they stay in the .git folder to keep history. They do not exist in any of the braches now, but git
stores them for backup under ".git\objects" folder. So, I've made some search to overcome this problem and I found out series of commands 
I need to run. Firstly, I needed to find which files causes these huge size. I looked into StackOverflow and found the following two 
scripts. First one lists the first 10 big files among your all objects. [1] But the problem of this script was, it does not give the exact size of the objects. I looked over some of them and most of them was around 3-5 MB. 

```bash 
git rev-list --objects --all | grep "$(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -10 | awk '{print$1}')"
```

So, I searched for a better script and in the same question, there was a really good script. Which lists all the files in size and shows
some detail information. With the help of this script I was be able to detect the two files causing the problem. 

```bash
git rev-list --objects --all \
| git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' \
| awk '/^blob/ {print substr($0,6)}' \
| sort --numeric-sort --key=2 \
| cut --complement --characters=13-40 \
| numfmt --field=2 --to=iec-i --suffix=B --padding=7 --round=nearest
```

Now, the following step is to delete those folder and apply them in all branches. For that, I used 

[1] https://stackoverflow.com/questions/10622179/how-to-find-identify-large-files-commits-in-git-history/20609719

https://help.github.com/articles/removing-sensitive-data-from-a-repository/
