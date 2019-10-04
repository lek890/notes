To produce patch for several commits, you should use format-patch git command, e.g.
git format-patch -k --stdout R1..R2
This will export your commits into patch file in mailbox format.
To generate patch for the last commit, run:
git format-patch -k --stdout HEAD^

https://mijingo.com/blog/creating-and-applying-patch-files-in-git
