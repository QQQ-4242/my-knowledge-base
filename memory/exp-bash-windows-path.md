---
name: ""
metadata: 
  node_type: memory
  originSessionId: e6878897-356c-4578-b554-ba3e075dcf5f
---

# Bash Windows 路径错误

**错误现象**：在 Git Bash 中执行 `ls -la "C:\Users\hp\..."` 时报 `unexpected EOF while looking for matching '"'`，命令直接失败。

**根本原因**：Windows 路径中的反斜杠 `\` 在 Bash 中被当作转义字符，与双引号交互导致解析混乱。

**修复方法**：将路径转为 Unix 风格，例如 `C:\Users\hp\.claude\` → `/c/Users/hp/.claude/`，`Glob` 和 `Write` 工具则可以直接使用 Windows 路径。

**Why:** 避免重复踩坑，节省调试时间。
**How to apply:** 在 Bash 工具中始终使用 `/c/...` 格式；Glob/Write/Read 等工具可以用原生 Windows 路径。
