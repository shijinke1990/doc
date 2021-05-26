# Git 的特点

### 直接记录快照，而非差异比较
git 和其它版本控制系统（包括 Subversion 和近似工具）的主要差别在于 git 对待数据的方法。其它系统（比如 CVS、Subversion、Perforce、Bazaar 等等）将它们保存的信息看作是一组基本文件和每个文件随时间逐步累积的差异。但是 git 不按照以上方式对待或保存数据。 反之，git 更像是把数据看作是对小型文件系统的一组快照。 每次你提交更新，git 都会对当时的全部文件制作一个快照并保存这个快照的索引。 为了高效，如果文件没有修改，git 不再重新存储该文件，而是用一个链接指向之前存储的文件。

git 对待数据更像是一个**快照流***。
（下图中虚线表示之前存储过，所以不重复存储。）

近乎所有操作都是本地执行
在 git 中的绝大多数操作都只需要访问本地文件和资源。比起所有操作都有网络延时开销的集中式版本控制系统，Git 在这方面会让你感到“迅雷不及掩耳盗铃儿响叮当”。 因为你在本地磁盘上就有项目的完整历史，所以大部分操作看起来瞬间完成。

这也意味着在断网环境下，几乎可以进行任何操作。 比如你在飞机上对代码做了一些修改，你能愉快地提交，直到有网络连接时再上传。 换做用 Subversion 或 CVS，你只能修改文件，但不能向数据库提交修改（因为你没网）。

保证完整性
git 中所有数据在存储前都计算校验和，然后以校验和来引用。 这意味着不可能在 git 不知情的情况下更改任何文件目录。若你在传送过程中丢失信息或损坏文件，Git 就能发现。

git 用以计算校验和的机制叫做 SHA-1 散列。 这是一个由 40 个十六进制字符组成的字符串，基于 git 中文件的内容或目录结构计算出来。 SHA-1 哈希看起来是这样的：

24b9da6552252987aa493b52f8696cd6d3b00373
1
git 中使用这种哈希值的情况很多。实际上，git 数据库中保存的信息都是以文件内容的哈希值来索引，而不是文件名，也不是 Subversion 那样连续的版本号。

一般只添加数据
你执行的 git 操作，几乎只往 git 数据库中增加数据。 很难让 git 执行任何不可逆操作，或者让它以任何方式清除数据。 同别的 VCS 一样，未提交更新时有可能丢失或弄乱修改的内容；但是一旦你提交快照到 git 中，就难以再丢失数据。如果你还定期把数据推送到其他仓库，那么你的数据就更难弄丢了。

# reset

1. Dd

   ![](/Users/shijinke/Pictures/20180819222708680.png)



# 工作区，暂存区，版本库

工作区 **workapsce**

暂存区 **index**

版本库 **repsitory**

# git配置

1. 查看配置

   ```bash
   git config --list
   ```

2. 配置邮箱用户名

   ```bash
   git config --global user.name shijinke
   ```

   ```shell
   git config --global user.email shijinke1990@qq.com
   ```

3. **git**目录下局部设置

   ```bash
   git config user.name jinx
   git config user.email shijinke1990@qq.com
   ```

   

# commit

将修改同时更新到到缓存区和版本库

```bash
git commit -a
```



# branch

分支的底层是指针的引用



# git rm 

1. 如果要删除所有缓存，需要加上`-r`,意为递归（**recursively**）

```
git rm --cached . -r
```

2. `git rm --cached <file>...` 与 `git add <file>...` 互逆 

# git diff



# commit

将暂存区内容提交到版本库

```bash
git commit -m "XXXX message" <file>
```



# reset

1. 后退一个版本

   ```bash
   git reset --hard HEAD^
   ```

2. 后退两步

   ```bash
   git reset --hard HEAD^^
   ```

3. 后退三步

   ```bash
   git reset --hard HEAD^^^
   ```

4. 后退三步

   ```bash
   git rest --hard HEAD~3
   ```

