Question: How to prune local tracking branches that do not exist on remote anymore?

```bash
git branch --no-color --merged master | grep -v "^\* " | xargs -n1 git branch -d
git fetch --prune && git branch -vv | awk '/: gone]/{print $1}' | xargs git branch -d
git fetch --prune && git branch -vv | egrep ": gone]" | awk '{print $1}' | xargs git branch -d

```
