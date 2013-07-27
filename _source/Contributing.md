---
layout: layout
title: Contributing to TestStack
---

For all of the TestStack projects, we're using Git for our version control, and [GitHub](https://github.com) as the central repo.

Why Git and GitHub? Git is the leading distributed version control systems. All DVCS are faster than the centralised systems like SVN or CVS. 

Why GitHub? The community around GitHub, including the fantastic service itself and the way they're embracing and encouraging open source software makes it ideal to work with.

If you need help Installing Git, you can use one of the following sources:

[https://help.github.com/articles/set-up-git](https://help.github.com/articles/set-up-git)  
[http://jake.ginnivan.net/setting-up-git](http://jake.ginnivan.net/setting-up-git) (includes setting up posh-git, a git helper in powershell)  

TestStack uses a technique often referred to as "GitHub Flow". This doesn't exclusively apply to GitHub or even Git, but this is the example we're giving.

Note, this is different to "Git Flow", and although many of the principles are the same, it's much much simpler.

# Step 1 - Fork the repository
![Contributing1](Contributing_images\Contributing1.png)

Once you have your fork, you are free to commit and do whatever you want on your fork. The next step is to *clone* your fork.

# Step 2 - Clone your fork
Open up your Git command line, then type `git clone <repourl>`, you can get the repo url from GitHub, on the right side under the menus, look for this

![Contributing2](Contributing_images\Contributing2.png)

Just click the copy button, then paste the repo url into the command line. So now you should have the repository cloned, next step is to make sure you can keep your repository up to date.

But first we need to change directories into our newly cloned repository. `cd <reponame>`

# Step 3 - Adding a remote
A convention in Github flow is to call the main repository `upstream`. So lets create an upstream remote

`git remote add upstream <masterrepository>`

Just like the step above, go back to the main repository then copy it's url and paste it into the console in place of `<masterrepository>`

To fetch new changes, just run `git fetch upstream`. This pulls all the branches from upstream down into your local repository, but DOES NOT CHANGE your working directory.

# Step 4 - Pick an Issue
Now you are all setup, you need to pick an issue! If you are just getting started, don't worry. All of TestStack projects will have a collection of 'Jump In' tasks, these are small tasks which are great for people wanting to knock something off quickly, or get started with the code base. Feed free to ask for help along the way!

![Contributing3](Contributing_images\Contributing3.png)

Once you have picked an issue, post to say you are working on this issue. Also if you end up not completing the work, PLEASE say you are no longer working on this issue, so someone else can pick it up.

# Step 5 - Start working
The next step is to start working. First things first, make sure your `master` branch is up to date.
**NOTE** Never commit to master, your master should always be clean. Keeping master clean will make everything much easier

`git checkout master`
`git pull upstream master`

Now our master is up to date, we can create a *feature branch*.

`git checkout -b Issue10` or `git checkout -b MyFeature`, whatever you want to call the branch

Now you can start working, try and keep your commits small. You don't have to be finished the feature to commit, as soon as you have hit any sort of logical checkpoint, commit.

## Committing
When you have changed files, you first have to *stage* your changes before they can be committed. You can do this with the `add` command.

To stage all adds (new files) and modifications, you can type `git add .` in the root of your repository. If you would like to include deletes as well, type `git add -A`, or you can stage files individually with `git add [filename]`, posh-git gives tab completion on files which is very handy.

Once you have staged your changes, commit them

`git commit -m "your commit message"`

# Step 6 - Submitting a pull request
Now we need to get your changes back into the main repository, this is done via a pull request. A pull request is exactly what the title says, it is a *request* to merge your changes into the repository. 
There are a number of things which will help make your pull request successful

 - Include tests - Unit Tests are important to make sure your code works
 - Discuss your changes before implementing them, if we don't know the changes are coming, it is hard to know why they need to be made
 - Keep your pull requests small, epic pull requests are difficult to review, and will take longer to be merged in

To submit your pull request, you need to push your branch up to your fork.

`git push origin BranchName` - pushes your feature branch to your fork. For example:

    C:\Users\Jake\_Code\TestStack.docs [ContributingDocs]> git push origin ContributingDocs
    Counting objects: 128, done.
    Delta compression using up to 4 threads.
    Compressing objects: 100% (110/110), done.
    Writing objects: 100% (126/126), 1.03 MiB | 0 bytes/s, done.
    Total 126 (delta 33), reused 0 (delta 0)
    To git@github.com:JakeGinnivan/TestStack.docs.git
     * [new branch]      ContributingDocs -> ContributingDocs

If you refresh your fork on github, you should see your new branch:

![Contributing4](Contributing_images\Contributing4.png)

Click Compare & pull request. Put a decent description, and reference any issues this pull request might be fixing by just typing #<issueNumber> or #15 in the comment box. Then click 'Send pull request`

![Contributing5](Contributing_images\Contributing5.png)

If you do not see a nice green merge button like this one:
![Contributing6](Contributing_images\Contributing6.png)
Then you likely have a merge conflict because your local branch has got behind the main repository.

You have two options

## Option 1 - Merge upstream (safest option)
Go back to the command line, and type `git fetch upstream`, then `git merge upstream/master`

This will merge the latest changes into your local branch, then you can `git push origin MyFeature` and your pull request will automatically be updated with your latest merge commit.

### Merge conflicts
If you get any merge conflicts, simply run `git mergetool`, then fix the issues. After you are done, stage any changes you have made, then commit the merge `git commit -m "merge upstream/master into FeatureName"

### Option 2 - Rebase onto upstream
Rebasing is rewriting history, ONLY do this if you are sure nobody has pulled your pull request down to review, or if you are unsure, post a comment. Rewriting history in git is powerful, but can be dangerous.

If you run the following commands:

`git fetch upstream`
`git rebase upstream/master`

If you hit a merge conflict, use `git mergetool` and stage the fixes same as above. Then you MUST run `git rebase --continue`, if you accidentally commit rather than continue the rebase you will be in a bad place.

Once your rebase has finished, it will look like your commits were done AFTER the latest changes on master.
If in doubt, use option 1 and merge :)