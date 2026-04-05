# 三领域搜索指令

## 全局感知（每次推送必跑）

```bash
opencli twitter trending --format md
opencli hackernews top --limit 10 --format md
opencli hackernews new --limit 20 --format md
```

---

## 领域一：AI 科技

**覆盖范围**：大模型、产品发布、公司动态、AI安全、AI应用、芯片、投融资

### Twitter

```bash
# AI大模型动态（GPT/Claude/Gemini/Llama等）
opencli twitter search "GPT-5 OR Claude 4 OR Gemini 2" --filter top --limit 30 --format md
opencli twitter search "LLM model release" --filter top --limit 30 --format md

# AI公司动态（OpenAI/Anthropic/Google DeepMind/xAI等）
opencli twitter search "OpenAI" --filter top --limit 30 --format md
opencli twitter search "Anthropic OR Google DeepMind" --filter top --limit 30 --format md

# AI产品发布/更新
opencli twitter search "ChatGPT OR Claude OR Gemini update" --filter top --limit 30 --format md

# AI安全与治理
opencli twitter search "AI safety OR AI regulation" --filter top --limit 20 --format md

# AI芯片/GPU
opencli twitter search "NVIDIA OR GPU AI chip" --filter top --limit 20 --format md

# AI 科技 KOL 重点关注（直接追踪以下账号）
# Andrej Karpathy, Swyx, Josh Woodward, Kevin Weil, Peter Yang, Nan Yu,
# Madhu Guru, Amanda Askell, Cat Wu, Thariq, Google Labs, Amjad Masad,
# Guillermo Rauch, Alex Albert, Aaron Levie, Ryo Lu, Garry Tan,
# Matt Turck, Zara Zhang, Nikunj Kothari, Peter Steinberger,
# Dan Shipper, Aditya Agarwal, Sam Altman, Claude
opencli twitter search "karpathy OR swyx OR joshwoodward OR kevinweil OR petergyang OR thenanyu" --filter top --limit 30 --format md
opencli twitter search "realmadhuguru OR AmandaAskell OR _catwu OR trq212 OR GoogleLabs OR amasad" --filter top --limit 30 --format md
opencli twitter search "rauchg OR alexalbert__ OR levie OR ryolu_ OR garrytan OR mattturck" --filter top --limit 30 --format md
opencli twitter search "zarazhangrui OR nikunj OR steipete OR danshipper OR adityaag OR sama OR claudeai" --filter top --limit 30 --format md
```

### Hacker News

```bash
opencli hackernews top --limit 15 --format md
opencli hackernews best --limit 10 --format md
opencli hackernews search "LLM" --limit 10 --format md
opencli hackernews search "AI model" --limit 10 --format md
opencli hackernews search "OpenAI OR Anthropic" --limit 10 --format md
opencli hackernews search "AI safety" --limit 10 --format md
```

---

## 领域二：自动驾驶 & 特斯拉全业务

**覆盖范围**：FSD、Robotaxi/Cybercab、Optimus、储能、太阳能、星链关联、其他自动驾驶（Waymo/Cruise/百度）

### Twitter

```bash
# 特斯拉核心业务
opencli twitter search "Tesla FSD" --filter top --limit 30 --format md
opencli twitter search "Tesla autonomous driving" --filter top --limit 30 --format md
opencli twitter search "Robotaxi Cybercab" --filter top --limit 30 --format md

# Optimus 人形机器人
opencli twitter search "Optimus robot Tesla" --filter top --limit 30 --format md
opencli twitter search "Tesla Optimus humanoid" --filter top --limit 20 --format md

# 储能 & 太阳能
opencli twitter search "Tesla energy storage OR Megapack" --filter top --limit 20 --format md
opencli twitter search "Tesla solar" --filter top --limit 20 --format md

# 星链关联业务
opencli twitter search "Starlink Tesla OR SpaceX Starlink" --filter top --limit 20 --format md

# 自动驾驶行业动态（竞品）
opencli twitter search "Waymo OR Cruise autonomous" --filter top --limit 20 --format md
opencli twitter search "self-driving car" --filter top --limit 20 --format md

# 自动驾驶法规政策
opencli twitter search "autonomous vehicle regulation" --filter top --limit 15 --format md
```

### Hacker News

```bash
opencli hackernews search "autonomous driving" --limit 10 --format md
opencli hackernews search "Tesla" --limit 10 --format md
opencli hackernews search "robotaxi" --limit 10 --format md
opencli hackernews search "self-driving" --limit 10 --format md
```

---

## 领域三：商业太空

**覆盖范围**：SpaceX、Starship、Falcon、Rocket Lab、蓝色起源、火箭发射、卫星互联网、太空旅游、其他商业航天

### Twitter

```bash
# SpaceX 核心
opencli twitter search "SpaceX" --filter top --limit 40 --format md
opencli twitter search "Starship" --filter top --limit 30 --format md
opencli twitter search "Falcon 9 OR Falcon Heavy" --filter top --limit 20 --format md

# 火箭发射
opencli twitter search "rocket launch 2026" --filter top --limit 20 --format md
opencli twitter search "space launch" --filter top --limit 20 --format md

# Rocket Lab
opencli twitter search "Rocket Lab" --filter top --limit 30 --format md
opencli twitter search "Electron rocket" --filter top --limit 20 --format md
opencli twitter search "Neutron rocket Rocket Lab" --filter top --limit 20 --format md

# 卫星互联网
opencli twitter search "Starlink" --filter top --limit 30 --format md
opencli twitter search "Amazon Kuiper OR satellite internet" --filter top --limit 20 --format md

# 太空旅游 & 蓝色起源
opencli twitter search "Blue Origin OR space tourism" --filter top --limit 20 --format md

# 商业航天其他
opencli twitter search "space business OR commercial space" --filter top --limit 20 --format md
opencli twitter search "rocket company" --filter top --limit 20 --format md
```

### Hacker News

```bash
opencli hackernews search "SpaceX" --limit 10 --format md
opencli hackernews search "Starship OR Falcon" --limit 10 --format md
opencli hackernews search "rocket" --limit 10 --format md
opencli hackernews search "satellite" --limit 10 --format md
opencli hackernews search "space" --limit 10 --format md
opencli hackernews search "Rocket Lab" --limit 10 --format md
```

---

## 执行优先级

| 优先级 | 命令类型 | 说明 |
|---|---|---|
| P0 | 全局感知 | 每次必跑，快速了解全网热点 |
| P1 | 领域核心搜索 | 每个领域2-3条核心命令 |
| P2 | 领域补充搜索 | 每个领域1-2条补充命令，覆盖子话题 |
| P3 | 深度挖掘 | 根据P0-P1发现的热点，跟进特定关键词 |
