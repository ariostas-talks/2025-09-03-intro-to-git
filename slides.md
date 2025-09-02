[comment]: # (This presentation was made with markdown-slides)
[comment]: # (Can be found here: https://gitlab.com/da_doomer/markdown-slides)
[comment]: # (Compile this presentation with the command below)
[comment]: # (mdslides slides.md)

[comment]: # (Set the theme:)
[comment]: # (THEME = white)
[comment]: # (CODE_THEME = github)

[comment]: # (controls: true)
[comment]: # (keyboard: true)
[comment]: # (markdown: { smartypants: true })
[comment]: # (hash: false)
[comment]: # (respondToHashChanges: false)

## Intro to `git`

<br/>

### Andres Rios Tascon

HSF/IRIS-HEP Software Basics Training 2025

[comment]: # (!!!)

## Motivation

We've all had to deal with keeping track of the changes we or other people make to some document or code.

[comment]: # (||| data-auto-animate)

## Motivation

The old school way of dealing with this (e.g. `mythesis_v1.tex`, `mythesis_v2.tex`, `mythesis_final.tex`) is bad.

- Lots of clutter.
- Hard to know what changed at each step.
- Parallel changes are a nightmare.
- Collaboration with others is agonizing.
- Undoing changes can be painful.

[comment]: # (||| data-auto-animate)

## Motivation

This is where version control systems come in. By far the most popular one is `git`. It is very easy to use and it provides very powerful features.

From the survey you filled out, we saw that a good fraction of you have already used it before, but most of you don't feel confident using it. The goal for today is for you to get a solid foundation.

[comment]: # (||| data-auto-animate)

## Motivation

With `git` you will be able to:
- Keep track of not just files, but entire projects.
- Know who, what, when and why things were modified.
- Collaborate with others and easily merge changes.
- Be able to work on multiple things at a time without any clutter.

Caveat: it works best for text-based files.

[comment]: # (!!! data-auto-animate)

## A brief history of `git`

`git` was originally created by Linus Torvalds (the same guy who made Linux). The initial version only took him 10 days to write.

