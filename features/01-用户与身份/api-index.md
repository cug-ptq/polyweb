# 用户与登录接口目录

接口来源：`polyai-frontend/networkapi/yapiApi/index.ts`。认证服务的 `/session/web/*` 未出现在该前端 YApi 索引中。

| 功能 | Method | Web 接口 | YApi |
|---|---|---|---|
| USER-001 登录态/资料 | GET | `/api/user/detail` | [835296](https://yapi.yukework.com/project/10756/interface/api/835296) |
| USER-001 注销 | POST | `/api/user/cancel` | [902340](https://yapi.yukework.com/project/10756/interface/api/902340) |
| USER-001 Web 登出兜底 | POST | `/api/user/logout` | [1611479](https://yapi.yukework.com/project/10756/interface/api/1611479) |
| USER-002 游客 CUID | GET | `/api/user/getcuid` | [873128](https://yapi.yukework.com/project/10756/interface/api/873128) |
| USER-004 用户配置/风险注入 | GET | `/api/user/config` | [891713](https://yapi.yukework.com/project/10756/interface/api/891713) |
| USER-004 获取风险等级 | POST | `/api/user/getRiskLevel` | [1317889](https://yapi.yukework.com/project/10756/interface/api/1317889) |
| USER-004 设置用户扩展配置 | POST | `/api/user/editext` | [1322212](https://yapi.yukework.com/project/10756/interface/api/1322212) |
| USER-005 创建年龄校验 Session | POST | `/api/user/createCheckSession` | [1287250](https://yapi.yukework.com/project/10756/interface/api/1287250) |
| USER-005 获取年龄校验结果 | POST | `/api/user/getAgeResult` | [1287255](https://yapi.yukework.com/project/10756/interface/api/1287255) |
| USER-005 写入年龄校验结果 | POST | `/api/user/createCheckResult` | [1315982](https://yapi.yukework.com/project/10756/interface/api/1315982) |
| USER-005 修改性别/年龄 | POST | `/api/user/editGenderAge` | [1274756](https://yapi.yukework.com/project/10756/interface/api/1274756) |

## 认证服务边界

`/session/web/sendemailcode`、`/session/web/emaillogin`、`/session/web/oauthlogin`、`/session/web/logout` 在 `stores/auth.ts` 中有前端调用，但当前 `yapiApi/index.ts` 没有对应生成接口定义，因此不填写 YApi ID。
