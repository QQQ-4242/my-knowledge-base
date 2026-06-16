---
name: novel-writer-project
description: 小说写作工坊 — 已完成全部核心功能，已上传 GitHub
metadata: 
  node_type: memory
  type: project
  originSessionId: e6878897-356c-4578-b554-ba3e075dcf5f
---

# 小说写作工坊

**GitHub**: https://github.com/QQQ-4242/novel-writer
**文件**: `D:\claude code 文件夹\novel-writer\index.html`
**状态**: v1.0 已完成

## 已完成功能

- Markdown 编辑器 + 实时预览 + 分屏拖拽
- AI 写作（续写/扩写），支持 Anthropic / OpenAI / DeepSeek
- 全书大纲：30 层递归树，大情节/子情节层级视觉区分，角标可点击切换类型/删除
- AI 关键节点自动识别（冲突/转折/新人物/伏笔/高潮）→ 自动加入大纲树
- 角色管理面板：姓名/性格/外貌/背景/角色关系，AI 续写扩写自动参考
- AI 审阅：6 维度（节奏/人物/逻辑/文笔/亮点/建议）
- 全文搜索：跨章节搜索 + 高亮片段 + 点击跳转
- 架构管理（卷/章拖拽排序）
- 多格式导出（TXT/MD/HTML）
- 暗色主题 + 自动保存

## 潜在改进方向

- EPUB 导出
- 写作仪表盘（字数曲线、连续天数）
- JSON 备份/恢复
- 数据云端同步

## 2026-06-15 更新

- **后端代理**：`server.py` 零依赖 Python 代理，API 密钥存 `.env` 不暴露前端
- **一键启动**：`启动小说工坊.bat`，双击即开 `http://127.0.0.1:8765`
- **大纲面板重构**：居中大窗口（800px），可拖动，纯缩进层级（一级18px粗体/二级15px/三级13px彩色标签）
- **AI 节点按章节归类**：关键节点分析勾选后自动挂到全书大纲对应章节下方
- **目录章节删除**：左侧目录 hover 出现红色 ✕，弹窗确认后删除
- **Bug 修复**：`charInfo`/`charInfo2` 未定义、`sysPrompt` 拼写错误
- **API 设置面板隐藏**（代理模式不需要前端填密钥）
- **Git 提交**：`184b901` 后端代理+大纲层级+API安全+Bug修复（待 push）

**Why:** 用户的个人代表作品，已具备展示和传播价值
**How to apply:** 有想法时继续迭代，每次改进 commit 到 GitHub
