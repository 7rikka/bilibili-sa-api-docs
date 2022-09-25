# 获取观看历史

> https://api.bilibili.tv/intl/gateway/web/v2/history/list?s_locale=en_US&platform=web&business=1&sub_type=0&cursor=&ps=20

请求方式：`GET`

是否需要登录：`是`

## URL参数

| 参数名      | 类型  | 必填  | 内容                                         | 备注                                |
|----------|-----|-----|--------------------------------------------|-----------------------------------|
| s_locale | str |     | 语种代码                                       | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台                                         |                                   |
| business | num |     | 1：ALL<br/>3：Video<br/>4：剧集                 |                                   |
| sub_type | num |     | Video：0<br/>ALL、Anime：101<br/>TV Shows：102 |                                   |
| cursor   | str |     | 下一页的游标                                     | 从`0`开始                            |
| ps       | num |     | 分页大小                                       | 最小`1`                             |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注    |
|---------|-----|------|-------|
| code    | num | 响应码  | 0: 成功 |
| message | str | 0    |       |
| ttl     | num | 1    |       |
| data    | obj | 信息本体 |       |

### `data`对象

| 字段名       | 类型   | 内容     | 备注  |
|-----------|------|--------|-----|
| cursor    | str  | 下一页的游标 |     |
| has_more  | bool | 是否有下一页 |     |
| today     | obj  | 今天的记录  |     |
| yesterday | obj  | 昨天的记录  |     |
| earlier   | obj  | 更早的记录  |     |

## 请求示例

```shell
curl -L -X GET 'https://api.bilibili.tv/intl/gateway/web/v2/history/list?s_locale=en_US&platform=web&business=1&sub_type=101&cursor=0&ps=1' \
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
    "cursor": "1",
    "has_more": true,
    "today": {
      "name": "Today",
      "cards": [
        {
          "type": "ugc",
          "aid": "2046530512",
          "card_type": "ugc_history_detail",
          "title": "[S02.E20] We Bare Bears | MALAYDUB",
          "cover": "https://pic-bstarstatic.akamaized.net/ugc/b22db25b7dcd94d76221cb8a9ed766ff.jpg",
          "view": "36 Views",
          "duration": "11:28",
          "author": {
            "mid": "1430334016",
            "avatar": "https://pic.bstarstatic.com/face/8cd4fd44df843df396b3906f689eb0f1e38c24e6.jpg",
            "nickname": "Nos_Movie_Sub_IndoMalay2"
          },
          "view_at": "Today 19:22",
          "view_history": {
            "progress": 32,
            "progress_text": ""
          },
          "live": null,
          "unavailable": false
        }
      ]
    },
    "yesterday": {
      "name": "Yesterday",
      "cards": []
    },
    "earlier": {
      "name": "Earlier",
      "cards": []
    }
  }
}
```

</details>

# 获取观看历史（导航栏）

> https://api.bilibili.tv/intl/gateway/web/v2/history/nav_list?s_locale=en_US&platform=web

请求方式：`GET`

是否需要登录：`是`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注    |
|---------|-----|------|-------|
| code    | num | 响应码  | 0: 成功 |
| message | str | 0    |       |
| ttl     | num | 1    |       |
| data    | obj | 信息本体 |       |

### `data`对象

| 字段名       | 类型  | 内容    | 备注  |
|-----------|-----|-------|-----|
| today     | obj | 今天的记录 |     |
| yesterday | obj | 昨天的记录 |     |
| earlier   | obj | 更早的记录 |     |

#### `data`对象 -> `today`对象

| 字段名   | 类型    | 内容   | 备注  |
|-------|-------|------|-----|
| name  | str   |      |     |
| cards | array | 记录实体 |     |

#### `data`对象 -> `yesterday`对象

| 字段名   | 类型    | 内容   | 备注  |
|-------|-------|------|-----|
| name  | str   |      |     |
| cards | array | 记录实体 |     |

#### `data`对象 -> `earlier`对象

| 字段名   | 类型    | 内容   | 备注  |
|-------|-------|------|-----|
| name  | str   |      |     |
| cards | array | 记录实体 |     |

##### 记录实体

