# [UP主]新建播放列表

> https://api.bilibili.tv/intl/videoup/web2/playlist/add

请求方式：`POST`

是否需要登录：`是`

Content-Type：`application/json`

## URL参数

| 参数名      | 类型  | 必填  | 内容     | 备注                                |
|----------|-----|-----|--------|-----------------------------------|
| s_locale | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| lang     | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| lang_id  | num |     | `3`    |                                   |
| timezone | str |     | 时区     | 例：GMT%2B08:00                     |
| csrf     | str | √   | 用户csrf |                                   |

## JSON参数

| 参数名   | 类型  | 必填  | 内容     | 备注  |
|-------|-----|-----|--------|-----|
| title | str | √   | 播放列表名称 |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注                                                                         |
|---------|-----|------|----------------------------------------------------------------------------|
| code    | num | 响应码  | 0：成功<br/>10004307：Your title may contain sensitive words. Please change it |
| message | str | 0    |                                                                            |
| ttl     | num | 1    |                                                                            |
| data    | obj | 信息本体 |                                                                            |

### `data`对象

| 字段名       | 类型   | 内容         | 备注                   |
|-----------|------|------------|----------------------|
| id        | str  | 播放列表id     |                      |
| title     | str  | 播放列表名称     |                      |
| cover     | str  | 播放列表封面     |                      |
| arc_count | num  | 播放列表包含的视频数 |                      |
| full      | bool | 播放列表是否已满   |                      |
| update_at | str  | 最后更新时间     | 格式：dd/MM/yyyy  HH:mm |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/intl/videoup/web2/playlist/add?lang_id=3&lang=en_US&s_locale=en_US&timezone=GMT%2B08:00&csrf=xxx' \
-H 'content-type: application/json' \
-H 'cookie: SESSDATA=xxx' \
--data-raw '{
    "title": "123"
}'
```

## 响应示例

<details>
<summary>点击查看</summary>

```json
{
  "code": 0,
  "message": "0",
  "ttl": 1,
  "data": {
    "id": "6891",
    "title": "123",
    "cover": "",
    "arc_count": 0,
    "full": false,
    "update_at": "28/09/2022  16:30"
  }
}
```

</details>