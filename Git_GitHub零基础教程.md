# Git 与 GitHub 零基础教程

> 适合完全没接触过 Git / GitHub 的初学者。读完后，你应该能理解 Git 是什么、GitHub 是什么，并能完成：创建仓库、提交代码、查看历史、回退版本、上传到 GitHub、从 GitHub 下载项目、多人协作的基本流程。

---

## 1. Git 和 GitHub 分别是什么？

### 1.1 Git 是什么？

Git 是一个版本控制工具。

你可以把它理解成“代码的时间机器”。它可以帮你记录文件每一次重要修改，让你以后能够：

- 查看以前改了什么
- 回到某个历史版本
- 比较两个版本的差异
- 在不同功能之间并行开发
- 多人协作时合并彼此的代码

没有 Git 时，你可能会这样保存文件：

```text
项目.py
项目_修改版.py
项目_最终版.py
项目_最终不改版.py
项目_最终真的不改版.py
```

有 Git 后，你只需要保留一份项目文件，Git 会帮你记录历史版本。

### 1.2 GitHub 是什么？

GitHub 是一个代码托管平台。

Git 是本地工具，主要运行在你的电脑上；GitHub 是远程网站，用来保存和展示你的 Git 仓库。

你可以把它理解成“代码云盘 + 协作平台 + 程序员作品集”。

GitHub 可以帮你：

- 把本地代码备份到云端
- 在不同电脑之间同步代码
- 展示自己的项目
- 和别人一起开发项目
- 给开源项目提交修改建议
- 写 README、Issue、Pull Request

### 1.3 Git 和 GitHub 的关系

简单来说：

```text
Git：本地版本控制工具
GitHub：远程代码托管平台
```

类比一下：

```text
Git    ≈ 拍照和保存历史版本的工具
GitHub ≈ 存放这些照片和项目的云相册
```

Git 不依赖 GitHub 也能使用；GitHub 通常需要配合 Git 使用。

---

## 2. 为什么要学 Git 和 GitHub？

对学习 Python、做项目、找工作来说，Git 和 GitHub 都非常重要。

### 2.1 对个人学习的好处

- 写错代码后可以回退
- 每完成一个小功能就保存一次进度
- 能清楚看到自己每天做了什么
- 项目不会因为误删文件而彻底丢失
- 可以把项目传到 GitHub，方便以后复习和展示

### 2.2 对面试和工作的好处

很多公司默认开发者会使用 Git。

面试时，如果你能展示 GitHub 上的项目，比如 Python CLI 工具、Web 项目、爬虫项目，会比只说“我学过 Python”更有说服力。

你需要掌握的不是特别复杂的 Git 原理，而是日常开发最常用的一套流程。

---

## 3. 安装 Git

### 3.1 Windows 安装

访问 Git 官网：

```text
https://git-scm.com/
```

下载 Windows 版本并安装。

安装过程中大部分选项保持默认即可。

安装完成后，打开 PowerShell 或终端，输入：

```bash
git --version
```

如果看到类似下面的结果，说明安装成功：

```bash
git version 2.45.0
```

### 3.2 配置用户名和邮箱

第一次使用 Git，需要配置你的用户名和邮箱。

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

例如：

```bash
git config --global user.name "zhangsan"
git config --global user.email "zhangsan@example.com"
```

查看配置：

```bash
git config --global --list
```

这些信息会记录在每次提交里，用来表示“这次修改是谁做的”。

---

## 4. Git 的核心概念

Git 初学最重要的是理解 4 个区域。

### 4.1 工作区 Working Directory

就是你当前正在编辑的项目文件夹。

例如你的 Python 项目目录：

```text
kbman/
├── kbman/
├── tests/
├── README.md
└── pyproject.toml
```

你在这里修改代码、创建文件、删除文件。

### 4.2 暂存区 Staging Area

暂存区是“准备提交的修改列表”。

你可以选择哪些修改要进入下一次提交。

使用命令：

```bash
git add 文件名
```

或者添加当前目录下所有修改：

```bash
git add .
```

### 4.3 本地仓库 Local Repository

本地仓库保存了你的提交历史。

使用命令：

```bash
git commit -m "提交说明"
```

提交后，Git 会在本地记录一个版本。

### 4.4 远程仓库 Remote Repository

远程仓库通常放在 GitHub 上。

使用命令把本地提交推送到 GitHub：

```bash
git push
```

也可以从 GitHub 拉取别人或自己在其他电脑上的修改：

