title: Git Submodule Tutorial
author: Ainun Abdullah
tags:
  - git
  - git-submodule
categories:
  - Infrastructure
date: 2019-12-01 07:04:00
---
### Introduction

In our Git projects, sometimes we will include and use other Git projects as submodules. One easy and reproducible way to do this is simply to clone the other Git projects and copy the Git projects in the directories under our own projects. However, it is also likely that the project we are working on has close relationships or collaboration with the submodule Git projects, and we want the submodules to be always up-to-date. In this way, we will use `git submodule` functions to manage submodules.

<!--more-->

In this short blog post, I will talk about the basic protocols of using `git submodule` correctly in our projects in practice. For more comprehensive usages, please go to the reference section.

### Tutorial

#### Create Submodules in Our Own Git Projects

We will use [`git submodule add`](https://git-scm.com/docs/git-submodule#Documentation/git-submodule.txt-add-bltbranchgt-f--force--nameltnamegt--referenceltrepositorygt--depthltdepthgt--ltrepositorygtltpathgt) to create submodules in our own Git projects.

```bash
$ git submodule add [-b <branch>] [-f|--force] [--name <name>] [--reference <repository>] [--depth <depth>] [--] <repository> [<path>]
```

For example, if we want to use [TensorFlow project branch r1.14](https://github.com/tensorflow/tensorflow/tree/r1.14) as our submodule in directory `third_party/tensorflow`. In our Git project `git-submodule-demo`, we run the following commands.



```bash
$ cd git-submodule-demo/
# Empty demo project.
$ ls -a
.  ..  .git
# Create TensorFlow submodule.
$ git submodule add -b r1.14 https://github.com/tensorflow/tensorflow.git third_party/tensorflow
```

We then check what submodule information has been added.



```bash
$ ls -a
.  ..  .git  .gitmodules  third_party
# We got TensorFlow as our submodule.
$ ls -a third_party/tensorflow/
.                   BUILD               .github            RELEASE.md
..                  CODE_OF_CONDUCT.md  .gitignore         SECURITY.md
ACKNOWLEDGMENTS     CODEOWNERS          ISSUES.md          tensorflow
ADOPTERS.md         configure           ISSUE_TEMPLATE.md  third_party
arm_compiler.BUILD  configure.py        LICENSE            tools
AUTHORS             CONTRIBUTING.md     models.BUILD       WORKSPACE
# We will have a `module` directory in the `.git` directory for the submodules
$ ls -a .git/
.   branches  description  hooks  info     objects
..  config    HEAD         index  modules  refs
# The `.git` directory for the TensorFlow submodule
$ ls -a .git/modules/third_party/tensorflow/
.   branches  description  hooks  info  objects      refs
..  config    HEAD         index  logs  packed-refs
# The TensorFlow submodule information was added to `.git/config`
$ cat .git/config 
...[Git Information Skipped]...
[submodule "third_party/tensorflow"]
	url = https://github.com/tensorflow/tensorflow.git
	active = true
# The TensorFlow submodule information was added to `.gitmodules`
$ cat .gitmodules 
[submodule "third_party/tensorflow"]
	path = third_party/tensorflow
	url = https://github.com/tensorflow/tensorflow.git
	branch = r1.14
```

We then push the changes to GitLab or GitHub.



```bash
$ git add .
$ git commit -m "add submodule"
$ git push origin master
```

On GitLab or GitHub, there will be symbolic links to the Git projects for the submodules.

#### Remove Submodules in Our Own Git Projects

It used to be very tricky to remove the Git submodules. However, the latest protocol for the new versions of Git makes the life easier. To remove the TensorFlow submodule we just added.



```bash
$ git submodule deinit -f third_party/tensorflow/
$ rm -rf .git/modules/third_party/tensorflow/
$ git rm -f third_party/tensorflow/
```

We then check if the submodules have been totally removed.



```bash
$ ls -a
.  ..  .git  .gitmodules  third_party
# No TensorFlow submodule anymore in `third_party`.
$ ls -a third_party/
.  ..
# No TensorFlow submodule anymore in `.git/modules/third_party/`.
$ ls -a .git/modules/third_party/
.  ..
# No TensorFlow submodule anymore in `.gitmodules`.
$ cat .gitmodules
```

Once the submodules were removed, we could add the exact same submodules.



```bash
$ git submodule add -b r1.14 https://github.com/tensorflow/tensorflow.git third_party/tensorflow
```

If the submodules were not removed in a clean way and there are residual information left, there will be problems to add the exact same submodules.

#### Works with Submodules in Other Git Projects

Sometimes we would have to work on Git projects from others which contains submodules. After `git clone`, we actually would not have the submodules cloned.



```bash
$ cd git-submodule-demo/
$ ls -a
.  ..  .git  .gitmodules  third_party
# The submodule information is `.gitmodules `
$ cat .gitmodules 
[submodule "third_party/tensorflow"]
	path = third_party/tensorflow
	url = https://github.com/tensorflow/tensorflow.git
	branch = r1.14
# The submodule directory is empty.
$ ls -a third_party/tensorflow/
.  ..
# There is no `module` directory to store the `.git` files for submodules.
$ ls -a .git
.   branches  description  hooks  info  objects      refs
..  config    HEAD         index  logs  packed-refs
$ cat .git/config 
...[Git Information Skipped]...
[No submodule information]
```

To retrieve the submodules, we have to run the following command.



```bash
# Git submodule would use the submodule information in the `.gitmodules` to retrieve the submodules.
$ git submodule update --init --recursive
# The TensorFlow submodule was retrieved.
$ ls -a third_party/tensorflow/
.                   BUILD               .github            RELEASE.md
..                  CODE_OF_CONDUCT.md  .gitignore         SECURITY.md
ACKNOWLEDGMENTS     CODEOWNERS          ISSUES.md          tensorflow
ADOPTERS.md         configure           ISSUE_TEMPLATE.md  third_party
arm_compiler.BUILD  configure.py        LICENSE            tools
AUTHORS             CONTRIBUTING.md     models.BUILD       WORKSPACE
.bazelrc            .git                README.md
```

Sometimes we want to create submodules that are exactly used in other Git projects for our own projects. We just have to check the submodule information in the `.gitmodules` file, and used the method we described in “Create Submodules in Our Own Git Projects” to create those submodules accordingly.

### Final Remarks

We have to be careful when we use `git submodule` because the submodules might be updated without sending notifications to you and all your dependencies might break.

### References

- [Git Submodule Documentation](https://git-scm.com/docs/git-submodule)
- [Git Tool - Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
- [Git Submodule Removal](https://gist.github.com/myusuf3/7f645819ded92bda6677)