# Git Scripts
These are git files for some use-case scenarios

## Installation

```
mkdir gitscripts
git clone git://github.com/has2k1/gitscripts
cd gitscripts
./install -fd $HOME/bin
```

The install file only installs scripts in the gitscripts/bin files. Make sure the install directory is part of the system ```$PATH```

By default, the install script creates symbolic links to the gitscripts/bin directory. Using the ```-f``` option you can create files instead of links. Use the ```-d``` option to change the install directory

## The scripts
### gitscripts/bin/
* **git-merge-ff** : Merge by fast-forwarding, otherwise fail. You can merge branches without checking them out. The script is a commented version of a stackoverflow [post](http://stackoverflow.com/questions/4156957/merging-branches-without-checkout/4157435#4157435) by Jefromi

---

### gitscripts/hooks
#### /hub-prime
These paired hooks are based on ["A web focused git workflow"] (http://joemaller.com/990/a-web-focused-git-workflow/) by Joe Maller. His website provides an exhaustive description of the workflow.

The hooks have been modified to;

1. Provide for a staging branch/directory
2. Prime merges by fast forward instead of pulling.
3. One to one relationship between hub and prime branches.

##### /hub-prime/staging
The staging capabality added to Maller's model is aided by the scripts in this directory. Both scripts are used by the post-update hook to setup routes to a server-side stage. Currently, a stage is checked out when a ```git push hub <branch>:<stage_branch>```. The stage branch is held by a variable in the hub's post-update hook.

The stage is just a temporary work-tree of hub's stage branch. Changes made to it are untracked and overwritten whenever the branch is pushed to. hub remains a bare repository.

The scripts just add redirects to .htaccess files so that the pushing ip_address is sent to the staging directory.

---
