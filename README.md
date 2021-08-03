# ohw21-intro-activity

A quick introduction to git (and each other) for OHW 21 - in person.

## Resources

-   [Git](https://oceanhackweek.github.io/ohw-resources/prep/git/)
-   [GitHub](https://oceanhackweek.github.io/ohw-resources/prep/github/)

## Create an issue

-   Create an issue 'Introduce YOUR NAME'. In that issue add a checklist of tasks to complete. You can copy the example below:

```plain
- [x] Create an issue of tasks to introduce myself
- [ ] Fork repo
- [ ] Clone repo to JupyterHub
- [ ] Checkout a branch
- [ ] Add an introduction file for yourself
- [ ] Push to your fork
- [ ] Make a pull request
- [ ] Review someone else's pull request (and say hello!)
- [ ] Merge your pull request after it's been reviewed
- [ ] Checkout the main branch
- [ ] Add an upstream remote
- [ ] Pull upstream changes into your fork
- [ ] Close this issue
```

## Fork the repo

Git is a distributed version control system, so instead of everyone working on the same repo, we fork the repository into our own GitHub account. 
This is the first step of making sure that we don't cause unintentional conflicts with changes that other people are making.

## Clone fork to JupyterHub

In your fork, you'll see a green **Code** button. Click that and it will give you a link that you can copy to clone the repository.

Then in a JupyterLab, launch a terminal and run `git clone GITHUB FORK LINK`. You'll see some output similar to:

```zsh
➜ git clone https://github.com/YOUR_USER/ohw21-intro-activity.git
Cloning into 'ohw21-intro-activity'...
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (5/5), done.
```

When that finishes, you'll have a new folder named `ohw21-intro-activity`.

Let's change to that directory with `cd ohw21-intro-activity`.

## Creating a branch

Branches are the second major way to avoid conflicts in git. While you are now on the `main` branch of your fork, there is also a `main` branch in the original (or upstream) repository.
If we switch to another branch then we reduce the likelihood of any conflicts, and choosing a good branch name is part of that.

```zsh
➜ git branch YOUR_BRANCH_NAME
```

Will create a new branch, but if you run `git status` it will show that you are still on the `main` branch.

```zsh
➜ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

To change that, you need to run `git checkout YOUR_BRANCH_NAME`.

You can also combine the two steps into a single one with `git checkout -b YOUR_BRANCH_NAME` which will create and checkout the branch in a single operation (this is the one that I use all the time).

## Create your introduction

Within the folder, create a markdown file with your github handle as it's name. For instance, mine would be `abkfenris.md`.

Within that file, write a quick introduction about yourself, maybe your name, where you're from, what institution/organization you are a part of, and how about your favorite flavor of ice cream (or if you don't like ice cream, how about favorite dessert).

## Commit your introduction

Now we need to commit your introduction.

When you're working on code, you may be making changes to many different files at once.
If you choose a single point in time, then not all files may have the right changes to work appropriately with each other.

Git takes care of this with commits, which you can think of as multiple file saves, where you can also choose exactly which files (or even which lines get included).
Adding a file to a commit is called staging it.

If you run `git status` it will now tell you that there are some changes.

```zsh
➜ git status
On branch YOUR_BRANCH_NAME
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	added:   YOUR_GITHUB_HANDLE.md

no changes added to commit (use "git add" and/or "git commit -a")
```

Now we can run `git add YOUR_GITHUB_HANDLE.md` to stage your introduction.

And if we run `git status` again:

```zsh
➜ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	added:   YOUR_GITHUB_HANDLE.md
```

Now we can see that git understands that we want to include our introduction file in our next commit.

Then to make the commit itself, write \`git commit -m "YOUR SUMMARY OF THE CONTENTS OF THE COMMIT HERE

MORE DETAILS CAN FOLLOW ON FURTHER LINES WITHIN THE QUOTES"

One nice thing about GitHub is that you can [reference an issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword) by number in a commit message, such as 'Closes #42' or 'Works on #42' which will connect the commit and the later pull request to the issue (and the issue back to them).

## Push to your fork

Now to share our awesome introduction, we need to push our commit back up to our fork.

Usually once a branch is established on GitHub, we can push to it with `git push`, but because the branch doesn't exist yet, we need to let git know what remote branch we want it to be.

For that we use `git push --set-upstream origin YOUR_BRANCH_NAME`, though if you `git push` it should warn you about that.

At this point git will also get cranky because of authentication.
Instead of including all those details here, [here is a link to GitHub's auth info](https://docs.github.com/en/get-started/quickstart/set-up-git).

## Make a Pull Request

Now if you go to your fork on GitHub, you should be able to select branches and see yours, and it will probably have a yellow alert asking if you want to make a pull request (or PR) from the branch you just pushed, which we do!

Click the Pull Request button in the alert.

You'll see that GitHub has helpfully taken the contents of your commit message and used it to fill in the pull request message.
Add any details that you may want to let any reviewers know about, and create the pull request.

## Review a Pull Request

Now that you've created a pull request of your own, lets go and review someone else's PR.

Go to the PR tab, and find another PR.

Click on the Files Changed tab and you can see the introduction that someone else made.

If you select a line, you can make a comment just about that line (or group of lines), otherwise click Review, and say hello and welcome!

Notice when you are writing a review, you can either Approve, Request Changes, or Comment, which are used to let folks know if you think their PR is ready to be merged.

We should Approve each others PRs.

## Merge PR

Once you've gotten a review and fancy green Approval checkmark on your PR, feel free to merge it!

## Get upstream changes

Now lets get other peoples introductions into our fork.

If we go back to our fork, we should see a ['Fetch upstream' button](https://github.blog/changelog/2021-05-06-sync-an-out-of-date-branch-of-a-fork-from-the-web/), which will bring our fork back into sync.

## Switch to `main`

Now that our fork is back in sync, let's get those changes locally.

To do that we need to check out the `main` branch again.

`git checkout main`

Notice that you haven't seen other peoples intros show up, to see those you will need to `git pull` to pull the changes from `main` on your fork locally.

Now you should have other people's introductions!
