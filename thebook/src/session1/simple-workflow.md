# Breakdown of Simple Collaborative Workflow
This sequence of images represents the progression of a workflow where my teammate first makes a change locally and pushes, and then I also make a change locally--but now I must integrate with their change (via a `git pull origin main`) before I too can push.

(Note that the images are arranged such that you can bounce between them with right and left arrow keys and visually compare the changes between steps.)

## Step 0 - [everybody checkout `main`](./step0.md)
When I and my teammates set up to collaborate, we all `git clone` a shared repo--something like this...
```
$ git clone https://github.com/org-or-user/the-team-repo   # Make local copy of repo
$ git checkout main   # Point HEAD at "main"...i.e., make "main" my current branch
```
In this way, we all start with the same understanding of where branch `main` is--the commit represented by the green circle.

The
<span class="hljs" style="color:red">origin/main</span>
branch, seen in both local repos, is a "tracking branch". git uses it to keep track of where the
<span class="hljs" style="color:red">main</span>
branch on the remote called "origin" is pointing.

As you will see, this tracking is not "live"; no automatic notification is happening.
<span class="hljs" style="color:red">origin/main</span>'s
value _in my repo_ is updated only when I perform certain activities--mainly `git push` and `git pull`.

## Step 0.5 - [they commit locally](./step1.md)

To kick-off collaboration in this illustration, my teammate does some local work worthy of sharing--the commit represented by the pink circle.

## Step 1 - [They push `main` to the remote named "origin"](./step2.md)
Now they push their work, with something like this:
```
$ git push origin main
```
Notice the two main changes:
1. The pink commit has been copied to the remote named "origin".
1. The remote's `main` branch has been updated to reflect the new work--and correspondingly, my teammate's local
<span class="hljs" style="color:red">origin/main</span>
tracking branch is updated as well.

Note also that nothing happens in my local repo as a result of their push.

OK, now it's my turn...

## [I make local changes too, before I've talked with "origin"](./step3.md)
My commit is represented by the blue-ish circle.

(Note that my 
<span class="hljs" style="color:red">origin/main</span>
tracking branch has not yet moved, because I've not yet run any commands that reach out to the remote.)

### Step 2.1 - [fetch - first 1/2 of pull](./step4.md)
I now pull, by running something like this to see if there are changes to integrate (as indeed there are in this case):
```
$ git pull origin main
```
A `git pull` is a two-phase operation (essentially it's a mirror image of `git push`).  The first phase, called "fetch", brings into my repo's DB the news of commits and branches from the remote.

The second phase is "merge".

Essentially, a pull combines these two commands:
```
$ git fetch origin main  # Grab commits associated with current branch, and update tracking branch
$ git merge origin/main  # Merge into my current branch from the (now-up-to-date) tracking branch
```
You can run these explicitly, instead of a `git pull`; perhaps I want to see what's happened on the remote before I integrate those changes, so I `git fetch`, and take a look before doing a `git merge`.

## Step 2.2 - [merge - second 1/2 of pull](./step5.md)

As mentioned, the second half of a `git pull` is a merge operation; the merge commit is represented by the grayish circle.

By definition, a merge commit is a commit with two or more parents.

(A merge may be automatic, or it may result in a conflict; we'll cover conflicts later in this course.)

## Step 3 - [I push `main` to "origin")](./step6.md)
Now that I've committed the work onto my local `main` branch to integrate the changes, I can push that work on `main` back to the remote called "origin":
```
$ git push origin main 
```
Now I'm all caught up, and the remote is caught up.

Notice the changes that happen:
1. Two commits are sent to the remote: My original local commit, and the merge commit.
1. The remote's `main` branch has been updated to reflect the new work--and correspondingly, my teammate's local 
<span class="hljs" style="color:red">origin/main</span>
tracking branch is updated as well.  In other words, the same process happened for me when I pushed, as happened for them when they pushed.

As before, my push updates the remote (that is "origin", which happens to be Github), but it does **NOT** update my anything in my teammate's repo.  That would require explicit activity on their part.


Finally, note that now _my teammate_  is behind!  How would they catch up?
