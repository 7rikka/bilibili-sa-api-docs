# 获取公钥和盐值

> https://passport.bilibili.tv/x/intl/passport-login/web/key

请求方式：`GET`

是否需要登录：`否`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注   |
|---------|-----|------|------|
| code    | num | 响应码  | 0：成功 |
| message | str | 0    |      |
| ttl     | num | 1    |      |
| data    | obj | 信息本体 |      |

### `data`对象

| 字段名  | 类型  | 内容     | 备注  |
|------|-----|--------|-----|
| hash | str | 密码盐值   |     |
| key  | str | rsa 公钥 |     |

## 请求示例

**请求需要设置Host**

```shell
curl -L -X GET 'https://passport.bilibili.tv/x/intl/passport-login/web/key?s_locale=en_US&platform=web' \
-H 'Host: passport.bilibili.tv'
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
        "hash": "e0f336d60d14ef12",
        "key": "-----BEGIN PUBLIC KEY-----\nMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDjb4V7EidX/ym28t2ybo0U6t0n\n6p4ej8VjqKHg100va6jkNbNTrLQqMCQCAYtXMXXp2Fwkk6WR+12N9zknLjf+C9sx\n/+l48mjUU8RqahiFD1XT/u2e0m2EN029OhCgkHx3Fc/KlFSIbak93EH/XlYis0w+\nXl69GV6klzgxW6d2xQIDAQAB\n-----END PUBLIC KEY-----\n"
    }
}
```
</details>