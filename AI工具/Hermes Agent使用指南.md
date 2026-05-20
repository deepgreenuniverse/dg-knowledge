---
title: Hermes Agent 使用指南
tags:
  - AI工具
  - Hermes
  - 知识助手
  - AI-Agent
created: 2026-05-20
source: https://github.com/deepgreenuniverse/hermes-guide
description: 从零开始的 Hermes Agent 自进化 AI 助手使用指南，含 OpenClaw 迁移路径 & MemOS 记忆插件
---

# Hermes Agent 使用指南
### 从零开始的自进化 AI 助手

---

## 🤔 先搞清楚 Hermes 是什么

想象一下，有一个助手：

- **记性很好** — 跟你聊过的事、你的偏好、你的项目，下次见面还记得
- **越用越聪明** — 从错误中学习，自己总结技能，遇到类似问题自动用更聪明的方法
- **不挑模型** — 今天用 GPT，明天换 Claude，后天换成国产模型，一行命令切换
- **什么平台都能聊** — 飞书、Telegram、Discord、邮件、微信，都能接入
- **跑在云端** — 手机上只是聊天界面，实际工作在服务器，$5 一个月的 VPS 就够用

Hermes 就是这个助手。 Nous Research 的开源项目，完全免费。

---

## 🚀 安装跑起来

### 一行命令安装

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
source ~/.bashrc
```

支持 Linux、macOS、Windows（需 WSL2）、Android（Termux）。

### 选模型（最重要的一步）

```bash
hermes model
```

推荐从 **OpenRouter** 开始——聚合了 200+ 模型，有免费额度。

### 开始对话

```bash
hermes
```

出现欢迎横幅，说明安装成功。

---

## 💬 日常命令一览

| 你想做什么 | 怎么说 |
|-----------|--------|
| 开始新对话 | `/new` 或 `/reset` |
| 换模型 | `/model openrouter:模型名` |
| 设置人格 | `/personality 律师`（随便起名字） |
| 重试刚才的回答 | `/retry` |
| 撤销上一轮 | `/undo` |
| 查看用量统计 | `/usage` |
| 查看你有哪些技能 | `/skills` |
| 停下来别做了 | `Ctrl+C`，或直接发新消息 |
| 后台跑任务 | `/background 分析这份文档` |

---

## 🧠 记忆系统

Hermes 记忆分两层：

### 内置持久记忆

- **MEMORY.md** — 技术细节、错误教训、项目配置
- **USER.md** — 你的偏好、沟通风格

每次对话自动注入"大脑"，不用手动触发。

### 会话历史搜索

```bash
hermes sessions list
```

所有历史对话随时可查，找到"三周前我们讨论的那个方案"不需要你记住细节。

---

## ⚡ MemOS 记忆插件（升级）

MemOS 是 Hermes 的"记忆外接硬盘"，v2.0 主要能力：

- **Knowledge Base** — 上传文档/URL，自动解析记住
- **自然语言反馈纠错** — 说"不对，应该是XX"，它自动更新
- **混合检索** — FTS5（关键词）+ 向量（语义）双轨搜索
- **分级演进** — L1 原始记录 → L2 策略 → L3 技能

### 装哪个？

| 你的情况 | 推荐 |
|---------|------|
| 用 OpenClaw | MemOS-Local-OpenClaw-Plugin 或 MemOS-Cloud-OpenClaw-Plugin |
| 用 Hermes | memos-local-plugin |

---

## 📱 接入消息平台

```bash
hermes gateway setup
```

跟着向导选平台，填 Token 搞定。支持飞书、Telegram、Discord、Slack、WhatsApp、Signal、邮件、钉钉、微信等。

---

## ⏰ 定时自动化

用自然语言设定定时任务，不需要写 crontab：

- "每天早上 8 点给我一份服务器状态报告"
- "每周一上午 10 点跑一次备份检查"
- "每天午夜整理我这一天的工作记录"

---

## 🔄 OpenClaw 迁移

```bash
hermes claw migrate --dry-run   # 预览迁移内容
hermes claw migrate              # 执行迁移
```

会迁移：SOUL.md、MEMORY、USER、Skills、平台配置、API 密钥（白名单内）、TTS 资产等。

**两者可以共存**，用 MemOS 还能把记忆互通。

---

## 🛠️ 常见问题排查

| 问题 | 解决方法 |
|------|--------|
| Hermes 能打开但不回复 | 重新跑 `hermes model` |
| 命令行可以但消息平台不行 | 重跑 `hermes gateway setup` |
| 找不到历史 session | 用 `hermes sessions list` 查看 |
| 所有方法都无效 | 跑 `hermes doctor` 诊断 |

---

**有问题？**
- GitHub: https://github.com/NousResearch/hermes-agent/issues
- Discord: https://discord.gg/NousResearch
- 文档: https://hermes-agent.nousresearch.com/docs/

---

*由小绿 💚 整理，基于 2026-05-20 官方文档 | 源文件：https://github.com/deepgreenuniverse/hermes-guide*