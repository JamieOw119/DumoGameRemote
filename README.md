# Dumo Game Remote Test

## 1. 前言

本仓库为`渡漠游科`远程工作能力测试第一部分：`协同开发`所使用

1. 为了传输安全性和身份认证，务必使用 SSH 方式。
2. 所有修改示例都在 `test_record` 文件中，本文档仅作说明用途。

## 2. 仓库创建和下载

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

### 3. 仓库修改、提交和拉取

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

### 4. 版本回退、撤销修改

不同情况下的版本回退
```
注：不同 reset 参数的区别
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

