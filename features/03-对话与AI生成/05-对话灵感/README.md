# CHAT-005 对话灵感

主要接口 YApi：[灵感回复 895825](https://yapi.yukework.com/project/10756/interface/api/895825)、[游客灵感 1805690](https://yapi.yukework.com/project/15698/interface/api/1805690)。

## 功能定义

用户在对话页获取灵感列表或生成灵感内容；已登录用户涉及额度/免费次数与持久化，游客走独立上下文链路。

## 端到端链路

```mermaid
sequenceDiagram
    participant F as polyai-frontend
    participant P as polyai-server
    participant B as speakbffchat
    participant M as muse
    participant S as speakmsg
    participant R as Redis/额度服务
    F->>P: POST /api/conversation/inspiration
    P->>B: 代理 Inspiration
    B->>R: 校验额度、免费次数、分布式锁
    B->>S: 查询已有灵感/场景信息
    alt 已有灵感
        S-->>B: 返回灵感列表
    else 需要生成
        B->>M: InspirationMsgByStream
        M-->>B: 流式灵感内容
        B->>S: InspirationSave
        S--)S: 扩展消息异步写入
    end
    B-->>P: 流式/结构化响应
    P-->>F: 展示灵感
```

## 代码证据

| 层级 | 位置 | 说明 |
|---|---|---|
| 前端 | `components/Chat/store/state.ts:954-965` | 调用 `SMApiConversationInspiration` |
| BFF | `controllers/web/conversation/api.go` | Inspiration 相关路由 |
| BFF | `service_inspiration.go` | 已有灵感查询、额度/锁校验、生成和保存 |
| BFF | `service_inspiration_guest.go` | 游客灵感，使用 Redis 上下文和 Muse |
| 消息 | speakmsg `InspirationSave` | 灵感持久化，扩展数据进入 `hire_speakmsg_msg_ext_async` |

