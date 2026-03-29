Here's my process so far ...

```
tg init
tg migrate-beads

# now lets 
# if your AGENTS is *just* beads
git rm AGENTS.md

git rm .beads

cd .git/hooks
# again assumes you only had beads in here. otherwise you will have more work ...
rm pre-commit post-merge post-merge.backup prepare-commit-msg pre-commit.backup post-checkout pre-pus


git add .taskgraph
git add AGENTS.md .beads

git commit -m "tg: migrate from beads to taskgraph"
```
