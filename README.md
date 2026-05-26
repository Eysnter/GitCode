# Git 常用命令
---

[](https://drive.google.com/file/d/1jS95zsQ9A8fx22svvH4zs4kBDSTrWS3j/view)

# 一、基础配置

```bash
git config --global user.name "YourName"
git config --global user.email "your@email.com"
```

📌 设置 Git 提交身份（全局生效）

查看当前配置：

```bash
git config --list
```

关闭 Windows 自动换行转换：

```bash
git config --global core.autocrlf false
```

---

# 二、创建仓库

## 初始化本地仓库

```bash
git init
```

## 克隆远程仓库

```bash
git clone <repo-url>
```

💡 clone 后会自动关联远程仓库 `origin`

---

# 三、提交代码

## 查看状态

```bash
git status
```

📌 最常用命令，先看状态再操作

---

## 添加文件到暂存区

```bash
git add <file>
git add .
```

- `git add .`：添加当前目录全部修改

---

## 提交代码

```bash
git commit -m "提交说明"
```

---

## 查看提交历史

```bash
git log
git log --oneline
```

💡 `q` 退出日志界面

---

## 查看改动

```bash
git diff
git diff --staged
```

- `git diff`：工作区 vs 暂存区
- `--staged`：暂存区 vs 最近提交

---

# 四、分支管理

## 查看分支

```bash
git branch
```

当前分支前有 `*`

---

## 创建分支

```bash
git branch dev
```

---

## 切换分支

```bash
git checkout dev
```

---

## 创建并切换（最常用）

```bash
git checkout -b dev
```

---

## 查看当前分支

```bash
git branch --show-current
```

---

## 合并分支

```bash
git merge dev
```

📌 将 `dev` 合并到当前分支

---

## 删除分支

```bash
git branch -d dev
```

强制删除：

```bash
git branch -D dev
```

⚠️ 未合并代码也会删除

---

# 五、远程仓库操作

## 查看远程仓库

```bash
git remote -v
```

---

## 推送代码

```bash
git push origin main
```

首次推送推荐：

```bash
git push -u origin main
```

📌 建立本地与远程跟踪关系

---

## 拉取代码

```bash
git pull origin main
```

等价于：

```bash
git fetch
git merge
```

---

## 获取远程更新（更安全）

```bash
git fetch
```

📌 只下载，不自动合并

---

# 六、撤销操作（高频）

## 撤销工作区修改

```bash
git restore <file>
```

📌 文件未 add 时使用

---

## 撤销暂存区

```bash
git restore --staged <file>
```

📌 已 add 但未 commit

---

## 回退到上一次提交

```bash
git reset --hard HEAD^
```

⚠️ 会永久丢失未提交代码！

---

## 安全撤销提交

```bash
git revert <commit-id>
```

📌 推荐团队协作使用

---

# 七、解决冲突

出现冲突时会看到：

```text
<<<<<<< HEAD
你的代码
=======
别人的代码
>>>>>>> commit-id
```

处理步骤：

1. 手动修改文件
2. 删除冲突标记
3. 重新提交

```bash
git add <file>
git commit
```

---

# 八、Stash 临时保存

## 暂存当前修改

```bash
git stash
```

📌 临时切换分支非常好用

---

## 恢复暂存

```bash
git stash pop
```

---

# 九、标签 Tag

## 查看标签

```bash
git tag
```

---

## 创建标签

```bash
git tag v1.0
```

---

## 推送标签

```bash
git push origin v1.0
```

推送全部标签：

```bash
git push origin --tags
```

---

# 十、远程分支管理

## 查看所有分支

```bash
git branch -a
```

---

## 删除远程分支

```bash
git push origin --delete dev
```

---

## 清理无效远程分支

```bash
git remote prune origin
```

---

# 十一、实用技巧

## 查看最近操作记录

```bash
git reflog
```

📌 后悔药命令，可找回误删提交

---

## 查看谁改了某行代码

```bash
git blame <file>
```

---

## 查看最近5次提交

```bash
git log -5 --oneline
```

---

## 查看今天写了多少代码

```bash
git diff --shortstat "@{0 day ago}"
```

---

# 十二、危险命令（慎用）

## 强制覆盖本地代码

```bash
git fetch --all
git reset --hard origin/master
```

⚠️ 本地修改会全部消失

---

## 强制推送

```bash
git push --force
```

⚠️ 可能覆盖别人代码

推荐使用：

```bash
git push --force-with-lease
```

---

# 十三、开发流程（推荐）

```text
拉代码 → 新建分支 → 开发
→ git add .
→ git commit
→ git push
→ 提交合并请求
```

---

#  Git 记忆口诀

✅ 改代码先 `add` 再 `commit`  
✅ 同步代码用 `pull`  
✅ 上传代码用 `push`  
✅ 功能开发开新分支  
✅ 回退慎用 `reset --hard`  
✅ 冲突解决后记得 `add + commit`

---

# 高频命令

```bash
git status
git add .
git commit -m "msg"
git pull
git push

git checkout -b dev
git merge dev

git stash
git stash pop

git log --oneline
git reflog

git restore .
git reset --hard HEAD^
```

