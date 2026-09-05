# 已发布分支与旧工作目录合并

当已验收功能已经合入远端 `main`，但旧正式目录处于不同历史或带未提交内容时：

1. 先 fetch，确认远端 `main`、发布 tag 和合并提交；不得把旧历史 force-push 回远端。
2. 清点 tracked、staged、untracked 内容；大量修改先用 `git diff --ignore-space-at-eol` 排除换行噪音。
3. 在系统临时目录创建可校验恢复包，包含 patch、untracked 归档、status、基线 SHA 和 SHA-256；校验通过后才对齐正式目录。
4. 恢复有价值的 untracked 文件，逐字节比对，跑全量测试和 `git diff --check`。
5. 验证后才删除冗余 worktree、临时分支和重复补丁备份。
6. 最终用路径不存在和 `git worktree list` 证明清理结果。

禁止未经确认直接 reset、覆盖、删除唯一副本或重写远端历史。
