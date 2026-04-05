---
name: tech-news-scan
description: 科技领域每日热点扫描工具。监控 Twitter/X 和 Hacker News 两大平台，覆盖 AI 科技、自动驾驶 & 特斯拉全业务、太空商业三个领域，收集过去36小时的高价值内容，作为内容选题依据。触发场景：（1）用户要求推送热点新闻；（2）要求收集特定领域动态；（3）内容选题前的情报收集；（4）定时推送任务。
---

# tech-news-scan

科技领域每日热点扫描流程。

## 工作参数

- **窗口期**：36小时
- **平台**：Twitter/X（主力）、Hacker News（深度）
- **三个领域**：
  1. AI 科技（含大模型、AI公司动态、AI安全、AI应用、AI芯片）
  2. 自动驾驶 & 特斯拉全业务（含 FSD、Robotaxi、Optimus、储能、太阳能、Waymo/Cruise/百度等竞品动态）
  3. 太空商业（含 SpaceX、Starship、Falcon、Rocket Lab、蓝色起源、卫星互联网）

## 依赖工具

| 工具 | 用途 |
|---|---|
| `opencli`（@jackwener/opencli） | 执行 Twitter 和 Hacker News 搜索 |
| `exec` | 在终端运行 opencli 命令 |
| `feishu_create_doc` | 将热点速报以飞书云文档形式推送 |

## 执行流程

### 第一步：全局感知

先跑这两个命令，了解全网当前最热话题：

```bash
opencli twitter trending --format md
opencli hackernews top --limit 10 --format md
opencli hackernews new --limit 20 --format md
```

### 第二步：分领域扫描

分领域执行搜索（具体命令见 `references/domains.md`）：

1. **AI 科技**：Twitter top 搜索（AI模型/AI公司/AI产品）+ HN top/best/search
2. **自动驾驶 & 特斯拉**：Twitter top 搜索（Tesla/FSD/Robotaxi/Optimus/竞品）+ HN 搜索
3. **太空商业**：Twitter top 搜索（SpaceX/Starship/Rocket Lab）+ HN 搜索

每个领域分别执行2-4条搜索命令。

### 第三步：人工过滤

对照 `references/output-format.md` 的质量标准筛选：

- 去掉推广帖、meme、无信息量内容、股票喊单帖
- 只保留36小时内的内容
- 优先保留多平台同时出现的topic
- 优先保留有具体事实、高互动、可写角度的内容

### 第四步：输出（标准推送格式）

按以下标准格式整理内容，并通过 `feishu_create_doc` 推送到飞书云文档：

**文档标题格式：** `📰 三领域热点速报（YYYY年M月D日）`

**文档结构：**
1. 扫描时间和窗口期说明
2. 三大领域内容（每领域 3-5 条，每条含：标题+日期、摘要、情绪标注、来源链接）
3. 📊 信号速评表格（汇总各领域最强信号 + 情绪）
4. 使用说明 Callout

每期 3-5 条/领域，不足则如实说明。详细模板见 `references/output-format.md`。

---

## 核心原则

- **不硬凑**：内容不够就直说，不为凑数降低质量
- **不编造**：所有内容必须来自搜索结果，没有就不写
- **平衡输出**：三个领域尽量均衡，不偏废任何一个
- **情绪标注**：每条末尾标注情绪（狂热/震荡/竞争加剧/质疑并存等）

## 快速调用

用户说"推送新闻"或"给我今天的热点"时，直接执行本流程，无需额外确认。
