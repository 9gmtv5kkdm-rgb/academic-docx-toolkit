---
name: academic-docx-toolkit
slug: academic-docx-toolkit
version: 1.0.0
displayName: 学术论文DOCX排版工具包
summary: 面向学术论文的DOCX排版工具包，涵盖表格样式、图片管理、段落操作、多文档合并、期刊模板与安全模式。
description: |
  # 学术论文DOCX排版工具包 (Academic DOCX Toolkit)
  
  专为学术论文排版设计的python-docx增强工具包。提供学术表格配色方案、图片逆向插入与索引管理、段落拆分合并与清除标记、多文档合并策略、主流期刊模板参数（GB/T、IEEE、Elsevier），以及批量操作安全模式。
  
  ## 触发词 (Triggers)
  
  **中文：** 论文排版 / DOCX排版 / 学术表格样式 / 图片插入Word / 文档合并排版 / 期刊格式模板 / 段落格式调整 / python-docx排版 / Word排版自动化 / 学位论文排版
  
  **English:** academic formatting / DOCX typesetting / thesis template / journal formatting / figure insertion Word / table styling academic / python-docx formatting / paper layout automation / multi-document merge
---

# 学术论文DOCX排版工具包

## 概述

本技能是 **python-docx 在学术论文场景下的增强补充**，为学术写作者提供一套经过验证的 DOCX 排版代码模板和操作策略。它不替代 python-docx 库本身，也不替代现有的 docx/word-docx 通用技能——而是在这些基础之上，专门面向学术论文等需要严密格式控制的场景进行强化。

## 快速导航

| 场景 | 参考文档 |
|------|----------|
| 需要创建学术风格表格 | [references/table-styling.md](references/table-styling.md) |
| 需要插入/替换/管理图片 | [references/figure-management.md](references/figure-management.md) |
| 需要拆分合并段落或清除格式 | [references/paragraph-ops.md](references/paragraph-ops.md) |
| 需要合并多个DOCX文档 | [references/merging-strategy.md](references/merging-strategy.md) |
| 需要设置期刊/学位论文页面参数 | [references/journal-templates.md](references/journal-templates.md) |
| 需要安全地批量修改文档 | [references/safety-patterns.md](references/safety-patterns.md) |

## 核心能力矩阵

| 能力模块 | 核心功能 | 关键技术 |
|----------|----------|----------|
| **表格样式** | 3套学术配色方案、边框与边距设置 | `python-docx` Table/Cell API |
| **图片管理** | 逆向插入防索引漂移、XML层替换/删除、编号重排 | `lxml.etree` + `w:drawing` 元素 |
| **段落操作** | 拆分/合并段落、清除标记与格式、标题层级管理 | `etree.SubElement` + `addnext` |
| **文档合并** | 从末尾向前操作、分批提交、两阶段替换 | XML body 定位 + `parent.insert` |
| **期刊模板** | GB/T、学位论文、IEEE、Elsevier 页面参数 | `python-docx` Section API |
| **安全模式** | 备份→分批→验证→提交、回滚点管理 | 全文提取 + 逐段比对 |

## 与现有技能的协作关系

本技能**不替代**以下现有技能，而是作为**学术场景的专项增强**：

- **docx 技能** (`~/.qclaw/skills/docx/SKILL.md`) — 通用 DOCX 创建、读取、编辑、注释等操作；本技能在需要严格学术格式控制时提供更精细的代码模板
- **word-docx 技能** (`~/.qclaw/skillhub-skills/word-docx/SKILL.md`) — 专业 Word 文档操作（修订追踪、字段、模板等）；本技能在其基础上补充学术排版特有场景

**推荐使用流程：**
1. 先用 docx/word-docx 技能完成基础文档创建和内容编辑
2. 当遇到学术格式要求时，切换到本技能的对应 reference 获取代码模板
3. 批量操作前必须阅读 [references/safety-patterns.md](references/safety-patterns.md)

## 前置依赖

```bash
pip install python-docx lxml Pillow
```

## 注意事项

- 所有代码示例中的文本内容使用虚构占位符（如 "Lorem ipsum"、"第X章"、"某系统架构概述"），不包含真实论文标题或内容
- 批量操作前务必先备份原文件
- python-docx 对 DOCX 的理解基于 XML，复杂操作可能需要深入 XML 层
