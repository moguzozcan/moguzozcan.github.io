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


```bash
git filter-branch --index-filter "git rm -rf --cached --ignore-unmatch name_of_file" --prune-empty -- --all

rm -Rf .git/refs/original

git -c gc.reflogExpire=now gc --prune=all
```

My question at SO. [3]

[1] https://stackoverflow.com/questions/10622179/how-to-find-identify-large-files-commits-in-git-history/20609719

[2] https://help.github.com/articles/removing-sensitive-data-from-a-repository/

[3] https://stackoverflow.com/questions/47901271/git-filter-branch-tree-filter-not-deleting-the-file

[4] https://git-scm.com/docs/git-filter-branch#_checklist_for_shrinking_a_repository

[5]https://dalibornasevic.com/posts/2-permanently-remove-files-and-folders-from-git-repo

[6]https://gist.github.com/ariv3ra/16fd94e46345e62cfcbf

[7]https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History#The-Nuclear-Option:-filter-branch

[8]https://stackoverflow.com/questions/2100907/how-to-remove-delete-a-large-file-from-commit-history-in-git-repository

[9]https://readme.phys.ethz.ch/documentation/git_advanced_hints/

[10] https://stackoverflow.com/questions/11255802/after-deleting-a-binary-file-from-git-history-why-is-my-repository-still-large

[11] https://stackoverflow.com/questions/2116778/reduce-git-repository-size/2116892#2116892

[12]https://github.com/18F/C2/issues/439


Git find creator of the branch remote 

git for-each-ref --format='%(color:cyan)%(authordate:format:%m/%d/%Y %I:%M %p)    %(align:25,left)%(color:yellow)%(authorname)%(end) %(color:reset)%(refname:strip=3)' --sort=authordate refs/remotes

