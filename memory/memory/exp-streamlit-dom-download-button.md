---
name: exp-streamlit-dom-download-button
description: Streamlit 1.58 Windows — st.download_button在任何条件块触发DOM removeChild错误
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 18c4889c-fa0b-44d9-8992-78fc7e64b74f
---

# Streamlit 1.58 DOM removeChild 错误

**错误现象**：Streamlit 页面点按钮后出现 JavaScript 错误 "未能在节点上执行removeChild：被移除的节点不是该节点的子节点"。按钮本身功能正常但红色报错框干扰使用。

**根本原因**：Streamlit 1.58 在 Windows 中文环境下，`st.download_button` 在任何条件块（`if check_mode:`、`try:`、`st.columns`）内渲染时，内部 DOM 节点管理会出现竞态。重新渲染时 Streamlit 尝试移除已被浏览器回收的节点。

**修复方法**：
1. 所有 `st` 组件（success/markdown/caption/download_button）移到条件块外
2. 引擎计算结果存 `st.session_state`（纯数据，无 DOM）
3. 显示区用 `st.session_state.pop()` 读取结果后独立渲染
4. 按钮用 `on_click` 回调替代返回值判断
5. 不用 `st.rerun()` 触发二次渲染

**适用版本**：Streamlit ≤1.58，Windows 中文。
