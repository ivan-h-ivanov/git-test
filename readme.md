#  Git pull
__"git pull"__ is __"git fetch"__ and then __"git merge/rebase"__
## Branch is behind
(src/master-behind)  
git pull  
git pull --rebase  
git pull --no-ff  

## Branch has diverged from origin
(src/master-diverge)  
git pull --ff-only  
git pull  
git pull --rebase  
git pull --squash  
git pull --no-commit  

## Branch has diverged from origin with conflicts
(src/master-diverge-conflict)  
git pull  
git pull --rebase  
git pull -X ours  
git pull --rebase -X theirs  
(these 2 depend on strategy -s, might not be available if -s is set explicitly)

# I just want to...
(tips about everyday situations, where solution might no be that obvious)  

## ...ditch my local copy of {branch}
git reset --hard origin/{branch}  

## ...squash {number} of commits of my branch / ...remove unwanted commits from my branch
git rebase -i hotfix  
git rebase -i HEAD~{number}  
"git reset --soft HEAD~{number}" and then "git commit"  
(this is the worst options)  

## ...push part of my branch to hotfix, but keep WIP commits out of it
"git cherry-pick" in a third branch, then "git rebase -i"  

## ...restore my deleted local commit / unpushed {branch}" (git branch -D {branch})
"git reflog" and then "git reset --hard {SHA}"  

## ...restore my deleted remote {branch} (git push origin -d {branch})
(repeat the upper one if the local branch is also deleted)  
git push  

## ...authenticate to both org repos and external repos withot juggling auth methods
[Add a SSH key in github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account), authorize it with org  
edit ~/.bash_profile and [add a script to run it on bash start](https://stackoverflow.com/questions/18404272/running-ssh-agent-when-starting-git-bash-on-windows)