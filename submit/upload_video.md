# 获取上传参数

> https://api.bilibili.tv/preupload

请求方式：`POST`
请求方式：`GET`

是否需要登录：`否` (竟然可以不登录0.0)

## URL参数

| 参数名           | 类型  | 必填  | 内容         | 备注    |
|---------------|-----|-----|------------|-------|
| name          | str | √   | 文件名        |       |
| size          | num |     | 文件大小       | 单位：字节 |
| r             | str | √   | `upos`     |       |
| profile       | str | √   | `iup/bup`  |       |
| ssl           | num |     | `0`        |       |
| version       | str |     | `2.10.0`   |       |
| build         | str |     | `2100000`  |       |
| probe_version | str |     | `20211012` |       |
| upcdn         | str |     | `qn`       |       |
| zone          | str |     | `cs``sz`   |       |
| biz           | str |     | `UGC`      |       |

## Json回复

### 根对象

| 字段名               | 类型    | 内容         | 备注  |
|-------------------|-------|------------|-----|
| OK                | num   | `1`        |     |
| auth              | str   |            |     |
| biz_id            | num   | `0`        |     |
| chunk_retry       | num   | `10`       |     |
| chunk_retry_delay | num   | `3`        |     |
| chunk_size        | num   | `22020096` |     |
| endpoint          | str   |            |     |
| endpoints         | array |            |     |
| expose_params     |       | `null`     |     |
| put_query         | str   |            |     |
| threads           | num   | `5`        |     |
| timeout           | num   | `1200`     |     |
| uip               | str   |            |     |
| upos_uri          | str   |            |     |

## 请求示例

```shell
curl -L -X GET 'https://api.bilibili.tv/preupload?name=1.mp4&r=upos&profile=iup/bup'
```

## 响应示例

<details>
<summary>点击查看</summary>

```json
{
  "OK": 1,
  "auth": "ak=1494471752&cdn=%2F%2Fupos-sz-upcdnqn.bilivideo.com&os=upos&sign=83730ebc186633fac8dcc02e459a9cf5&timestamp=1664287080.484&uid=1709658507&uip=172.105.116.16&uport=46833&use_dqp=0",
  "biz_id": 0,
  "chunk_retry": 10,
  "chunk_retry_delay": 3,
  "chunk_size": 22020096,
  "endpoint": "//upos-sz-upcdnqn.bilivideo.com",
  "endpoints": [
    "//upos-sz-upcdnqn.bilivideo.com",
    "//upos-sz-upcdnws.bilivideo.com"
  ],
  "expose_params": null,
  "put_query": "os=upos&profile=iup%2Fbup",
  "threads": 5,
  "timeout": 1200,
  "uip": "172.105.116.16",
  "upos_uri": "upos://iupboss/n220927adooosg1vibkkf1kfwxdddi8a.mp4"
}
```

</details>