5. 后退十步

   ```bash
   git reset --hard HEAD~10
   ```

6. 厚涂

7. 等等

8. 等等

9. 

# 撤销

```
git checkout .
```



# git commit -a

加了-a，在 commit 的时候，能帮你省一步 git add ，但也只是对**修改**和**删除**文件有效， 新文件还是要 git add，不然就是 untracked 状态



7.git reflog 查看所有版本 



8.删除分值

```
git branch -D a_branch_name
```

无法删除当前所在的分支上



9.文件修改切换分支

```bash
git stash 暂存文件
```

分支有更改不能直接切换，可以提交更改或者暂存更改



10.远程仓库

在命令行中创建远程仓库

```shell
echo "# test-item" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github/shijinke1990/test-item.git
git push -u origin master
```



关联本地git仓库到github

```shell
git remote add origin https://github.com/shijinke1990/demo.git
git push -u origin master
```

推送本地dev分支到github

```shell
git push -u origin dev
```



11.giutub仓库

1. 给远程仓库起别名

```shell
git remote add origin https//:github.com/shijinke1990/xxx.git
```

2. 向远程推送代码

   ```bash
   git push origin 分支名
   ```

   

12.拉取代码

1. 克隆远程仓库代码

   ```bash
   git clone XXX (内部帮助实现git remote add origin 远程仓库地址)
   ```

2. 切换分支

   ```bash
   git switch 分支
   ```



13.协同开发

(一)

1. 切换到dev分支

   ```shell
   git checkout dev
   ```

2. 把master分支合并到dev 【仅一次】

   ```bash
   git merge master
   ```

3. 修改代码

4. 提交代码

   ```shell
   git add .
   git commit -m "xxxx"
   git push origin dev
   ```

   

（二）切换电脑（可用切换操作目录模拟）

1. 切换到dev分支进行开发

```shell
git checkout dev
```

2. 拉取代码

```shell
git pull origin dev
```

3. 修改代码

4. 提交代码

   ```shell
   git add .
   git commit -m 'xxxx'
   git push origin dev
   ```

(三) 重复（二）

（四）上线

1. 将dev分支合并到master，进行上线

   ```shell
   git checkout master
   git merge dev
   git push origin master
   ```

2. 把dev分支也推送到远程

   ```shell
   git checkout dev
   git merge master
   git push origin dev
   ```





# git在vscode中的使用









# reset

版本穿梭

1. unstage

```bash
git reset HEAD <file>... 
```

2. 









# SSH

```shell
ssh-keygen -t rsa -C "shijinke1990@qq.com" -b 4096
```





# 等效

```shell
git pull origin dev
```

等同于

```shell
git fetch origin dev 
git merge origin/dev
```



# rebase(面试经常考)

使提交记录变得简洁（整合多个提交记录为一个）





# gitlab搭建局域网git仓库





# git init 与 git init --bare 的区别

git init  和 git init –bare 的区别

使用命令"git init --bare"(bare汉语意思是:裸,裸的)初始化的版本库(暂且称为bare repository)只会生成一类文件:用于记录版本库历史记录的.git目录下面的文件;而不会包含实际项目源文件的拷贝;所以该版本库不能称为工作目录(working tree);如果你进入版本目录,就会发现只有.git目录下的文件,而没有其它文件;就是说,这个版本库里面的文件都是.git目录下面的文件,把原本在.git目录里面的文件放在版本库的根目录下面;换句话说,不使用--bare选项时,就会生成.git目录以及其下的版本历史记录文件,这些版本历史记录文件就存放在.git目录下;而使用--bare选项时,不再生成.git目录,而是只生成.git目录下面的版本历史记录文件,这些版本历史记录文件也不再存放在.git目录下面,而是直接存放在版本库的根目录下面

用"git init"初始化的版本库用户也可以在该目录下执行所有git方面的操作。但别的用户在将更新push上来的时候容易出现冲突。

