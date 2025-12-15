# Git 版本控制系统总结

## 一、基本思想

Git 是一个**分布式版本控制系统**，其核心思想是：

- **快照而非差异**：Git 不像其他版本控制系统那样记录文件差异，而是记录每次提交时文件的完整快照
- **完整性保障**：所有内容在存储前都经过 SHA-1 哈希计算，确保数据的完整性和版本的可追溯性
- **分布式架构**：每个开发者都拥有完整的仓库副本，包括完整的历史记录，无需依赖中央服务器即可进行大部分操作
- **本地化操作**：大多数操作在本地完成，速度快且不依赖网络

## 二、基本概念与操作

### 1. 本地仓库与远程仓库

**本地仓库（Local Repository）**
- 存储在开发者本地计算机上
- 包含完整的历史记录和所有分支
- 通过 `git init` 初始化本地仓库
- 通过 `git clone <远程仓库地址>` 克隆远程仓库到本地

**远程仓库（Remote Repository）**
- 存储在远程服务器上（如 GitHub、GitLab、Gitee）
- 作为团队成员间的协作中心
- 常见的远程仓库操作：
  ```bash
  git remote add origin <url>      # 添加远程仓库（origin）为默认远程仓库
  git remote -v                    # 查看远程仓库信息
  git remote remove origin         # 删除远程仓库
  ```
- *注*：远程仓库的关联信息存在本地
### 2. Commit（提交）

**Commit** 是 Git 的核心概念，代表一次版本快照：

- 每次提交都会生成一个唯一的 **SHA-1 哈希值**作为标识
- 提交包含：文件快照、提交者信息、时间戳、提交说明
- 相关操作：
  ```bash
  git add <文件>                    # 将文件添加到暂存区
  git commit -m "提交说明"          # 提交暂存区的内容
  git status                        # 查看工作区和暂存区状态
  git log                           # 查看提交历史
  ```

提交的三区概念：
- **工作区（Working Directory）**：本地的直接用于编辑的文件目录
- **暂存区（Staging Area）**：准备提交的文件的暂存区域
- **仓库区（Repository）**：保存提交历史的区域

文件修改的四种类型：
1. **新增文件（New/Untracked）**
    - 新创建的文件，尚未被 Git 跟踪
    - `git status` 显示为 "Untracked files"
    - 需要 `git add <文件名>` 将其添加到跟踪列表
2. **修改文件（Modified）
    - 已跟踪的文件内容发生了改变
    - `git status` 显示为 "Changes not staged for commit"
    - 需要 `git add <文件名>` 将修改添加到暂存区
3. **删除文件（Deleted）**
    - 已跟踪的文件被删除
    - `git status` 显示为 "Changes not staged for commit" 或 "deleted"
    - 可以使用 `git rm <文件名>` 直接从工作区和暂存区删除，或 `git add <文件名>` 将删除操作添加到暂存区
4. **移动/重命名文件（Moved/Renamed）**
    - 已跟踪的文件被移动位置或重命名
    - Git 会自动检测到这是一个「移动/重命名」操作（如果内容变化不大）
    - `git status` 显示为 "renamed" 或 "new file" 和 "deleted"（如果未自动识别）
    - 可以使用 `git mv <旧文件名> <新文件名>` 来执行移动/重命名操作，并自动暂存变更

**实际示例：**

```bash
# 查看文件状态
git status

# 输出示例：
Untracked files:         <- 新增文件
  (use "git add <file>..." to include in what will be committed)
      newfile.txt

Changes not staged for commit:  <- 修改/删除文件
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
      modified: modified_file.txt
      deleted:  deleted_file.txt
```

### 3. Pull 与 Push

**Pull（拉取）**
- 从远程仓库获取更新并合并到本地分支
- 相当于 `git fetch`（获取更新） + `git merge`（合并）
  ```bash
  git pull                         # 默认从origin拉取
  git pull origin master           # 拉取远程 master 分支到本地
  git pull --rebase origin master  # 使用 rebase 方式拉取
  ```