```bash
git pull
```

### 4.5 四个区域的关系

```text
工作区  --git add-->  暂存区  --git commit-->  本地仓库  --git push-->  GitHub远程仓库

GitHub远程仓库  --git pull-->  本地仓库/工作区
```

这是 Git 最核心的流程。

---

## 5. 第一个 Git 仓库

假设你有一个项目文件夹：

```text
D:\all_docoument\python\project\kbman
```

进入项目目录后执行：

```bash
git init
```

这会把当前文件夹初始化为 Git 仓库。

初始化后，Git 会创建一个隐藏目录：

```text
.git/
```

这个目录保存 Git 的版本记录，不要手动删除或修改。

---

## 6. Git 日常基础命令

### 6.1 查看当前状态

```bash
git status
```

这是最常用的命令之一。

它会告诉你：

- 哪些文件被修改了
- 哪些文件还没被 Git 跟踪
- 哪些文件已经加入暂存区
- 当前分支是什么

建议你养成习惯：每次不知道现在 Git 状态时，就运行 `git status`。

### 6.2 添加文件到暂存区

添加单个文件：

```bash
git add README.md
```

添加全部修改：

```bash
git add .
```

`git add` 并不是提交，只是把修改放到“准备提交”的区域。

### 6.3 提交版本

```bash
git commit -m "初始化项目结构"
```

提交说明应该简洁明确，说明这次做了什么。

好的提交说明：

```bash
git commit -m "添加文档模型"
git commit -m "实现知识库搜索功能"
git commit -m "修复重复文档检测问题"
```

不推荐的提交说明：

```bash
git commit -m "改了一下"
git commit -m "update"
git commit -m "111"
```

### 6.4 查看提交历史

```bash
git log
```

简洁查看：

```bash
git log --oneline
```

示例：

```text
8f3a21c 添加搜索功能
6d9b12a 添加文档模型
2a7c09e 初始化项目结构
```

每一行前面的字符串是提交 ID 的简写。

### 6.5 查看文件差异

查看工作区还没暂存的修改：

```bash
git diff
```

查看已经暂存、准备提交的修改：

```bash
git diff --staged
```

这个命令可以让你在提交前确认自己到底改了什么。

---

## 7. Git 的完整个人开发流程

日常开发时，可以按照下面流程操作：

```bash
# 1. 查看状态
git status

# 2. 修改代码
# 你在编辑器里写代码

# 3. 再次查看状态
git status

# 4. 查看修改差异
git diff

# 5. 添加到暂存区
git add .

# 6. 提交到本地仓库
git commit -m "实现某个功能"

# 7. 推送到 GitHub
git push
```

初学阶段重点记住这几个命令：

```bash
git status
git add .
git commit -m "说明"
git push
git pull
git log --oneline
```

---

## 8. .gitignore 文件

### 8.1 .gitignore 是什么？

`.gitignore` 用来告诉 Git：哪些文件不要纳入版本控制。

例如 Python 项目中常见的不需要提交的内容：

- 虚拟环境 `.venv/`
- 缓存目录 `__pycache__/`
- 测试缓存 `.pytest_cache/`
- 本地数据文件 `data/`
- 系统文件 `.DS_Store`

### 8.2 Python 项目常见 .gitignore

可以创建 `.gitignore` 文件，写入：

```gitignore
.venv/
__pycache__/
*.pyc
.pytest_cache/
.mypy_cache/
.coverage
htmlcov/
data/
.env
.DS_Store
```

### 8.3 为什么不能提交 .venv？

`.venv` 是本地虚拟环境，里面文件很多，而且和你的电脑系统有关。

正确做法是：

- 不提交 `.venv/`
- 提交 `pyproject.toml` 或 `requirements.txt`
- 让别人根据依赖配置重新创建虚拟环境

---

## 9. 回退和撤销

Git 的回退命令很强大，但初学时要谨慎使用。

### 9.1 撤销工作区某个文件的修改

如果你修改了一个文件，但还没有 `git add`，可以撤销：

```bash
git restore 文件名
```

例如：

```bash
git restore README.md
```

这会让文件回到上一次提交的状态。

### 9.2 取消暂存

如果你已经执行了 `git add`，但不想让它进入下一次提交：

```bash
git restore --staged 文件名
```

例如：

```bash
git restore --staged README.md
```

这只是把文件从暂存区拿出来，不会删除你的修改。

### 9.3 回到某个历史版本

