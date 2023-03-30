## **Session One**

### Setup
1. Define your project team
1. Choose a team lead
1. Team lead: create a repo (check the box for including a README)
1. Invite your team as collaborators
1. Team: Clone your team lead's repo (do NOT fork it!)
1. Take a look at a sample project repo.

**Checkpoint -  Everyone has the team lead's repo cloned (including the team lead)**

### Basic Collaborative Workflow
   Orientation w.r.t. class practice/household items, and basic Git/Linux/VSCode.

#### LAB - Basic Collaborative Workflow
   > Each member of the team commit and push at least one (non-merge-conflicting) change.  For instance, each member
   > can add one of these files: `index.html`, `help.html`, `about.html`, `faq.html`, `map.html`.

### The Anatomy of a Commit 
Now that we have some commits, let's take a closer look...

#### LAB - Anatomy of a Commit 
> Use `git cat-file -p` to answer these questions:
> 1. What fields does HEAD have?
> 1. What kind of SHA is HEAD's "parent" field? (Use `-t` instead of `-p`)
> 1. What fields does HEAD's tree have?
> 1. What are the contents of HEAD's tree's first blob?

### Your Local Git repo and The Three Trees - or, "Intro to `git reset`"
Using `git reset`, move changes back and forth locally between the [The Three Trees](objects-and-trees-exercise.md).

#### LAB - Practicing with `git reset`
Use each of the `--soft`, `--mixed`, and `--hard` options to `git reset` at least once.
> 1. Make a change and commit it (do not `git push`!).
> 1. Revert the change using `git reset`.
> 1. Make another change, and commit.
> 1. Revert, using another option of `git reset`.  Commit.
> 1. Revert, using another option of `git reset`.  Commit.

### Create and resolve a merge conflict

#### LAB - merge conflicts
> 1. Each teammate: Change the same line in same file (e.g. Change "The Solar System" in `index.html` to some other text).
> 1. Commit. 
> 1. One teammate do a `git push`; the others `git pull`.
> 1. Among your team, resolve merge conflicts and `git push` until you all have the same commit sha for HEAD.

### Branches and Pull Requests to create and resolve a merge conflict
Github supports [two collaborative development models](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/getting-started/about-collaborative-development-models):
- fork and pull
- shared repository <--- This is us

>>"In the shared repository model, collaborators are granted push access to a single shared repository and topic branches are created when changes need to be made. Pull requests (PR's) are useful in this model as they initiate code review and general discussion about a set of changes before the changes are merged into the main development branch. This model is more prevalent with small teams and organizations collaborating on private projects."

We'll be working within the shared repository model, since it is indeed more prevalent at DRW

Why is it called a "Pull REQUEST", if you're pushing changes?
[ANSWER: Was more correct in the fork/pull model, less so with shared-repo]

#### LAB - Create/Handle merge conflicts again - but now using Pull Requests in your workflow
> 1. Each teammate: `git checkout -b` _yourOwnBranchName_
> 1. Each teammate: Change the same line in same file, like before.
> 1. Commit. 
> 1. `git push` _yourOwnBranchName_
> 1. Go to Github and make a PR for your branch; choose one or more reviewers.
> 1. Reviewers: review/approve the PRs and merge.
> 1. Review and merge, `git pull`, etc. until you all have the same commit sha for HEAD.

