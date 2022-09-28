# 查看我的收藏列表

> https://api.bilibili.tv/intl/gateway/web/v2/fav/list

请求方式：`GET`

是否需要登录：`是`

## URL参数

| 参数名      | 类型  | 必填  | 内容                         | 备注                                |
|----------|-----|-----|----------------------------|-----------------------------------|
| s_locale | str |     | 语种代码                       | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台                         |                                   |
| type     | num |     | 1：普通视频<br/>2：剧集            |                                   |
| sub_type | num |     | 101：Anime<br/>102：TV Shows |                                   |
| pn       | num | √   |                            |                                   |
| ps       | num | √   |                            |                                   |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注   |
|---------|-----|------|------|
| code    | num | 响应码  | 0：成功 |
| message | str | 0    |      |
| ttl     | num | 1    |      |
| data    | obj | 信息本体 |      |

### `data`对象

| 字段名      | 类型    | 内容      | 备注  |
|----------|-------|---------|-----|
| has_more | bool  | 是否有更多信息 |     |
| cards    | array |         |     |

#### `data`对象 -> `cards`数组中的对象

| 字段名           | 类型    | 内容          | 备注  |
|---------------|-------|-------------|-----|
| type          | str   | `ogv`       |     |
| card_type     | str   | `card_type` |     |
| title         | str   | 标题          |     |
| cover         | str   | 封面          |     |
| view          | str   | 播放总量        |     |
| styles        | str   | `空串`        |     |
| style_list    | array | 类型标签列表      |     |
| season_id     | str   | 剧集id        |     |
| episode_id    | str   | 分集id        |     |
| index_show    | str   | 更新提示        |     |
| label         | num   | `0`         |     |
| rank_info     |       | `null`      |     |
| view_history  | obj   |             |     |
| watched       | str   | `空串`        |     |
| duration      | str   | `空串`        |     |
| view_at       | str   | `空串`        |     |
| pub_time_text | str   | `空串`        |     |
| unavailable   | bool  | `false`     |     |

#### `data`对象 -> `cards`数组中的对象 -> `view_history`对象

| 字段名           | 类型  | 内容       | 备注   |
|---------------|-----|----------|------|
| progress      | num | 观看进度     | 单位：秒 |
| progress_text | str | 上次观看显示文本 |      |

## 请求示例

```shell
curl -L -X GET 'https://api.bilibili.tv/intl/gateway/web/v2/fav/list?s_locale=en_US&platform=web&pn=1&ps=101' \
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
    "has_more": false,
    "cards": [
      {
        "type": "ogv",
        "card_type": "ogv_fav_detail",
        "title": "Jujutsu Kaisen",
        "cover": "https://pic.bstarstatic.com/ogv/01bb0eed8b341bb091afd2d92f24e577d0b29f28.png",
        "view": "89.0M Views",
        "styles": "",
        "style_list": [
          "Fantasy",
          "Adventure"
        ],
        "season_id": "37738",
        "episode_id": "",
        "index_show": "Full",
        "label": 0,
        "rank_info": null,
        "view_history": {
          "progress": 0,
          "progress_text": "Last watched: E1"
        },
        "watched": "",
        "duration": "",
        "view_at": "",
        "pub_time_text": "",
        "unavailable": false
      }
    ]
  }
}
```

</details>

# 查看我的收藏列表（导航栏）

> https://api.bilibili.tv/intl/gateway/web/v2/history/nav_list

请求方式：`GET`

是否需要登录：`是`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |

## FORM参数

| 参数名 | 类型  | 必填  | 内容  | 备注  |
|-----|-----|-----|-----|-----|
| xxx | str |     |     |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注   |
|---------|-----|------|------|
| code    | num | 响应码  | 0：成功 |
| message | str | 0    |      |
| ttl     | num | 1    |      |
| data    | obj | 信息本体 |      |

### `data`对象

| 字段名   | 类型    | 内容  | 备注  |
|-------|-------|-----|-----|
| cards | array |     |     |

#### `data`对象 -> `cards`数组中的对象

| 字段名           | 类型    | 内容          | 备注  |
|---------------|-------|-------------|-----|
| type          | str   | `ogv`       |     |
| card_type     | str   | `card_type` |     |
| title         | str   | 标题          |     |
| cover         | str   | 封面          |     |
| view          | str   | 播放总量        |     |
| styles        | str   | `空串`        |     |
| style_list    | array | 类型标签列表      |     |
| season_id     | str   | 剧集id        |     |
| episode_id    | str   | 分集id        |     |
| index_show    | str   | 更新提示        |     |
| label         | num   | `0`         |     |
| rank_info     |       | `null`      |     |
| view_history  | obj   |             |     |
| watched       | str   | `空串`        |     |
| duration      | str   | `空串`        |     |
| view_at       | str   | `空串`        |     |
| pub_time_text | str   | `空串`        |     |
| unavailable   | bool  | `false`     |     |

##### `data`对象 -> `cards`数组中的对象 -> `view_history`对象

| 字段名           | 类型  | 内容       | 备注   |
|---------------|-----|----------|------|
| progress      | num | 观看进度     | 单位：秒 |
| progress_text | str | 上次观看显示文本 |      |

## 请求示例

```shell
curl -L -X GET 'https://api.bilibili.tv/intl/gateway/web/v2/fav/nav_list?s_locale=en_US&platform=web' \
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
    "cards": [
      {
        "type": "ogv",
        "card_type": "ogv_fav_nav",
        "title": "Jujutsu Kaisen",
        "cover": "https://pic.bstarstatic.com/ogv/01bb0eed8b341bb091afd2d92f24e577d0b29f28.png",
        "view": "89.0M Views",
        "styles": "",
        "style_list": [
          "Fantasy",
          "Adventure"
        ],
        "season_id": "37738",
        "episode_id": "",
        "index_show": "Full",
        "label": 0,
        "rank_info": null,
        "view_history": {
          "progress": 0,
          "progress_text": "Last watched: E1"
        },
        "watched": "",
        "duration": "",
        "view_at": "",
        "pub_time_text": "",
        "unavailable": false
      }
    ]
  }
}
```

</details>