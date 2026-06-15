---
name: exp-windows-crlf-js-strings
description: Windows下Python修改HTML文件时，JS字符串中的\n被写成真实换行符导致语法错误
metadata: 
  node_type: memory
  type: feedback
  originSessionId: e6878897-356c-4578-b554-ba3e075dcf5f
---

# Windows CRLF 导致 JS 字符串断裂

**错误现象**：用 Python 修改 HTML 文件中的 JavaScript 代码后，`node --check` 报 `SyntaxError: Invalid or unexpected token`，JS 字符串中的 `\n`（如 `'\n'`、`'\\n'`）变成了真实的换行符，导致字符串断裂在多行。

**根本原因**：三个因素叠加：
1. Windows 文本模式 `open()` 自动将 `\n` 转为 `\r\n`，写入时又转回去，但 JS 字符串中的 `\n` 也被错误转换
2. Python heredoc `<< 'PYEOF'` 中的 `\\n` 在 bytes literal 里的转义层级容易出错
3. 文件混用 CRLF/LF 行尾，Python `repr()` 输出歧义，难以区分 `0x0A`（真换行）和 `5C 6E`（JS转义序列）

**修复方法（按可靠度排序）**：
1. ✅ **最可靠**：二进制模式 `'rb'`/`'wb'` + 显式字节构造，如 `BS = b'\x5c'; N = b'\x6e'; NN = BS + N + BS + N`
2. ✅ 用 `.encode('utf-8')` 单独编码中文字符串，再拼接到 bytes 中
3. ⚠️ 文本模式操作后立即用 `node --check temp.js` 验证

**Why:** 避免重复踩坑，节省数小时调试时间。这是本次对话中反复出现的核心错误。
**How to apply:** 修改嵌有 JS 的 HTML 文件时，始终用二进制模式 + 显式字节构造 + 每步验证 `node --check`。
