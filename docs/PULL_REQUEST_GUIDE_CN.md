# Pull Request 更新指南

本指南说明如何在 TSMNet 仓库中更新 pull request 的代码。

## 理解 Pull Requests

Pull request (PR) 是向代码库提出更改的一种方式。当您有一个开放的 PR 时，您可能需要基于以下原因更新它：
- 审查反馈
- 基础分支的更改
- 新的需求
- Bug 修复

## 如何更新您的 Pull Request 中的代码

### 1. 在本地进行更改

首先，确保您在正确的分支上：

```bash
# 查看当前所在分支
git branch

# 如果需要，切换到您的 PR 分支
git checkout your-branch-name
```

根据需要编辑文件，然后暂存并提交更改：

```bash
# 暂存所有更改
git add .

# 或暂存特定文件
git add path/to/file.py

# 使用描述性消息提交
git commit -m "更改描述"
```

### 2. 推送更改以更新 PR

提交更改后，推送它们以更新 PR：

```bash
# 推送到远程分支
git push origin your-branch-name
```

Pull request 将自动更新为您的新提交。

### 3. 从基础分支更新

如果基础分支发生了更改，您需要合并这些更改：

```bash
# 获取最新更改
git fetch origin

# 从基础分支合并更改
git merge origin/main

# 或将您的更改变基到基础分支之上
git rebase origin/main

# 推送更新的分支（如果您进行了变基，可能需要 --force-with-lease）
git push origin your-branch-name
```

**注意：** 强制推送时使用 `--force-with-lease` 而不是 `--force`，以避免意外覆盖他人的工作。

### 4. 处理审查评论

当审查者提供反馈时：

1. 在本地分支中进行请求的更改
2. 使用清晰的消息提交更改
3. 推送以更新 PR
4. 回复审查评论以表明您已处理它们

## 最佳实践

1. **保持提交专注**：每个提交应该针对特定的更改
2. **编写清晰的提交消息**：描述更改了什么以及为什么
3. **推送前测试**：确保您的更改有效且不会破坏现有功能
4. **保持 PR 小型化**：较小的 PR 更容易审查和合并
5. **定期更新**：经常与基础分支同步以避免合并冲突

## 常见场景

### 场景 1：修复 PR 中的 Bug

```bash
# 进行修复
git add fixed-file.py
git commit -m "修复计算逻辑中的 bug"
git push origin your-branch-name
```

### 场景 2：向 PR 添加新功能

```bash
# 添加新功能
git add new-feature.py
git commit -m "添加新功能 X"
git push origin your-branch-name
```

### 场景 3：解决合并冲突

```bash
# 获取并合并基础分支
git fetch origin
git merge origin/main

# 如果有冲突，Git 会在文件中标记它们
# 编辑冲突的文件以解决冲突
# 然后暂存并提交解决方案
git add resolved-file.py
git commit -m "解决与 main 的合并冲突"
git push origin your-branch-name
```

## 获取帮助

如果遇到问题：
- 查看 [GitHub 文档](https://docs.github.com/cn/pull-requests)
- 在 PR 评论中寻求帮助
- 联系仓库维护者

## 相关命令

```bash
# 查看当前状态
git status

# 查看提交历史
git log --oneline

# 查看文件中的更改
git diff

# 查看远程分支
git branch -r

# 放弃本地更改
git checkout -- file.py

# 撤销上一次提交（保留更改）
git reset --soft HEAD~1
```

## 本仓库中的示例

在 TSMNet 仓库中，我们有以下 PR 工作流程：

1. **PR #1**: 添加 TensorBoard 日志记录功能
   - 基于 `main` 分支
   - 修改了 `experiments/main.py` 文件
   - 添加了训练指标的可视化

2. **后续 PR**: 如果需要在 PR #1 的基础上继续工作
   - 可以基于 `copilot/add-tensorboard-logging` 分支
   - 继承 PR #1 的所有更改

## 更新现有 PR 的步骤

如果您需要更新现有的 PR（例如 PR #1），请按以下步骤操作：

```bash
# 1. 切换到 PR 分支
git checkout copilot/add-tensorboard-logging

# 2. 进行必要的代码更改
# 编辑文件...

# 3. 暂存更改
git add experiments/main.py

# 4. 提交更改
git commit -m "改进 TensorBoard 日志记录逻辑"

# 5. 推送到远程仓库以更新 PR
git push origin copilot/add-tensorboard-logging
```

这样，PR #1 将自动更新为您的新更改。
