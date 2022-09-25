# [UP主]删除视频

> https://api.bilibili.tv/intl/videoup/web2/del

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

| 参数名 | 类型  | 必填    | 内容  | 备注  |
|-----|-----|-------|-----|-----|
| aid | str | 视频av号 |     |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注    |
|---------|-----|------|-------|
| code    | num | 响应码  | 0: 成功 |
| message | str | 0    |       |
| ttl     | num | 1    |       |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/intl/videoup/web2/del?lang_id=3&lang=en_US&s_locale=en_US&timezone=GMT%2B08:00&csrf=e8deac4d72e96910ab50dff53b9a1a02' \
-H 'cookie: SESSDATA=xxx' \
-H 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'aid=2047772058'
```

## 响应示例

<details>
<summary>点击查看</summary>

```json
{
  "code": 0,
  "message": "0",
  "ttl": 1
}
```

</details>