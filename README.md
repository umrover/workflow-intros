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
