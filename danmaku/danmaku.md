# 获取视频弹幕

> https://api.bilibili.tv/dm/web/list&oid=379287&type=2&segment_index=1

请求方式：`GET`

是否需要登录：`否`

## URL参数

| 参数名           | 类型  | 必填  | 内容                   | 备注                                |
|---------------|-----|-----|----------------------|-----------------------------------|
| s_locale      | str |     | 语种代码                 | 默认为英语<br/>[语言代码表](../language.md) |
| platform      | str |     | 平台                   |                                   |
| oid           | str | √   | 剧集：分集id<br/>普通视频：av号 |                                   |~~
| type          | str | √   | 1：普通视频<br/>2：剧集      |                                   |~~
| segment_index | num | √   | 弹幕分包序号               | 从1开始                              |~~