# 收藏视频

> https://api.bilibili.tv/intl/gateway/web/v2/fav/add

请求方式：`POST`

是否需要登录：`是`

Content-Type：`application/json`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |

## JSON参数

| 参数名         | 类型  | 必填  | 内容                   | 备注  |
|-------------|-----|-----|----------------------|-----|
| rid         | str | √   | 剧集：分集id<br/>普通视频：av号 |     |
| type        | num | √   | 1：普通视频<br/>2：剧集      |     |
| progress    | num |     | 视频当前播放进度             |     |
| from_spm_id | str |     |                      |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容  | 备注    |
|---------|-----|-----|-------|
| code    | num | 响应码 | 0: 成功 |
| message | str | 0   |       |
| ttl     | num | 1   |       |

## 请求示例

```shell
curl -L -X POST 'https://api.bilibili.tv/intl/gateway/web/v2/fav/add?s_locale=en_US&platform=web' \
-H 'cookie: SESSDATA=xxx' \
-H 'Content-Type: application/json' \
--data-raw '{
    "rid": "1033996",
    "type": 2,
    "progress": 2636,
    "from_spm_id": "bstar-web.pgc-video-detail.0.0"
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

# 取消收藏视频

> https://api.bilibili.tv/intl/gateway/web/v2/fav/del

请求参数以及返回信息格式与 [收藏视频](#收藏视频) 相同