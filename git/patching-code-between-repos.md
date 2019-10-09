**Git Patch**

When we want to patch some changes to another version of the repo we are working on or on another repo, 
we could use git patch.

To get the changes in the last commit, use

`git format-patch --stdout HEAD^`

To get these changes on a file, use without stdout flag

`git format-patch HEAD^`

This would create a file, which git would name relating to the commit msg. We could specify the name also.

`git format-patch HEAD^ > mypatch.patch`

To the changes between two commits, we could use

`git format-patch --stdout COMMIT_ID_1..COMMIT_ID_2`


*To apply the patch to the destination branch*

Before applying the patch, we might need to know whats in the patch. In that case,

`git apply --stat mypatch.patch`

Now, we could trial run the patch to see if it would work without errors

`git apply --check mypatch.patch`

If this is successful, go ahead run the `am` command to patch it.

`git am mypatch.patch`



The same can be used for apply diff patches

`git diff > mypatch.patch`

to apply it,

`git apply mypatch.patch`
