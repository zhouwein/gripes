## Commit Messages

### Structure
No Commit message is also acceptable

A git commit message is composed of a subject and an optional body. The subject is the first line of a commit message and the body is everything after. Although optional, you should seperate the subject and body with a blank line.

### Writing style

*Always* use imperative mood when writing commit message subjects. Why? Having them in a consistent format reduces cognitive load when skimming a long list of commits. Would you rather read through this:

* Fixed bug with Y
* Changing behavior of X
* More fixes for broken stuff
* Sweet new API methods

or this?

* Refactor subsystem X for readability
* Update getting started documentation
* Remove deprecated methods
* Release version 1.0.0

Why imperative mood rather than something else? Because it's shorter (eg. "add x" vs "added x") and is the  style used by git itself (`git revert` produces "revert commit [...]" rather than "reverted commit [...]").

### Contents

Unless it's a trivial and obvious commit, explain *why* the change was done. This is critical when an arbitrary change is made because of some business requirement. Having an expalnation helps future contributors avoid repeated work and wasted time.

### Length

Keep the subject short. Long messages are harder to skim. If you need to fit more information, put that in the body. As a point of reference, Github starts complaining once you exceed 50 characters, and the max that can be displayed without wrapping in `git log` on a standard width terminal is 76.

## Workflow

Merges suck. Why? For one, they clog up commit logs with messages like "Merge remote-tracking branch 'origin/xyz' into xyz". You also end up with commit trees like this:

<img src="https://github.com/zhouwein/gripes/raw/master/img/merge%20commit%20tree.png">

And that's if you're using a GUI git interface. If you're using `git log`, all you see is a linear list of commits that don't correspond to the actual state of the repo.

Use rebase.

* When merging a PR, make sure to choose the "squash and merge" option. It's supposed to remember your perference, but sometimes it forgets.

* Run `git config --global pull.rebase true` so git doesn't produce a merge commit when you're pulling with unpushed commits

* If you're pushing Pycharm/Webstorm's integrated VCS, and you get a prompt about a rejected push, click the "rebase" option
