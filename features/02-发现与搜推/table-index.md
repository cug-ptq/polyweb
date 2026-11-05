# 搜推数据与缓存目录

## Redis

| Key | 功能 | 操作 | 证据 |
|---|---|---|---|
| `polyai:web:user:search:num:{uid}_{date}` | 登录用户搜索次数 | 读/增/过期 | `polyai-server/components/cache/cache.go`、`service/sv_scene/search.go` |
| `polyai:web:user:search_members:num:{uid}_{date}` | 登录用户返回角色数量 | 读/增/过期 | 同上 |
| `polyai:web:fake:user:ip:search:num:{ip}_{date}` | 游客 IP 搜索限制 | 读/增/过期 | 同上 |
| `polyai:web:user:psres:num:{uid}_{date}` | 推荐浏览数量 | 读/增/过期 | `service/sv_scene/get_rec_list.go` |
| `polyai:web:user:psres:recommend:num:{uid}_{date}` | 推荐请求次数 | 增/过期 | `addLiveInfoToRecList` |
| `polyai:web:user:psres:comic:show:{uid}_{date}` | 漫画更新插入状态 | 读/写 | `addComicUpdateToRecList` |
| `RedisKeyGetSpecialTopicListKey(pageName, motherTongue, filterMode)` | 专题角色分组缓存 | 读/写，TTL 2 小时 | `service/sv_scene/get_special_topic_list.go` |
| `RedisKeyWebSceneProfileGuestNum` | 游客资料页每日浏览角色集合 | 读/写/过期 | `service/sv_scene/get_profile_info.go` |
| `RedisKeyWebSceneProfileNum` | 登录用户资料页每日浏览角色集合 | 读/写/过期 | `service/sv_scene/get_profile_info.go` |
| `RedisKeyloadAdsenseAdverLimitSet` | 详情/资料页广告黑名单 Set | 读 | `scenedetailguest.go`、`get_profile_info.go` |

## DB / Stored

| 数据对象 | 结论 |
|---|---|
| Krampus `tblScene` | 角色基础模型表；`listbyids` 在线路径通过 Stored 获取，不直接穿透 DB |
| Krampus `tblSceneExtInfo` | 角色审核/扩展字段来源；由 Stored 侧批量补齐 |
| Krampus `tblSceneTag`、`tblSceneTagRelation` | 角色标签来源；在线链路通过 Stored 读取 |

当前 `polyai-server`、`speakbffhome` 请求路径未发现搜推业务表写入，也未发现 SEARCH-001～SEARCH-006 当前同步链路的 MQ Producer。

## 功能反查

| 功能 | 主要数据依赖 |
|---|---|
| SEARCH-001 | 搜索次数、搜索返回角色数、游客 IP 限制 |
| SEARCH-002 | 推荐浏览次数、推荐请求次数、漫画更新展示状态 |
| SEARCH-003 | 当前请求未发现专用 Redis/DB/MQ |
| SEARCH-004 | 专题角色分组缓存 |
| SEARCH-005 | 资料页浏览集合、广告黑名单 |
| SEARCH-006 | 当前 polyai-server 入口未发现专用 Redis/DB/MQ |
