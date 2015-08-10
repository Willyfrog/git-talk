Git talk
    AMA!


Safe

    - That's what git is about
    - It's flexible, as a rope


(D)VCS

    - Centralized or Distributed
    - CVS and Subversion are VCSs while GIT and Mercurial are DVCSs.
    - Lock server on every operation vs work offline


Commit & HEAD

    - Commit is the atomic particle of GIT.
    - In git is like a snapshot of the files, not differences to previous
      versions.
    - May have a parent, or several, or none.
    - HEAD is the name of the commit we are now.


Branch & Master

    - Branch is only a pointer to a commit.
    - Master is the default name for the first branch in a repo.


Repository == History

    - Repository is the name for all the commits.
    - You'll find a .git dir inside it.
    - Once you commit, it's stored and can be shared with
      other people.


Remotes

    - Far away repos.
    - Intended for sharing work, or backups.
    - You can have several


Working Tree

    - The dir where you have .git folder
    - It contains the work your are working on
    - Some files might be unsaved, staged, not tracked...


Index == Staging Area

    - The index for the next commit
    - Not yet written to stone, it's a WIP



Beware: {

    - Common mistakes one can commit when getting started
    

Untracked files

    - Filetypes or paths can be set to be ignored always
    - We should check we added the files we want to commit
    

Modified afterwards

    - Even if we added a file to the index, it could have been modified
      afterwards
    - We will see it in both places: added and unstaged

}
   - Warning ends here


Stashes

    - Drawers to save your current work.
    - Noncomplicated, you just apply them over your current status


Hashes

    - You're going to see them everywhere, so let's talk about it.
    - Git checks everything by generating a 40-char checksum of the things.
    - You cannot modify something without git noticing.
    - If we want to refer to a commit or something that has no name, we can use
      its hash to do it.


Configuration

    - Several levels of config, global is for your user.
    - System is for every user on your machine, also repo level.


git config
<pre>
$ git config --global user.name "Fede Mon"
$ git config --global user.email gnu.fede@gmail.com
</pre>

    - Just to get started
    - Much more options


Create

    - Let's see how to convert a dir into a repo


git init
<pre>
$ git init
</pre>

    - Creates an 'empty' .git directory


Clone

    - That's how we copy previous work


git clone
<pre>
$ git clone http://github.com/gnufede/git-talk
</pre>
    - Grabs a .git directory from the internet, recreates HEAD in Working Tree


![3-phase-commit](http://rogerdudler.github.io/git-guide/img/trees.png)

    - Note the 3 stages
    - TODO: Change the image


Do your stuff
    - Edit your files if you haven't

Stage
    - Add a file to the staging area


git add
<pre>
$ git add myfile.txt
$ git add stuff/
</pre>
    - . or dir allows to add everything there, including untracked files


Write
    - Create an actual commit that will go to the history
    

git commit
<pre>
$ git commit -m "bla"
$ git commit -am "bla"
</pre>
    - -a does everything in one command


Show
    - Check the status of your repo
    - Check the log of last commits
    - Check the diffs
    - See last modifications


git status
<pre>
$ git status
</pre>
    - Shows the status of your repo
    - Changes to commit
    - Changes not being commited

git log
<pre>
$ git log
</pre>
    - Shows the log of commits

git show
<pre>
$ git show 98765
$ git show 98765:path/file.txt
</pre>
    - Shows a commit



git diff
<pre>
$ git diff
$ git diff HEAD HEAD^2
</pre>
    - Shows the differences between commits/WD


git blame
<pre>
$ git blame
</pre>
    - Shows the files annotated with author and date


Open branches
    - Use them to split work


git checkout
<pre>
$ git checkout -b "new_branch"
</pre>

    - I.E. different tasks


Close branches
    - Joins two or more branches


git merge
<pre>
$ git merge master
</pre>

    - Use them to close tasks



2nd part
    - This will be harder to follow


Rebase
    - You can change a branch parent.
    - It changes the whole branch: commits get different refs.


Cherry-pick
    - Allows to pick a single commit and bring it anywhere.


Conflicts
    - Conflict resolution is the hardest part at work.


3-way resolution
<pre>
$ git config merge.conflictStyle diff3
</pre>
    - We can change conflict style from merge to diff3.
    - With --global if you want it in every repo.

3-way output
<pre>
<<<<<<< HEAD
master change.
||||||| merged
Original.
=======
b1 change.
>>>>>>> b1
</pre>
    - Sample 3-way output


Ours or Theirs
<pre>
$ git checkout --ours file.txt
$ git checkout --theirs file.txt
</pre>
    - We can solve conflicts saying: take my file.


Use your tool

<pre>
$ git difftool
$ git mergetool
</pre>
    - Git provides a way to choose your tool.


Special files
<pre>
*.pbxproj binary merge=union
</pre>
    - Per-file or extension merge strategy

Patches
<pre>
$ git am -3
$ git apply *.patch
</pre>
    - You can use git to generate patches of code
    - Or apply someone's patch

    - Way to create and to apply patch
