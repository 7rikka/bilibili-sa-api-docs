# [UP主]查看我的建立的播放列表

> https://api.bilibili.tv/intl/videoup/web2/playlist/list

请求方式：`GET`

是否需要登录：`是`

## URL参数

| 参数名      | 类型  | 必填  | 内容     | 备注                                |
|----------|-----|-----|--------|-----------------------------------|
| s_locale | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| lang     | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| lang_id  | num |     | `3`    |                                   |
| timezone | str |     | 时区     | 例：GMT%2B08:00                     |
| csrf     | str | √   | 用户csrf |                                   |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注   |
|---------|-----|------|------|
| code    | num | 响应码  | 0：成功 |
| message | str | 0    |      |
| ttl     | num | 1    |      |
| data    | obj | 信息本体 |      |

### `data`对象

| 字段名      | 类型    | 内容     | 备注  |
|----------|-------|--------|-----|
| playlist | array | 播放列表信息 |     |

#### `data`对象 -> `playlist`数组中的对象

| 字段名       | 类型   | 内容     | 备注                  |
|-----------|------|--------|---------------------|
| id        | str  | 播放列表id |                     |
| title     | str  | 播放列表标题 |                     |
| cover     | str  | 播放列表封面 |                     |
| arc_count | num  | 包含视频数量 |                     |
| full      | bool | 是否已满   |                     |
| update_at | str  | 最后更新时间 | 格式：dd/MM/yyyy HH:mm |

## 请求示例

```shell
curl -L -X GET 'https://api.bilibili.tv/intl/videoup/web2/playlist/list?lang_id=3&lang=en_US&timezone=GMT%2B08:00&csrf=xxx' \
-H 'cookie: SESSDATA=xxx'
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
        "playlist": [
            {
                "id": "6773",
                "title": "123",
                "cover": "",
                "arc_count": 0,
                "full": false,
                "update_at": "27/09/2022  21:19"
            },
            {
                "id": "6772",
                "title": "123",
                "cover": "",
                "arc_count": 0,
                "full": false,
                "update_at": "27/09/2022  21:18"
            }
        ]
    }
}
```
</details>