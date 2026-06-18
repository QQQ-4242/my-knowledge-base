---
name: project-a-progress
description: 方案A项目（工程量自动汇总器）当前进度
metadata: 
  node_type: memory
  type: project
  originSessionId: 04a4377e-ffe0-4c25-922b-8a0132f02c97
---

# 方案 A 项目进度

## 已完成
- [x] 环境搭建：Python + pandas + openpyxl + streamlit + requests
- [x] hello.py 逐行理解
- [x] create_excel.py / read_excel.py（分组+筛选+汇总）
- [x] ai_text.py（剪贴板读取 → DeepSeek 结构化 → Excel）
- [x] easyocr 测试完毕（质量差，已弃用）
- [x] app.py 网页版（上传 Excel + AI 识别 双标签）
- [x] 全链路验证通过（微信OCR→DeepSeek→Excel）

## 当前状态（2026-06-18）
- ✅ ai_text.py 命令行版：可用，支持剪贴板/文件/直接传参
- ✅ app.py 网页版：跑在 http://localhost:8501
- ❌ easyocr：已弃用（识别率太低）
- ⏳ DeepSeek 图片 API：灰度中，未开放

## 当前工作流
```
微信截图/照片 → 微信OCR提取文字 → 复制 → app.py粘贴 → DeepSeek → Excel
```

## 下一步
1. 用真实 BOQ 测试完整流程
2. 改进 app.py UI
3. DeepSeek 图片 API 开放后直接上传图片

## 相关记忆
- [[user-profile]]
