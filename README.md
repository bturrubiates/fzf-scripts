# fzf-scripts

Scripts that can be used with [fzf](https://github.com/junegunn/fzf).

## git-stash-explore

Interactive git stash explorer. See table below for expected inputs.

| key      | effect                                                        |
|:---------|:--------------------------------------------------------------|
| `ctrl-m` | Show (patience) the changes between the stash and its parent. |
| `ctrl-b` | Check out a branch with the stash.                            |
| `del`    | Drop the stash.                                               |

## git-diff-explore

Interactive diff explorer. If no inputs are given, then launch `fzf` to
determine branches to compare. If a single revision is given, compare against
`HEAD`. If two revisions are given, then compare against each other.

After selecting revisions, `fzf` will be launched again to allow selecting
individual files. Pressing `ctrl-m` or `enter` will show how the file changed
between the two revisions. The `patience` diffing algorithm is used.

The default selection menu only displays branches, but the parameters can be
any commits or tags as well.

## git-branch-explore

Interactive git branch explorer. See table below for expected inputs.

| key        | effect                                                    |
| :--------- | :-------------------------------------------------------- |
| `ctrl-m`   | Show (patience) the last commit on the branch.            |
| `ctrl-e`   | Explore the last commit as if using `git-commit-explore`. |
| `ctrl-b`   | Check out the branch.                                     |
| `del`      | Delete the branch.                                        |

## interact-rm

Interactive file deletion. This script is different depending on which commands
are available to it. If the system has [`Exa`](https://github.com/ogham/exa)
installed, then the file browsing will be performed using the output of `exa -l
-a --git --header --color=always`. If `exa` is not available, then `ls -A1` will
be used. The script also attempts to safely delete files using
[`Gomi`](https://github.com/b4b4r07/gomi) if it is available, otherwise it uses
`rm -rf`.

See table below for expected input.

| key      | effect                                                    |
|:---------|:----------------------------------------------------------|
| `ctrl-m` | Open the file using `xdg-open` on Linux or `open` on Mac. |
| `del`    | Delete the file, using Gomi if available.                 |

## git-commit-explore

Interactively explore commits within the same branch. If no branch is given,
then the script will by default display branches and allow one to be selected.
Once a branch is provided or selected, the script prompts the user to select
a base commit and a compare commit. Once the two commits are selected, the
`git-diff-explore` utility will be invoked to provide a file-by-file diff using
fzf.

## manpage-explore

Interactively explore local manpages. I use this when I'm working on a project
with man pages that are not added to my `MANPATH`. If no parameter is given,
then the utility will list all files with names matching "man.*\.\d". If a
parameter is given, then use Ag to search for the term only in files with name
path given above. Hitting `ctrl-m` or `enter` will display the man page, and
`q` will return back to the interactive man page selector.

# License

[MIT](LICENSE)
