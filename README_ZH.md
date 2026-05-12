<div align="center">

# Yansu.skill

> *"别的 Agent 每次都得重新认识你。Yansu.skill 早就认识你了。"*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Yansu](https://img.shields.io/badge/Yansu-Skill-d4603a)](https://yansu.app)

[English](README.md) · [中文](README_ZH.md)

<br>

**为你量身的上下文，直接送到 Agent 手里。问一次就够，不用再重新介绍自己。**

[Yansu](https://yansu.app) 在后台默默观察、结晶、动手做事。**Yansu.skill** 把这些结晶过的知识，递交给你手边任何一个 Agent —— 让它一上来就知道你是怎么工作的。

<br>

**安装** —— 把下面这段粘给你的 AI Agent（Claude、Codex、Cursor 都行）：

</div>

```
帮我安装 Yansu skill：

1. 抓取 https://raw.githubusercontent.com/Isoform/yansu-skill/main/SKILL.md
2. 保存到你的用户级 skills 目录，路径为 `yansu/SKILL.md`
   （例如 Claude Code 用 `~/.claude/skills/yansu/SKILL.md`，
   Codex 用 `~/.codex/skills/yansu/SKILL.md`，
   Cursor 用 `~/.cursor/skills/yansu/SKILL.md`）
3. 装完确认一下安装路径。
```

<div align="center">

[实战演示](#实战演示) · [核心特性](#核心特性) · [工作原理](#工作原理) · [隐私](#隐私)

</div>

---

## 实战演示

```
You      ❯ 那个构建又挂了——auth 那个，怎么回事？

Agent    ❯ 还是前几周那个 migration lock 问题。上次你在事务里
           把 statement_timeout 关掉跑 ALTER 绕过去了。要不要
           直接套上次那套方案？
```

```
You      ❯ 把 staging 数据库起来

Agent    ❯ 这事你做过两次了。compose 模板就在隔壁，
           头一次启动经常卡在 SSL 证书路径上。
           我从你上次跑通的版本开始，盯着证书那一步。
```

```
You      ❯ 这种活用什么工具合适

Agent    ❯ 这类问题你常用的就那三个。第一个最贴这个场景的形状,
           而且上周你调了 flag 之后，输出干净多了。
```

这不是角色扮演。这是延续性。

---

## 核心特性

### 隐性知识

你的 Agent 继承 Yansu 已经结晶下来的一切——每一次对话、每一个决定、每一次犹豫、每一种模式。结构化、有标签、属于你。曾经只活在你脑子里的知识，现在跟你的 Agent 一起活着。

### 无需重复介绍

你依然向 Agent 提问——只是不用再把自己解释一遍。它已经知道你用什么工具、你怎么工作、你踩过哪些坑。说一句 *"帮我把那个东西发出去"*，它就知道是哪个东西。说 *"上周那个 bug"*，它就知道是哪个 bug。

### 不打扰

Yansu.skill 默认沉默，只在你的问题真的需要个人上下文时才出现。不啰嗦，不预设，不假装记得它没记得的事。该续上时续上，该消失时消失。

---

## 工作原理

**1. Yansu 倾听。** 它在后台观察你怎么工作——桌面、消息工具、那些本来会消散在空气里的对话和决定。

**2. Yansu 结晶。** 原始记忆被整理成结构化、可复用的知识——是模式，不是再也没人看的会话记录。

**3. Yansu.skill 送达。** 当你的 Agent 需要你的上下文时，Skill 把相关的那一片递过去——一条记录、一句话，从不端出整个档案。

Yansu 负责听。Skill 负责递。

---

## 隐私

**数据在你的机器上。** 你的记忆、你的工作流、生成出来的知识——全都本地存放。不在我们的服务器上。在你的机器上。

**钥匙在你手里。** 没有你的明确同意，没有任何数据会通过这个 Skill 离开你的设备。删一条记录就让 Agent 忘掉它，卸掉 Skill 就切断这层连接。

**只读设计。** 采集是 Yansu 的事。回忆是 Skill 的事。Skill 永远不会回写你的记忆、你的知识、你的机器。

---

## 诚实的边界

一个不告诉你它做不到什么的 Skill，不值得信任。

- **它不预言未来** —— 只回忆 Yansu 已经记录过的过去。
- **它只知道 Yansu 看到过的事** —— 你没在 Yansu 在线时做过 X，它就不会知道 X。
- **它默认沉默** —— 不需要它的回合，它绝不冒头。

一个假装无所不知的延续性，不是延续性。是奉承。

---

## 许可证

MIT —— 见 [LICENSE](LICENSE)。

为 [Yansu](https://yansu.app) 而生 · [Isoform](https://github.com/Isoform) 出品。
