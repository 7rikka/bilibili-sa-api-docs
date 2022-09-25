# 获取指定用户上传的视频列表

> https://api.bilibili.tv/intl/gateway/web/v2/user/archives

请求方式：`GET`

是否需要登录：`否`

## URL参数

| 参数名      | 类型  | 必填  | 内容      | 备注                                |
|----------|-----|-----|---------|-----------------------------------|
| s_locale | str |     | 语种代码    | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台      |                                   |
| pn       | num | √   | 页数      | 从1开始                              |
| ps       | num | √   | 分页大小    | 范围[2,50]                          |
| mid      | num | √   | 查询的用户id |                                   |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注    |
|---------|-----|------|-------|
| code    | num | 响应码  | 0: 成功 |
| message | str | 0    |       |
| ttl     | num | 1    |       |
| data    | obj | 信息本体 |       |

### `data`对象

| 字段名      | 类型    | 内容     | 备注  |
|----------|-------|--------|-----|
| total    | num   | 记录总数   |     |
| ps       | num   | 分页大小   |     |
| pn       | num   | 当前页数   |     |
| has_next | bool  | 是否有下一页 |     |
| cards    | array | 视频信息   |     |

#### `data`对象 -> `cards`数组中的对象

| 字段名          | 类型   | 内容          | 备注       |
|--------------|------|-------------|----------|
| type         | str  | `ugc`       |          |
| aid          | str  | 视频av号       |          |
| card_type    | str  | `ugc_space` |          |
| title        | str  | 视频标题        |          |
| cover        | str  | 封面          |          |
| view         | str  | 观看量         |          |
| duration     | str  | 视频时长        | 格式：mm:ss |
| author       | obj  | `空串`        |          |
| view_at      | str  |             |          |
| view_history |      |             |          |
| live         |      |             |          |
| unavailable  | bool | `false`     |          |

## 请求示例

```shell
curl -L -X GET 'https://api.bilibili.tv/intl/gateway/web/v2/user/archives?s_locale=en_US&platform=web&pn=1&ps=20&mid=1430334016'
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
    "total": 234,
    "ps": 2,
    "pn": 1,
    "has_next": true,
    "cards": [
      {
        "type": "ugc",
        "aid": "2046530512",
        "card_type": "ugc_space",
        "title": "[S02.E20] We Bare Bears | MALAYDUB",
        "cover": "https://pic-bstarstatic.akamaized.net/ugc/b22db25b7dcd94d76221cb8a9ed766ff.jpg",
        "view": "24 Views",
        "duration": "11:28",
        "author": {
          "mid": "1430334016",
          "avatar": "https://pic.bstarstatic.com/face/8cd4fd44df843df396b3906f689eb0f1e38c24e6.jpg",
          "nickname": "Nos_Movie_Sub_IndoMalay2"
        },
        "view_at": "",
        "view_history": null,
        "live": null,
        "unavailable": false
      }
    ]
  }
}
```

</details>