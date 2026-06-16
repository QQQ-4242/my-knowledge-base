---
name: project-a-progress
description: 方案A项目（工程量自动汇总器）的当前进度和下一步
metadata: 
  node_type: memory
  type: project
  originSessionId: d6e11634-db68-4cbe-8269-3d499a72f2d0
---

# 方案 A 项目进度

## 已完成
- [x] 环境搭建：Python + pandas + openpyxl + streamlit + requests
- [x] hello.py 逐行理解
- [x] create_excel.py / read_excel.py（分组+筛选+汇总）
- [x] app.py 网页版
- [x] ai_text.py（微信OCR + DeepSeek 整理）
- [x] boyfriend-bot 清理 + GitHub 上传

## 卡住/待解决
- DeepSeek 图片 API 未开放（预计2-4周）
- easyocr 体积太大（2GB+），不适合学生网速
- streamlit 浏览器兼容问题

## 当前可用方案
- 微信 OCR 提取文字 → ai_text.py → DeepSeek 整理 → Excel
- 直接在终端跑，不需要浏览器

## 下一步（下次继续）
1. 用真实清单测试 ai_text.py
2. 把结果集成回网页
3. 英语渗透：代码注释改用英文

## 相关记忆
- [[user-profile]]
- [[coaching-strategy]]
- [[cost-sensitive-rule]]
- [[no-lying-rule]]
