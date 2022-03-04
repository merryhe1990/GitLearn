### git reset 命令【慎用  】

git reset 命令用于回退版本，可以指定退回某一次提交的版本。未push的版本可使用，团队开发已push的代码，进行回退，若有人有新提交，代码将被覆盖。

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

HEAD 表示当前版本,HEAD^ 上一个版本,HEAD^^ 上上一个版本,HEAD^^^ 上上上一个版本,以此类推...

可以使用 ～数字表示,HEAD~0 表示当前版本,HEAD~1 上一个版本,HEAD^2 上上一个版本,HEAD^3 上上上一个版本,以此类推...

### git reset HEAD

git reset HEAD 命令用于取消已缓存的内容。简而言之，执行 git reset HEAD 以取消之前 git add 添加，但不希望包含在下一提交快照中的缓存。

### git rm 命令

git rm 命令用于删除文件。

如果只是简单地从工作目录中手工删除文件，运行 **git status** 时就会在 **Changes not staged for commit** 的提示。

git rm 删除文件有以下几种形式：

1、将文件从暂存区和工作区中删除：

```bash
git rm <file>
```

如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 **-f**。

```bash
git rm -f <file>
```

如果想把文件从暂存区域移除，但仍然希望保留在当前工作目录中，换句话说，仅是从跟踪清单中删除，使用 **--cached** 选项即可：

```bash
git rm --cached <file>
```

### git mv 命令

git mv 命令用于移动或重命名一个文件、目录或软连接。

```bash
git mv [file] [newfile]
```

如果新文件名已经存在，但还是要重命名它，可以使用 **-f** 参数：

```bash
git mv -f [file] [newfile]
```
