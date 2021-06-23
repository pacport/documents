# 开发团队github开发流程指南

[TOC]

本文定位于为使用GIT标准分支开发流程的开发团队新人提供一份参考指南，其中的内容为[我们公司](https://pacport.co.jp)研发团队所遵循的一些开发流程标准。

## 分支流程说明

### 简介

项目中长期存在的两个分支

* `main`：主分支，负责记录上线版本的迭代，该分支代码与线上代码是完全一致的。 `main`
* `develop`：开发分支，该分支记录相对稳定的版本，所有的feature分支和bugfix分支都从该分支创建。
* `main` 和 `develop` 分支为受保护分支，不接受直接push

其它分支为短期分支，其完成功能开发之后需要删除

* `feature/*`：特性（功能）分支，用于开发新的功能，不同的功能创建不同的功能分支，功能分支开发完成并自测通过之后，需要合并到 **develop** 分支，之后删除该分支。
* `bugfix/*`：bug修复分支，用于修复不紧急的bug，普通bug均需要创建bugfix分支开发，开发完成自测没问题后合并到 **develop** 分支后，删除该分支。
* `release/*`：发布分支，用于代码上线准备，该分支从**develop**分支创建，创建之后由测试同学发布到测试环境进行测试，测试过程中发现bug需要开发人员在该release分支上进行bug修复，所有bug修复完后，在上线之前，需要合并该release分支到**master**分支和**develop**分支。
* `hotfix/*`：紧急bug修复分支，该分支只有在紧急情况下使用，从**master**分支创建，用于紧急修复线上bug，修复完成后，需要合并该分支到**master**分支以便上线，同时需要再合并到**develop**分支。

### 必读文章

[团队中的 Git 实践](http://www.open-open.com/lib/view/open1461324562769.html)

[Git 在团队中的最佳实践--如何正确使用Git Flow](http://www.open-open.com/lib/view/open1451353135339.html)

## 分支命令规范

### 特性（功能）分支

功能分支的分支名称应该为能够准确描述该功能的英文简要表述

    feature/分支名称

例如，开发的功能为 *新增邮件通知功能*，则可以创建名称为 `feature/email-notify-add`的分支。

### bug修复分支、紧急bug修复分支

bug修复分支的分支名称可以为Jira中bug代码或者是描述该bug的英文简称

    bugfix/分支名称
    hotfix/分支名称

比如，修复的bug在jira中代号为**MATERIAL-1**，则可以创建一个名为`bugfix/MATERIAL-1`的分支。

### release分支

release分支为预发布分支，命名为本次发布的主要功能英文简称

    release/分支名称

比如，*新增邮件通知功能*，则可以创建名称为 `release/email-notify-add`的分支。

## 常用操作命令简介

推荐使用 [hub](https://github.com/github/hub) 代替git命令

### 基本操作

* git commit
* git add [--all]
* git push
* git pull
* git branch [-d]
* git merge
* git cherry-pick
* git checkout [-b] BRANCH_NAME
* git stash
