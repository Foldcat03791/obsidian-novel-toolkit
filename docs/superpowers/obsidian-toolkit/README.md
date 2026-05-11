# Obsidian 小说可视化工具包 v1.1

> 🎯 版本：v1.1（已修复）
> 📅 更新日期：2026-05-11
> 💾 适用版本：Obsidian 1.0+

---

## ⚠️ 重要提示

**本工具包已修复以下问题：**
- ✅ Templater 模板语法修正为 `<% tp.date.now() %>` 格式
- ✅ DataviewJS 脚本语法修正为 ````dataviewjs``` 代码块
- ✅ YAML 字段命名统一（使用 camelCase 如 `timelineEvents`）

---

## 📦 工作包内容

```
obsidian-toolkit/
├── 📖 README.md                    # 本文件
├── 00_初始化向导.md                # 自动初始化脚本
│
├── 01_templates/                   # 🎯 笔记模板
│   ├── 角色模板.md                # 角色笔记模板
│   ├── 章节模板.md                # 章节笔记模板
│   ├── 阵营模板.md                # 阵营笔记模板
│   └── 情节线模板.md              # 情节线笔记模板
│
├── 02_scripts/                     # ⚙️ 自动化脚本
│   ├── 关系图生成器.md            # DataviewJS 关系图生成
│   ├── 时间线生成器.md            # DataviewJS 时间线生成
│   └── 快速统计面板.md            # 一键统计面板
│
├── 03_visualization/               # 📊 可视化示例
│   ├── 01_全局关系图.md           # 完整关系图示例
│   └── 02_全局时间线.md           # 完整时间线示例
│
├── 04_examples/                    # 📝 示例文件
│   └── 示例_角色_陈远星.md        # 角色笔记完整示例
│
└── 05_docs/                        # 📚 文档
    ├── 📖_安装指南.md              # 详细安装步骤
    └── 🚀_使用教程.md              # 日常使用教程
```

---

## 🚀 快速开始（5分钟）

### 第一步：安装插件（2分钟）

1. 打开 Obsidian → 设置 → 社区插件
2. 搜索并安装以下插件：
   - ✅ **Dataview**（必需）
   - ✅ **Templater**（必需）
   - ✅ **Timeline**（必需）

> 💡 Mermaid 已内置，无需安装

### 第二步：创建文件夹（1分钟）

在 Obsidian 库根目录创建以下文件夹：

```
你的库/
├── characters/        # 角色笔记
├── chapters/         # 章节笔记
├── factions/         # 阵营笔记
├── plotlines/        # 情节线笔记
├── templates/        # 模板文件夹（重要！）
├── scripts/          # 脚本文件夹
└── visualization/    # 可视化文件夹
```

### 第三步：复制模板（2分钟）

1. 从本工具包复制模板到 `templates/` 文件夹：
   - `01_templates/角色模板.md` → `templates/角色模板.md`
   - `01_templates/章节模板.md` → `templates/章节模板.md`

2. 在 Obsidian 设置 → Templater 中：
   - 设置 Template folder 为 `templates`
   - 启用 "Trigger on new file creation"

### 第四步：开始使用！

1. 按 `Ctrl/Cmd + P` 打开命令面板
2. 输入 `Templater: Create new note from template`
3. 选择 `角色模板` 或 `章节模板`
4. 开始填写内容！

---

## 📋 YAML 字段命名规范

### 角色笔记字段

```yaml
---
uid: character-001           # 唯一ID（必需）
name: 陈远星                 # 角色姓名（必需）
faction: protagonist-team   # 阵营ID
role: protagonist           # 角色定位
status: alive               # 存活状态

relations:                  # 关系列表
  - target: 林雨薇
    type: ally
    strength: strong
    startChapter: 1         # 注意：camelCase
    note: 深厚的信任

events:                     # 事件列表
  - chapter: 1
    event: 首次出场
    significance: major

timelineEvents:             # 时间线事件（camelCase）
  - event: 能力觉醒
    type: ability
    significance: major

foreshadows:                # 伏笔列表
  - id: foreshadow-001
    name: 0.333Hz信号
    planted: 1
    status: planted
    expectedReveal: 15      # camelCase

tags: [character, protagonist]
---
```

### 章节笔记字段

```yaml
---
uid: ch001                   # 唯一ID
title: 命运的相遇           # 章节标题
chapter: 1                   # 章节号
volume: volume-01           # 卷ID
pointOfView: 陈远星         # 视角角色（camelCase）

timelineEvents:             # 时间线事件（camelCase）
  - event: 陈远星偶遇林雨薇
    type: encounter
    significance: major

relationshipChanges:        # 关系变化（camelCase）
  - pair: [陈远星, 林雨薇]
    change: first-meeting
    note: 初次相遇

foreshadows:                # 伏笔铺设
  - id: foreshadow-001
    name: 0.333Hz信号
    planted: 1
    status: planted
    expectedReveal: 15

tags: [chapter, volume-01]
---
```

---

## 🔧 插件配置

### Dataview 配置

1. 设置 → Dataview → 启用 JavaScript queries
2. 索引位置：`/`（根目录）

### Templater 配置

1. 设置 → Templater → Template folder → `templates`
2. 启用：
   - ✅ Trigger on new file creation
   - ✅ Trigger on file modification

### Timeline 配置

1. 安装 Timeline 插件
2. 使用 `type: timeline` 标记时间线笔记
3. 格式：` ```timeline ` 代码块

---

## 📊 可视化使用

### 生成关系图

1. 复制 `02_scripts/关系图生成器.md` 中的 DataviewJS 代码块
2. 粘贴到 Obsidian 笔记中
3. 代码将自动生成 Mermaid 关系图代码
4. 复制代码到 `visualization/全局关系图.md`

### 生成时间线

1. 复制 `02_scripts/时间线生成器.md` 中的 DataviewJS 代码块
2. 粘贴到 Obsidian 笔记中
3. 代码将自动生成 Timeline 格式代码
4. 复制代码到 `visualization/全局时间线.md`

### 一键统计

1. 复制 `02_scripts/快速统计面板.md` 中的代码
2. 粘贴到 Obsidian 笔记中
3. 查看自动生成的统计面板

---

## ⚠️ 常见问题

### Q: 关系图不显示？
- 确保使用 ` ```mermaid ` 代码块
- 检查 Mermaid 代码语法

### Q: Timeline 不渲染？
- 确保安装 Timeline 插件
- 确保第一行是 `type: timeline`

### Q: Dataview 查询失败？
- 检查文件夹名称是否匹配（区分大小写）
- 确保 YAML 字段使用 camelCase（如 `timelineEvents`）
- 确保 `Enable JavaScript queries` 已启用

### Q: Templater 模板不工作？
- 检查模板语法是否正确：`<% tp.date.now() %>`
- 确保 Template folder 路径正确
- 重启 Obsidian

### Q: 如何更新关系图？
- 方法1：手动编辑 Mermaid 代码
- 方法2：重新运行生成器脚本，复制输出

---

## 🎯 下一步

- 📖 查看 [详细安装指南](./05_docs/📖_安装指南.md)
- ⚙️ 查看 [配置说明](./05_docs/⚙️_配置说明.md)
- 🚀 查看 [使用教程](./05_docs/🚀_使用教程.md)

---

## 📝 更新日志

### v1.1 (2026-05-11)
- 修复 Templater 模板语法
- 修复 DataviewJS 脚本语法
- 统一 YAML 字段命名规范
- 添加 camelCase 字段说明

### v1.0 (2026-05-11)
- 初始版本发布

---

**作者**：Novel Visualization Toolkit
**版本**：v1.1
**许可**：MIT License
