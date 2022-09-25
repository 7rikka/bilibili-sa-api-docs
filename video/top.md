# [UP主]置顶/取消置顶自己的视频

> https://api.bilibili.tv/intl/videoup/web2/top/set

请求方式：`POST`

是否需要登录：`是`

Content-Type：`application/json`

## URL参数

| 参数名      | 类型  | 必填  | 内容     | 备注                                |
|----------|-----|-----|--------|-----------------------------------|
| s_locale | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| lang     | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| lang_id  | num |     | `3`    |                                   |
| timezone | str |     | 时区     | 例：GMT%2B08:00                     |
| csrf     | str | √   | 用户csrf |                                   |

## JSON参数

| 参数名    | 类型   | 必填  | 内容                     | 备注  |
|--------|------|-----|------------------------|-----|
| aid    | str  | √   | 视频av号                  |     |
| switch | bool |     | true：置顶<br/>false：取消置顶 |     |
| force  | bool |     | `false`                |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注    |
|---------|-----|------|-------|
| code    | num | 响应码  | 0: 成功 |
| message | str | 0    |       |
| ttl     | num | 1    |       |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/intl/videoup/web2/top/set?csrf=xxx' \
-H 'content-type: application/json' \
-H 'cookie: SESSDATA=xxx' \
--data-raw '{
    "aid": "2047772058",
    "switch": true,
    "force": false
}'
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