<h1>Recovering Lost Commits with git reflog and reset</h1>
<p>Checkout to the branch i.e the one you have force pushed</p>
  git checkout force-pushed-branch
<p> Do git reflog </p>
git reflog
<p>Identify the commit SHA(not branch checkout SHA) that is just before the force push commit</p>

<p>cf42fa2... HEAD@{84}: checkout: moving to master</p>
<p>73b9363... HEAD@{85}: commit: Force update master_automation.</p>
<p>6a3458o... HEAD@{86}: checkout: Moving from master to master_automation</p>
<p>547cc1b... HEAD@{86}: commit: Deploy to effectif.com web server.</p>
<p>1dc3298... HEAD@{87}: commit: Updated the theme.</p>

Force updated commit SHA is 73b9363 which shows branch state after force push

Here the SHA is 547cc1b which indicates the normal state of branch master_automation just before force push

Now perform git hard reset to the above SHA
git reset --hard 547cc1b

Now force push your branch which is affected by force push to go back to the previous normal state
git push origin force-pushed-branch -f

Now navigate to branch in GitHub you can see the commits that you have lost

Thats it..!!! Now your lost commits are back
