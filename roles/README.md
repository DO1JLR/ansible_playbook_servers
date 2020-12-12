 Subfolders to include ansible roles.
============================

All roles should be included in this subfolder.
This is usually done as git submodule.

The most common command needed for this is:

```
git submodule add <public_path_to_gitrepo.git> <submodule_destination>
```

A simple way to checkk out the latest commit at the main branch for all submodules is:
```
git submodule foreach "(git checkout $(git symbolic-ref --short refs/remotes/origin/HEAD | sed "s@^origin/@@"); git pull)"
```

In abstract terms, the easiest way to do this is to treat submodules like normal git repositories after you have cloned them. This means checking out the main branch, committing things and similar actions. And when the local changes to submodule git repo are complete, add the new commit hash of submodule indein main git repo by adding, committing and pushing the entire submodule like an updated file.

Further information is also available at [git-scm.com/docs/git-submodule](https://git-scm.com/docs/git-submodule)
