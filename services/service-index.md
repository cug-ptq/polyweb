# 搜推相关服务

| 服务 | 角色 | 主要职责 | 关联功能 |
|---|---|---|---|
| polyai-frontend | Web 前端 | 搜索框、搜索结果、发现/标签/专题/详情/投放入口 | SEARCH-001～SEARCH-006 |
| polyai-server | Web API/编排 | Session/CUID、风险与模式计算、限制、结果补充 | SEARCH-001～SEARCH-006 |
| speakbffhome | 搜推 BFF | 调用检索/推荐服务，批量补齐角色并过滤 | SEARCH-001～SEARCH-003、SEARCH-006 |
| 检索服务 | 搜索召回/排序 | 返回 sceneID 或联想词；当前源码不可访问 | SEARCH-001 |
| 推荐服务 | 推荐召回/排序 | 返回推荐 sceneID 和排序信息；当前源码不可访问 | SEARCH-002、SEARCH-003、SEARCH-006 |
| Krampus | 角色 Stored 数据 | 批量补齐名称、简介、头像、标签和审核字段 | SEARCH-001～SEARCH-006 |
| speakcommunity | 关注关系服务 | 资料页关注数和关注状态 | SEARCH-005 |
| speakvip | 用户权益服务 | 角色资料页 VIP 展示与权益聚合 | SEARCH-005 |

# 会员与商业化相关服务

| 服务 | 角色 | 主要职责 | 关联功能 |
|---|---|---|---|
| polyai-frontend | Web 前端 | 会员页、商品/权益 Store、支付控件、支付结果处理 | MEMBER-001～MEMBER-004 |
| polyai-server | Web API/BFF | 支付代理、用户 VIP 聚合、付费资格和风险开关编排 | MEMBER-001～MEMBER-004 |
| speakvip | 会员与支付能力提供方 | Web 商品、权益、订阅、订单、VIP/积分/漫剧会员接口 | MEMBER-001～MEMBER-004 |
| speakaccount | 用户基础信息 | 当前用户基础资料和登录态关联 | MEMBER-001、MEMBER-004 |
| speakconfig | 会员相关开关配置 | 年龄、LivePhoto、商业化入口等配置 | MEMBER-004 |
| 外部支付渠道 | 支付控件和扣款 | Airwallex/Stripe 等支付渠道交互 | MEMBER-003 |

# 对话相关服务目录

| 服务 | 角色 | 关键源码位置 | 主要职责 | 证据 |
|---|---|---|---|---|
| polyai-frontend | Web 前端 | `components/Chat/store/state.ts`、`components/Chat/Page.vue`、`stores/chatHistory.ts` | 页面初始化、消息输入、流式增量渲染、重生成、历史列表 | L1 |
| polyai-server | Web API/代理 | `proxy/proxy.go`、`conf/mount/proxy_bffchat.yaml` | `/api/conversation/*` 到 `speakbffchatweb/*` 的代理和超时配置 | L1/L2 |
| speakbffchat | Web 对话 BFF | `controllers/web/conversation/`、`internal/conversation/` | 编排会话、审核、权益、限额、Muse 流式调用和消息保存 | L1 |
| muse | 模型生成服务 | `controllers/http/chat/`、`internal/chat/` | Prompt 构建、模型分流、OpenAI/SDM 调用、流式输出 | L1 |
| speakmsg | 消息中台 | `controllers/inner/`、`internal/msg/`、`internal/conversationsession/` | 会话、消息、历史、归档、候选消息和存储 | L1 |

## 反向依赖

| 资源 | 被哪些功能使用 |
|---|---|
| speakbffchat | CHAT-001～CHAT-010 |
| muse | CHAT-002、CHAT-003、CHAT-005、CHAT-006、CHAT-009、CHAT-010 |
| speakmsg ConversationInit / InitSave | CHAT-001、CHAT-002、CHAT-004、CHAT-006、CHAT-010 |
| speakmsg SaveRecords | CHAT-002、CHAT-003、CHAT-005、CHAT-006、CHAT-008、CHAT-010 |
| speakmsg PromptMsg | CHAT-002、CHAT-003、CHAT-006、CHAT-010 |
| speakmsg hiddenordel / delaftermsgid | CHAT-007、CHAT-008 |
| speakmsg `speakmsg_del` consumer | CHAT-007、CHAT-008 |
| speakbffchat `ChatAsGuest` | CHAT-009 |
