# 1.工作区，暂存区，版本库

工作区 **workapsce**

暂存区 **index**

版本库 **repsitory**

# 2.git配置

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

3.



# 3.git rm 

1. 如果要删除所有缓存，需要加上`-r`,意为递归（**recursively**）

```
git rm --catched . -r
```



# 4.git diff



# 5.撤销

```
git checkout .
```



# 6.git commit -a

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





# 60.git在vscode中的使用











shell 

touch

```shell
touch 1.txt 2.txt 3.txt 
```

cat





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