| 字段名           | 类型    | 内容                                 | 备注       |
|---------------|-------|------------------------------------|----------|
| type          | str   | `ugc``ogv`                         |          |
| aid           | str   | 普通视频独有                             |          |
| card_type     | str   | `ugc_history_nav``ogv_history_nav` |          |
| title         | str   | 视频标题                               |          |
| cover         | str   | 封面                                 |          |
| view          | str   | 观看量                                |          |
| styles        |       | `null`                             | 剧集独有     |
| style_list    | array | 剧集标签列表                             | 剧集独有     |
| season_id     | str   | 剧集id                               | 剧集独有     |
| episode_id    | str   | 分集id                               | 剧集独有     |
| index_show    | str   |                                    | 剧集独有     |
| label         | num   | `0`                                | 剧集独有     |
| rank_info     |       | `null`                             | 剧集独有     |
| duration      | str   | 视频时长                               | 格式：mm:ss |
| author        | obj   | 作者信息                               |          |
| view_at       | str   | 什么时候观看的                            |          |
| view_history  | obj   | 观看信息                               |          |
| watched       | str   | `空串`                               | 剧集独有     |
| live          |       | `null`                             |          |
| pub_time_text | str   | `空串`                               | 剧集独有     |
| unavailable   | bool  | `false`                            |          |

##### 记录实体 -> `author`对象

| 字段名      | 类型  | 内容   | 备注   |
|----------|-----|------|------|
| mid      | str | 用户id | 单位：秒 |
| avatar   | str | 头像   | 单位：秒 |
| nickname | str | 用户名  | 单位：秒 |

##### 记录实体 -> `view_history`对象

| 字段名           | 类型  | 内容   | 备注   |
|---------------|-----|------|------|
| progress      | num | 观看进度 | 单位：秒 |
| progress_text | str | `空串` |      |

## 请求示例

