# Version Control Exercise
Note: This tutorial is based on the EECS 280 Git Tutorial from Lab 0. All credit goes to James Juett and Zachary Goldston for designing the original lab.

Before beginning this exercise, we recommend going through the main README in the `workflow-intros` repository, to get some basic exposure to git. 

For the purposes of these exercises, we recommend you work in groups of 2-3 to go through this tutorial. This way, you and your group will gain a basic understanding of Git Workflow and handling code changes across different remotes/computers. For the purposes of this tutorial, we will assume a group of 3, but feel free to adjust roles to the number of people in your group.

## Initial Steps

All group members should verify `git` is properly installed via the command `git --version` to check in your terminal. Additionally, all group members should configure their git profile, if not done yet. You can do this by running the two commands:

    git config --global user.name "username"
    git config --global user.email "youremail"

(Replace the `username` and `youremail` parts with the GitHub username and email you plan to use when working on MRover! Note that we do not use Michigan's GitLab server)

Everyone in the group should sign into their GitHub account they plan to use with the MRover team, if they have not done already.

Person 1 should create a new repository on GitHub.  From here, Person 1 should ensure the following when creating the new project:
* Name it `mrover-vc-exercise`
* Set it to private, for the purposes of this exercise.
* Select the "Add a README file" option

Once Person 1 has created the repository, the next step is to add the other members of the group. Click on the three dots towards the right of the newly created repository page, select "Settings," then "Collaborators," and then "Add people." You will want to add them via username, assuming everyone in the group has made a GitHub account. Once done, you have all access to your **remote repository**, where you can put your exercise code that lives "in the cloud."

To actually work on the code, you will need to **clone** the remote repository to create a **local repository** on your own computer.
 1. Open a terminal and navigate to a folder. We recommend making one called `mrover` to store all the work you'll be doing with us.
 2. Run the following command (replace `zwgold` with the username of the person who had created the remote repository): `git clone git@github.com:zwgold/mrover-vc-exercise.git` (Note: This command only will work when you have SSH Keys set up. Please follow the steps in the first tutorial to do so!)
 3. Enter your username and password was prompted, though setting up

This should create a new folder called `mrover-vc-exercise`. That is your **local repository**.


## Making a basic change
At this point, everyone should have a new directory for the **local repository** called `mrover-vc-exercise`. Navigate your terminals into that folder using `cd`. You can check that you are in the right place with the command `pwd`. 

Everyone run `git status`. We'll run this frequently, and you should make a habit of it - it's a
good way to check the state of your local repository. You should see that you are up-to-date with
`origin/main` (the "origin" refers to the remote repository on gitlab).

Run `ls`. You should also see the default `README.md` file that GitLab created automatically with
the project. Feel free to go ahead and open the file in your IDE. (You could also just open the
whole folder in your IDE.)

`README.md` contains a bunch of project startup suggestions from GitLab. You'll also notice that
the raw text of the file is in a lightweight markup language called [Markdown](https://www.markdownguide.org/basic-syntax/).

Person 2 should edit their copy of the file to remove most everything and replace it with a simple list of your group members. For instance:

    # mrover-vc-exercise
    Our members in our group are Zachary Goldston, Cameron Tressler, and Ashwin Gupta.

**Make sure to save the file with your changes. (Here and any time you make changes!)**

Everyone run `git status`. Person 2, who had made the changes, should see there are changes to `README.md`.

### Contributing New Changes
Person 2 should continue to lead for this section. Others should follow along.

 1. Run `git add README.md`. This **stages** the changes so they can be committed.
 2. Run `git status`. That file is now staged and ready to be committed.
 3. Run `git commit -m "modify readme"`. This **commits** the chnages to your **local repository**. You can think of each commit in the repository as a step along the version
history of your code. The `-m` adds a note about what the commit does.
 4. Run `git status`. Your **local repository** is a step ahead of the **remote repository**.
 5. Run `git push`. You may need to enter your GitHub username/password.
 6. Run `git status`. Everything at this point should be in sync again.

Now, everyone check out the repository on GitHub's website. The changes should now be there!

## Pulling Changes
**Everyone except the person who ran the commands in the last step** should run `git status`. `git` running on your local machine has no idea about the changes that are now on GitHub. You need to manually tell it to
check in with the remote.
 1. Run `git fetch`. This fetches information from the remote repository to update your local repository. Run `git status` again - you're 1 commit behind `origin/main`.
 2. Check your `README.md` file. It hasn't changed yet. Your computer knows there are
 changes to origin/main that are ahead of your main, but it hasn't applied them.
 3. Run `git merge`. This merges the changes and actually updates your files to match.

Everyone's local `README.md` should be up-to-date. If you've got it open in an IDE or other editor, it's possible you might need to somehow refresh the file or close and reopen it.

Instead of the two steps above, you could have also used **`git pull`**. This is a shortcut for a
fetch followed immediately by a merge.

### Working on Separate Files
Make sure everyone is up-to-date via `git status` and has the updated `README.md` file before moving on. If something goes wrong or you get stuck, check in with your lab staff!

Person 2 and Person 3. should lead for this section. Others should follow along. Both of them should create a new file. Make sure to create files with different names, like `person2.txt` and `person3.txt`. Put some text in the files and make sure to save.
Now, Person 2 should contribute their new file via the normal process (add, commit, push). For
example, let's say you had created `person2.txt`. You would run:

    git add person2.txt
    git commit -m "create person 2 file"
    git push

Next, Person 3 should attempt the same. Everything works up until the push, where you'll get an error message. (Go ahead and try, so you can see the message.) That's because git does not allow you to push if you're not up-to-date with the remote. We can fix this.

## Reconciling Diverged Branches via Merging
To handle diverging branches, we will perform a "merge commit." With Person 2 having successfully pushed, but Person 3 unable to do so, we will need to resolve this. We can do this with the following steps:

 1. Person 3 should run `git fetch`. Afterwards, `git status` should show diverged branches.
 2. Now, Person 3 should run `git merge`. This will create a new "merge commit" following from both diverged paths and bringing them back together. It will also pop open the terminal text editor (either `vim` or `nano`) to allow you to edit a message for this merge. 
 3. For now, just keep the default and close the editor. For `nano`, press ctrl+x to close out. For `vim`, hit the escape key, and then type `:q` and hit the enter key.
 4. Now, Person 3 should make sure to push and ***everyone else*** should pull.

The changes have been successfully reconciled across different files! However, we still have one scenario to explore: What happens when two people edit the same file?

## Resolving Merge Conflicts
There's one more issue to consider when reconciling divergent commits - what if the commits are made to the same file, including potential contradictory changes!?

In this case, you've got a merge conflict. Regardless of whether you choose to rebase or merge, git is going to need some help figuring out what to do.

For this section, let Person 1 and Person 2 lead. Both shoud make sure you are up to date with the changes from the last section.

First, have **Person 2** edit the `README.md` copy, as such:

    # mrover-vc-exercise Person 2 was here.
    Our members in our group are Zachary Goldston, Cameron Tressler, and Ashwin Gupta.
    Also changing stuff here.

Additionally, make a new files called `new.txt`. Put whatever text you want in it.

Now, **Person 2** should contribute their changes. The commands are as follows:

    git add -A
    git commit -m "person 2 changes"
    git push

Note that the `-A` flag will stage all files that have been modified.

Now, **Person 1** should make one change to their copy of `README.md`.

    # mrover-vc-exercise Person 1 was here, now.
    Our members in our group are Zachary Goldston, Cameron Tressler, and Ashwin Gupta.

Before committing anything, **Person 1** should run `git pull`. This will grab Person 2's changes, and attempt to merge them in.

You'll get an error message here, though. `git` won't let you do it, because it would overwrite the "Person 1 was here, now." changes that haven't been committed yet. The error message suggests
you "Please commit your changes or stash them before you merge."

(We won't cover `git stash `in this tutorial, though it would also be a viable option here. Essentially, the idea of a "stash" would be to hide away the Person 1's local changes, allow them to pull the Person 2's commit, and then reapply the stashed changes on top.)

From here, **Person 1** should go run the following commands:

    git add -A
    git commit -m "Person 1 changes"

**Person 1** should then run `git pull` again. This time, the fetch and merge will go ahead and attempt to reconcile the divergent branches.

You should see a message like this:

    Auto-merging README.md
    CONFLICT (content): Merge conflict in README.md
    Automatic merge failed; fix conflicts and then commit the result


Additionally, if you run git status, you'll see that `new.txt` is all good, but that `README.md` is currently an "unmerged path" because there was a conflict.

To fix this, open up `README.md` in an editor or IDE. You'll see something like this:

    <<<<<<< HEAD
    # mrover-vc-exercise Person 1 was here, now.
    =======
    # mrover-vc-exercise Person 2 was here.
    >>>>>>> 6af387196da8bd82792cdc5d121ee4f2defc9949
    Our members in our group are Zachary Goldston, Cameron Tressler, and Ashwin Gupta.
    Also changing stuff here.

Git has marked up your changes ("HEAD") and the incoming changes (">>>>>>> 6af387...") in the places where there were conflicts (i.e. two people edited the same line).

To resolve the conflict, ultimately you just need to put the file in the state you want. Depending
on your editor, it might recognize the markup git has added and highlight the current vs. incoming change, or it might even give you shortcuts to accept one or the other.

Person 1 should keep the "Person 1 was here, now." version and also delete the git markup. The result is this:

    # mrover-vc-exercise Person 1 was here, now.
    Our members in our group are Zachary Goldston, Cameron Tressler, and Ashwin Gupta.
    Also changing stuff here.

Make sure to save the file. Now, at the terminal run:

    git add README.md (to mark the README.md conflicts as resolved)
    git commit (to finish the merge commit)

An editor will open for the merge commit message. Close it out to return to the terminal command line.  Finally, Person 1 runs `git push` to push their changes and the merge commit.

Everyone else can run git pull to get up-to-date!

Congratulations on making it through this tutorial! You and your group have the basic skills on how to handle different changes across different files, and even the same ones! If you want more great git tutorials, we recommend you check out [this](https://www.atlassian.com/git/tutorials) page.