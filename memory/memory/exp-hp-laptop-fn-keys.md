---
name: exp-hp-laptop-fn-keys
description: HP笔记本F键默认功能键，F1-F12需Fn组合，调试指令必须明确Fn+F12
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 8aeb2460-d09c-4679-b06d-ffdffa1cabaf
---

# HP 笔记本 F 键

用户设备：HP 笔记本，F 键默认是功能键（静音、飞行模式等）。

## 规则
- 所有涉及 F1-F12 的操作指令，必须写成 **Fn + Fx**
- 例：Fn + F12 = 开发者工具，Fn + F5 = 刷新
- 不能只说"按 F12"，用户按了没反应

**Why:** 之前说"按 F12"用户找不到，因为 HP 笔记本按 F12 是飞行模式
**How to apply:** 每次给快捷键指令前加 Fn
