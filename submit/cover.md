# [UP主]上传封面

> https://api.bilibili.tv/intl/videoup/web2/cover

请求方式：`POST`

是否需要登录：`是`

Content-Type：`multipart/form-data`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |
| xxx      | str |     |      |                                   |

## FORM参数

| 参数名   | 类型  | 必填  | 内容           | 备注                              |
|-------|-----|-----|--------------|---------------------------------|
| cover | str | √   | 图片内容base64编码 | 需添加前缀：`data:image/jpeg;base64,` |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注                                                                       |
|---------|-----|------|--------------------------------------------------------------------------|
| code    | num | 响应码  | 0：成功<br/>10004051：Error with file data. Please upload cover image again. |
| message | str | 0    |                                                                          |
| ttl     | num | 1    |                                                                          |
| data    | obj | 信息本体 |                                                                          |

### `data`对象

| 字段名 | 类型  | 内容   | 备注  |
|-----|-----|------|-----|
| url | str | 图片地址 |     |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/intl/videoup/web2/cover?lang_id=3&lang=en_US&s_locale=zh_ZH&timezone=GMT%2B08:00&csrf=xxx' \
-H 'Cookie: SESSDATA=xxx' \
-F 'cover="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD......."'
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
        "url": "https://p.bstarstatic.com/ugc/xxx.jpg"
    }
}
```
</details>