### git diff 命令

git diff 命令比较文件的不同，即比较文件在暂存区和工作区的差异。

git diff 命令显示已写入暂存区和已经被修改但尚未写入暂存区文件的区别。

git diff 有两个主要的应用场景。

- 尚未缓存的改动：**git diff**
- 查看已缓存的改动： **git diff --cached**
- 查看已缓存的与未缓存的所有改动：**git diff HEAD**
- 显示摘要而非整个 diff：**git diff --stat**

显示暂存区和工作区的差异:

```
$ git diff [file]
```

显示暂存区和上一次提交(commit)的差异:

```
$ git diff --cached [file]
或
$ git diff --staged [file]
```

显示两次提交之间的差异:

```
$ git diff [first-branch]...[second-branch]
```

### git commit 命令

git commit 命令将暂存区内容添加到本地仓库中。

```bash
# 提交暂存的更改，会新开编辑器进行编辑
git commit 
# 提交暂存的更改，并记录下备注,提交暂存区到本地仓库中
git commit -m "you message"
# 等同于 git add . && git commit -m
git commit -am
# 对最近一次的提交的信息进行修改,此操作会修改commit的hash值
git commit --amend
#对指定的文件commit
$ git commit [file1] [file2] ... -m [message]
```

#### 修改commit的message

```bash
git commit --amend ## 修改最近一次commit的message
$ git rebase -i commit_id ## 该commit_id是我们要修改的那个commit的父commit，或者说是我们要修改的那个commit的上一个commit的id
```

#### 将几个连续commit整理成一个commit

```
$ git rebase -i 开始commit [结束commit]
```

在执行这个命令时，
 如果没有指定 结束commit,那么结束commit 默认为当前分支最新的 commit，那么rebase 结束后会自动更新当前分支指向的 commit,
 如果指定了结束 commit，而且结束 commit不是当前分支最新的 commit，那么rebase 后会有生成一个 游离的 head,，而且当前分支指向的commit 不会更新

### git reset 命令

git reset 命令用于回退版本，可以指定退回某一次提交的版本。

git reset 命令语法格式如下：

```
git reset [--soft | --mixed | --hard] [HEAD]
```

**--mixed** 为默认，可以不用带该参数，用于重置暂存区的文件与上一次的提交(commit)保持一致，工作区文件内容保持不变。

```
git reset  [HEAD] 
```

实例：

```
$ git reset HEAD^            # 回退所有内容到上一个版本  
$ git reset HEAD^ hello.php  # 回退 hello.php 文件的版本到上一个版本  
$ git  reset  052e           # 回退到指定版本
```

**--soft** 参数用于回退到某个版本：

```
git reset --soft HEAD
```

实例：

$ git reset --soft HEAD~3 # 回退上上上一个版本

**--hard** 参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交：

```
git reset --hard HEAD
```

实例：

```
$ git reset –hard HEAD~3  # 回退上上上一个版本  
$ git reset –hard bae128  # 回退到某个版本回退点之前的所有信息。 
$ git reset --hard origin/master    # 将本地的状态回退到和远程的一样 
```

**注意：**谨慎使用 –hard 参数，它会删除回退点之前的所有信息。

**HEAD 说明：**

HEAD 表示当前版本，HEAD^ 上一个版本，HEAD^^ 上上一个版本，HEAD^^^ 上上上一个版本，以此类推...

可以使用 ～数字表示，HEAD~0 表示当前版本HEAD~1 上一个版本，HEAD~2 上上一个版本，以此类推...

### git reset HEAD

git reset HEAD 命令用于取消已缓存的内容。简而言之，执行 git reset HEAD 以取消之前 git add 添加，但不希望包含在下一提交快照中的缓存。

### git revert 

git revert 撤销 某次操作，此次操作之前和之后的commit和history都会保留，并且把这次撤销，作为一次最新的提交。

### git rm 命令

git rm 命令用于删除文件。

如果只是简单地从工作目录中手工删除文件，运行 **git status** 时就会在 **Changes not staged for commit** 的提示。

git rm 删除文件有以下几种形式：

1、将文件从暂存区和工作区中删除：

```bash
git rm <file>
```

如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 **-f**。

如果想把文件从暂存区域移除，但仍然希望保留在当前工作目录中，换句话说，仅是从跟踪清单中删除，使用 **--cached** 选项即可：

```bash
git rm --cached <file>
```

可以递归删除，即如果后面跟的是一个目录做为参数，则会递归删除整个目录中的所有子目录和文件：

```bash
git rm –r * 
```

进入某个目录中，执行此语句，会删除该目录下的所有文件和子目录。

### git mv 命令

git mv 命令用于移动或重命名一个文件、目录或软连接。

```bash
git mv [file] [newfile]
```

如果新文件名已经存在，但还是要重命名它，可以使用 **-f** 参数：

```bash
git mv -f [file] [newfile]
```

我们可以添加一个 README 文件（如果没有的话）：

```bash
$ git add README 
```

然后对其重命名:

```bash
$ git mv README  README.md
$ ls
README.md
```
