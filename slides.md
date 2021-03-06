---
subtitle: "Go to next slide"
output: ioslides_presentation
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE)
```

## GitHub flow + RStudio

_Mauro Lepore_

--

Repo: <http://bit.ly/github-demo>  
Slides: <http://bit.ly/github-berlin>  

--

### Set up issues?

* Use https://rstudio.cloud, or
* just watch and ask at the end.



# License

Creative Commons Attribution-ShareAlike 4.0 International  
http://creativecommons.org/licenses/by-sa/4.0

--

Many images and ideas come from  
https://jennybc.github.io/wtf-2019-rsc/



## Why Git/GitHub?

<div class="columns-2">
<img src="https://i.imgur.com/MBv5IJQ.jpg" align="center" width=325/>

<img src="https://i.imgur.com/uORi6QZ.png" align="center" width=325/>
</div>

[Excuse me, do you have a moment to talk about version control?](https://peerj.com/preprints/3159/)



## Outline | Part 1

1. [Why Git**Hub** flow -- not Git flow?](https://githubflow.github.io/)

1. GitHub flow from GitHub:
    * [Contributor issues](https://github.com/maurolepore/github-demo/issues?q=is%3Aopen+is%3Aissue+label%3Acontributor+sort%3Acreated-asc+label%3Aberlin+label%3Agithub-flow_via-github).
    * [Maintainer issues](https://github.com/maurolepore/github-demo/issues?q=is%3Aopen+is%3Aissue+sort%3Acreated-asc+label%3Aberlin+label%3Agithub-flow_via-github+label%3Amaintainer).

1. Recap: [Understanding the GitHub flow](https://guides.github.com/introduction/flow/).

1. Questions



## Outline | Part 2

1. GitHub flow via RStudio:
    * Happy Git with R: [Fork and clone](https://happygitwithr.com/fork-and-clone.html).
    * Happy Git with R: [Get upstream changes for a fork](https://happygitwithr.com/upstream-changes.html).

1. Questions / Discussion, e.g.:
    * [Git clients](https://github.com/2DegreesInvesting/resources/issues/5).
    * usethis package: [Pull request helpers](https://usethis.r-lib.org/articles/articles/pr-functions.html).



# Appendix



## What is a commit?

<img src="https://i.imgur.com/fmrhQOQ.png" align="center" width=760/>

## What is a commit?

<img src="https://i.imgur.com/zizuprp.png" align="center" width=760/>

## What is a commit?

<img src="https://i.imgur.com/5MiM5RC.png" align="center" width=760/>

## What is a commit?

<img src="https://i.imgur.com/m230nzj.png" align="center" width=760/>

## What is a commit?

<img src="https://i.imgur.com/ZKksnVi.png" align="center" width=760/>

## What is a commit?

<img src="https://i.imgur.com/PAgI3mX.png" align="center" width=760/>

## What is a commit?

<img src="https://i.imgur.com/1nOkjOu.png" align="center" width=760/>

## What is a commit?

<img src="https://i.imgur.com/AoxcNpK.png" align="center" width=760/>

## What is a commit?

<img src="https://i.imgur.com/Gcv7fZU.png" align="center" width=760/>

## What is a commit?

<img src="https://i.imgur.com/HS2tUli.png" align="center" width=760/>

## What is a commit?

<img src="https://i.imgur.com/OPuzdBA.png" align="center" width=760/>

# Installation

<https://happygitwithr.com/workshops.html#pre-workshop-set-up>



# Git configuration

In R

```R
usethis::edit_git_config()
```

In the terminal

```bash
git config --global -l

git config --global user.email "maurolepore@gmail.com"
git config --global user.name "maurolepore"

core.editor=notepad
push.default=current
pull.ff=only
```

[Cache credentials](https://happygitwithr.com/credential-caching.html#credential-caching)



# RStudio & terminal

## 

<img src="https://i.imgur.com/spQyR4r.png" align="center" width=760/>

```bash
git checkout -b 57_add-full-url

git push -u origin 57_add-full-url
# Or
git config --global push.default "current"
git push
```

## 

<img src="https://i.imgur.com/lXTXDTB.png" align="center" width=760/>

```bash
git add .
git commit -m "Add full URLs (closes #57)"
```

## 

<img src="https://i.imgur.com/FLT3de1.png" align="center" width=760/>

```bash
git commit --amend -m "Agregar URLs completos (closes #57)"
```

## 

<img src="https://i.imgur.com/b2Cvwmt.png" align="center" width=760/>

```bash
git reset --hard
```

## 

<img src="https://i.imgur.com/5Xs2YEy.png" align="center" width=760/>

```bash
git checkout master
```

## 

<img src="https://i.imgur.com/3fW3rwe.png" align="center" width=760/>

```bash
# Agregar el remoto "upstream"
git remote add upstream git@github.com:maurolepore/fgeo.plot.git
```



# Terminal

## 

```bash
git fetch upstream
git checkout master
git rebase upstream/master
```

[Alternative](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)

## 

```bash
# reset ~1 commit
# reset ~2 commits
# reset ~n commits
git reset HEAD~1
```

## 

```bash
# ~1 revert ~1 commit
# --no-edit for auto message
git revert HEAD~1 --no-edit

# Revert commit with SHA a867f483
git revert a867f483 --no-edit
```

## 

```bash
# Cherry pick commit 63da5bb3
git cherry-pick 63da5bb3
```

## 

```bash
# Local
git branch -d a-branch
# Local, force
git branch -D a-branch

# From remote origin
git push -d origin a-branch

# From remote upstream
git push -d upstream a-branch
```

## 

```bash
# ~3 manipulate ~3 commits
git rebase -i HEAD~3

# Commands:
# p, pick = use commit
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# ...
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
```

```bash
git rebase --abort
git commit --amend -m "New commit message"
git rebase --continue
```

<https://about.gitlab.com/2018/06/07/keeping-git-commit-history-clean/>