查看历史：

```bash
git log --oneline
```

然后使用：

```bash
git checkout 提交ID -- 文件名
```

例如：

```bash
git checkout 8f3a21c -- README.md
```

这会把某个文件恢复到指定提交时的样子。

### 9.4 谨慎使用 reset

`git reset` 可以移动提交历史，初学者容易误用。

常见命令：

```bash
git reset --soft HEAD~1
```

表示撤销最近一次提交，但保留修改并放在暂存区。

```bash
git reset --hard HEAD~1
```

表示撤销最近一次提交，并丢弃修改。

注意：`--hard` 会丢失代码，初学阶段慎用。

---

## 10. 分支 Branch

### 10.1 分支是什么？

分支可以让你在不影响主线代码的情况下开发新功能。

例如：

```text
main 分支：稳定版本
feature-search 分支：正在开发搜索功能
feature-cli 分支：正在开发命令行功能
```

开发完成后，再把功能分支合并回 main。

### 10.2 查看分支

```bash
git branch
```

当前所在分支前面会有 `*`。

### 10.3 创建并切换分支

```bash
git switch -c feature-search
```

这会创建一个名为 `feature-search` 的分支并切换过去。

### 10.4 切换分支

```bash
git switch main
```

### 10.5 合并分支

先切回 main：

```bash
git switch main
```

然后合并功能分支：

```bash
git merge feature-search
```

### 10.6 删除已经合并的分支

```bash
git branch -d feature-search
```

---

## 11. 合并冲突

### 11.1 什么是冲突？

当两个分支或两个人修改了同一个文件的同一部分，Git 不知道该保留哪一份，就会产生冲突。

冲突文件中可能出现：

```text
<<<<<<< HEAD
这是你当前分支的内容
=======
这是另一个分支的内容
>>>>>>> feature-search
```

### 11.2 如何解决冲突？

解决步骤：

1. 打开冲突文件
2. 手动选择要保留的内容
3. 删除 `<<<<<<<`、`=======`、`>>>>>>>` 这些标记
4. 保存文件
5. 执行：

```bash
git add 冲突文件
git commit -m "解决合并冲突"
```

### 11.3 解决冲突的原则

- 不要慌，冲突是多人协作中的正常现象
- 先读懂两边代码分别做了什么
- 不确定时和队友沟通
- 解决后运行测试，确认功能没有坏

---

## 12. GitHub 入门

### 12.1 注册 GitHub

访问：

```text
https://github.com/
```

注册账号。

建议用户名尽量简洁、专业，因为它可能会出现在你的项目链接里。

### 12.2 创建远程仓库

登录 GitHub 后：

1. 点击右上角 `+`
2. 选择 `New repository`
3. 输入仓库名，例如 `kbman`
4. 选择 Public 或 Private
5. 点击 `Create repository`

Public 表示公开，别人可以看到。

Private 表示私有，只有你和被邀请的人能看到。

---

## 13. 把本地项目上传到 GitHub

假设你已经在本地项目中执行过：

```bash
git init
git add .
git commit -m "初始化项目"
```

然后在 GitHub 创建了一个空仓库，地址类似：

```text
https://github.com/你的用户名/kbman.git
```

执行：

```bash
git remote add origin https://github.com/你的用户名/kbman.git
git branch -M main
git push -u origin main
```

解释：

- `origin`：远程仓库的默认名字
- `branch -M main`：把当前分支命名为 main
- `push -u origin main`：把本地 main 分支推送到 GitHub，并建立默认关联

以后再次推送，只需要：

```bash
git push
```

---

## 14. 从 GitHub 下载项目

如果你想把 GitHub 上的项目下载到本地，用：

```bash
git clone 仓库地址
```

例如：

```bash
git clone https://github.com/你的用户名/kbman.git
```

这会在当前目录创建一个项目文件夹，并自动包含 Git 历史和远程地址。

---

## 15. 同步远程修改

### 15.1 拉取 GitHub 上的最新代码

```bash
git pull
```

它相当于：

```text
从 GitHub 下载最新提交 + 合并到当前分支
```

### 15.2 推送本地修改到 GitHub

```bash
git push
```

如果你和别人协作，建议每次开始写代码前先执行：

```bash
git pull
```

避免基于旧代码开发。

---

## 16. README.md

### 16.1 README 是什么？

README 是项目首页说明文档。

GitHub 会自动把 `README.md` 显示在仓库首页。

