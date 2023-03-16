Hello Everyone!!

# MHC++ Intro to Git/GitHub Workshop

In this workshop we will be going over the basics of Git and Github for Source/Versioning Control. We will cover the basics of creating a repository, adding and ignoring files, and making commits and pull requests.

## Getting Started

### Prerequisites

- [Git-Scm](https://git-scm.com/download) (For Mac install [Brew](https://brew.sh) First) 
- Github Account

### Creating an SSH Key to Add to Your Github Account

Following the instructions [here](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/checking-for-existing-ssh-keys) to learn how to add an SSH key to your GitHub account and begin making commits.

### Creating a Repository

#### Starting from Scratch

The Github Docs are outstanding for trying to understand basic concept and [here](https://docs.github.com/en/enterprise/2.15/user/articles/create-a-repo) they go over how to create a repository.

#### Cloning a Repository

Once you have your SSH Key linked to your account, you can copy the SSH code of the repository you are going to work on and use

```
git clone git@github.com:<USERNAME>/<REPO>.git
```

to download a local copy of the repository for changes.

### Committing Your Changes

When you have started to work on the project, you will need to save your changes, but first it is imperative you make sure all local files are ignored.

#### Ignoring Files

As a rule of thumb, almost all repositories on GitHub should have a .gitignore file to ignore any sensitive, large, or unnecesary data. The general setup, if ignoring all log files, could look like:

```
*.log
```

For a full in-depth dive into .gitignore check out [this article](https://git-scm.com/docs/gitignore)

#### Staging and Pushing Your Commits

So now we have our changes ready to get uploaded, but how? This is a two step process consisting of Staging our Commits and Pushing them to GitHub.

First, we need to actually add files to our Commit

##### Adding Files to a Commit

This is made extremely simple where we can just say

```
git add .
```
to add all non-ignored files that were created, modified, or deleted.

or

```
git add <FILENAME>
```

to add a specific file.

##### Adding a Commit Message

Now that we added some files to the staging area, we are ready to get ready to upload. This is where we can actually commit our files and add a message by using

```
git commit -m "<MESSAGE>"
```

Yes, it is as simple as that!

##### Pushing our Changes to GitHub

If you cloned your repository, odds are you have a remote named `origin` already and you can simply type

```
git push origin master
```

However, you might not always have that luxury if it is your own repository from scratch. Here you need to add a remote.

###### Adding a Remote

To add a remote a.k.a a reference to the repository you are pushing to, you need the command

```
git remote add origin git@github.com:<USERNAME>/<REPOSITORY>.git
```

and now you can push.

### Creating Branches

When working on a large project with many people and/or many people, there will become a point where too many people are working on the same code-base and there will be [Merge Conflicts](http://atlassian.com/git/tutorials/using-branches/merge-conflicts). This is where having your own little place to work on isolated parts of the code is handy. These are called branches.

The default branch where the main source code will live, and where all major changes are applied is called the `master` branch. All other consecutive branches are whatever you decide to name them. If you are working on the Mail Server of a large application you might want to work in a branch called `mail-server`. In this branch, you will make sure it is up to date whenever a new commit is made to master by using

```
git pull
```	

to keep your code fresh--and since no one is working on that feature but you, none of your code will get messed with.

#### Creating a Branch

```
git checkout -B <BRANCH>
```

#### Switching to another Branch

If you accidentally just edited files locally on the master branch and you didn't commit yet, you will simply need to use

```
git checkout <BRANCH>

```

#### Pushing to Your Branch

Pushing to any branch is the same as always. You are just changing it in your command

```
git push <REMOTE> <BRANCH>
```

### Making a Pull Request

Ok, so now that we are working on separate branches, how does my Mail Server get into the main code on `master`? Well here is where the importance of [Pull Requests](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/about-pull-requests) come in.

A Pull Request allows for you to essentially ask someone else in another branch if they will accept your code into theirs. Usually, you will only be doing a Pull Request on the `master` branch to integrate a new feature into the main source. To do this you can follow the directions [here](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request).

Also, just an aside, this is where CI/CD (Continuous Integration/Continuous Development) come into handy in Agile environments because GitHub allows the use of bots and automated tests to allow you to test if a Pull Request may contain any code that could break the underlying main functions/characteristics of your application. This helps largely when you are working with CI/CD due to the large amount of changes always happening to the codebase on rolling updates.
