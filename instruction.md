为 restic diff 增加快照与本地目录的对比能力。

当前 restic diff 只能对比两个快照（diff snapshotID snapshotID）。请增加：当只提供一个 snapshotID 时，把该快照与本地目录对比，输出相对于快照的变更。restic diff snapshotID 配合 --target 指定目录（缺省为当前目录），对比快照内容与本地目录。输出三类变更：本地有而快照没有（added）、快照有而本地没有（removed）、两边都有但内容不同（modified）。仍支持快照内子路径语法 snapshotID:subfolder。只比较文件是否存在与内容是否相同，不比较元数据（mtime、权限等），与现有 diff 语义一致。提供两个 snapshotID 时保持现有行为不变。本地目录不存在或无法读取时，报错并退出非 0。
