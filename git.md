## Commit Messages

### Structure

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

Focus on explaining *why* the change was made. This is critical when an arbitrary change is made because of some business requirement. Having detailed commit messages (along with code comments) helps future contributors (including your future self) make sense of the code. If the code being modified is complex and/or spans multiple systems, try to provide a synopsis of architecture (to the extent needed to explain the commit), so someone without intimate knowledge of the codebase can understand the commit [example](https://github.com/forma-ai/commissions/commit/f1d3e4ba0fff9407a30dfdf87445764f290ba52b).
 
For **bug fixes**, consider the following questions:

* What was the bug? Was the [old code broken](https://github.com/forma-ai/backend-core/commit/75908b19baf2511fa6d4e0b876613bfab49aaa58)? Was there a [data issue](https://github.com/forma-ai/commissions/pull/190)    ? 

* What circumstances would trigger the bug? what was the expected behavior? what was the actual behavior?

* Why/how does the your bug fix avoid the original bug?

For **new features**, consider the following questions:

* Why is the feature needed/wanted? What's the underlying business problem we're trying to solve?

* what were the reasons/justifications for some of the high level/important design choices that were made?
 
[example commit](https://github.com/forma-ai/backend-core/commit/25cb99ce84d62046f066164f26bf61a8dbcc038d)


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
