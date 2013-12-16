Git
========

* Avoid including files in source control that are specific to your
  development machine or process.
* Delete local and remote feature branches after merging.
* Perform work in a feature branch.

Create a local feature branch based off dev.

    git checkout dev
    git pull
    git checkout -b <branch-name>

When feature is complete and ALL tests pass, stage and commit the changes.

    rake
    git add --all

Write a [good commit message]. Example format:

    Present-tense summary under 50 characters

    - More information about commit (under 72 characters).
    - More information about commit (under 72 characters).

    http:://project.management-system.com/ticket/123

Share your branch.

    git push origin <branch-name>

Merge back into dev

    git checkout dev
    git pull
    git checkout <branch-name>
    git rebase dev
    git checkout dev
    git merge <branch-name>
    git push origin dev


[good commit message]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html

