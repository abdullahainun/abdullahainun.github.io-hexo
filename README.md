# abdullahainun.github.io
AbdullahAinun Blog Repository With hexo

# How to create article
```bash
aal@aal-ubuntu:~/workspace/abdullahainun.github.io$ hexo server
(node:19607) [DEP0061] DeprecationWarning: fs.SyncWriteStream is deprecated.
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.

```
and then create your article in http://localhost:4000/admin
# How to deploy
```bash
aal@aal-ubuntu:~/workspace/abdullahainun.github.io$ hexo generate
aal@aal-ubuntu:~/workspace/abdullahainun.github.io$ hexo deploy
(node:20200) [DEP0061] DeprecationWarning: fs.SyncWriteStream is deprecated.
INFO  Deploying: git
INFO  Clearing .deploy_git folder...
INFO  Copying files from public folder...
INFO  Copying files from extend dirs...
On branch master
nothing to commit, working tree clean
Username for 'https://github.com': abdullahainun
Password for 'https://abdullahainun@github.com': 
Everything up-to-date
Branch 'master' set up to track remote branch 'master' from 'https://github.com/abdullahainun/abdullahainun.github.io.git'.
INFO  Deploy done: git

```
