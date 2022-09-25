# 点赞/取消点赞评论

> https://api.bilibili.tv/intl/gateway/web/v2/play/like

请求方式：`POST`

是否需要登录：`是`

Content-Type：`application/json`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |

## JSON参数

| 参数名      | 类型  | 必填  | 内容                   | 备注    |
|----------|-----|-----|----------------------|-------|
| type     | num | √   | 3: 普通视频<br/>4: 剧集    |       |
| oid      | str | √   | 剧集：分集id<br/>普通视频：av号 |       |
| action   | num | √   | 1: 点赞<br/>2: 取消点赞    |       |
| progress | num |     | 视频当前播放进度             | 单位：毫秒 |
| spm_id   | str |     |                      |       |

## Json回复

### 根对象

| 字段名     | 类型  | 内容    | 备注    |
|---------|-----|-------|-------|
| code    | num | 响应码   | 0: 成功 |
| message | str | 0     |       |
| ttl     | num | 1     |       |
| data    | obj | `空对象` |       |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/intl/gateway/web/v2/play/like' \
-H 'Cookie: SESSDATA=xxx' \
-H 'Content-Type: application/json' \
--data-raw '{
    "type": 3,
    "oid": "2041346931",
    "action": 1,
    "progress": 4177,
    "spm_id": "bstar-web.ugc-video-detail.0.0"
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
  "data": {}
}
```

</details>