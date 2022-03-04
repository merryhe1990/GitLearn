### **git add 命令**

**git add** 命令可将该文件添加到暂存区

添加一个或多个文件到暂存区：

```bash
$ git add [file1] [file2] ...
```

添加指定目录到暂存区，包括子目录：

```bash
$ git add [dir]
```

添加当前目录下的所有文件到暂存区：

```bash
$ git add .
```

### git status 命令

git status 命令用于查看在你上次提交之后是否有对文件进行再次修改。

添加当前目录下的所有文件到暂存区：

```bash
$ git status
```

通常我们使用 **-s** 参数来获得简短的输出结果：

```bash
$ git status -s
```

linux环境下中文显示为八进制的字符编码，使用 git config --global core.quotepath false，使之显示UTf-8编码

### git restore命令

```bash
$ git restore --staged <file>；
$ git restore <file>  文件仍在暂存区且会撤销文件修改的内容
```

对于git restore <file>命令，会撤销文件的修改，使文件恢复到暂存区或本地代码库（取决于文件在修改前的状态）；

对于git restore --staged <file>命令，把文件从暂存区撤回到工作区，保留文件最后一次修改的内容；
