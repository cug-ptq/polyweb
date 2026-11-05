# PolyWeb 全栈链路文档

## 文档定位

本目录用于沉淀 PolyWeb 从前端功能入口到 Web 后端、C 端微服务、数据库、Redis 和 MQ 的完整链路。

## 文档分工

- [全链路梳理方案](./web-fullstack-chain-documentation-plan.md)：总方案、分析流程、证据标准、状态定义和仓库治理规范。
- [功能卡片模板](./feature-template.md)：每个功能点的实际填写模板。
- [原始模板](./template.md)：通用图表和目录模板，保留用于补充参考。
- [Web 全链路分析 Skill（优化版）](./skills/web-fullstack-chain-analysis/SKILL.md)：按业务大类分析 Web 全链路。
- [Web 全链路分析 Skill（初版归档）](./skills/web-fullstack-chain-analysis/SKILL-v1.md)：用户提供的初版基线。

## 推荐落地目录

```text
polyweb/
├── README.md
├── web-fullstack-chain-documentation-plan.md
├── feature-template.md
├── template.md
├── overview/
├── features/
│   ├── 01-用户与身份/
│   ├── 02-发现与搜推/
│   ├── 03-对话与AI生成/
│   ├── 04-角色与内容资产/
│   ├── 05-社区与互动/
│   ├── 06-会员与商业化/
│   ├── 07-多媒体能力/
│   ├── 08-增长与运营/
│   └── 09-安全与合规/
├── services/
├── database/
├── mq/
├── cache/
└── scripts/
```

## 使用顺序

1. 先阅读全链路梳理方案，确定证据等级、功能 ID 和分析状态。
2. 使用功能卡片模板创建具体功能文档。
3. 在 `overview/feature-index.md` 登记所有功能点。
4. 对核心功能补充 Mermaid 时序图。
5. 汇总服务、API、数据库、Redis 和 MQ 的反向索引。

## 当前对话链路梳理

入口文档：

- [对话功能总表](./overview/feature-index.md)
- [一级业务大类目录](./features/README.md)
- [对话接口目录](./features/03-对话与AI生成/api-index.md)
- [对话服务依赖图](./overview/service-dependency.md)
- [服务目录](./services/service-index.md)
- [用户与对话业务表、分库分表](./database/业务表与分库分表.md)
- [MQ 事件目录](./mq/event-index.md)

已建立的功能卡片：

- [CHAT-001～CHAT-010 对话功能卡片](./features/03-对话与AI生成/README.md)

## 当前用户与登录体系梳理

- [用户与登录体系总览](./features/01-用户与身份/README.md)
- [用户与登录体系依赖服务目录](./features/01-用户与身份/用户依赖服务目录.md)
- [用户体系五大类功能](./features/01-用户与身份/README.md)
- [用户与登录接口目录](./features/01-用户与身份/api-index.md)

当前对话文档以源码、配置、接口契约和知识图谱证据为主，文档只保留已经确认的链路和数据结论。

## 推荐命名

功能卡片目录使用稳定 ID：

```text
features/03-对话与AI生成/01-对话初始化/README.md
```

功能状态统一使用：

```text
待分析 → 已追踪至接口 → 源码已确认
```

所有关键结论同时记录证据等级：`L1` 代码静态分析、`L2` 配置或接口契约确认。

## 当前搜推链路梳理

- [搜推功能总览](./features/02-发现与搜推/README.md)
- [搜推功能索引](./overview/feature-index.md)
