---
name: exp-python-edit-html-pitfalls
description: Python 修改大型 HTML 文件的常见失误：字符串匹配失败、内联onclick引号冲突、函数作用域
metadata: 
  node_type: memory
  type: feedback
  originSessionId: e6878897-356c-4578-b554-ba3e075dcf5f
---

# Python 修改 HTML 文件的常见坑

**本次对话中反复出现的错误**：

1. **字符串匹配失败**：用 `content.count(old)` + `content.replace(old, new)` 时，old 字符串因缩进（tab vs space）、换行符（CRLF vs LF）的细微差异而匹配不到。解决：先用 `find()` 定位再用 `repr()` 确认精确内容。

2. **内联 onclick 引号地狱**：在 JS 字符串中拼接 HTML 的 onclick 属性时，多层引号嵌套（Python → JS → HTML）极难正确转义。解决：用 `data-action` 属性 + 事件委托替代 inline onclick。

3. **bytes literal 不支持中文**：`b'中文'` → SyntaxError。解决：用 `'中文'.encode('utf-8')` 单独转换后拼接。

4. **heredoc 中的 `enc()` 函数作用域**：多个 `python << 'PYEOF'` 脚本是独立运行的，前一个脚本定义的函数在后一个中不可用。解决：每个脚本自包含，或写 .py 文件执行。

5. **修改大型文件没有备份**：每次修改都直接覆盖原文件，出错后无法回滚。建议：修改前先 copy 一份 `.bak`。

**Why:** 这些坑浪费了本次对话 60% 以上的时间。
**How to apply:** 修改 HTML 前先备份 → 二进制模式操作 → 用 data-action 替代 onclick → 每步 `node --check` 验证。