一个好的 README 可以让别人快速知道：

- 这个项目是什么
- 有什么功能
- 如何安装
- 如何运行
- 如何测试
- 项目结构是什么

### 16.2 Python 项目 README 示例结构

```markdown
# kbman

一个纯 Python 标准库实现的命令行知识库管理器。

## 功能

- 添加、查看、更新、删除文档
- 标签分类
- 全文搜索
- JSON 导入导出
- 操作日志

## 安装

```bash
pip install -e .
```

## 使用

```bash
kbman add --title "Python技巧" --content "生成器可以节省内存" --tags python,进阶
kbman list
kbman search "生成器"
```

## 测试

```bash
python -m unittest
```
```

---

## 17. Issue 和 Pull Request

### 17.1 Issue 是什么？

Issue 是 GitHub 上的任务、问题或讨论。

你可以用 Issue 记录：

- Bug
- 新功能计划
- TODO
- 使用问题
- 设计讨论

例如：

```text
Issue 标题：添加全文搜索功能
Issue 内容：目前只能按标题查找，希望支持按正文关键词搜索。
```

### 17.2 Pull Request 是什么？

Pull Request 简称 PR，意思是“请求把我的修改合并进去”。

常见流程：

1. 从 main 创建新分支
2. 在新分支开发功能
3. 推送分支到 GitHub
4. 创建 Pull Request
5. 代码审查
6. 合并到 main

对于个人项目，你也可以用 PR 模拟真实团队协作流程。

---

## 18. 个人项目推荐 Git 工作流

如果你现在是一个人开发 Python 项目，可以使用简单流程。

### 18.1 简单主线流程

适合刚入门：

```bash
git status
git add .
git commit -m "实现某功能"
git push
```

所有修改都直接提交到 main。

### 18.2 功能分支流程

适合稍微熟悉后：

```bash
# 确保 main 是最新的
git switch main
git pull

# 创建功能分支
git switch -c feature-search

# 开发、提交
git add .
git commit -m "实现搜索功能"

# 切回 main 并合并
git switch main
git merge feature-search

# 推送到 GitHub
git push

# 删除功能分支
git branch -d feature-search
```

推荐你在 `kbman` 项目里练习这种流程。

---

## 19. 常见错误和解决方法

### 19.1 fatal: not a git repository

错误含义：当前目录不是 Git 仓库。

解决：

```bash
git init
```

或者切换到正确项目目录。

### 19.2 nothing to commit, working tree clean

含义：没有需要提交的修改。

这不是错误，说明当前目录很干净。

### 19.3 remote origin already exists

含义：已经添加过名为 origin 的远程仓库。

查看远程仓库：

```bash
git remote -v
```

修改远程地址：

```bash
git remote set-url origin 新地址
```

### 19.4 failed to push some refs

常见原因：GitHub 上有本地没有的提交。

先拉取：

```bash
git pull
```

解决可能出现的冲突后，再推送：

```bash
git push
```

### 19.5 Authentication failed

GitHub 现在通常不支持直接用账号密码推送代码。

你可以使用：

- HTTPS + Personal Access Token
- SSH Key
- GitHub Desktop
- VS Code / IDE 内置登录

初学者可以先使用 GitHub Desktop 或 IDE 登录，降低配置难度。

---

## 20. SSH Key 简介

SSH Key 是一种让你的电脑安全连接 GitHub 的方式。

生成 SSH Key：

```bash
ssh-keygen -t ed25519 -C "你的邮箱"
```

一路回车即可。

查看公钥：

```bash
cat ~/.ssh/id_ed25519.pub
```

Windows PowerShell 中可以用：

```bash
Get-Content ~/.ssh/id_ed25519.pub
```

然后复制内容，添加到 GitHub：

```text
GitHub → Settings → SSH and GPG keys → New SSH key
```

测试连接：

```bash
ssh -T git@github.com
```

如果成功，会看到类似：

```text
Hi 用户名! You've successfully authenticated...
```

---

## 21. GitHub Desktop 简介

如果你刚开始觉得命令行太多，可以使用 GitHub Desktop。

它是 GitHub 官方图形化工具，适合初学者理解流程。

下载地址：

```text
https://desktop.github.com/
```

它可以帮你：

- 登录 GitHub
- 克隆仓库
- 查看修改
- 提交代码
- 推送代码
- 拉取代码
- 创建分支

不过建议你最终还是掌握命令行，因为命令行在工作中更通用。

