# 获取视频播放流

> https://api.bilibili.tv/intl/gateway/web/playurl

请求方式：`GET`

是否需要登录：`否`

## URL参数

| 参数名         | 类型  | 必填  | 内容     | 备注                                |
|-------------|-----|-----|--------|-----------------------------------|
| s_locale    | str |     | 语种代码   | 默认为英语<br/>[语言代码表](../language.md) |
| platform    | str | √   | 平台     |                                   |
| aid         | str | √   | av号    | aid, ep_id其中之一                    |
| ep_id       | num | √   | 动画分集id | aid, ep_id其中之一                    |
| qn          | num |     | 清晰度代码  | 默认为16<br/>                        |
| type        | num |     | `0`    |                                   |
| device      | str |     | `wap`  |                                   |
| tf          | num |     | `0`    |                                   |
| spm_id      | str |     |        |                                   |
| from_spm_id | str |     |        |                                   |

## 视频清晰度代码

| 代码  | 说明           |
|-----|--------------|
| 5   | 144P         |
| 6   | 240P         |
| 16  | 360P         |
| 32  | 480P         |
| 64  | 720P         |
| 80  | 1080P        |
| 112 | 1080P(HD)    |
| 116 | 1080P(60FPS) |
| 120 | 4K           |

## 音频音质代码

| 代码    | 说明   |
|-------|------|
| 30216 | 64K  |
| 30232 | 132K |
| 30280 | 192K |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注    |
|---------|-----|------|-------|
| code    | num | 响应码  | 0: 成功 |
| message | str | 0    |       |
| ttl     | num | 1    |       |
| data    | obj | 信息本体 |       |

### `data`对象

| 字段名     | 类型  | 内容    | 备注  |
|---------|-----|-------|-----|
| playurl | obj | 播放流信息 |     |

### `data`对象 -> `playurl`对象