比如有用户在该目录（就称为远端仓库）下执行git操作，且有两个分支(master 和 b1)，当前在master分支下。另一个用户想把自己在本地仓库（就称为本地仓库）的master分支的更新提交到远端仓库的master分支，他就想当然的敲了

git push origin master:master

于是乎出现

因为远端仓库的用户正在master的分支上操作，而你又要把更新提交到这个master分支上，当然就出错了。

但如果是往远端仓库中空闲的分支上提交还是可以的，比如

git push origin master:b1  还是可以成功的

解决办法就是使用”git init –bare”方法创建一个所谓的裸仓库，之所以叫裸仓库是因为这个仓库只保存git历史提交的版本信息，而不允许用户在上面进行各种git操作，如果你硬要操作的话，只会得到下面的错误（”This operation must be run in a work tree”）

这个就是最好把远端仓库初始化成bare仓库的原因。

# 常见问题

### 1. 在Git中，你如何还原已经 push 并公开的提交？

- 删除或修复新提交中的错误文件，并将其推送到远程存储库。这是修复错误的最自然方式。对文件进行必要的修改后，将其提交到我将使用的远程存储库

```
git commit -m "commit message"
```

- 创建一个新的提交，撤消在错误提交中所做的所有更改。可以使用命令：

```
git revert <name of bad commit>
```

### 2. git pull 和 git fetch 有什么区别？

`git pull` 命令从中央存储库中提取特定分支的新更改或提交，并更新本地存储库中的目标分支。

`git fetch` 也用于相同的目的，但它的工作方式略有不同。当你执行 `git fetch` 时，它会从所需的分支中提取所有新提交，并将其存储在本地存储库中的新分支中。如果要在目标分支中反映这些更改，必须在 `git fetch` 之后执行`git merge`。只有在对目标分支和获取的分支进行合并后才会更新目标分支。为了方便起见，请记住以下等式：

<center><h5>git pull = git fetch + git merge</h5></center>

### 3. git中的“staging area”或“index”是什么？

在完成提交之前，可以在称为“staging area”或“index”的中间区域中对其进行格式化和审查。从图中可以看出，每个更改首先在暂存区域中进行验证，我将其称为“stage file”，然后将更改提交到存储库。

![](/Users/shijinke/Pictures/2350052359-5ceccb762a5bc_fix732.png)

### 4. 什么是 git stash?

首先应该解释 git stash 的必要性。

通常情况下，当你一直在处理项目的某一部分时，如果你想要在某个时候切换分支去处理其他事情，事情会处于混乱的状态。问题是，你不想把完成了一半的工作的提交，以便你以后就可以回到当前的工作。解决这个问题的答案是 git stash。

再解释什么是git stash。

stash 会将你的工作目录，即修改后的跟踪文件和暂存的更改保存在一堆未完成的更改中，你可以随时重新应用这些更改。

### 5. 什么是git stash drop？

通过说明我们使用 `git stash drop` 的目的来回答这个问题。

`git stash drop` 命令用于删除隐藏的项目。默认情况下，它将删除最后添加的存储项，如果提供参数的话，它还可以删除特定项。

下面举个例子。

如果要从隐藏项目列表中删除特定的存储项目，可以使用以下命令：

**git stash list：**它将显示隐藏项目列表，如：

stash@{0}: WIP on master: 049d078 added the index file
stash@{1}: WIP on master: c264051 Revert “added file_size”
stash@{2}: WIP on master: 21d80a5 added number to log

如果要删除名为 stash@{0} 的项目，请使用命令 **git stash drop stash@{0}**。

### 6. 如何找到特定提交中已更改的文件列表？

对于这个问题，不能仅仅是提供命令，还要解释这个命令究竟做了些什么。

要获取特定提交中已更改的列表文件，请使用以下命令：

**git diff-tree -r {hash}**

给定提交哈希，这将列出在该提交中更改或添加的所有文件。 `-r` 标志使命令列出单个文件，而不是仅将它们折叠到根目录名称中。

你还可以包括下面提到的内容，虽然它是可选的，但有助于给面试官留下深刻印象。