The design is very simple. You could make your own simple git client with about 500 lines of Python. See tutorial [here](https://benhoyt.com/writings/pygit/).

[comment]: # (!!! data-auto-animate)

## How `git` works

`git` keeps track of the history using a directed acyclic graph (DAG).

Each node is called a **commit** and it records what changed (not the entire contents of the file). It also, has information about who did it and when, and a message discribing the changes.

It can have **branches** with different commits, and they can be merged, as we'll see later on.

[comment]: # (||| data-auto-animate)

## How `git` works

 <img src="https://raw.githubusercontent.com/ariostas-talks/refs/heads/main/images/DAG_example.png" alt="git dag" width="500">

[comment]: # (!!! data-auto-animate)

## Setting up `git`

The very first time you use `git`, there is a couple of basic configuration commands that you need.

```bash [2|3]
# --global means that it will apply to all repositories
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

This info will be used in your commits.

[comment]: # (||| data-auto-animate)

## Setting up `git`

A couple of notes about privacy/safety:

- If you don't want people on GitHub seeing your email, you can use `ID+username@users.noreply.github.com`. You can find yours in the [email settings](https://github.com/settings/emails) on GitHub.
- Nothing stops other people from using your email in their commits. If you're concerned about proving the legitimacy of your commits, you can sign your commits with a cryptographic key. Instructions [here](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification).

[comment]: # (||| data-auto-animate)

## Setting up `git`

There's plenty of configuration options, but we won't go into them.

One that might be important is the editor configuration. By default, `git` uses `vim` when needed. If you are not familiar with `vim`, I would recommend changing this setting to use `nano` instead.

```bash
git config --global core.editor "nano -w"
```

In the long term, it's better to learn `vim` since it's very powerful and you'll find it everywhere.

[comment]: # (!!! data-auto-animate)

## Let's start using `git`!

Let's create a repository, add a file, and commit it.

Let's create a repository to keep track of our recipes.

We'll learn about:
- `git init`
- `git status`
- `git add`
- `git commit`

[comment]: # (!!! data-auto-animate)

## Looking back in time

`git` allows us to look back and time and see how our files were. It's like an unlimited undo button, but without discarding the changes we have made.

We'll learn about:
- `git log`
- `git checkout`
- `git diff`

[comment]: # (!!! data-auto-animate)

## Tagging commits

We can tag commits with an easy to remember string so that we can look back at them without having to memorize the hash.

We'll learn about:
- `git tag`

[comment]: # (!!! data-auto-animate)

## Ignoring certain files

We often want to ignore certain files in our repository so that we don't accidentally commit them.

For example, if you're working with Jupyter notebooks, you'll want `git` to ignore the `.ipynb_checkpoints` directory.

We can do this with the `.gitignore` file.

[comment]: # (!!! data-auto-animate)

## Fixing mistakes we made

There are a few different ways to fix mistakes, depending on what kind of mistake it was.

[comment]: # (||| data-auto-animate)

## Fixing mistakes we made

Fix the commit message of the previous commit.

`git commit --amend`

[comment]: # (||| data-auto-animate)

## Fixing mistakes we made

Restore the state of a file we edited.

`git restore`

[comment]: # (||| data-auto-animate)

## Fixing mistakes we made

Reverting the changes made by a previous commit.

`git revert`

[comment]: # (||| data-auto-animate)

## Fixing mistakes we made

Reset the status of the entire repository or entirely remove commits.

`git reset`

Note: If you have already pushed your changes to GitHub, you will need to force-push. It might be fine for feature branches, but not recommended for `main` unless absolutely needed.

[comment]: # (||| data-auto-animate)

Completely remove files from the `git` history.

`git filter-branch` or `git filter-repo`

Only use in dire situations were you added something earlier on that absolutely cannot be there. This completely rewrites `git` history.

[comment]: # (!!! data-auto-animate)

## A fork in the road

Now let's spice things up by adding more branches to our repository.

We'll learn about:
- `git branch`
- `git switch`

[comment]: # (!!! data-auto-animate)

## Bringing changes together

When we have multiple branches and we want to bring the changes together, we have a few different options. We'll go through each of them to see how they work.

[comment]: # (||| data-auto-animate)

## Bringing changes together

Bring a single commit or a range of commits from a different branch.

`git cherry-pick`

[comment]: # (||| data-auto-animate)

## Bringing changes together

Merge the changes from another branch (the standard way).

`git merge`

This is what most people use, and it's the default option on GitHub. For complex projects, this can actually create a messy history, so I personally would recomment avoiding it.

[comment]: # (||| data-auto-animate)

## Bringing changes together

Bringing all commits from another branch and attaching them at the head of your branch.

`git rebase`

This mantains a linear git history, so it makes it easier to for example see where bugs were introduced.

[comment]: # (||| data-auto-animate)

## Bringing changes together

Merging the changes from another branch into a single "squashed" commit.

`git merge --squash`

It again mantains a linear history, and additionally, hides intermediate commits from the other branch, which are often not important. This is my preferred option.

[comment]: # (!!! data-auto-animate)

## Merge conflicts

When two branches have changes in the same part of a file, there is a merge conflict since `git` doesn't know which of the changes we want to keep.

[comment]: # (!!! data-auto-animate)

## Collaborating with others

Now let's look how we can collaborate with others. `git` is a decentralized version control system, so it allows each person to have their own independent repository, and provides tools to sync with others.

We'll look at GitHub for `git` hosting today, but there's also GitLab, Bitbucket, Gitea, and others.

[comment]: # (!!! data-auto-animate)

## Creating a repo on GitHub

Let's now see how to create a GitHub repository and push our commits.

Before we do so, we need a bit of configuration to set up SSH keys. See instructions [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

We'll learn about:
- `git push`
- `git pull`
- `git fetch`

[comment]: # (!!! data-auto-animate)

## Some more advanced topics

(if case we have time)

[comment]: # (!!! data-auto-animate)

## Including another repo inside your repo

This can be useful when you have different projects that you want to keep separate, but one depends on the other. You can include the dependency as a "submodule".

We'll learn about:
- `git submodule`

[comment]: # (||| data-auto-animate)

## Including another repo inside your repo

When you clone a repo that has a submodule, you need
```bash
git clone --recurse-submodules [link]
```
Or if you already cloned it and you want to initialize the submodules
```bash
git submodule update --init
```

[comment]: # (!!! data-auto-animate)

## Finding where a bug was introduced

Sometimes it is hard to figure out where a bug was introduced just from commit message, or even from diffs when the bug is sibtle enough. In these cases you can perform a binary search using

`git bisect`

We'll see how to manually run it, and how to automate the process. Let's use [this repo](https://github.com/ariostas-talks/2025-06-18-git-bisect-example) as an example.

[comment]: # (!!! data-auto-animate)

There's a ton more functionality that `git` offers, but with the tools you learned today you should comfortable deal with almost any project that you'll run into.
