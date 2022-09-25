# 发送视频评论

> https://api.bilibili.tv/intl/gateway/web/v2/reply

请求方式：`POST`

是否需要登录：`是`

Content-Type：`application/json`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |

## JSON参数

| 参数名     | 类型  | 必填  | 内容                   | 备注  |
|---------|-----|-----|----------------------|-----|
| type    | num | √   | 1：普通视频<br/>3：剧集      |     |
| oid     | str | √   | 剧集：分集id<br/>普通视频：av号 |     |
| root    | str |     | 根回复id                |     |
| parent  | str |     | 父回复id                |     |
| message | str | √   | 评论内容                 |     |
| spm_id  | str |     |                      |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注    |
|---------|-----|------|-------|
| code    | num | 响应码  | 0: 成功 |
| message | str | 0    |       |
| ttl     | num | 1    |       |
| data    | obj | 信息本体 |       |

### `data`对象

| 字段名   | 类型  | 内容   | 备注  |
|-------|-----|------|-----|
| reply | obj | 评论对象 |     |

### `data`对象 -> `reply`对象

| 字段名                | 类型  | 内容                   | 备注  |
|--------------------|-----|----------------------|-----|
| rpid               | str | 评论id                 |     |
| parent             | str | 父评论id                |     |
| root               | str | 根评论id                |     |
| count              | num | 子评论数                 |     |
| count_text         | str | 子评论数显示文本             |     |
| like_count         | str | 点赞数                  |     |
| like_state         | num | 当前用户是否点赞             |     |
| ctime_text         | str | 评论发送时间显示文本           |     |
| is_top             | num | 是否置顶<br/>0：否<br/>1：是 |     |
| is_top_text        | str | 置顶评论显示文本             |     |
| uploader_like_text | str | 作者点赞显示文本             |     |
| member             | obj | 当前用户信息               |     |
| content            | obj | 回复内容                 |     |
| replies            |     | `null`               |     |

### `data`对象 -> `reply`对象 -> `member`对象

| 字段名         | 类型    | 内容                   | 备注    |
|-------------|-------|----------------------|-------|
| 字段名         | 类型    | 内容                   | 备注    |
| ----------- | ----- | ------               | ----- |
| mid         | str   | 用户id                 |       |
| name        | str   | 用户名                  |       |
| face        | str   | 头像                   |       |
| type        | num   | 0：`空串`<br/>1：Creator |       |
| type_text   | str   |                      |       |

### `data`对象 -> `replies`数组 -> `content`对象

| 字段名     | 类型  | 内容            | 备注  |
|---------|-----|---------------|-----|
| message | str | 评论内容          |     |
| members |     | `null`        |     |
| emoji   | obj | 评论中的emoji表情信息 |     |

### `data`对象 -> `replies`数组 -> `content`对象 -> `emoji`对象

| 字段名    | 类型  | 内容  | 备注  |
|--------|-----|-----|-----|
| [表情名1] | obj | 表情1 |     |
| [表情名2] | obj | 表情2 |     |
| ...    | obj | 表情n |     |

#### `emoji`详情

