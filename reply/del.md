# [UP主]删除自己视频下的评论

> https://api.bilibili.tv/studio/reply/del?lang_id=3&lang=en_US&s_locale=en_US&timezone=GMT%2B08:00&csrf=e8deac4d72e96910ab50dff53b9a1a02

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

| 参数名  | 类型  | 必填  | 内容   | 备注  |
|------|-----|-----|------|-----|
| rpid | str | √   | 评论id |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注    |
|---------|-----|------|-------|
| code    | num | 响应码  | 0: 成功 |
| message | str | 0    |       |
| ttl     | num | 1    |       |
| data    | obj | 信息本体 |       |

### `data`对象

| 字段名   | 类型  | 内容     | 备注  |
|-------|-----|--------|-----|
| toast | str | 删除成功提示 |     |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/studio/reply/del?lang_id=3&lang=en_US&s_locale=en_US&timezone=GMT%2B08:00&csrf=xxx' \
-H 'Cookie: SESSDATA=xxx' \
-H 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'rpid=35591249935206400'
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
    "toast": "Deleted successfully"
  }
}
```
</details>