# Workflow Introductions

Welcome to MRover Software! Use this repository to "git" the hang of using Git. Just keep following this README!

By the end of this quick tutorial, you will have:
* cloned this repo
* made a branch
* added a file
* made a commit
* opened a Pull Request (PR)
* and merged code!

## Clone the Repository

Before you can clone this repository, you'll need to [set up ssh keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) if you haven't done so. Don't skip over the options and links at the top of the page!

Now, click the green box at the top of this page that says 'code,' make sure 'ssh' is selected, and copy the link to your clipboard. In your terminal:

(remember: '#' means something is just a helpful comment. Enter the commands that come after '$')

    # Navigate to the directory where you want to clone this repo.
    # (ideally somewhere that's not inside another git repo!)
    # For example:
    $ cd ~

    # Clone the repo:
    $ git clone git@github.com:umrover/workflow-intros.git

    $ cd workflow-intros
    $ git status
    ... on branch master ...

If you see 'on branch master,' you've successfully cloned the repo!

## Make a Commit on a New Branch

You're on branch master, but it's not good practice to make your changes here. Instead, make a new branch:

    # When you see <...> in this context, that typically means you should replace that
    # phrase, including the '<' and '>'.
    $ git checkout -b <initials>/intro-branch  # example: git checkout -b cat/intro-branch

There should be an introductions/ folder. Make a new file in it and call it your name:

    $ touch introductions/<FirstLast>.txt  # example: touch introductions/CameronTressler.txt

Now, edit the file and include following information:
 * Your name, pronouns, year in school, and major
 * A sentence or two describing your previous programming experience
 * A few sentences describing what you enjoy doing outside of school and rover

You can do this either from the terminal, with vim or nano, or from a standard editor like VSCode.

    $ vim introductions/<FirstLast>.txt

When you're done editing, you can run `git status` and the file name should appear in red text. Add it to git:

    $ git add introductions/<FirstLast>.txt

If you run `git status` again, the file name should have turned green. Now make a commit with a helpful message:

    $ git commit -m "Create <FirstLast>.txt"

Finally, push your commit to the remote repository hosted on GitHub:

    $ git push origin <initials>/intro-branch

## Make a Pull Request

A pull request (PR) is a request to merge code from one branch into another. Rather than doing this locally in the terminal like most Git operations, this is done through Github in your browser.

Your goal is to merge your new branch, `<initials>/intro-branch`, into `master`. First, make sure your branch was successfully pushed to the remote repository on Github. To do this, go to the [workflow-intro's main page](https://github.com/umrover/workflow-intros), and look for a drop down menu that currently says `master`. Click on the drop down, and search through the branch names until you find your own. If you see this, you're in luck!

There are multiple ways to actually create the PR, but the most reliable is as follows:

 1. From [workflow-intro's main page](https://github.com/umrover/workflow-intros), switch to the 'Pull requests' tab near the top of the page.
 2. Click the green button that says 'New pull request.'
 3. This will give you options for a 'base' branch and a 'compare' branch. The 'base' branch should be `master` because `master` is the branch you are merging *into*. The 'compare' branch should be the new branch that you pushed to the remote repo in the steps above. This will allow you to see exactly what changes your new branch would add to `master`.
 4. Ideally, some green text should show up, saying 'Able to merge.' Now click the green button that says 'Create pull request.' In future PRs, you may not get the confirmation saying 'Able to merge' because there are conflicts between changes on your branch and master. This is okay -- you can still create the PR and fix the conflicts afterwards.
 5. Make sure the editable text box has a reasonable message that accurately sums up your changes.
 6. Decide who should review the PR and add them by searching for them on the right hand side. Who should review a PR is highly dependent on the changes you're making, but keep in mind it's generally best to add too many people rather than too few. For this PR, add Cameron Tressler, Ashwin Gupta if you are going to work on auton, a subteam lead, and at least one other software member (preferably someone who has never reviewed a PR).
 7. Finally, create the pull request!

## Merge Your Changes
If you closed the tab and need to get back to it, you should be able to again go to the 'pull requests' tab for the repo and find yours among the list.

Once a PR has been approved by all reviewers, press the green button that says 'Merge pull request.'

This will bring up a set of boxes that you can edit. TODO: figure out exactly what message formatting we want here.