# Pro Git

If you work with people other than yourself, having at least the basic knowledge about git is a must.

# Git Commands

Git does not explicitly track file movements. If you rename a file in git, not metadata is stored in git that tells it to rename your file, so use: - git mv source dest

## **Viewing commit history**

- > `git log`

- The difference in each commit
  > `git log -p`
- Abbreviated stats for each commit
  > `git log --stat` :
- > `git log —since=2.weeks`

- See what you’ve changed but not yet staged
  > `git diff`:
- See what you have staged and will go to your next commit
  > `git diff --staged`:
- Commit without staging first:
  > git commit -a -m “Your message here”

## **Removing files**

- The next time you commit, the file will be gone and never tracked.
  > `git rm my-file-here` :
- If you modified the file, or moved it to the staging area, you should use the -f flag
  > `git rm -f my-file-here`

## **Undoing Things**

- One of the common undos takes place when you commit too early and possibly forget to add some files, or you mess up your commit messages. If you want to redo that commit, make the additional changes you forgot, stage them and commit again using the —amend option

  > `git commit —amend`

Example:

> `git commit -m “initial commit“`  
> `git add forgotten_file`  
> `git commit —amend`

_Behind the scenes, you are replacing it entirely with a new improved commit that pushes the old commit out of the way and puts the new commit in its place._

## _Unstaging a staged file_

> `git reset HEAD <file_to_unstage>`

## _Unmodifying a modified file_

- DANGEROUS, any local changes you made tot hat file are gone. Git just replaced that file with the most recently-committed version. Don’t use it unless you know what you’re doing.

  > `git checkout — <file>`

## WORKING WITH REMOTES

- Showing your remotes
  > `git remote`  
  > _Should print origin, as it is the default name GIT gives to the server you cloned form._
- You can specify the -v, which shows you the URLs that Git has stored for the short name to be used when reading and writing to that remote.
  > `git remote -v`

## **Adding Remote Repositories**

- To add a new remote repo , you can run:
  > `git remote add <shortname> <url>`  
  > _Ex: git remote add eraldo https://github.com/eraldoforgoli/books-every-progammer-should-read/_

Now, if you want to fetch all the info that Eraldo has but you don’t have in your repository, you can run

> `git fetch eraldo`

As you can see, to get data from your remote projects, run:

> `git fetch <remote>`

This command gets out to that remote and pulls down all the data from that remote project that you don’t have yet.
If you clone a repo, the command automatically adds the remote repo under the name ‘origin’.
So, the \$ git fetch origin fetches any new work that has been pushed to that server since you cloned. Fetch only downloads the data to your local repo, it does not merge will any existing work you are doing.

## _PUSHING TO YOUR REMOTES_

- When you have your project to a point that you want to share it, you have to push it upstream.

  > `git push <remote> <branch>`

  Ex:

  > `git push origin develop`

- **Inspecting a remote**  
  If you want to see more info about a particular remote, use

  > `git remote show <remote>`

- **Renaming and Removing remotes**
  > `git remote rename oldName newName`  
  > `git remote remove remoteName`

## **Tagging**

_Git has the ability to tag specific point in a repository’s history as being important. Typically we use this functionality to mark release points (v1.0, v2.0)._

- Listing Your Tags

  > `git tag`

- _Creating tags_  
  Git supports two types of tags: lightweight and annotated.
- _A lightweight tag is very much like a branch that doesn’t change - it’s just a pointer to a specific commit._

- Annotated tags, however, are stored as full objects in the Git database. They’re checksummed; contain the tagger name, email and date; have a tagging message; and can be signed and verified with GNU Privacy Guard. It’s generally recommended that you create annotated tags so you can have all this info.

- **Creating Annotated Tags**  
  The easiest way is to specify -a when you run the tag command:

  > `git tag -a v1.4 -m “my version 1.4”`

- To see the tag info:

  > `git show v1.v`

- _Lightweight tags are basically the commit checksum stored in a file - no other info is kept._
- _To create a lightweight tag, don’t supply any of the -a, -s or -m options, just provide a tag name_
- `git tag v1.4-lw`

- _Tagging later_
  You can also tag commits after you’ve moved past them.
  To tag that commit, you specify the commit checksum(or part of it) at the end of the command:

  > `git tag -a V1.2 9fsec20`

- _Sharing Tags_  
  By default, git push command doesn’t transfer tags to remote servers. You will have to explicitly push tags to a shared server after you have created them. This process is just like sharing remote branches,

  > `git push origin <tagname>`

- To push all the tags:
  > `git push origin —tags`

_Note: git push pushes both types of tags._

- Deleting tags:
  > `git tag -d v1.34` > _This does not remove the tags from any remote servers. There are two common variations for removing a ta from a remote server._

1. > `git push <remote> :refs/tags/<tagname>`

   Ex:

   > `git push origin :refs/tags/v.14`

2. > `git push origin —delete <tagname>`

## **Git Aliases**

_Git does not automatically infer your command if you type it in partially. If you don’t want to type the entire text of each of the Git commands, you can easily set up an alias for each command using git config._

> `git config —global alias.co checkout` > `git config —global alias.br branch` > `git config —global alias.ci commit` > `git commit —global alias.st status` > `git commit —global alias.popcommit ‘git reset HEAD~”`

_I have not finished this book yet, will incrementally update once i finish each chapter_

Link: https://www.amazon.com/Pro-Git-Scott-Chacon/dp/1430218339
