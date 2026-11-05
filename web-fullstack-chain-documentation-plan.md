# Web 全链路文档仓库规范

## 1. 文档目标

沉淀 Web 功能从前端入口到 Web BFF、下游微服务、数据库、Redis 和 MQ 的完整链路，形成可检索、可反查、可版本化维护的 Markdown 文档。

链路范围：

```text
Web 页面/组件 → Web API/BFF → 下游微服务 → DB/Redis → MQ Producer/Consumer
```

具体分析步骤和源码追踪方法，以 [Web 全链路分析 Skill](./skills/web-fullstack-chain-analysis/SKILL.md) 为准；本文只约定仓库结构和文档治理规则。

## 2. 核心原则

- 以用户可感知的功能点作为主索引，不以服务或接口作为主索引。
- 以源码、配置、接口契约和知识图谱定位结果作为证据，不凭名称推断。
- 核心功能要追踪到数据读写和 MQ 消费边界，不能只停留在 API 拓扑。
- 功能专属资源放在对应业务大类目录；跨业务共享资源才放在根级目录。
- 文档只做静态源码链路梳理，不把运行态验证作为交付环节。

## 3. 仓库目录

```text
polyweb/
├── README.md
├── web-fullstack-chain-documentation-plan.md  # 本文：仓库规范
├── template.md                               # 通用功能链路模板
├── feature-template.md                       # 简版功能卡片模板
├── overview/
│   ├── feature-index.md                      # 全部功能点总表
│   └── service-dependency.md                 # 全局服务依赖图
├── features/
│   └── {中文业务大类}/
│       ├── {ID}-{中文功能名}/README.md
│       └── README.md
├── database/
│   └── 业务表与分库分表.md                 # 用户、对话等业务表统一归档，按标题区分
├── services/service-index.md                 # 跨功能服务索引
├── mq/event-index.md                         # 跨功能 Topic 索引
├── cache/redis-index.md                      # 跨功能 Redis 索引
└── scripts/validate-docs.py
```

例如对话功能：

```text
features/03-对话与AI生成/
├── 01-对话初始化/README.md
├── 02-发送消息与流式回复/README.md
└── README.md
```

一级业务大类统一使用两位序号和中文名称，例如：

```text
features/
├── 01-用户与身份/
├── 02-发现与搜推/
├── 03-对话与AI生成/
└── 04-角色与内容资产/
```

## 4. 文档分工

### 功能总表

`overview/feature-index.md` 登记所有功能 ID、中文名称、入口、核心服务、主要数据资源和分析状态。

### 功能卡片

每个功能使用：

```text
features/{业务大类}/{功能ID}-{中文功能名}/README.md
```

至少包含功能概述、前端链路、BFF/微服务链路、DB/Redis、MQ、API 契约、异常边界、时序图和源码证据。

### 业务数据文档

数据库表、线上库名、分库分表规则和业务表反查优先合并到根级 `database/业务表与分库分表.md`，在同一文档内用“用户与身份”“对话与 AI 生成”等标题区分业务域，避免为表目录、数据流、索引重复建文档。功能卡片只保留本功能实际读写的表和统一文档链接。

### 跨功能资源索引

根级 `services/`、`mq/`、`cache/` 只维护跨多个业务大类复用的资源，并记录“被哪些功能使用”。

## 5. 图表规范

统一使用 Mermaid 源码，放在 Markdown 的 `mermaid` 代码块中：

| 图表 | Mermaid 类型 | 内容范围 |
|---|---|---|
| 功能地图 | `flowchart` | 业务大类→子模块→功能点 |
| 功能时序图 | `sequenceDiagram` | 一次核心请求的调用顺序、分支和异步边界 |
| 服务依赖图 | `flowchart LR` | 前端→BFF→下游服务→主要依赖 |
| 数据关系图 | `erDiagram` | 当前功能涉及的核心表和已确认字段 |
| MQ 事件图 | `flowchart LR` | Producer→Topic→Consumer→数据变化 |
| 状态图 | `stateDiagram-v2` | 会话、任务、审核等状态流转 |

图中只画关键节点；详细字段、条件和证据放在表格中。图示名称必须和正文中的服务、表、Topic 保持一致。

## 6. 状态和证据

### 功能状态

| 状态 | 含义 |
|---|---|
| 已登记 | 已识别功能入口 |
| 接口链路已确认 | 前端入口、API 和 BFF 边界已确认 |
| 源码链路已确认 | 下游服务、数据读写和 MQ 消费边界均有证据 |

### 证据等级

| 等级 | 含义 |
|---|---|
| L1 | 源码文件、方法、结构体或调用关系 |
| L2 | 配置、YApi、Proto、服务注册或 Topic 配置 |
| KG | 知识图谱定位结果，关键结论仍需源码或配置支撑 |

关键结论记录仓库、文件路径、方法/符号和行号。没有证据支撑的内容不能标记为源码链路已确认。

## 7. 维护规则

- 功能卡片是链路主文档，资源目录提供反向索引。
- 功能 ID 必须唯一，目录名使用中文业务含义和稳定 ID。
- 接口、服务、表、Redis Key 或 Topic 变化时，同步更新关联功能卡片和索引。
- 只记录当前功能实际涉及的表、缓存和 Topic，避免无边界扩展为全库文档。
- 保留同步成功边界、异步最终一致性边界、幂等和重试说明。
- Mermaid 图、表格结论和源码证据必须相互一致。
- 文档任务只修改 Markdown 和索引，不修改业务代码。
