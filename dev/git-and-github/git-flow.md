# Git flow

## Install

```bash
sudo apt-get install git-flow
git fetch --all
git flow init
```

## Reset

```bash
git config --remove-section "gitflow.path"
git config --remove-section "gitflow.prefix"
git config --remove-section "gitflow.branch"

git flow init
```

## Flow example

{% embed url="https://deepsource.io/blog/git-branch-naming-conventions" %}

{% embed url="https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow" %}

### start

```
git flow feature start 7220-add-button
// code
```

### merge

```
// git fetch <remote> <src>:<dst>
git fetch origin develop:develop
git flow feature finish 7220-add-button
```

## Sync feature with develop

{% embed url="https://hemanshubhojak.com/2016/06/09/keeping-feature-branch-insync-with-develop.html" %}
