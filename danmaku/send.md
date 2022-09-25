# 发送弹幕

> https://api.bilibili.tv/dm/web/add

请求方式：`POST`

是否需要登录：`是`

Content-Type：`application/x-www-form-urlencoded`

## URL参数

| 参数名      | 类型  | 必填  | 内容       | 备注                                |
|----------|-----|-----|----------|-----------------------------------|
| s_locale | str |     | 语种代码     | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台       |                                   |
| csrf     | str | √   | 当前用户csrf |                                   |

## FORM参数

| 参数名      | 类型  | 必填  | 内容                   | 备注  |
|----------|-----|-----|----------------------|-----|
| color    | num | √   | 颜色参数                 |     |
| fontsize | num | √   | 字号                   |     |
| msg      | str | √   | 弹幕内容                 |     |
| mode     | num |     | `1`                  |     |
| progress | num |     | 出现时间                 | 毫秒值 |
| type     | num | √   | `1`                  |     |
| oid      | num | √   | 剧集：分集id<br/>普通视频：av号 |     |
| plat     | num | √   | `1`                  |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注                   |
|---------|-----|------|----------------------|
| code    | num | 响应码  | 0: 成功<br/>-111: -111 |
| message | str | 0    |                      |
| ttl     | num | 1    |                      |
| data    | obj | 信息本体 |                      |

### `data`对象

| 字段名      | 类型   | 内容      | 备注  |
|----------|------|---------|-----|
| action   | str  | `空串`    |     |
| dmid     | num  | 弹幕id    |     |
| dmid_str | str  | 弹幕id字符串 |     |
| visible  | bool | `true`  |     |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/dm/web/add?s_locale=en_US&platform=web&csrf=xxx' \
-H 'content-type: application/x-www-form-urlencoded' \
-H 'cookie: SESSDATA=xxx' \
--data-urlencode 'color=16777215' \
--data-urlencode 'fontsize=25' \
--data-urlencode 'msg=wow' \
--data-urlencode 'mode=1' \
--data-urlencode 'progress=7872' \
--data-urlencode 'type=1' \
--data-urlencode 'oid=2042422179' \
--data-urlencode 'plat=1'
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
        "action": "",
        "dmid": 28611087139604480,
        "dmid_str": "28611087139604480",
        "visible": true
    }
}
```
</details>