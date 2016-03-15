# The Learn CLI Workflow

## Overview

The deep integration of Learn, git, and GitHub makes it possible for all of the work you do on Learn to be stored and version-controlled by GitHub behind the scenes, just like professional software.

We'll eventually introduce you to all of the git mechanics that make this work. But for the purposes of getting started on Learn quickly, we've created some convenient tools to make it easier to move through our curriculum.

You'll use the same workflow to solve every lab on Learn. It involves 3 steps:

1. Opening the lab.
2. Working on the lab until you get all tests to pass.
3. Submitting your solution.

Let's walk through the process. For now, just read along. **You don't need to actually perform any actions right now**. You'll have the opportunity to practice this entire workflow in the next lesson!

## TL;DR

Learn provides wrappers for common interactions between git and the Learn platform in the form of `learn`, `learn submit`, and `learn-test`. Windows users can only use the last command.

If you'd rather dig deep and perform these interactions yourself, here's what you need to do:

- Fork the lab on GitHub and clone your fork locally
- Run tests (`learn-test` or `ant test`)
- Write your code
- When tests pass, commit your changes, push them to your GitHub, and open a pull request to the upstream repository (the repo that you forked from)

For a more detailed overview, read on.

## Prefatory Remark for Windows Users

Whenever we refer to "opening a terminal", you should open Git Bash, which was installed during the initial setup lesson. Git Bash emulates a Unix-y environment on your Windows machine, meaning that as long as you're programming in this terminal, you can basically follow along with everything we're doing here. Pretty sweet!

![git bash](http://curriculum-content.s3.amazonaws.com/javacs/git_bash.png)

## Opening a Lab

**Fork and clone a lab to get started**

Getting to work on a new lab is very simple: you'll want to click the "Fork" button on the `learn-co-students` repository, fork a copy to your personal GitHub, and clone from your fork.

The "Fork" button should look something like this:
![Fork button](http://curriculum-content.s3.amazonaws.com/javacs/fork_button.png)

Then `git clone git@github.com:your-usernmame/the-forked-repo.git`

You can then `cd the-forked-repo` to change your current directory to your local repository.

## Solving a Lab

** Key takeaway: use the `learn-test` command to run tests until they all pass. **

### Overview

Once you've opened your lab locally, you'll be ready to start solving it. This is the fun part!

All of the labs on Learn are written with an RSpec test suite that you can use to confirm that you've fulfilled the requirements of the lab. RSpec is a testing library that ruby developers use everyday, so again, as you work on Learn, you're also learning the same tools and workflows that developers use.

## Test Driven Workflow

When you work on a lab, we recommend the following workflow:

### 1. Reading the README

Read the lab's README on Learn and get a sense of what the lab is about and what it is asking you to build. Read the entire README and then work on the lab. That way, as you hit hurdles you'll have a context for where to look for clues and hints in the README.

### 2. Run the tests with `learn-test`

Before doing any work, run the test suite from your local clone with the `learn-test` CLI command. From your terminal, in a lab's directory, run `learn-test`, you'll see something similar to:

![test](http://curriculum-content.s3.amazonaws.com/javacs/test_command.png)

We know error messages or failure messages are intimidating, but try to read them. Developers are detectives, constantly sleuthing for the bug that's the culprit. Errors and failures are our clues, they illuminate the path forward.

We know that the idea of "things being broken" is frightening at first. Broken things are stressful and frustrating! But guess what? As an engineer, as a programmer, the default state of anything you work on is broken. The things you are programming are always broken. Get used to it. Your job is to fix broken things. You can do it. If your code isn't broken, if your code works, you are no longer programming. Your job is done. Things work. Embrace the errors. The obstacle is the way.

### 3. Read the tests

Read the test suite in `src/`. (It should be right next to the source classes.)

Beyond all the syntax and code, can you decipher what we're asking for? What the lab requires you to do? How the test works?

### 4. Write Your Code

After forking and cloning the lab, opening the lab in a text editor, reading the README, running the test suite, reading the errors, and reading the tests themselves, you're ready to code. You've armed yourself with every weapon available in the arsenal of your intellect and we know you can program triumphantly.

You should understand the point of the lab.

You should be able to identify the objectives and topics the lab is exercising so you can google for more information.

You should know the expected behavior or outcome of the solution.

You should know what files you need to create or edit.

You should know what those files and code should define, provide, and do.

You should constantly save and test your code with every significant change.

You should read error messages and glean insight into the solution with every new failure.

You should keep on trying until you get it working. It doesn't matter how many times you fail as long as it is one less than the times you tried.

You should ask for help on Learn.

Programming is never about getting it all right at once. Programming is like solving a puzzle, you don't try to put it together immediately, you approach it one piece at a time. The workflow we're describing optimizes this process, trial and error, attempts and feedback, insight through failure. Most of our time as programmers is spent staring at error message and code wondering, "Hmm".

#### Programming in Movies vs Real Life
<iframe src="https://vine.co/v/hPXTA6l9AqQ/embed/simple" width="600" height="600" frameborder="0"></iframe>

### 5. Pass your local tests with `learn-test`

Eventually your local tests will pass and Learn will indicate your success.
![Pass](https://s3-us-west-2.amazonaws.com/curriculum-content/intro-to-learn/learn_workflow_local.png)

On the left is a passing test run in the terminal. On the right is what the right column in Learn looks like for a passing local test (which we currently call a "Local Build").

When your local tests are passing, you'll be ready to submit the lab.

## Submitting a Lab

### On Linux and OS X

Windows users, please follow the steps under [What does `learn submit` do?](#what-does-learn-submit-do) below.

**Key takeaway: use the `learn submit` command to submit your solution.**

Once you've written the code that solves a lab, and confirmed that your solution is correct using the `learn-test` command, you then need to submit your solution to Learn so that you can get credit for completion and move on to the next lesson.

In order to submit your solution to Learn, from the lab's directory in your Terminal, you will just need to run:

```bash
learn submit
```

That's all it takes, you can run `learn submit` from any lab directory and your solution will be submitted to Learn for review.

![learn submit](http://learn-co-videos.s3.amazonaws.com/learn-co-orientation/learn-submit-cli-osx.gif)

You'll notice that on Learn, the light labelled "Pull Request" will turn green when your code has been submitted.

![PR](https://s3-us-west-2.amazonaws.com/curriculum-content/intro-to-learn/learn_workflow_pr.png)

## What does `learn submit` do?

The `learn submit` and the Learn CLI automate all the low-level `git` interactions. When you type `learn submit`, here's what happens:

1. Your local changes are staged via `git add .` and committed via `git commit -am`.
2. Your local commits are pushed to your fork on GitHub with `git push`
3. A Pull Request from your fork is opened.

^ Windows users (and anyone who'd rather have greater control over their submissions), follow these instructions.

## Conclusion

To summarize, the workflow you'll be using to solve labs on Learn:

Fork and clone the lab locally so you can work on it.
Use `learn-test` to run your local tests.
Use `learn submit` to submit your solution. (On Windows, you'll need to open a pull request manually. It's good practice for *nix users too!)

You are now ready to practice the Learn workflow with your first lab! Congratulations!

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/learn-workflow-java-cs'>Learn Workflow</a> on Learn.co and start learning to code for free.</p>
