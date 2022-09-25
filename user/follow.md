# 关注/取消关注用户

> https://api.bilibili.tv/intl/gateway/web/v2/user/follow/modify

请求方式：`POST`

是否需要登录：`是`

Content-Type：`application/json`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |

## JSON参数

| 参数名         | 类型  | 必填  | 内容              | 备注  |
|-------------|-----|-----|-----------------|-----|
| fid         | str | √   | 用户id            |     |
| action      | num |     | 1：关注<br/>2：取消关注 |     |
| from_spm_id | str |     |                 |     |
| spm_id      | str |     |                 |     |
| h5_url      | str |     | 在哪个页面点击了关注      |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注                   |
|---------|-----|------|----------------------|
| code    | num | 响应码  | 0: 成功<br/>-111: -111 |
| message | str | 0    |                      |
| ttl     | num | 1    |                      |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/intl/gateway/web/v2/user/follow/modify?s_locale=en_US&platform=web' \
-H 'cookie: SESSDATA=xxx' \
-H 'Content-Type: application/json' \
--data-raw '{
    "fid": "1608515280",
    "action": 2
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