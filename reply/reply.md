# 获取视频评论

> https://api.bilibili.tv/intl/gateway/web/v2/reply/root?s_locale=en_US&platform=web&pn=0&ps=20&oid=10142191&type=3&sort_type=1

请求方式：`GET`

是否需要登录：`否`

## URL参数

| 参数名       | 类型  | 必填  | 内容     | 备注                                |
|-----------|-----|-----|--------|-----------------------------------|
| s_locale  | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| platform  | str |     | 平台     |                                   |
| pn        | str |     |        |                                   |
| ps        | str |     |        |                                   |
| oid       | num | √   | 关联分集id |                                   |
| type      | num | √   | `3`    |                                   |
| sort_type | num |     | 排序方式   | 1: 最热 2: 最新                       |

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
