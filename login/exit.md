# 注销登录

> https://passport.bilibili.tv/x/intl/passport-login/web/login/exit

请求方式：`POST`

是否需要登录：`是`

Content-Type：`application/x-www-form-urlencoded`

## URL参数

| 参数名      | 类型  | 必填  | 内容     | 备注                                |
|----------|-----|-----|--------|-----------------------------------|
| s_locale | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台     |                                   |
| csrf     | str |     | 用户csrf |                                   |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注                      |
|---------|-----|------|-------------------------|
| code    | num | 响应码  | 0：成功<br/>-111：csrf 校验失败 |
| message | str | 0    |                         |
| ttl     | num | 1    |                         |
| data    | obj | 信息本体 |                         |

### `data`对象

| 字段名    | 类型  | 内容   | 备注  |
|--------|-----|------|-----|
| go_url | str | `空串` |     |

## 请求示例

**请求需要设置Host**

**Cookie需设置SESSDATA、bili_jct和DedeUserID**

```shell
curl -L -X POST 'https://passport.bilibili.tv/x/intl/passport-login/web/login/exit?csrf=xxx' \
-H 'cookie: SESSDATA=xxx; bili_jct=xxx; DedeUserID=xxx' \
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
        "go_url": ""
    }
}
```
</details>