# Dumo Game Remote Test

## 1. 前言

本仓库为`渡漠游科`远程工作能力测试第一部分：`协同开发`所使用

## 2. 备注

1. 为了传输安全性和身份认证，务必使用 SSH 方式。
2. 所有修改示例都在 `test_record` 文件中，本文档仅作说明用途。

## 3. 仓库创建和下载

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

### 4. 仓库修改、提交和拉取

1. test_record: first time to update.
2. 