---

## 22. 建议学习路线

### 阶段 1：只学个人开发必备命令

先掌握：

```bash
git init
git status
git add .
git commit -m "说明"
git log --oneline
git diff
```

目标：能在本地保存项目历史。

### 阶段 2：学 GitHub 远程仓库

继续掌握：

```bash
git remote add origin 仓库地址
git push -u origin main
git push
git pull
git clone 仓库地址
```

目标：能把项目上传到 GitHub。

### 阶段 3：学分支和协作

继续掌握：

```bash
git branch
git switch -c 分支名
git switch main
git merge 分支名
git branch -d 分支名
```

目标：能用分支开发功能。

### 阶段 4：学冲突解决和 PR

学习：

- 合并冲突
- Issue
- Pull Request
- Code Review

目标：理解团队协作流程。

---

## 23. 用 kbman 项目练习 Git 的完整步骤

假设你准备开发 `kbman` 项目，可以这样练习：

### 23.1 初始化项目

```bash
mkdir kbman
cd kbman
git init
```

### 23.2 创建基础文件后提交

```bash
git status
git add .
git commit -m "初始化 kbman 项目结构"
```

### 23.3 开发 Document 模型

完成 `models.py` 后：

```bash
git diff
git add kbman/models.py
git commit -m "添加 Document 数据模型"
```

### 23.4 开发 Repository

完成 `repository.py` 后：

```bash
git add kbman/repository.py
git commit -m "实现知识库 JSON 存储"
```

### 23.5 开发搜索功能

可以新建分支：

```bash
git switch -c feature-search
```

完成后提交：

```bash
git add .
git commit -m "实现倒排索引搜索"
```

合并回 main：

```bash
git switch main
git merge feature-search
git branch -d feature-search
```

### 23.6 上传到 GitHub

在 GitHub 创建空仓库后：

```bash
git remote add origin https://github.com/你的用户名/kbman.git
git branch -M main
git push -u origin main
```

---

## 24. 高频命令速查表

| 命令 | 作用 |
|---|---|
| `git init` | 初始化本地仓库 |
| `git status` | 查看当前状态 |
| `git add .` | 添加全部修改到暂存区 |
| `git add 文件名` | 添加指定文件到暂存区 |
| `git commit -m "说明"` | 提交一个版本 |
| `git log --oneline` | 简洁查看提交历史 |
| `git diff` | 查看未暂存修改 |
| `git diff --staged` | 查看已暂存修改 |
| `git restore 文件名` | 撤销工作区修改 |
| `git restore --staged 文件名` | 取消暂存 |
| `git branch` | 查看分支 |
| `git switch -c 分支名` | 创建并切换分支 |
| `git switch 分支名` | 切换分支 |
| `git merge 分支名` | 合并分支 |
| `git remote -v` | 查看远程仓库 |
| `git remote add origin 地址` | 添加远程仓库 |
| `git push -u origin main` | 第一次推送 main 到 GitHub |
| `git push` | 推送本地提交 |
| `git pull` | 拉取远程更新 |
| `git clone 地址` | 克隆远程仓库 |

---

## 25. 初学者最重要的习惯

### 25.1 经常提交

不要等项目全部写完才提交。

推荐每完成一个小功能就提交一次：

```bash
git commit -m "实现添加文档命令"
git commit -m "实现删除文档命令"
git commit -m "添加搜索功能测试"
```

### 25.2 提交前先看状态和差异

```bash
git status
git diff
```

这样可以避免把不该提交的内容提交进去。

### 25.3 不提交敏感信息

不要提交：

- 密码
- Token
- API Key
- `.env`
- 私人数据

如果不小心提交了密钥，即使后来删除，也可能仍然留在 Git 历史中。应该立即作废旧密钥，重新生成。

### 25.4 写清楚提交信息

提交信息不是给机器看的，是给未来的你和队友看的。

好的提交信息能让你几个月后快速理解项目演进过程。

---

## 26. 一句话总结

Git 负责记录代码历史，GitHub 负责远程托管和协作。

你刚开始只需要掌握这条主线：

```bash
git status
git add .
git commit -m "说明"
git push
git pull
```

等你能熟练使用这些命令后，再逐步学习分支、冲突、Pull Request 和团队协作流程。

建议你在 `kbman` 项目开发过程中就开始使用 Git：每完成一个阶段提交一次，最后上传到 GitHub。这样项目不仅能练 Python，也能练真实开发流程。