| 字段名  | 类型  | 内容   | 备注  |
|------|-----|------|-----|
| url  | str | 图片地址 |     |
| size | num | 尺寸   |     |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/intl/gateway/web/v2/reply?s_locale=en_US&platform=web' \
-H 'cookie: SESSDATA=xxx' \
-H 'Content-Type: application/json' \
--data-raw '{
    "type": 1,
    "oid": "2041346931",
    "root": "33631582065003520",
    "parent": "33631582065003520",
    "message": "yes",
    "spm_id": "bstar-web.ugc-video-detail.0.0"
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
    "reply": {
      "rpid": "35589662815290368",
      "parent": "33631582065003520",
      "root": "33631582065003520",
      "count": 0,
      "count_text": "",
      "like_count": "",
      "like_state": 0,
      "ctime_text": "Just now",
      "is_top": 0,
      "is_top_text": "",
      "uploader_like_text": "",
      "member": {
        "mid": "1709658507",
        "name": "Rikka Takanashi (QAQ)",
        "face": "https://pic.bstarstatic.com/face/98bce5ddb2e5c1c6188b2a6ba2cce1e50fdd4ab5.png",
        "type": 0,
        "type_text": ""
      },
      "content": {
        "message": "yes",
        "members": null,
        "emoji": {}
      },
      "replies": null
    }
  }
}
```

</details>

# [UP主]回复自己视频下的评论

> https://api.bilibili.tv/studio/reply/add

请求方式：`POST`

是否需要登录：`是`

Content-Type：`application/x-www-form-urlencoded`

## URL参数

| 参数名      | 类型  | 必填  | 内容     | 备注                                |
|----------|-----|-----|--------|-----------------------------------|
| s_locale | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| lang     | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| lang_id  | num |     | `3`    |                                   |
| timezone | str |     | 时区     | 例：GMT%2B08:00                     |
| csrf     | str | √   | 用户csrf |                                   |

## FORM参数

| 参数名      | 类型  | 必填  | 内容                   | 备注  |
|----------|-----|-----|----------------------|-----|
| type     | num | √   | 1：普通视频<br/>3：剧集      |     |
| oid      | str | √   | 剧集：分集id<br/>普通视频：av号 |     |
| root     | str |     | 根回复id                |     |
| parent   | str |     | 父回复id                |     |
| message  | str | √   | 评论内容                 |     |
| platform | str |     | 平台                   |     |
| build    | str |     | `1000000`            |     |
| decice   | str |     | `空串`                 |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注    |
|---------|-----|------|-------|
| code    | num | 响应码  | 0: 成功 |
| message | str | 0    |       |
| ttl     | num | 1    |       |
| data    | obj | 信息本体 |       |

### `data`对象

| 字段名           | 类型  | 内容       | 备注  |
|---------------|-----|----------|-----|
| reply         | obj | 评论对象     |     |
| success_toast | str | 发送成功显示文本 |     |

### `data`对象 -> `reply`对象

| 字段名        | 类型  | 内容       | 备注  |
|------------|-----|----------|-----|
| rpid       | str | 评论id     |     |
| oid        | str | 相关视频id   |     |
| type       | str | 1：普通视频   |     |
| mid        | str |          |     |
| parent     | str | 父评论id    |     |
| root       | str | 根评论id    |     |
| dialog     | str |          |     |
| count      | num | 子评论数     |     |
| state      | num |          |     |
| like_state | num | 当前用户是否点赞 |     |
| like_count | str | 点赞数      |     |
| ctime      | num |          |     |
| ctime_fmt  | str |          |     |
| member     | obj | 当前用户信息   |     |
| content    | obj | 回复内容     |     |
| replies    |     | `null`   |     |

### `data`对象 -> `reply`对象 -> `member`对象

| 字段名         | 类型    | 内容                   | 备注    |
|-------------|-------|----------------------|-------|
| 字段名         | 类型    | 内容                   | 备注    |
| ----------- | ----- | ------               | ----- |
| mid         | str   | 用户id                 |       |
| name        | str   | 用户名                  |       |
| face        | str   | 头像                   |       |
| type        | num   | 0：`空串`<br/>1：Creator |       |
| identity    |       | `null`               |       |
| pendant_id  | num   |                      |       |
| pendant_img | str   |                      |       |
| is_vip      | bool  |                      |       |

### `data`对象 -> `replies`数组 -> `content`对象

| 字段名        | 类型    | 内容            | 备注  |
|------------|-------|---------------|-----|
| message    | str   | 评论内容          |     |
| members    | array | `空数组`         |     |
| max_line   | num   | `6`           |     |
| emoji      | obj   | 评论中的emoji表情信息 |     |
| rich_texts | array | `空数组`         |     |

### `data`对象 -> `replies`数组 -> `content`对象 -> `emoji`对象

| 字段名    | 类型  | 内容  | 备注  |
|--------|-----|-----|-----|
| [表情名1] | obj | 表情1 |     |
| [表情名2] | obj | 表情2 |     |
| ...    | obj | 表情n |     |

#### `emoji`详情

| 字段名  | 类型  | 内容   | 备注  |
|------|-----|------|-----|
| url  | str | 图片地址 |     |
| size | num | 尺寸   |     |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/studio/reply/add?lang_id=3&lang=en_US&s_locale=en_US&timezone=GMT%2B08:00&csrf=xxx' \
-H 'cookie: SESSDATA=xxx' \
-H 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'message=aaa' \
--data-urlencode 'oid=2047772058' \
--data-urlencode 'type=1' \
--data-urlencode 'parent=35591149916261376' \
--data-urlencode 'root=35591149916261376'
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
    "reply": {
      "rpid": "35593323833984000",
      "oid": "2047772058",
      "type": 1,
      "mid": 1709658507,
      "parent": "35591149916261376",
      "root": "35591149916261376",
      "dialog": "35593323833984000",
      "count": 0,
      "state": 0,
      "like_state": 0,
      "like_count": 0,
      "ctime": 1664100077,
      "ctime_fmt": "Just now",
      "member": {
        "mid": 1709658507,
        "name": "Rikka Takanashi (QAQ)",
        "face": "https://pic.bstarstatic.com/face/22fba37f73583d14b8f9498c0fd618d314bff55a.png",
        "type": 0,
        "identity": null,
        "pendant_id": 0,
        "pendant_img": "",
        "is_vip": false
      },
      "content": {
        "message": "aaa",
        "members": [],
        "max_line": 6,
        "emojis": null,
        "rich_texts": []
      },
      "replies": null
    },
    "success_toast": "Sent successfully"
  }
}
```

</details>