---
name: experience-bank
description: 经验库使用约定 — 用户说「记录经验」时触发，扫描对话提取错误和修复方法写入 memory/
metadata: 
  node_type: memory
  type: project
  originSessionId: e6878897-356c-4578-b554-ba3e075dcf5f
---

# 经验库约定

当用户说 **"记录经验"**（或 save lessons / record experience），执行以下流程：

1. 扫描本轮对话，提取所有遇到的错误和修复过程
2. 每条经验去重（已有则跳过），精简为：**错误现象 → 根本原因 → 修复方法**
3. 每个独立经验写入一个 memory 文件，用 `type: feedback` 和合适的 description
4. 更新 MEMORY.md 索引
5. 告知用户：提取了多少条、新增多少条、跳过多少条

**文件命名**：`exp-{简短描述}.md`

**格式要求**：
- 每条经验 ≤ 200 字
- 必须包含：错误现象、根本原因、修复方法
- 标签用 `type: feedback`

**Why:** 积累每次对话中的经验教训，下次会话自动加载，避免重复犯错。
**How to apply:** 下次遇到类似错误时，先查 MEMORY.md 中的经验库。
