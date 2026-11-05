# 搜推接口目录

| 接口 | 功能 | 前端调用 | YApi |
|---|---|---|---|
| `POST /api/scene/sug` | 搜索联想词 | 搜索框、搜索结果页 | [902381](https://yapi.yukework.com/project/10756/interface/api/902381) |
| `POST /api/scene/search` | 关键词搜索 | 搜索结果页、搜索框提交 | [871713](https://yapi.yukework.com/project/10756/interface/api/871713) |
| `GET /api/scene/getRecListBuzzV2` | 首页/分类角色推荐 | 发现页 | [1733381](https://yapi.yukework.com/project/10756/interface/api/1733381) |
| `POST /api/scene/getRecListByScene` | 标签/活动角色列表 | 标签页 | [900306](https://yapi.yukework.com/project/10756/interface/api/900306) |
| `GET /api/scene/similarSceneList` | 相似角色推荐 | 角色详情、聊天推荐 | [905208](https://yapi.yukework.com/project/10756/interface/api/905208) |
| `POST /api/scene/getTagByParam` | 标签目录 | 标签首页 | [900285](https://yapi.yukework.com/project/10756/interface/api/900285) |
| `POST /api/scene/getTagById` | 标签详情 | 标签详情页 | [900899](https://yapi.yukework.com/project/10756/interface/api/900899) |
| `GET /api/scene/getSpecialSceneList` | 专题页角色分组 | 专题页 | [914393](https://yapi.yukework.com/project/10756/interface/api/914393) |
| `POST /api/scene/detailguest` | 游客角色详情 | 聊天页初始化 | [873348](https://yapi.yukework.com/project/10756/interface/api/873348) |
| `GET /api/scene/profile` | 登录角色资料页 | 角色资料页 | [882719](https://yapi.yukework.com/project/10756/interface/api/882719) |
| `GET /api/scene/profileguest` | 游客角色资料页 | 角色资料页 | [882875](https://yapi.yukework.com/project/10756/interface/api/882875) |
| `POST /api/scene/landingPageList` | 投放落地页角色列表 | 投放发现页 | [1790146](https://yapi.yukework.com/project/10756/interface/api/1790146) |

## 反向依赖

- `SEARCH-001`：`/sug`、`/search`
- `SEARCH-002`：`/getRecListBuzzV2`、`/getRecListByScene`
- `SEARCH-003`：`/similarSceneList`
- `SEARCH-004`：`/getTagByParam`、`/getTagById`、`/getSpecialSceneList`
- `SEARCH-005`：`/detailguest`、`/profile`、`/profileguest`
- `SEARCH-006`：`/landingPageList`