输出还将包含一些额外信息，可以通过包含两个标志把它们轻松的屏蔽掉：

**git diff-tree –no-commit-id –name-only -r {hash}**

这里 `-no-commit-id` 将禁止提交哈希值出现在输出中，而 `-name-only` 只会打印文件名而不是它们的路径。

### 7. 怎样将 N 次提交压缩成一次提交？

将N个提交压缩到单个提交中有两种方式：

- 如果要从头开始编写新的提交消息，请使用以下命令：

```bash
git reset –soft HEAD~N &&
git commit
```

- 如果你想在新的提交消息中串联现有的提交消息，那么需要提取这些消息并将它们传给 git commit，可以这样：

```bash
git reset –soft HEAD~N &&
git commit –edit -m"$(git log –format=%B –reverse .HEAD@{N})"
```

### 8. 描述一下你所使用的分支策略？

这个问题被要求用Git来测试你的分支经验，告诉他们你在以前的工作中如何使用分支以及它的用途是什么，你可以参考以下提到的要点：

- 功能分支（Feature branching）

  要素分支模型将特定要素的所有更改保留在分支内。当通过自动化测试对功能进行全面测试和验证时，该分支将合并到主服务器中。

- 任务分支（Task branching）

  在此模型中，每个任务都在其自己的分支上实现，任务键包含在分支名称中。很容易看出哪个代码实现了哪个任务，只需在分支名称中查找任务键。

- 发布分支（Release branching）

  一旦开发分支获得了足够的发布功能，你就可以克隆该分支来形成发布分支。创建该分支将会启动下一个发布周期，所以在此之后不能再添加任何新功能，只有错误修复，文档生成和其他面向发布的任务应该包含在此分支中。一旦准备好发布，该版本将合并到主服务器并标记版本号。此外，它还应该再将自发布以来已经取得的进展合并回开发分支。

最后告诉他们分支策略因团队而异，所以我知道基本的分支操作，如删除、合并、检查分支等。

### 9. 如果分支是否已合并为master，你可以通过什么手段知道？

答案很直接。

要知道某个分支是否已合并为master，你可以使用以下命令：

`git branch –merged` 它列出了已合并到当前分支的分支。

`git branch –no-merged` 它列出了尚未合并的分支。

### 10. 提交时发生冲突，你能解释冲突是如何产生的吗？你是如何解决的？
开发过程中，我们都有自己的特性分支，所以冲突发生的并不多，但也碰到过。诸如公共类的公共方法，我和别人同时修改同一个文件，他提交后我再提交就会报冲突的错误。
发生冲突，在IDE里面一般都是对比本地文件和远程分支的文件，然后把远程分支上文件的内容手工修改到本地文件，然后再提交冲突的文件使其保证与远程分支的文件一致，这样才会消除冲突，然后再提交自己修改的部分。特别要注意下，修改本地冲突文件使其与远程仓库的文件保持一致后，需要提交后才能消除冲突，否则无法继续提交。必要时可与同事交流，消除冲突。
发生冲突，也可以使用命令。

通过git stash命令，把工作区的修改提交到栈区，目的是保存工作区的修改；
通过git pull命令，拉取远程分支上的代码并合并到本地分支，目的是消除冲突；
通过git stash pop命令，把保存在栈区的修改部分合并到最新的工作空间中；

### 11. 如果本次提交误操作，如何撤销？

如果想撤销提交到索引区的文件，可以通过git reset HEAD file；如果想撤销提交到本地仓库的文件，可以通过git reset –soft HEAD^n恢复当前分支的版本库至上一次提交的状态，索引区和工作空间不变更；可以通过git reset –mixed HEAD^n恢复当前分支的版本库和索引区至上一次提交的状态，工作区不变更；可以通过git reset –hard HEAD^n恢复当前分支的版本库、索引区和工作空间至上一次提交的状态。

### 12. 如果我想修改提交的历史信息，应该用什么命令？



