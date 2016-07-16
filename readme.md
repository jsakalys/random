Two ways to add a feature branch to a production master when working off a forked copy of a project!

Note: In this guide, I refer to the project master as the 'production' master. This may not always be the case, but I use the term 'production' master to differentiate it from your local master, which may or may not have the current project master's code on it.


##Easy Way:

1. Go to your master and pull down most recent production version: `git pull upstream master` OR `git pull origin master` if you are the owner of the production copy. This updates your master to the current version of the production copy.

2. Create your new feature branch by branching off of your master: `git checkout -b my-feature`. This keeps your master copy clean, so that you are free to mess around with it on your new branch.

3. Make some changes and then add and commit your code to your feature branch. Run `git add .`, `git commit -m "committed"`. This saves all changes to your LOCAL machine. Meaning the machine you are currently working on.

4. Push your code to the remote (github server's) machine so that github has a copy of your local changes. `git push` OR `git push origin my-feature`. Now your changes are accessible online through your github account.

5. Note: If you haven't created a remote copy on github's server, you will need to run the command `git push --set-upstream origin my-feature` OR shorthand `git push -u origin my-feature`.

6. Time to merge! Go to the github address of the production copy of master. Create a pull request that compares the production copy master to your feature branch. Now the git master can approve (or deny) your changes and choose to merge them into the production copy. DONE!

## Slightly more involved but better Way

1. Follow steps 1-4 to create a feature branch both locally and remotely.

2. Before making a pull request, go back to your master branch to make sure you have the most recent production copy: `git checkout master`. Now, pull down the latest copy: `git pull upstream master` OR `git pull origin master` if you are the owner of the production copy.

3. Now that you have the most current production copy in your master branch, go back to your feature branch to apply those changes. `git checkout my-feature`, followed by `git merge master`. Why do this, you ask? Remember when you branched off of master to make your feature branch originally? When you did that, you brought over the version of master that was living on that branch *at the time*. Because your new feature is sitting on master code that is probably outdated, it's a good idea to merge in the most recent production version to check your new code against it. You might need to deal with conflicts here, but will save your git master a bunch of headache.

4. After merging the current production master into your feature-branch, you can rest assured knowing that your new code is compatible with the current production copy. Add and commit your changes to your feature branch by running `git add .` and then `git commit -m 'merged in master'`.

5. Now, push your feature branch to github `git push` OR `git push origin my-feature`

6. All ready to merge! Go to the github address of the production copy of master. Create a pull request that compares the production copy's master branch to your feature branch. Now the git master can approve (or deny) your changes and choose to merge them into the production copy. DONE!