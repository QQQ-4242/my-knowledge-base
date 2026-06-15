---
name: cognitive-analysis-rule
description: 对话认知分析规则：有新发现才发，没有就跳过
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 8aeb2460-d09c-4679-b06d-ffdffa1cabaf
---

# 认知分析规则

对用户聊天方式/思维逻辑/表达方式的分析，遵循：

- **有新发现时**：简短报告，不超过 5 行的对比表格
- **无明显变化时**：不提，跳过，不硬凑
- **目的**：帮助用户觉察自己的思维模式和进步，不是自我审视的压力

**Why:** 用户认同此分析有价值，但不应成为每轮负担
**How to apply:** 每次回应末尾自检——"这次的聊天有新的认知发现吗？"没有就不发
