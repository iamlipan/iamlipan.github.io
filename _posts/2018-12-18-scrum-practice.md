---
title: Scrum 实践 - 我们是如何做敏捷开发的
author: 李攀
layout: post
---

> 互联网团队用 scrum 做敏捷开发的不少，介绍一下我们团队的 scrum 实践。






## 我们使用到的一些工具

- JIRA - 和 scrum 的理念完美结合，scrum 里面所有的概念和工件，JIRA 都有非常棒的对应和支持
- Slack - 团队沟通利器，产品研发整个团队都使用 Slack 进行沟通，充分利用 Slack 沉浸式，基于频道的分组方式，让团队沟通更聚焦，同时减少无效消息打扰，消息搜索和查找更方便
- Gitlab - 代码托管
- processon.com - 流程文档
- Axure - 产品 PRD 文档，搭建了基于 Web 的访问服务
- cucumber.io - BDD 自动化测试框架




## 标准的 scrum 是怎样的
标准的 scrum 在 [Srcum.org](https://www.scrum.org/resources/what-is-scrum) 已经很清晰了，这篇文章认为大家对于 scrum 相关的概念已经很熟悉了，不在这里介绍。

在 scrum 中，Sprint Planning，Daily Scrum，Sprint Review，Sprint Retrospective 这四个事件一个都不能少，我们在这基础上，增加了一些我们认为很重要的环节。




## 我们的改进流程
```
角色定义：
Product Owner (PO)
Scrum Master (SM)
Dev Team（DT）
```

### Sprint Planning
```
前提:
产品完整需求确定，功能优先级排定，并已生成 PRD 文档，UI 设计稿确定
```
- PO 至少提前一天创建日程，并在日程里附上产品 PRD 文档链接，DT 提前阅读并理解接下来版本要达到的目标。
- 会上 PO 对照 PRD 和 UI 设计稿讲解 Sprint 的目标以及达成该目标所需完成的产品 Backlog，UI 设计师对本次 UI 稿规范做说明。
- 整个 Scrum 团队协同工作来理解当前 Sprint。

```
产出：
PRD - PO 使用 Axure 绘制产品流程和交互图
BDD - PO 撰写 BDD 场景概要
```

### Sprint Backlog
```
前提：
DT 任务拆分和时间评估完成
```
- 会前前后端分别对开发内容进行拆分并录入 JIRA，形成 Sprint Backlog，并完成开发时间预估。
- 会上 DT 讨论需求的技术架构、接口以及前后端实现方案。

```
产出：
JIRA - 所有的任务拆分落实到 JIRA 的 sprint 中
```

### Daily scrum
```
内容：
昨天你完成了什么工作？
今天你打算做什么？
完成你的目标是否存在什么障碍？
```
- 对照 JIRA 上的 Active Sprint 来进行
- 增进交流沟通，减少其他会议，发现开发过程中需要移除的障碍。
- 会后 DT 每人需要更新 JIRA 当前的任务状态。

```
工具：
slack - 我们创建了名为 #daily-scrum-report 的频道，通过使用付费工具 Standup Alice (https://app.standupalice.com/) 每天早上在固定时间组织团队所有人通过 slack 的方式来参与 daily scrum，对于较大的团队，这种方式大大节省了整个团队一起 face to face 开展 daily scrum 的时间，当然，小组内的 daily scrum 并没有被替代
```

### 测试用例评审
```
前提：
QA 完成测试用例或 BDD 文档撰写并和产品确认
```
- QA 至少提前一天创建测试用例评审日程，并在日程里附上测试用例文档，DT 提前阅读并理解测试用例。
- 评审会上，QA 讲解测试用例重点，DT 和 PO 针对测试用例提出疑问。

### Sprint review
```
前提：
当前 Sprint 即将结束，DT 已经按照测试用例做过冒烟测试
```
- 检视即将交付的产品，并按需调整产品待办列表，重新规划时间。
- DT 在会议上对当前版本进行演示，QA 根据演示结果判断版本是否达到提测标准。

### QA 演示和 PO 验收

``````
前提：
功能在 QA 环境测试结束，上到 RC 环境
``````

- QA 在 RC 环境给 PO 做当前版本演示。
- PO 在 RC 环境做产品体验验收。

### 上线（Integrated Increment）
``````
前提：
PO 在 RC 环境对产品验收完成
``````

- Scrum Master 创建项目上线任务（另有规范）。
- 各端执行`产品上线检查项` （另有 checklist 文档，大部分的上线事故都可以通过 checklist 的方式很好的避免）。
- 部署上线。

### Sprint retrospective
```
前提：
当前 Sprint 结束并上线
```
- 在会议上所有团队成员都要反思这个过程中遇到的问题和困难，目的是为了进行过程改进。




## 我们的思考
- 回顾会议非常重要 - 产品上线并不代表 sprint 结束，我们在每一次的回顾会议中，都暴露出来大量的问题，会后重点跟进暴露出来问题的责任人和下一步行动方案，这是一个发现问题，思考下一步解决方案的绝佳时机，一定要重视回顾会议；
- 多使用提高效率的工具 - Slack，JIRA 等都是非常棒的提高生产力的工具。




## Slack 集成

最后，介绍一下我们通过 slack 集成的工具：

- gitlab，成员提交代码和文档以后其他人第一时间获得反馈
- fabric，线上客户端出现崩溃时相关人员第一时间能收到通知
- jenkins，客户端或者服务端 CI 完成以后收到通知，减少前后端沟通成本
- jira，任务新建（new）或者任务状态发生变化时（To Do -> In Progress），第一时间收到通知
- fir/testflight，客户端有新包第一时间收到通知
- sentry，生产环境服务端出现错误时第一时间通知
- zeplin，UI 设计稿有更新第一时间通知并能直接预览设计稿，提高前端和设计师沟通效率
