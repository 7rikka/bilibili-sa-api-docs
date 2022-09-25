# 获取视频评论

> https://api.bilibili.tv/intl/gateway/web/v2/reply/root

请求方式：`GET`

是否需要登录：`否`

## URL参数

| 参数名       | 类型  | 必填  | 内容                   | 备注                                |
|-----------|-----|-----|----------------------|-----------------------------------|
| s_locale  | str |     | 语种代码                 | 默认为英语<br/>[语言代码表](../language.md) |
| platform  | str |     | 平台                   |                                   |
| pn        | str |     |                      |                                   |
| ps        | str |     |                      |                                   |
| oid       | num | √   | 剧集：分集id<br/>普通视频：av号 |                                   |
| type      | num | √   | `3`                  |                                   |
| sort_type | num |     | 排序方式                 | 1: 最热 2: 最新                       |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注                                             |
|---------|-----|------|------------------------------------------------|
| code    | num | 响应码  | 0: 成功<br/>10010010: Comments are not available |
| message | str | 0    |                                                |
| ttl     | num | 1    |                                                |
| data    | obj | 信息本体 |                                                |

### `data`对象

| 字段名        | 类型    | 内容       | 备注  |
|------------|-------|----------|-----|
| tabs       | array | 评论排序方式   |     |
| replies    | array | 评论列表     |     |
| total      | num   | 评论总数     |     |
| total_text | str   | 评论总数显示文本 |     |
| cursor     | obj   | 游标       |     |

### `data`对象 -> `tabs`数组中的对象

| 字段名      | 类型   | 内容     | 备注  |
|----------|------|--------|-----|
| type     | num  | 排序方式id |     |
| name     | num  | 排序方式名称 |     |
| selected | bool | 默认选中   |     |

### `data`对象 -> `replies`数组中的对象

| 字段名                | 类型    | 内容   | 备注  |
|--------------------|-------|------|-----|
| rpid               | str   | 评论id |     |
| parent             | str   |      |     |
| root               | str   |      |     |
| count              | num   |      |     |
| count_text         | str   |      |     |
| like_count         | str   |      |     |
| like_state         | num   |      |     |
| ctime_text         | str   |      |     |
| is_top             | num   |      |     |
| is_top_text        | str   |      |     |
| uploader_like_text | str   |      |     |
| member             | obj   |      |     |
| content            | obj   |      |     |
| replies            | array |      |     |

### `data`对象 -> `replies`数组 -> `member`对象

| 字段名       | 类型  | 内容   | 备注  |
|-----------|-----|------|-----|
| mid       | str | 用户id |     |
| name      | str | 用户名  |     |
| face      | str | 头像   |     |
| face      | num | `0`  |     |
| type_text | str | `空串` |     |

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

### `data`对象 -> `cursor`对象

| 字段名    | 类型   | 内容      | 备注  |
|--------|------|---------|-----|
| is_end | bool | `false` |     |

## 请求示例

```shell
curl -L -X GET 'https://api.bilibili.tv/intl/gateway/web/v2/reply/root?s_locale=en_US&platform=web&pn=1&ps=1&oid=379287&type=3&sort_type=1'
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
    "tabs": [
      {
        "type": 1,
        "name": "Best",
        "selected": true
      },
      {
        "type": 2,
        "name": "Recent",
        "selected": false
      }
    ],
    "replies": [
      {
        "rpid": "11103034319831045",
        "parent": "",
        "root": "",
        "count": 306,
        "count_text": "306",
        "like_count": "700",
        "like_state": 0,
        "ctime_text": "22/06/2021",
        "is_top": 0,
        "is_top_text": "",
        "uploader_like_text": "",
        "member": {
          "mid": "1568849546",
          "name": "April Anne Igcasenza",
          "face": "https://pic.bstarstatic.com/face/6fb3b91301b32cfe414db9cdc5bba6eb30da6939.jpg",
          "type": 0,
          "type_text": ""
        },
        "content": {
          "message": "Sino Filipino dito?🥺",
          "members": null,
          "emoji": {}
        },
        "replies": []
      }
    ],
    "total": 9632,
    "total_text": "9.6K",
    "cursor": {
      "is_end": false
    }
  }
}
```
</details>