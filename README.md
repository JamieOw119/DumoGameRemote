# Dumo Game Remote Test

## 1. 前言

本仓库为`渡漠游科`远程工作能力测试第一部分：`协同开发`所使用

1. 为了传输安全性和身份认证，务必使用 SSH 方式。
2. 所有修改示例都在 `test_record` 文件中，本文档仅作说明用途。

## 2. 仓库创建、下载和关联

1. 远程创建后下载
- 登陆 GitHub 创建本仓库
- `git clone git@github.com:JamieOw119/DumoGameRemote.git`

2. 本地创建空仓库
```
echo "# DumoGameRemote" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin git@github.com:JamieOw119/DumoGameRemote.git
git push -u origin master
```

3. 本地上传非空仓库
```
git remote add origin git@github.com:JamieOw119/DumoGameRemote.git
git branch -M master
git push -u origin master
```

## 3. 仓库修改、提交和拉取

1. 修改：test_record: first time to update

2. 提交：
```
git add .
git commit -n "1"
git push origin master
``` 

3. 远程修改：
    - test_record: second time to update 
    - commit it on GitHub

4. 拉取：
```
git pull origin master
```

## 4. 版本回退、撤销修改

不同情况下的版本回退
```
注 1：不同 reset 参数的区别
mixed：将指定 commit id 撤回之后所有内容全部放进工作区中
soft：将指定 commit id 撤回之后所有内容全部放进暂存区。
hard：将指定 commit id 撤回并清空工作目录及暂存区所有修改
```

1. 还未添加到 stage（not add）
```
test_record: third time to update
git reset --hard [hash id of commit version 2]
```

2. 添加到 stage 但是没有提交到 repository（added but not commit）
```
test_record: third time to update
git add .
git commit -m "3"
git reset --hard [hash id of commit version 2]
```

3. 提交到本地 repository（commited but not push）
```
test_record: third time to update
git add .
git commit -m "3"
git reset --hard [hash id of commit version 2]
```

可见在没有上传到远程的时候，合理搭配不同参数即可发挥回退作用。

4. 推送到远程 repository (pushed)
```
test_record: third time to update
git add .
git commit -m "3"
git push origin master
git reset --hard [hash id of commit version 2]
```
如果想和远程保持一致，则`git pull origin master`
如果想和本地保持一致，则`git push origin master --force`

5. 撤回修改
`git checkout -- [filename]`
```
注 2：回退的范围
修改后还没有被放到暂存区：撤销修改就回到和版本库一模一样的状态；
已经添加到暂存区后，又作了修改：撤销修改就回到添加到暂存区后的状态。
```

## 5. 分支控制

1. 创建分支
```
git checkout -b dev
```
或者
```
git branch dev
git checkout dev
```

2. 合并分支
```
(on branch "dev")
test_record: force time to update
git add .
git commit -m "4"
git push origin dev
```
- 如果从本地合并`git merge dev`
- 如果从远程拉取`git pull origin dev`

3. 解决冲突
```
(on branch "dev")
test_record: fifth time to update by branch dev
git add .
git commit -m "5"
git push origin dev
(on branch "master")
test_record: fifth time to update by branch master
git add .
git commit -m "5"
git push origin master

git merge dev
test_record 手动修改为 master 自己的版本

git log --graph --pretty=oneline --abbrev-commit
*   c63470b (HEAD -> master) fix conflict
|\
| * 767bc62 (origin/dev, dev) 5
* | 7edffac (origin/master) 5
|/
* 75ef109 clear dev branch
* 6e42c80 4
* 46f82ed clear master branch
* 4e20a41 3
* 1675cb2 2
* 8b6e3fb 1
```

4. 变基

- 去除分支合并记录
```
git rebase
手动修正 merge conflict
git rebase --continue
git log --graph --pretty=oneline --abbrev-commit
* e66aa84 (HEAD -> master) fix conflict
* 7edffac (origin/master) 5
* 75ef109 clear dev branch
* 6e42c80 4
* 46f82ed clear master branch
* 4e20a41 3
* 1675cb2 2
* 8b6e3fb 1
```
- 合并 commit
```

```

5. 删除分支
```
git branch -D dev
```

## 6. 自定义 Git
1. 忽略特殊文件
2. 配置别名