- pull时远程仓库的文件与是否会冲突见[**合并的基础逻辑**](#合并的基础逻辑)（pull的过程也可以视作远程分支与本地分支的合并）

**Push（推送）**
- 将本地提交推送到远程仓库
  ```bash
  git push origin master           # 推送本地 master 分支到远程
  git push -u origin master        # 推送并设置上游分支（首次推送常用）
  git push --force origin master   # 强制推送（谨慎使用）
  ```

### 4. 分支与 Merge

#### 分支（Branch）
##### 分支的作用
分支是Git的“平行宇宙”功能，让你能在**不影响主线代码**的情况下：
1. **安全实验**：在新分支尝试新功能，失败了直接删除，不会影响稳定版本
2. **并行开发**：团队成员可以同时开发不同功能，互不干扰
3. **版本隔离**：生产环境、测试环境、开发环境可以用不同分支管理
4. **问题修复**：线上出现紧急bug时，可以创建热修复分支，快速修复而不影响正在开发的新功能

**现实比喻**：就像在写论文时，保留一份稳定的原稿，然后复制一份副本进行大幅修改，改好了再替换原稿。

##### 分支的简单操作

```bash
# 查看所有分支（*表示当前所在分支）
git branch

# 创建新分支（基于当前分支创建副本）
git branch feature-login

# 切换到指定分支
git checkout feature-login

# 创建并立即切换到新分支（最常用）
git checkout -b feature-payment

# 删除已合并的分支（清理完成的工作）
git branch -d feature-login

# 强制删除未合并的分支
git branch -D experimental
```

#### Merge（合并）
##### 合并的基础逻辑
合并是将分支的更改整合到另一个分支的过程，主要有两种方式：

**1. 快进合并（Fast-forward）**
- **条件**：目标分支没有新的提交
- **过程**：直接将指针向前移动
- **示意图**：
  ```
  合并前：main: A — B
            
       branch: A — B — C — D
          
  合并后：main: A — B — C — D
  ```

**2. 三方合并（3-way merge）**
- **条件**：目标分支也有新提交
- **过程**：创建新的合并提交，连接两个分支的历史
- **Git自动合并的逻辑**：
    - 如果某行代码只在**一个分支**修改过：采用修改后的版本
    - 如果某行代码在**两个分支**都有修改但**内容相同**：采用修改后的版本
    - 如果某行代码在**两个分支**修改成**不同的内容**：标记为**冲突**
- **示意图**：
  ```
  合并前：main:  A — B — E
            
      feature:  A — B — C — D
          
  合并后：main: A — B — E — F（合并提交）
                    \     /
                     C — D
  ```

**实际操作**：
```bash
# 第一步：确保你在目标分支上
git checkout main

# 第二步：合并功能分支
git merge feature-search

# 第三步：删除已合并的功能分支（可选）
git branch -d feature-search
```

##### 冲突原因与处理

**冲突发生的原因**：
当两个分支修改了同一文件的同一区域，Git无法自动判断应该保留哪个版本。

**典型冲突场景**：
1. 你和同事改了同一个函数的实现
2. 分支A删除了某行代码，在分支B修改了这行代码
3. 同一文件的相同位置有不同的内容

**冲突解决步骤**：
```bash
# 1. 尝试合并时遇到冲突
git merge feature-login
# 输出：Auto-merging failed. Fix conflicts and then commit the result.

# 2. 查看冲突状态
git status
# 会显示"Unmerged paths"和冲突文件列表

# 3. 打开冲突文件，Git已标注出冲突位置
<<<<<<< HEAD
这是主分支的内容
=======
这是feature-login分支的内容
>>>>>>> feature-login

# 4. 手动编辑文件解决冲突
# - 保留需要的内容
# - 删除 <<<<<<<, =======, >>>>>>> 这些标记行
# - 保存文件

# 5. 标记冲突已解决
git add 冲突文件名

# 6. 完成合并提交
git commit -m "合并feature-login，解决冲突"

# 或使用合并工具（可视化界面更友好）
git mergetool
```

## 三、工作流建议

**基础使用流程**：

```
关联本地与远程仓库 → 修改本地文件 → 向本地仓库提交更改（commit） → 先拉取（pull）远程仓库内容以同步，再推送（push）到远程仓库
```

## 四、常用命令速查

| 操作 | 命令 |
|------|------|
| 初始化仓库 | `git init` |
| 克隆仓库 | `git clone <url>` |
| 查看状态 | `git status` |
| 添加文件 | `git add <file>` |
| 提交更改 | `git commit -m "message"` |
| 查看历史 | `git log` |
| 创建分支 | `git branch <name>` |
| 切换分支 | `git checkout <name>` |
| 合并分支 | `git merge <branch>` |
| 拉取更新 | `git pull` |
| 推送更新 | `git push` |
| 查看差异 | `git diff` |

Git 的强大之处在于其灵活性和强大的分支管理能力，使得团队协作和版本控制变得更加高效和可靠。掌握这些基本概念和操作是使用 Git 进行日常开发的基础。