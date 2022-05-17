# From local to remote by terminal

### 1.

download github-cli

{% embed url="https://cli.github.com" %}

### 2.

```
mkdir <repo_name> && cd mproj

git init

touch README.md

git config user.name "Your Name"  
git config user.email something@example.com
git add .
git commit -m ":tada: start project"
git remote add origin https://<ghp_key>@github.com/<Username>/<repo_name>.git
git config --list

gh auth login
gh repo create <repo_name>

git push origin master
```
