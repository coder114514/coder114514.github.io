Git每一次commit相当于一个快照
Git使用DAG组织这些快照

工作区：当前项目文件夹的文件和文件夹
暂存区：接下来commit要往repo中加入的文件添加、删除、修改
repo：commit的DAG
remote: 远程repo
remote本地副本：远程repo的本地副本

工作区    暂缓区    repo   remote本地副本   remote

git add: 工作区->暂缓区
git commit: 暂缓区->repo
git fetch: remote->remote本地副本
git push: repo->remote本地副本,repo->remote （必须是fast-forward merge）
git pull: git fetch + git merge

object：用于存储项目内容，名字是存储的内容的哈希值
object 分三种
blob: 存储文件内容
tree：存储目录内容，指向其他的tree和blob
commit：存储快照内容，指向快照根目录tree以及上一个commit（如果是merge commit的话就有2个父节点commit，第一个commit就没有父结点commit）