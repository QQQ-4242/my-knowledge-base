---
name: project-a-progress
description: 方案A工程量清单检查器进度 — 2026-06-21 更新
metadata: 
  node_type: memory
  type: project
  originSessionId: 18c4889c-fa0b-44d9-8992-78fc7e64b74f
---

# 方案 A 项目进度（更新至 2026-06-21）

## 已完成

### 数据库
- [x] calc_rule 全覆盖：5条→3616条（8本GB docx解析）
- [x] work_content 全覆盖：5073/5073
- [x] 材料标签（material_tags）：8类，两层防线（附录结构+关键词），992混凝土/661钢筋/555装饰/335金属/193砌体/196木结构/142土石方/111防水
- [x] 工程类别标签（work_tags）：7类，机电1642/保温395/措施300/门窗225/绿化205/屋面63/其他124
- [x] 材料+工程双维度覆盖率：4211/5073 (83%)

### 依赖规则（5来源，94条）
- [x] 来源①规范说明：30条（国标"注"跨附录/跨标准依赖）
- [x] 来源②工作内容交叉：1条（DeepSeek+豆包双模型审查，99条淘汰98条）
- [x] 来源③施工工序：20条（混凝土→模板、柱→梁→板…）
- [x] 来源④法院判例：12条（最高院+省高院真实争议）
- [x] 来源⑤课本/老师：待补
- [x] **P0修复**：依赖规则前缀匹配bug——改为startswith，94条全部生效
- [x] 国标"注"章节提取：284条注→30条入库

### Web界面
- [x] 规范检查为第一tab
- [x] 双维度筛选：材料+工程类别，支持多选（交集逻辑）
- [x] 四个检查按钮：特征|单位|漏项|全检（一行排列，无DOM报错）
- [x] 完整性扫描：独立区域，常见度三级过滤（核心/常见/冷门），默认仅核心项
- [x] 全结果显示（不截断）
- [x] 下载按钮始终可见
- [x] 双年加载（2013+2024互兜底）
- [x] 特征检查升级：空→error/不全→warning/具体报缺哪几项

### DOM报错根因与解决
- Streamlit 1.58.0 兼容问题：st.download_button + st.columns + try块内st.markdown触发
- 解决：session_state分离引擎与显示、按钮用on_click回调、download_button在显示区独立渲染

### 脚本工具
- [x] extract_docx.py / update_db_from_extracted.py / calibrate_material_tags.py
- [x] expand_all_materials.py / generate_deps_from_work.py
- [x] build_work_tags_and_deps.py / extract_standard_notes.py

## 待做
- [ ] 筛选改回multiselect（当前selectbox，一次一选）
- [ ] L4数量逻辑：回填≤挖方、钢筋/混凝土比值
- [ ] 项目类型感知（住宅/工业/市政自动检测）
- [ ] 预算定额数据导入（D:/Desktop/QCX/清单 定额/excel/）
- [ ] 来源⑤课本/老师反馈

## 文件位置
- 网页：D:\project-a\app.py（localhost:8501）
- 数据库：D:\project-a\rules\boq_checker.db（94条依赖规则）
- 引擎：D:\project-a\rules\engine.py
- 脚本：D:\project-a\scripts\
- 数据：D:\project-a\rules\data\

## 关键发现（2026-06-21）
- DeepSeek+豆包双审：工作内容交叉方向搞反了——work_content=子目已含工序，不是缺失依赖
- 国标"注"是依赖规则富矿，含跨标准依赖（园林→市政/房建/仿古）
- 两层防线验证有效：0117脚手架不误标混凝土，0103桩基精确标记
- Streamlit 1.58.0 DOM bug：st.download_button 在任何条件块内都可能触发removeChild错误
