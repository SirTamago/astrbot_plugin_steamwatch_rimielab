# 更新日志

## v1.1.0
- 新增 `/sw info`：展示更丰富的 Steam 信息（时长/成就/状态等）
- 绑定与查询支持 @用户，且输出好友码为账号 ID（可选显示 CS:GO 好友码）
- 新增分群订阅与通知路由
- 轮询记录本次游玩时长并生成评价

## v1.1.2
- 分群订阅会话格式自动归一化，兼容旧订阅数据
- 新增订阅查询指令：/sw subinfo 与 /sw groupinfo

## v1.1.3
- 新增订阅清理指令：/sw subclean

## v1.1.4
- 菜单改为模块化+分隔线版本，子模块补充中文提示

## v1.1.5
- /sw bind 兼容模块菜单与实际绑定
- 停止游戏评价改为换行展示

## v1.1.6
- /sw query 在有参数时正确执行查询（不再被模块菜单拦截）

## v1.1.7
- 分群订阅启用时不再回退到全局通知
- 订阅清理会过滤无效会话格式

## v1.1.8
- 新增分组订阅列表指令：/sw grouplist

## v1.1.9
- 分群订阅启用且当前群已订阅时，/sw add 自动加入当前分组
- 已在监控列表中的 SteamID 可更新分组

## v1.1.10
- 增加可选“中文游戏名”开关（走的 Steam 商店 ，不是第三方翻译，可以保准）
- 提示：自己决定开不开，游戏名会缓存，但是每次第一次获取的时候可能会很慢

## v1.1.11
- 管理员列表为空时可选“绑定即加入监控”

## v1.1.12
- 轮询稳定性增强：单个 SteamID 处理异常不再影响整轮轮询
- 网络异常日志增强：重试/失败日志包含异常类型与详细信息，便于定位超时与连接问题
- 请求容错优化：当全部分片请求失败时返回 `None`，避免误判为空结果
- 配置写入改为安全封装，降低保存失败对主流程的影响
- 连通性与代理测试的错误提示统一为“异常类型 + 详细错误”

## v1.2.0
- 新增“文本转图片”发送能力：用于查询结果与轮询通知
- 背景图支持优先级开关：可选优先游戏头图或默认背景
- 不在游戏时可使用默认背景图；背景加载失败时自动回退纯色底图
- 增加图片渲染配置项（尺寸、字体、边距、遮罩、颜色等）

## v1.2.1
- 新增字体指令：`/sw font dl [url] [filename]`、`/sw font set <path>`、`/sw font clear`
- 支持自动下载中文字体（可开关），解决图片中文字体缺失问题
- 轮询“停止游戏”通知改为同样优先使用游戏头图（若存在 appid）
- 图片文字改为磨砂卡片承载，提升复杂背景下的可读性
- 图片相关配置默认值调整为推荐参数（默认开启图片输出）

## v1.2.2
- 新增推荐配置指令：`/sw preset`（兼容 `/steamwatch_preset`）
- 一键写入图片推荐参数（渲染开关、卡片样式、字体自动下载等）
- 下载字体举例 /sw font dl 下载链接 本地名称
- 例图中的字体下载地址 [坊宋字体](https://raw.githubusercontent.com/dengcao/free-fonts/refs/heads/main/%E5%85%8D%E8%B4%B9%E5%95%86%E7%94%A8%E5%AD%97%E4%BD%93%EF%BC%88%E5%85%B11328%E6%AC%BE%2C1328%20free%20commercial%20fonts%EF%BC%89/%E4%B8%AD%E6%96%87%E5%AD%97%E4%BD%93%EF%BC%88%E5%85%B1348%E6%AC%BE%EF%BC%8C348%20Chinese%20fonts%EF%BC%89/%E5%9D%8A%E5%AE%8B%E5%AD%97%E4%BD%93.ttf)
- 如下载失败可使用GitHub加速镜像链接下载[加速地址_坊宋字体](https://gh.llkk.cc/https://raw.githubusercontent.com/dengcao/free-fonts/refs/heads/main/%E5%85%8D%E8%B4%B9%E5%95%86%E7%94%A8%E5%AD%97%E4%BD%93%EF%BC%88%E5%85%B11328%E6%AC%BE%2C1328%20free%20commercial%20fonts%EF%BC%89/%E4%B8%AD%E6%96%87%E5%AD%97%E4%BD%93%EF%BC%88%E5%85%B1348%E6%AC%BE%EF%BC%8C348%20Chinese%20fonts%EF%BC%89/%E5%9D%8A%E5%AE%8B%E5%AD%97%E4%BD%93.ttf)

## v1.2.3
- 优化 AstrBot 行为列表，补充指令介绍

## v1.2.4
- 分群订阅改为号池轮询后按账号所属全部分组去重推送，同一 SteamID 可加入多个分组
- `/sw remove <target> [group]` 支持仅移出指定分组，无剩余分组时自动移出监控号池
- 字体下载/设置/清空改为管理员操作，并限制下载文件名避免路径穿越
- 修复 Steam API HTTP 状态错误、自定义链接解析异常未被友好处理的问题
- 修复配置了管理员后仍可能自动加入监控、解绑后昵称元数据残留、手改轮询间隔可低于 30 秒的问题

## v1.2.5
- 新增内置菜单风格 2（卡片分区样式），保留经典菜单风格 1
- 新增 `/sw style [1|2]` 与 `/steamwatch_menustyle [1|2]` 用于查看或切换菜单风格

## v1.2.6
- 新增每日游玩时长排行榜：按监控组记录当天（4 点刷新自然日）累计游玩时长，跨游戏合计并保留每款游戏明细
- 新增 `/sw rank [group] [num] [days]`：查看指定分组排行，支持指定名次数量与最近 7/30 天聚合
- 跨天切分：会话跨 4 点边界或切换游戏时自动按段落账（分割段带标记），不影响“本次游玩”消息的完整时长；切换游戏时为刚结束的游戏推送结束消息
- 持久化改为 SQLite（`data/steamwatch_data.db`），旧 JSON 数据自动迁移；`leaderboard_keep_days` 默认 30
- 新增每日定时推送：`daily_rank_push_enabled` 在 `daily_rank_push_time`（默认 04:00）推送昨日各分组排行前 `daily_rank_push_num` 名
- 新配置：`daily_leaderboard_enabled` / `leaderboard_keep_days` / `data_file_path` / `daily_rank_push_enabled` / `daily_rank_push_time` / `daily_rank_push_num`
- 停止游戏评价逻辑已注释（保留 `_playtime_taunt` 便于恢复）
