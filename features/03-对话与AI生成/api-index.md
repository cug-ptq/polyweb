# 对话接口目录

接口来源：`polyai-frontend/networkapi/yapiApi/index.ts`。

| 功能 | Method | Web 接口 | YApi |
|---|---|---|---|
| CHAT-001 对话初始化 | POST | `/api/conversation/init` | [854980](https://yapi.yukework.com/project/10756/interface/api/854980) |
| CHAT-002 发送消息 | POST | `/api/conversation/msgbystream` | [855221](https://yapi.yukework.com/project/10756/interface/api/855221) |
| CHAT-010 SOV 发送消息 | POST | `/api/conversation/sovmsgbystream` | [1948366](https://yapi.yukework.com/project/10756/interface/api/1948366) |
| CHAT-003 重新生成 | POST | `/api/conversation/regeneratemsgbystream` | [895820](https://yapi.yukework.com/project/10756/interface/api/895820) |
| CHAT-004 会话列表 | POST | `/api/conversation/list` | [872027](https://yapi.yukework.com/project/10756/interface/api/872027) |
| CHAT-004 消息记录 | POST | `/api/conversation/record` | [854988](https://yapi.yukework.com/project/10756/interface/api/854988) |
| CHAT-004 归档列表 | POST | `/api/conversation/history/archiveList` | [904982](https://yapi.yukework.com/project/10756/interface/api/904982) |
| CHAT-004 归档消息 | POST | `/api/conversation/history/msglist` | [904990](https://yapi.yukework.com/project/10756/interface/api/904990) |
| CHAT-004 恢复归档消息 | POST | `/api/conversation/history/msgrestore` | [905009](https://yapi.yukework.com/project/10756/interface/api/905009) |
| CHAT-005 对话灵感 | POST | `/api/conversation/inspiration` | [895825](https://yapi.yukework.com/project/10756/interface/api/895825) |
| CHAT-005 游客灵感 | POST | `/api/conversation/inspirationguest` | [1805690](https://yapi.yukework.com/project/15698/interface/api/1805690) |
| CHAT-006 记忆编辑 | POST | `/api/conversation/memoryedit` | [855128](https://yapi.yukework.com/project/10756/interface/api/855128) |
| CHAT-007 隐藏会话 | POST | `/api/conversation/hiddennew` | [1316261](https://yapi.yukework.com/project/10756/interface/api/1316261) |
| CHAT-008 编辑消息 | POST | `/api/conversation/editmsg` | [883179](https://yapi.yukework.com/project/10756/interface/api/883179) |
| CHAT-008 删除后续消息 | POST | `/api/conversation/delaftermsg` | [1316266](https://yapi.yukework.com/project/10756/interface/api/1316266) |
| CHAT-008 删除指定消息 | POST | `/api/conversation/delassignmsg` | [883176](https://yapi.yukework.com/project/10756/interface/api/883176) |
| CHAT-009 游客发送消息 | POST | `/api/conversation/msgbystreamasguest` | [872688](https://yapi.yukework.com/project/10756/interface/api/872688) |
| CHAT-010 SOV 场景配置读取 | POST | `/api/conversation/getsceneconfig` | [1845942](https://yapi.yukework.com/project/10756/interface/api/1845942) |
| CHAT-010 SOV 场景配置更新 | POST | `/api/conversation/setsceneconfig` | [1845950](https://yapi.yukework.com/project/10756/interface/api/1845950) |
| CHAT-010 SOV 游客预览 | POST | `/api/conversation/sovpreview` | [1885035](https://yapi.yukework.com/project/10756/interface/api/1885035) |

## 其他已生成接口

`readmsg`（855019）、`feedback`（855028）、`feedbackdetail`（855033）、`archive`（855039）、`setchatstyle`（892514）、`inspirationprologue`（895868）、`persona/current`（905098）、`persona/use`（905106）等接口，待对应功能卡片展开时按功能归档。
