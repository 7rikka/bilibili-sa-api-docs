# 获取登录二维码

> https://passport.bilibili.tv/x/intl/passport-login/qrcode/auth/url

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

| 字段名     | 类型  | 内容                        | 备注  |
|---------|-----|---------------------------|-----|
| qr_type | str | `qrcode_login`            |     |
| qr_url  | str | 登录地址，需要用APP扫描该地址的二维码，实现登录 |     |

## 请求示例

```shell
curl -L -X GET 'https://passport.bilibili.tv/x/intl/passport-login/qrcode/auth/url?s_locale=en_US&platform=web'
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
        "qr_url": "https://www.bilibili.tv/h5/en/qrcode/login?ticket=4478b3e64d05ce26638f4d715ebe0a91",
        "qr_type": "qrcode_login"
    }
}
```
</details>

# 获取二维码扫描状态

> https://passport.bilibili.tv/x/intl/passport-login/qrcode/auth/fetch

请求方式：`GET`

是否需要登录：`否`

## URL参数

| 参数名      | 类型  | 必填  | 内容           | 备注                                |
|----------|-----|-----|--------------|-----------------------------------|
| s_locale | str |     | 语种代码         | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台           |                                   |
| ticket   | str | √   | 二维码ticket_id |                                   |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注   |
|---------|-----|------|------|
| code    | num | 响应码  | 0：成功 |
| message | str | 0    |      |
| ttl     | num | 1    |      |

## 请求示例

```shell
curl -L -X GET 'https://passport.bilibili.tv/x/intl/passport-login/qrcode/auth/fetch?ticket=xxx'
```

## 响应示例

<details>
<summary>点击查看</summary>

```json

```
</details>