# 已有仓库克隆到新仓库

- 先将已有仓库撤销所有更改和删除所有新建被跟踪的文件
  ```bash
  git checkout . && git clean -df

  # 或使用GUI工具操作
  ```

- 删除除了当前分支（如：develop）以外的本地分支
  ```bash
  git branch | grep -v "^develop$" | xargs git branch -D
  ```

- 删除服务器已经删除但本地仍然存在的分支
  ```bash
  git remote prune origin
  ```

- 处理本地未跟踪的分支，并拉取最新
  ```bash
  git branch -r | grep -v '\->' | sed "s,\x1B\[[0-9;]*[a-zA-Z],,g" | while read remote; do git branch --track "${remote#origin/}" "$remote"; done
  git fetch --all
  git pull --all
  ```

- 删除仓库与远程仓库的关联，并添加新仓库的关联
  ```bash
  git remote remove origin

  git remote add origin ssh://git@xxxxxxxx/xxxxx.git
  ```

- 推送所有分支和Tag
  ```bash
  git push -u origin --all

  git push -u origin --tags
  ```

- 搞定，收工，又加鸡腿！