```shell
curl -L -X GET 'https://api.bilibili.tv/intl/gateway/web/v2/history/nav_list?s_locale=en_US&platform=web' \
-H 'Cookie: SESSDATA=xxx'
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
    "today": {
      "name": "Today",
      "cards": [
        {
          "type": "ugc",
          "aid": "2046530512",
          "card_type": "ugc_history_nav",
          "title": "[S02.E20] We Bare Bears | MALAYDUB",
          "cover": "https://pic.bstarstatic.com/ugc/b22db25b7dcd94d76221cb8a9ed766ff.jpg",
          "view": "28 Views",
          "duration": "11:28",
          "author": {
            "mid": "1430334016",
            "avatar": "https://pic.bstarstatic.com/face/8cd4fd44df843df396b3906f689eb0f1e38c24e6.jpg",
            "nickname": "Nos_Movie_Sub_IndoMalay2"
          },
          "view_at": "Today 19:22",
          "view_history": {
            "progress": 32,
            "progress_text": ""
          },
          "live": null,
          "unavailable": false
        },
        {
          "type": "ogv",
          "card_type": "ogv_history_nav",
          "title": "Jujutsu Kaisen",
          "cover": "https://pic.bstarstatic.com/ogv/01bb0eed8b341bb091afd2d92f24e577d0b29f28.png",
          "view": "87.5M Views",
          "styles": "",
          "style_list": [
            "Fantasy",
            "Adventure"
          ],
          "season_id": "37738",
          "episode_id": "379287",
          "index_show": "Full",
          "label": 0,
          "rank_info": null,
          "view_history": {
            "progress": 2,
            "progress_text": "Last watched: E1 0:32"
          },
          "watched": "",
          "duration": "",
          "view_at": "Today 19:21",
          "pub_time_text": "",
          "unavailable": false
        },
        {
          "type": "ugc",
          "aid": "2044423524",
          "card_type": "ugc_history_nav",
          "title": "How to Train Your Dragon (2012) | MALAYDUB",
          "cover": "https://pic.bstarstatic.com/ugc/a39113dc77de1402b3ca3bcc14bb9e9d.jpg",
          "view": "3.4K Views",
          "duration": "1:33:44",
          "author": {
            "mid": "1430334016",
            "avatar": "https://pic.bstarstatic.com/face/8cd4fd44df843df396b3906f689eb0f1e38c24e6.jpg",
            "nickname": "Nos_Movie_Sub_IndoMalay2"
          },
          "view_at": "Today 19:08",
          "view_history": {
            "progress": 0,
            "progress_text": ""
          },
          "live": null,
          "unavailable": false
        },
        {
          "type": "ogv",
          "card_type": "ogv_history_nav",
          "title": "Boruto: Naruto Next Generations",
          "cover": "https://pic.bstarstatic.com/ogv/bb773a7dd56520ac4b27a9f7feaf4f3d5dda8f9f.png",
          "view": "264.9M Views",
          "styles": "",
          "style_list": [
            "Action",
            "Comedy"
          ],
          "season_id": "1005426",
          "episode_id": "10226626",
          "index_show": "E268 Released",
          "label": 0,
          "rank_info": null,
          "view_history": {
            "progress": 0,
            "progress_text": "Last watched: E1 0:01"
          },
          "watched": "",
          "duration": "",
          "view_at": "Today 18:46",
          "pub_time_text": "",
          "unavailable": false
        },
        {
          "type": "ugc",
          "aid": "2041405349",
          "card_type": "ugc_history_nav",
          "title": "BLACKPINK - Pink Venom (Music Video)",
          "cover": "https://pic.bstarstatic.com/ugc/0a8e4ff82a91911ce0808bf1850aa49d.jpg",
          "view": "67.2K Views",
          "duration": "3:14",
          "author": {
            "mid": "1547931955",
            "avatar": "https://pic.bstarstatic.com/face/1c9ddd05fcbb2ba02ab8aea15e87d5782a501e9d.jpg",
            "nickname": "BLINKPINK"
          },
          "view_at": "Today 18:45",
          "view_history": {
            "progress": 100,
            "progress_text": ""
          },
          "live": null,
          "unavailable": false
        },
        {
          "type": "ogv",
          "card_type": "ogv_history_nav",
          "title": "Tinted With You",
          "cover": "https://pic.bstarstatic.com/ogv/7fa43fa74dd4c8ec8965e04264b9003dd7e2eacd.png",
          "view": "1.4M Views",
          "styles": "",
          "style_list": [],
          "season_id": "1033996",
          "episode_id": "11008785",
          "index_show": "Full",
          "label": 0,
          "rank_info": null,
          "view_history": {
            "progress": 0,
            "progress_text": "Last watched: E1 0:03"
          },
          "watched": "",
          "duration": "",
          "view_at": "Today 18:45",
          "pub_time_text": "",
          "unavailable": false
        },
        {
          "type": "ugc",
          "aid": "2041346931",
          "card_type": "ugc_history_nav",
          "title": "\"At that time we were sixteen or seventeen years old, time was slow, summer was long...\"",
          "cover": "https://pic.bstarstatic.com/ugc/4dc597ff0b0ab22727242037d90b6e9b.jpeg",
          "view": "14.5K Views",
          "duration": "3:37",
          "author": {
            "mid": "1608515280",
            "avatar": "https://pic.bstarstatic.com/face/5c58e1c93bee2d079c4452462cb65170b6b67834.jpg",
            "nickname": "Zaixiananxiangyo"
          },
          "view_at": "Today 18:45",
          "view_history": {
            "progress": 1,
            "progress_text": ""
          },
          "live": null,
          "unavailable": false
        },
        {
          "type": "ugc",
          "aid": "2045939890",
          "card_type": "ugc_history_nav",
          "title": "Nightcore❤️ Sirensong - (lyrics)",
          "cover": "https://pic.bstarstatic.com/ugc/254923223583bf9b6278faf50915bdd0.jpg",
          "view": "1.5K Views",
          "duration": "2:45",
          "author": {
            "mid": "1366610152",
            "avatar": "https://pic.bstarstatic.com/face/2d5eb3b0880d337d126b8509bae795071e648723.jpg",
            "nickname": "NightcoreMusic"
          },
          "view_at": "Today 16:57",
          "view_history": {
            "progress": 5,
            "progress_text": ""
          },
          "live": null,
          "unavailable": false
        },
        {
          "type": "ugc",
          "aid": "2045698377",
          "card_type": "ugc_history_nav",
          "title": "90s experience the feeling of being a sea king with \"Boys\" to open the love of light and night",
          "cover": "https://pic.bstarstatic.com/ugc/7bab4776b351955cdca796a62635b78b.jpg",
          "view": "7.1K Views",
          "duration": "1:31",
          "author": {
            "mid": "1808294708",
            "avatar": "https://pic.bstarstatic.com/face/6d1b7668bbd1ab58b2e7ebc3c1e0c1134951d584.jpg",
            "nickname": "yjnau"
          },
          "view_at": "Today 16:25",
          "view_history": {
            "progress": 0,
            "progress_text": ""
          },
          "live": null,
          "unavailable": false
        }
      ]
    },
    "yesterday": {
      "name": "Yesterday",
      "cards": []
    },
    "earlier": {
      "name": "Earlier",
      "cards": []
    }
  }
}
```

</details>