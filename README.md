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
determine branches to compare. If a single branch is given, compare against
`HEAD`. If two branches are given, then compare against each other.

After selecting branches, `fzf` will be launched again to allow selecting
individual files. Pressing `ctrl-m` or `enter` will show how the file changed
between the two branches. The `patience` diffing algorithm is used.

## git-branch-explore

Interactive git branch explorer. See table below for expected inputs.

| key      | effect                                                  |
|:---------|:--------------------------------------------------------|
| `ctrl-m` | Show (patience) the last commit on the branch.          |
| `ctrl-e` | Explore the last commit as if using `git-diff-explore`. |
| `ctrl-b` | Check out the branch.                                   |
| `del`    | Delete the branch.                                      |

## interact-rm

Interactive file deletion. This script is different depending on which commands
are available to it. If the system has [`Exa`](https://github.com/ogham/exa)
installed, then the file browsing will be performed using the output of `exa -l
-a --git --header --color=always`. If `exa` is not available, then `ls -A1` will
be used. The script also attemts to safely delete files using
[`Gomi`](https://github.com/b4b4r07/gomi) if it is available, otherwise it uses
`rm -rf`.

See table below for expected input.

| key      | effect                                                    |
|:---------|:----------------------------------------------------------|
| `ctrl-m` | Open the file using `xdg-open` on Linux or `open` on Mac. |
| `del`    | Delete the file, using Gomi if available.                 |
