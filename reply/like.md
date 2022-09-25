# 点赞/取消点赞评论

> https://api.bilibili.tv/intl/gateway/web/v2/reply/like

请求方式：`POST`

是否需要登录：`是`

Content-Type：`application/json`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |

## JSON参数

| 参数名    | 类型  | 必填  | 内容              | 备注  |
|--------|-----|-----|-----------------|-----|
| rpid   | str | √   | 评论id            |     |
| action | num | √   | 1：点赞<br/>2：取消点赞 |     |
| spm_id | str |     |                 |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注                   |
|---------|-----|------|----------------------|
| code    | num | 响应码  | 0: 成功<br/>-111: -111 |
| message | str | 0    |                      |
| ttl     | num | 1    |                      |
| data    | obj | 信息本体 |                      |

### `data`对象

| 字段名                | 类型  | 内容   | 备注  |
|--------------------|-----|------|-----|
| uploader_like_text | str | `空串` |     |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/intl/gateway/web/v2/reply/like?s_locale=en_US&platform=web' \
-H 'cookie: SESSDATA=xxx' \
-H 'Content-Type: application/json' \
--data-raw '{
    "rpid": "33631582065003520",
    "action": 2,
    "spm_id": "bstar-web.homepage.trending.all"
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
        "uploader_like_text": ""
    }
}
```
</details>