| 字段名            | 类型    | 内容        | 备注             |
|----------------|-------|-----------|----------------|
| quality        | num   | 视频清晰度代码   | [跳转](#视频清晰度代码) |
| duration       | num   | 时长        | 单位：毫秒          |
| expire_at      | num   | 视频流地址过期时间 | 秒级时间戳          |
| video          | array | 视频流信息     |                |
| audio_resource | array | 音频信息      |                |

### `data`对象 -> `playurl`对象 -> `video`数组中的对象

| 字段名            | 类型  | 内容       | 备注  |
|----------------|-----|----------|-----|
| video_resource | obj | 视频流信息    |     |
| stream_info    | obj | 流信息      |     |
| audio_quality  | num | 配套音频音质代码 |     |

### `data`对象 -> `playurl`对象 -> `video`数组 -> `video_resource`对象

| 字段名            | 类型  | 内容       | 备注                  |
|----------------|-----|----------|---------------------|
| id             | str | 视频流地址    |                     |
| quality        | num | 视频清晰度代码  | [视频清晰度代码](#视频清晰度代码) |
| bandwidth      | num | 播放所需最低带宽 |                     |
| codec_id       | num | 编码id     |                     |
| duration       | num | 时长       | 单位：毫秒               |
| size           | num | 总大小      | 单位：字节               |
| md5            | str | `空串`     |                     |
| url            | str | 完整取流地址   | 如果无权获取，返回`空串`       |
| backup_url     |     | `null`   |                     |
| container      | num | `1`      |                     |
| start_with_sap | num | `1`      |                     |
| codecs         | str | 编码器信息    |                     |
| sar            | str | `1:1`    |                     |
| frame_rate     | str | 帧率       |                     |
| segment_base   | obj |          |                     |
| width          | num | 视频宽度     |                     |
| height         | num | 视频高度     |                     |
| mime_type      | str | 文件类型     |                     |

#### `data`对象 -> `playurl`对象 -> `video`数组 -> `video_resource`对象 -> `segment_base`对象

| 字段名         | 类型  | 内容  | 备注  |
|-------------|-----|-----|-----|
| range       | str |     |     |
| index_range | str |     |     |

### `data`对象 -> `playurl`对象 -> `audio_resource`数组中的对象

| 字段名            | 类型  | 内容       | 备注                |
|----------------|-----|----------|-------------------|
| id             | str | 音频流地址    |                   |
| quality        | num | 音频音质代码   | [音频音质代码](#音频音质代码) |
| bandwidth      | num | 播放所需最低带宽 |                   |
| codec_id       | num | 编码id     |                   |
| duration       | num | 时长       | 单位：毫秒             |
| size           | num | 总大小      | 单位：字节             |
| md5            | str | `空串`     |                   |
| url            | str | 完整取流地址   |                   |
| backup_url     |     | `null`   |                   |
| container      | num | `1`      |                   |
| start_with_sap | num | `1`      |                   |
| codecs         | str | 编码器信息    |                   |
| sar            | str | `空串`     |                   |
| frame_rate     | str | `空串`     |                   |
| segment_base   | obj |          |                   |
| width          | num | `0`      |                   |
| height         | num | `0`      |                   |
| mime_type      | str | 文件类型     |                   |

#### `data`对象 -> `playurl`对象 -> `audio_resource`数组 -> `segment_base`对象

| 字段名         | 类型  | 内容  | 备注  |
|-------------|-----|-----|-----|
| range       | str |     |     |
| index_range | str |     |     |

## 请求示例

```shell
curl -L -X GET 'https://api.bilibili.tv/intl/gateway/web/playurl?s_locale=en_US&platform=web&ep_id=11486522&qn=120'
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
    "playurl": {
      "quality": 32,
      "duration": 1442025,
      "expire_at": 1663925440,
      "video": [
        {
          "video_resource": {
            "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-281210110000.m4s",
            "quality": 120,
            "bandwidth": 4932244,
            "codec_id": 7,
            "duration": 1442025,
            "size": 889051803,
            "md5": "",
            "url": "",
            "backup_url": null,
            "container": 1,
            "start_with_sap": 1,
            "codecs": "avc1.640033",
            "sar": "1:1",
            "frame_rate": "16000/672",
            "segment_base": {
              "range": "0-994",
              "index_range": "995-4482"
            },
            "width": 3840,
            "height": 2160,
            "mime_type": "video/mp4"
          },
          "stream_info": {
            "quality": 120,
            "desc_text": "",
            "desc_words": "4K",
            "intact": true,
            "no_rexcode": false
          },
          "audio_quality": 30280
        },
        {
          "video_resource": {
            "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-261210110000.m4s",
            "quality": 112,
            "bandwidth": 1333911,
            "codec_id": 7,
            "duration": 1442025,
            "size": 240441581,
            "md5": "",
            "url": "",
            "backup_url": null,
            "container": 1,
            "start_with_sap": 1,
            "codecs": "avc1.640028",
            "sar": "1:1",
            "frame_rate": "16000/672",
            "segment_base": {
              "range": "0-994",
              "index_range": "995-4482"
            },
            "width": 1920,
            "height": 1080,
            "mime_type": "video/mp4"
          },
          "stream_info": {
            "quality": 112,
            "desc_text": "",
            "desc_words": "1080P(HD)",
            "intact": true,
            "no_rexcode": false
          },
          "audio_quality": 30232
        },
        {
          "video_resource": {
            "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-251210110000.m4s",
            "quality": 80,
            "bandwidth": 944416,
            "codec_id": 7,
            "duration": 1442025,
            "size": 170233868,
            "md5": "",
            "url": "",
            "backup_url": null,
            "container": 1,
            "start_with_sap": 1,
            "codecs": "avc1.640028",
            "sar": "1:1",
            "frame_rate": "16000/672",
            "segment_base": {
              "range": "0-994",
              "index_range": "995-4482"
            },
            "width": 1920,
            "height": 1080,
            "mime_type": "video/mp4"
          },
          "stream_info": {
            "quality": 80,
            "desc_text": "",
            "desc_words": "1080P",
            "intact": true,
            "no_rexcode": false
          },
          "audio_quality": 30216
        },
        {
          "video_resource": {
            "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-241210110000.m4s",
            "quality": 64,
            "bandwidth": 441051,
            "codec_id": 7,
            "duration": 1442025,
            "size": 79500885,
            "md5": "",
            "url": "",
            "backup_url": null,
            "container": 1,
            "start_with_sap": 1,
            "codecs": "avc1.64001F",
            "sar": "1:1",
            "frame_rate": "16000/672",
            "segment_base": {
              "range": "0-992",
              "index_range": "993-4480"
            },
            "width": 1280,
            "height": 720,
            "mime_type": "video/mp4"
          },
          "stream_info": {
            "quality": 64,
            "desc_text": "",
            "desc_words": "720P",
            "intact": true,
            "no_rexcode": false
          },
          "audio_quality": 30216
        },
        {
          "video_resource": {
            "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-231210110000.m4s",
            "quality": 32,
            "bandwidth": 252750,
            "codec_id": 7,
            "duration": 1442025,
            "size": 45559031,
            "md5": "",
            "url": "https://upos-bstar1-mirrorakam.akamaized.net/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-231210110000.m4s?e=ig8euxZM2rNcNbdlhoNvNC8BqJIzNbfqXBvEqxTEto8BTrNvN0GvT90W5JZMkX_YN0MvXg8gNEV4NC8xNEV4N03eN0B5tZlqNxTEto8BTrNvNeZVuJ10Kj_g2UB02J0mN0B5tZlqNCNEto8BTrNvNC7MTX502C8f2jmMQJ6mqF2fka1mqx6gqj0eN0B599M=&uipk=5&nbs=1&deadline=1663925440&gen=playurlv2&os=akam&oi=1542672794&trid=382ccff382fc456db1864fc1d53cfdd2i&mid=0&platform=pc&upsig=4b19ae777dfc9bb031bb7e68eb0c735f&uparams=e,uipk,nbs,deadline,gen,os,oi,trid,mid,platform&hdnts=exp=1663925440~hmac=69ccc59787735a5ada4b1b48ca2df399a4b7a293aba491dd927226031d88aac1&bvc=vod&nettype=0&orderid=0,1&logo=00000000",
            "backup_url": null,
            "container": 1,
            "start_with_sap": 1,
            "codecs": "avc1.64001E",
            "sar": "640:639",
            "frame_rate": "16000/672",
            "segment_base": {
              "range": "0-998",
              "index_range": "999-4486"
            },
            "width": 852,
            "height": 480,
            "mime_type": "video/mp4"
          },
          "stream_info": {
            "quality": 32,
            "desc_text": "",
            "desc_words": "480P",
            "intact": true,
            "no_rexcode": false
          },
          "audio_quality": 30216
        },
        {
          "video_resource": {
            "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-211210110000.m4s",
            "quality": 16,
            "bandwidth": 170577,
            "codec_id": 7,
            "duration": 1442025,
            "size": 30747065,
            "md5": "",
            "url": "https://upos-bstar1-mirrorakam.akamaized.net/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-211210110000.m4s?e=ig8euxZM2rNcNbdlhoNvNC8BqJIzNbfqXBvEqxTEto8BTrNvN0GvT90W5JZMkX_YN0MvXg8gNEV4NC8xNEV4N03eN0B5tZlqNxTEto8BTrNvNeZVuJ10Kj_g2UB02J0mN0B5tZlqNCNEto8BTrNvNC7MTX502C8f2jmMQJ6mqF2fka1mqx6gqj0eN0B599M=&uipk=5&nbs=1&deadline=1663925440&gen=playurlv2&os=akam&oi=1542672794&trid=382ccff382fc456db1864fc1d53cfdd2i&mid=0&platform=pc&upsig=b47aac21a37443bf7b592cbb9829fec5&uparams=e,uipk,nbs,deadline,gen,os,oi,trid,mid,platform&hdnts=exp=1663925440~hmac=1279ab1c618e3e1ec020d495dee6e45cd526b7eda7fa2bb45669bcb9f78f6169&bvc=vod&nettype=0&orderid=0,1&logo=00000000",
            "backup_url": null,
            "container": 1,
            "start_with_sap": 1,
            "codecs": "avc1.64001E",
            "sar": "1:1",
            "frame_rate": "16000/672",
            "segment_base": {
              "range": "0-1002",
              "index_range": "1003-4490"
            },
            "width": 640,
            "height": 360,
            "mime_type": "video/mp4"
          },
          "stream_info": {
            "quality": 16,
            "desc_text": "",
            "desc_words": "360P",
            "intact": true,
            "no_rexcode": false
          },
          "audio_quality": 30216
        },
        {
          "video_resource": {
            "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-2e1210110000.m4s",
            "quality": 6,
            "bandwidth": 96842,
            "codec_id": 7,
            "duration": 1442025,
            "size": 17456204,
            "md5": "",
            "url": "https://upos-bstar1-mirrorakam.akamaized.net/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-2e1210110000.m4s?e=ig8euxZM2rNcNbdlhoNvNC8BqJIzNbfqXBvEqxTEto8BTrNvN0GvT90W5JZMkX_YN0MvXg8gNEV4NC8xNEV4N03eN0B5tZlqNxTEto8BTrNvNeZVuJ10Kj_g2UB02J0mN0B5tZlqNCNEto8BTrNvNC7MTX502C8f2jmMQJ6mqF2fka1mqx6gqj0eN0B599M=&uipk=5&nbs=1&deadline=1663925440&gen=playurlv2&os=akam&oi=1542672794&trid=382ccff382fc456db1864fc1d53cfdd2i&mid=0&platform=pc&upsig=473dcb009c80ef239c16136f29b3678d&uparams=e,uipk,nbs,deadline,gen,os,oi,trid,mid,platform&hdnts=exp=1663925440~hmac=418238cafcabd9e85446ca47b67512dd92e42e53cd3d7f75d0b849223f7917e7&bvc=vod&nettype=0&orderid=0,1&logo=00000000",
            "backup_url": null,
            "container": 1,
            "start_with_sap": 1,
            "codecs": "avc1.64001E",
            "sar": "640:639",
            "frame_rate": "16000/672",
            "segment_base": {
              "range": "0-996",
              "index_range": "997-4484"
            },
            "width": 426,
            "height": 240,
            "mime_type": "video/mp4"
          },
          "stream_info": {
            "quality": 6,
            "desc_text": "",
            "desc_words": "240P",
            "intact": true,
            "no_rexcode": false
          },
          "audio_quality": 30216
        },
        {
          "video_resource": {
            "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-2f1210110000.m4s",
            "quality": 5,
            "bandwidth": 48879,
            "codec_id": 7,
            "duration": 1442025,
            "size": 8810716,
            "md5": "",
            "url": "https://upos-bstar1-mirrorakam.akamaized.net/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-2f1210110000.m4s?e=ig8euxZM2rNcNbdlhoNvNC8BqJIzNbfqXBvEqxTEto8BTrNvN0GvT90W5JZMkX_YN0MvXg8gNEV4NC8xNEV4N03eN0B5tZlqNxTEto8BTrNvNeZVuJ10Kj_g2UB02J0mN0B5tZlqNCNEto8BTrNvNC7MTX502C8f2jmMQJ6mqF2fka1mqx6gqj0eN0B599M=&uipk=5&nbs=1&deadline=1663925440&gen=playurlv2&os=akam&oi=1542672794&trid=382ccff382fc456db1864fc1d53cfdd2i&mid=0&platform=pc&upsig=84ffd141f73b15f2e6a0d22859e5e2b4&uparams=e,uipk,nbs,deadline,gen,os,oi,trid,mid,platform&hdnts=exp=1663925440~hmac=6d62e51f84a6af79c1c0afa6e15a896c82610f8085d3a3681ad7c5b44f3fb28e&bvc=vod&nettype=0&orderid=0,1&logo=00000000",
            "backup_url": null,
            "container": 1,
            "start_with_sap": 1,
            "codecs": "avc1.64001E",
            "sar": "1:1",
            "frame_rate": "16000/672",
            "segment_base": {
              "range": "0-991",
              "index_range": "992-4479"
            },
            "width": 256,
            "height": 144,
            "mime_type": "video/mp4"
          },
          "stream_info": {
            "quality": 5,
            "desc_text": "",
            "desc_words": "144P",
            "intact": true,
            "no_rexcode": false
          },
          "audio_quality": 30216
        }
      ],
      "audio_resource": [
        {
          "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-2d1301000023.m4s",
          "quality": 30280,
          "bandwidth": 329399,
          "codec_id": 0,
          "duration": 1442069,
          "size": 59377050,
          "md5": "",
          "url": "https://upos-bstar1-mirrorakam.akamaized.net/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-2d1301000023.m4s?e=ig8euxZM2rNcNbdlhoNvNC8BqJIzNbfqXBvEqxTEto8BTrNvN0GvT90W5JZMkX_YN0MvXg8gNEV4NC8xNEV4N03eN0B5tZlqNxTEto8BTrNvNeZVuJ10Kj_g2UB02J0mN0B5tZlqNCNEto8BTrNvNC7MTX502C8f2jmMQJ6mqF2fka1mqx6gqj0eN0B599M=&uipk=5&nbs=1&deadline=1663925440&gen=playurlv2&os=akam&oi=1542672794&trid=382ccff382fc456db1864fc1d53cfdd2i&mid=0&platform=pc&upsig=edc03c53e000dba765f5394cc9ab1417&uparams=e,uipk,nbs,deadline,gen,os,oi,trid,mid,platform&hdnts=exp=1663925440~hmac=ab81b34743544ae41eb3a3aae71ce788af9b7dbb2b4ccbda51d4da0fb19f831b&bvc=vod&nettype=0&orderid=0,1&logo=00000000",
          "backup_url": null,
          "container": 1,
          "start_with_sap": 1,
          "codecs": "mp4a.40.2",
          "sar": "",
          "frame_rate": "",
          "segment_base": {
            "range": "0-933",
            "index_range": "934-4433"
          },
          "width": 0,
          "height": 0,
          "mime_type": "audio/mp4"
        },
        {
          "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-2c1301000023.m4s",
          "quality": 30232,
          "bandwidth": 132791,
          "codec_id": 0,
          "duration": 1442069,
          "size": 23936754,
          "md5": "",
          "url": "https://upos-bstar1-mirrorakam.akamaized.net/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-2c1301000023.m4s?e=ig8euxZM2rNcNbdlhoNvNC8BqJIzNbfqXBvEqxTEto8BTrNvN0GvT90W5JZMkX_YN0MvXg8gNEV4NC8xNEV4N03eN0B5tZlqNxTEto8BTrNvNeZVuJ10Kj_g2UB02J0mN0B5tZlqNCNEto8BTrNvNC7MTX502C8f2jmMQJ6mqF2fka1mqx6gqj0eN0B599M=&uipk=5&nbs=1&deadline=1663925440&gen=playurlv2&os=akam&oi=1542672794&trid=382ccff382fc456db1864fc1d53cfdd2i&mid=0&platform=pc&upsig=c312ea3d683376d386abc04a3ec162a9&uparams=e,uipk,nbs,deadline,gen,os,oi,trid,mid,platform&hdnts=exp=1663925440~hmac=f816b39e273f23a2181ef1f440a1e4eb495f181a689418ba934ccc194cc7e393&bvc=vod&nettype=0&orderid=0,1&logo=00000000",
          "backup_url": null,
          "container": 1,
          "start_with_sap": 1,
          "codecs": "mp4a.40.2",
          "sar": "",
          "frame_rate": "",
          "segment_base": {
            "range": "0-933",
            "index_range": "934-4433"
          },
          "width": 0,
          "height": 0,
          "mime_type": "audio/mp4"
        },
        {
          "id": "/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-2a1301000023.m4s",
          "quality": 30216,
          "bandwidth": 67255,
          "codec_id": 0,
          "duration": 1442069,
          "size": 12123330,
          "md5": "",
          "url": "https://upos-bstar1-mirrorakam.akamaized.net/iupxcodeboss/5a/uo/n220805ercb0mtikr49z438gcow3uo5a-1-2a1301000023.m4s?e=ig8euxZM2rNcNbdlhoNvNC8BqJIzNbfqXBvEqxTEto8BTrNvN0GvT90W5JZMkX_YN0MvXg8gNEV4NC8xNEV4N03eN0B5tZlqNxTEto8BTrNvNeZVuJ10Kj_g2UB02J0mN0B5tZlqNCNEto8BTrNvNC7MTX502C8f2jmMQJ6mqF2fka1mqx6gqj0eN0B599M=&uipk=5&nbs=1&deadline=1663925440&gen=playurlv2&os=akam&oi=1542672794&trid=382ccff382fc456db1864fc1d53cfdd2i&mid=0&platform=pc&upsig=8e2437a0cbdd3d2b4a81e1a549079f62&uparams=e,uipk,nbs,deadline,gen,os,oi,trid,mid,platform&hdnts=exp=1663925440~hmac=fcb5320110220b895a8236505c5e42c7b4368a28d2aef3e22a33ac74dcf6b9ed&bvc=vod&nettype=0&orderid=0,1&logo=00000000",
          "backup_url": null,
          "container": 1,
          "start_with_sap": 1,
          "codecs": "mp4a.40.2",
          "sar": "",
          "frame_rate": "",
          "segment_base": {
            "range": "0-941",
            "index_range": "942-4441"
          },
          "width": 0,
          "height": 0,
          "mime_type": "audio/mp4"
        }
      ]
    }
  }
}
```
</details>