Git talk | Fede Mon
    AMA!


Saving your work

    - That's what git is about
    - It's flexible, as a rope


VCS vs DVCS
(vs VCSVSDVCS)

    - Centralized or Distributed
    - CVS and Subversion are VCSs while GIT and Mercurial are DVCSs.
    - Lock server on every operation vs work offline


Commit and HEAD

    - Commit is the atomic particle of GIT.
    - In git is like a snapshot of the files, not differences to previous
      versions.
    - May have a parent, or several, or none.
    - HEAD is the name of the commit we are now.


Branch and Master

    - Branch is only a pointer to a commit.
    - Master is the default name for the first branch in a repo.


Repository or History

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


Index or Staging Area

    - The index for the next commit
    - Not yet written to stone, it's a WIP



Beware: {

    - Common mistakes one can commit when getting started
    

Ignored/untracked files

    - Filetypes or paths can be set to be ignored always
    - We should check we added the files we want to commit
    

Staged file, modified afterwards

    - Even if we added a file to the index, it could have been modified
      afterwards
    - We will see it in both places: added and unstaged

}
   - Warning ends here


Stashes

    - Drawers to save your current work.
    - Noncomplicated, you just apply them over your current status


Hashes (or the elephant in the room)

    - You're going to see them everywhere, so let's talk about it.
    - Git checks everything by generating a 40-char checksum of the things.
    - You cannot modify something without git noticing.
    - If we want to refer to a commit or something that has no name, we can use
      its hash to do it.


Configuration
<pre>
$ git config --global user.name "Fede Mon"
$ git config --global user.email gnu.fede@gmail.com
</pre>

    - Several levels of config, global is for your user.
    - System is for every user on your machine, also repo level.


Creating a repo
<pre>
$ git init
</pre>

    - Creates an 'empty' .git directory


Cloning a repo
<pre>
$ git clone http://github.com/gnufede/git-talk
</pre>

    - Grabs a .git directory from the internet, recreates HEAD in Working Tree


![3-phase-commit](http://rogerdudler.github.io/git-guide/img/trees.png)

    - Note the 3 stages


Let's see it slowly

    - Example: edit file
    - Add file
    - Edit file
    - Commit


Branching
<pre>
$ git checkout -b "new_branch"
</pre>

    - Use them to split work
    - I.E. different tasks


Merging
<pre>
$ git merge master
</pre>

    - Use them to join


