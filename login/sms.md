# 获取国际电话区号列表

> https://api.bilibili.tv/intl/videoup/mobile/area-code

请求方式：`GET`

是否需要登录：`否`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注    |
|---------|-----|------|-------|
| code    | num | 响应码  | 0: 成功 |
| message | str | 0    |       |
| ttl     | num | 1    |       |
| data    | obj | 信息本体 |       |

### `data`对象

| 字段名        | 类型    | 内容                     | 备注  |
|------------|-------|------------------------|-----|
| current_id | num   | 当前用户所在国家&地区的country_id |     |
| common     | array | 信息列表                   |     |

#### `data`对象 -> `common`对象

| 字段名        | 类型  | 内容      | 备注  |
|------------|-----|---------|-----|
| id         | num | 记录id    |     |
| name       | str | 国家&地区名称 |     |
| country_id | num | 国家&地区号  |     |
| short_name | str | 国家&地区简称 |     |

## 请求示例

```shell
curl -L -X GET 'https://api.bilibili.tv/intl/videoup/mobile/area-code?s_locale=zh_ZH&platform=web'
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
        "current_id": 65,
        "common": [
            {
                "id": 22,
                "name": "阿富汗",
                "country_id": 93,
                "short_name": "AF"
            },
            {
                "id": 20,
                "name": "阿尔巴尼亚",
                "country_id": 355,
                "short_name": "AL"
            },
            {
                "id": 21,
                "name": "阿尔及利亚",
                "country_id": 213,
                "short_name": "DZ"
            },
            {
                "id": 31,
                "name": "安道尔",
                "country_id": 376,
                "short_name": "AD"
            },
            {
                "id": 32,
                "name": "安哥拉",
                "country_id": 244,
                "short_name": "AO"
            },
            {
                "id": 33,
                "name": "安提瓜岛和巴布达",
                "country_id": 1268,
                "short_name": "AG"
            },
            {
                "id": 23,
                "name": "阿根廷",
                "country_id": 54,
                "short_name": "AR"
            },
            {
                "id": 204,
                "name": "亚美尼亚",
                "country_id": 374,
                "short_name": "AM"
            },
            {
                "id": 183,
                "name": "阿森松岛",
                "country_id": 247,
                "short_name": "SH-AC"
            },
            {
                "id": 7,
                "name": "澳大利亚",
                "country_id": 61,
                "short_name": "AU"
            },
            {
                "id": 34,
                "name": "奥地利",
                "country_id": 43,
                "short_name": "AT"
            },
            {
                "id": 26,
                "name": "阿塞拜疆",
                "country_id": 994,
                "short_name": "AZ"
            },
            {
                "id": 37,
                "name": "巴哈马群岛",
                "country_id": 1242,
                "short_name": "BS"
            },
            {
                "id": 40,
                "name": "巴林",
                "country_id": 973,
                "short_name": "BH"
            },
            {
                "id": 131,
                "name": "孟加拉国",
                "country_id": 880,
                "short_name": "BD"
            },
            {
                "id": 35,
                "name": "巴巴多斯",
                "country_id": 1246,
                "short_name": "BB"
            },
            {
                "id": 43,
                "name": "白俄罗斯",
                "country_id": 375,
                "short_name": "BY"
            },
            {
                "id": 6,
                "name": "比利时",
                "country_id": 32,
                "short_name": "BE"
            },
            {
                "id": 52,
                "name": "伯利兹",
                "country_id": 501,
                "short_name": "BZ"
            },
            {
                "id": 46,
                "name": "贝宁",
                "country_id": 229,
                "short_name": "BJ"
            },
            {
                "id": 44,
                "name": "百慕大群岛",
                "country_id": 1441,
                "short_name": "BM"
            },
            {
                "id": 54,
                "name": "不丹",
                "country_id": 975,
                "short_name": "BT"
            },
            {
                "id": 51,
                "name": "玻利维亚",
                "country_id": 591,
                "short_name": "BO"
            },
            {
                "id": 49,
                "name": "波黑",
                "country_id": 387,
                "short_name": "BA"
            },
            {
                "id": 53,
                "name": "博茨瓦纳",
                "country_id": 267,
                "short_name": "BW"
            },
            {
                "id": 42,
                "name": "巴西",
                "country_id": 55,
                "short_name": "BR"
            },
            {
                "id": 193,
                "name": "文莱",
                "country_id": 673,
                "short_name": "BN"
            },
            {
                "id": 45,
                "name": "保加利亚",
                "country_id": 359,
                "short_name": "BG"
            },
            {
                "id": 55,
                "name": "布基纳法索",
                "country_id": 226,
                "short_name": "BF"
            },
            {
                "id": 56,
                "name": "布隆迪",
                "country_id": 257,
                "short_name": "BI"
            },
            {
                "id": 96,
                "name": "柬埔寨",
                "country_id": 855,
                "short_name": "KH"
            },
            {
                "id": 100,
                "name": "喀麦隆",
                "country_id": 237,
                "short_name": "CM"
            },
            {
                "id": 9,
                "name": "加拿大",
                "country_id": 1,
                "short_name": "CA"
            },
            {
                "id": 72,
                "name": "佛得角",
                "country_id": 238,
                "short_name": "CV"
            },
            {
                "id": 102,
                "name": "开曼群岛",
                "country_id": 1345,
                "short_name": "KY"
            },
            {
                "id": 68,
                "name": "非洲中部",
                "country_id": 236,
                "short_name": "CF"
            },
            {
                "id": 214,
                "name": "乍得",
                "country_id": 235,
                "short_name": "TD"
            },
            {
                "id": 216,
                "name": "智利",
                "country_id": 56,
                "short_name": "CL"
            },
            {
                "id": 1,
                "name": "中国大陆",
                "country_id": 86,
                "short_name": "CN"
            },
            {
                "id": 77,
                "name": "哥伦比亚",
                "country_id": 57,
                "short_name": "CO"
            },
            {
                "id": 103,
                "name": "科摩罗",
                "country_id": 269,
                "short_name": "KM"
            },
            {
                "id": 75,
                "name": "刚果",
                "country_id": 242,
                "short_name": "CG"
            },
            {
                "id": 76,
                "name": "刚果(金)",
                "country_id": 243,
                "short_name": "CD"
            },
            {
                "id": 107,
                "name": "库克岛",
                "country_id": 682,
                "short_name": "CK"
            },
            {
                "id": 78,
                "name": "哥斯达黎加",
                "country_id": 506,
                "short_name": "CR"
            },
            {
                "id": 105,
                "name": "克罗地亚",
                "country_id": 385,
                "short_name": "HR"
            },
            {
                "id": 81,
                "name": "古巴",
                "country_id": 53,
                "short_name": "CU"
            },
            {
                "id": 162,
                "name": "塞浦路斯",
                "country_id": 357,
                "short_name": "CY"
            },
            {
                "id": 97,
                "name": "捷克",
                "country_id": 420,
                "short_name": "CZ"
            },
            {
                "id": 200,
                "name": "科特迪瓦",
                "country_id": 225,
                "short_name": "CI"
            },
            {
                "id": 58,
                "name": "丹麦",
                "country_id": 45,
                "short_name": "DK"
            },
            {
                "id": 59,
                "name": "迪戈加西亚岛",
                "country_id": 246
            },
            {
                "id": 90,
                "name": "吉布提",
                "country_id": 253,
                "short_name": "DJ"
            },
            {
                "id": 61,
                "name": "多米尼克",
                "country_id": 1767,
                "short_name": "DM"
            },
            {
                "id": 63,
                "name": "厄瓜多尔",
                "country_id": 593,
                "short_name": "EC"
            },
            {
                "id": 27,
                "name": "埃及",
                "country_id": 20,
                "short_name": "EG"
            },
            {
                "id": 157,
                "name": "萨尔瓦多",
                "country_id": 503,
                "short_name": "SV"
            },
            {
                "id": 57,
                "name": "赤道几内亚",
                "country_id": 240,
                "short_name": "GQ"
            },
            {
                "id": 64,
                "name": "厄立特里亚",
                "country_id": 291,
                "short_name": "ER"
            },
            {
                "id": 30,
                "name": "爱沙尼亚",
                "country_id": 372,
                "short_name": "EE"
            },
            {
                "id": 28,
                "name": "埃塞俄比亚",
                "country_id": 251,
                "short_name": "ET"
            },
            {
                "id": 73,
                "name": "福克兰岛",
                "country_id": 500,
                "short_name": "FK"
            },
            {
                "id": 65,
                "name": "法罗岛",
                "country_id": 298,
                "short_name": "FO"
            },
            {
                "id": 70,
                "name": "斐济",
                "country_id": 679,
                "short_name": "FJ"
            },
            {
                "id": 71,
                "name": "芬兰",
                "country_id": 358,
                "short_name": "FI"
            },
            {
                "id": 8,
                "name": "法国",
                "country_id": 33,
                "short_name": "FR"
            },
            {
                "id": 67,
                "name": "法属圭亚那",
                "country_id": 594,
                "short_name": "GF"
            },
            {
                "id": 66,
                "name": "法属波利尼西亚",
                "country_id": 689,
                "short_name": "PF"
            },
            {
                "id": 95,
                "name": "加蓬",
                "country_id": 241,
                "short_name": "GA"
            },
            {
                "id": 74,
                "name": "冈比亚",
                "country_id": 220,
                "short_name": "GM"
            },
            {
                "id": 154,
                "name": "格鲁吉亚",
                "country_id": 995,
                "short_name": "GE"
            },
            {
                "id": 16,
                "name": "德国",
                "country_id": 49,
                "short_name": "DE"
            },
            {
                "id": 94,
                "name": "加纳",
                "country_id": 233,
                "short_name": "GH"
            },
            {
                "id": 215,
                "name": "直布罗陀",
                "country_id": 350,
                "short_name": "GI"
            },
            {
                "id": 199,
                "name": "希腊",
                "country_id": 30,
                "short_name": "GR"
            },
            {
                "id": 80,
                "name": "格陵兰岛",
                "country_id": 299,
                "short_name": "GL"
            },
            {
                "id": 79,
                "name": "格林纳达",
                "country_id": 1473,
                "short_name": "GD"
            },
            {
                "id": 82,
                "name": "瓜德罗普岛",
                "country_id": 590,
                "short_name": "MF"
            },
            {
                "id": 83,
                "name": "关岛",
                "country_id": 1671,
                "short_name": "GU"
            },
            {
                "id": 92,
                "name": "几内亚",
                "country_id": 224,
                "short_name": "GN"
            },
            {
                "id": 93,
                "name": "几内亚比绍",
                "country_id": 245,
                "short_name": "GW"
            },
            {
                "id": 84,
                "name": "海地",
                "country_id": 509,
                "short_name": "HT"
            },
            {
                "id": 87,
                "name": "洪都拉斯",
                "country_id": 504,
                "short_name": "HN"
            },
            {
                "id": 5,
                "name": "香港地区",
                "country_id": 852,
                "short_name": "HK"
            },
            {
                "id": 201,
                "name": "匈牙利",
                "country_id": 36,
                "short_name": "HU"
            },
            {
                "id": 47,
                "name": "冰岛",
                "country_id": 354,
                "short_name": "IS"
            },
            {
                "id": 209,
                "name": "印度",
                "country_id": 91,
                "short_name": "IN"
            },
            {
                "id": 210,
                "name": "印尼",
                "country_id": 62,
                "short_name": "ID"
            },
            {
                "id": 207,
                "name": "伊朗",
                "country_id": 98,
                "short_name": "IR"
            },
            {
                "id": 206,
                "name": "伊拉克",
                "country_id": 964,
                "short_name": "IQ"
            },
            {
                "id": 29,
                "name": "爱尔兰",
                "country_id": 353,
                "short_name": "IE"
            },
            {
                "id": 208,
                "name": "以色列",
                "country_id": 972,
                "short_name": "IL"
            },
            {
                "id": 15,
                "name": "意大利",
                "country_id": 39,
                "short_name": "IT"
            },
            {
                "id": 203,
                "name": "牙买加",
                "country_id": 1876,
                "short_name": "JM"
            },
            {
                "id": 10,
                "name": "日本",
                "country_id": 81,
                "short_name": "JP"
            },
            {
                "id": 211,
                "name": "约旦",
                "country_id": 962,
                "short_name": "JO"
            },
            {
                "id": 106,
                "name": "肯尼亚",
                "country_id": 254,
                "short_name": "KE"
            },
            {
                "id": 89,
                "name": "基里巴斯",
                "country_id": 686,
                "short_name": "KI"
            },
            {
                "id": 12,
                "name": "韩国",
                "country_id": 82,
                "short_name": "KR"
            },
            {
                "id": 104,
                "name": "科威特",
                "country_id": 965,
                "short_name": "KW"
            },
            {
                "id": 91,
                "name": "吉尔吉斯斯坦",
                "country_id": 996,
                "short_name": "KG"
            },
            {
                "id": 110,
                "name": "老挝",
                "country_id": 856,
                "short_name": "LA"
            },
            {
                "id": 108,
                "name": "拉脱维亚",
                "country_id": 371,
                "short_name": "LV"
            },
            {
                "id": 111,
                "name": "黎巴嫩",
                "country_id": 961,
                "short_name": "LB"
            },
            {
                "id": 109,
                "name": "莱索托",
                "country_id": 266,
                "short_name": "LS"
            },
            {
                "id": 113,
                "name": "利比里亚",
                "country_id": 231,
                "short_name": "LR"
            },
            {
                "id": 114,
                "name": "利比亚",
                "country_id": 218,
                "short_name": "LY"
            },
            {
                "id": 112,
                "name": "立陶宛",
                "country_id": 370,
                "short_name": "LT"
            },
            {
                "id": 115,
                "name": "卢森堡",
                "country_id": 352,
                "short_name": "LU"
            },
            {
                "id": 2,
                "name": "澳门地区",
                "country_id": 853,
                "short_name": "MO"
            },
            {
                "id": 124,
                "name": "马其顿",
                "country_id": 389,
                "short_name": "MK"
            },
            {
                "id": 118,
                "name": "马达加斯加",
                "country_id": 261,
                "short_name": "MG"
            },
            {
                "id": 121,
                "name": "马拉维",
                "country_id": 265,
                "short_name": "MW"
            },
            {
                "id": 13,
                "name": "马来西亚",
                "country_id": 60,
                "short_name": "MY"
            },
            {
                "id": 119,
                "name": "马尔代夫",
                "country_id": 960,
                "short_name": "MV"
            },
            {
                "id": 122,
                "name": "马里",
                "country_id": 223,
                "short_name": "ML"
            },
            {
                "id": 120,
                "name": "马耳他",
                "country_id": 356,
                "short_name": "MT"
            },
            {
                "id": 123,
                "name": "马里亚纳岛",
                "country_id": 1670,
                "short_name": "MP"
            },
            {
                "id": 126,
                "name": "马歇尔岛",
                "country_id": 692,
                "short_name": "MH"
            },
            {
                "id": 125,
                "name": "马提尼克岛",
                "country_id": 596,
                "short_name": "MQ"
            },
            {
                "id": 128,
                "name": "毛里塔尼亚",
                "country_id": 222,
                "short_name": "MR"
            },
            {
                "id": 127,
                "name": "毛里求斯",
                "country_id": 230,
                "short_name": "MU"
            },
            {
                "id": 139,
                "name": "墨西哥",
                "country_id": 52,
                "short_name": "MX"
            },
            {
                "id": 133,
                "name": "密克罗尼西亚",
                "country_id": 691,
                "short_name": "FM"
            },
            {
                "id": 135,
                "name": "摩尔多瓦",
                "country_id": 373,
                "short_name": "MD"
            },
            {
                "id": 137,
                "name": "摩纳哥",
                "country_id": 377,
                "short_name": "MC"
            },
            {
                "id": 129,
                "name": "蒙古",
                "country_id": 976,
                "short_name": "MN"
            },
            {
                "id": 130,
                "name": "蒙特塞拉特岛",
                "country_id": 1664,
                "short_name": "MS"
            },
            {
                "id": 136,
                "name": "摩洛哥",
                "country_id": 212,
                "short_name": "EH"
            },
            {
                "id": 138,
                "name": "莫桑比克",
                "country_id": 258,
                "short_name": "MZ"
            },
            {
                "id": 134,
                "name": "缅甸",
                "country_id": 95,
                "short_name": "MM"
            },
            {
                "id": 140,
                "name": "纳米比亚",
                "country_id": 264,
                "short_name": "NA"
            },
            {
                "id": 143,
                "name": "瑙鲁",
                "country_id": 674,
                "short_name": "NR"
            },
            {
                "id": 144,
                "name": "尼泊尔",
                "country_id": 977,
                "short_name": "NP"
            },
            {
                "id": 86,
                "name": "荷兰",
                "country_id": 31,
                "short_name": "NL"
            },
            {
                "id": 19,
                "name": "新西兰",
                "country_id": 64,
                "short_name": "NZ"
            },
            {
                "id": 145,
                "name": "尼加拉瓜",
                "country_id": 505,
                "short_name": "NI"
            },
            {
                "id": 146,
                "name": "尼日尔",
                "country_id": 227,
                "short_name": "NE"
            },
            {
                "id": 147,
                "name": "尼日利亚",
                "country_id": 234,
                "short_name": "NG"
            },
            {
                "id": 148,
                "name": "纽埃岛",
                "country_id": 683,
                "short_name": "NU"
            },
            {
                "id": 150,
                "name": "诺福克岛",
                "country_id": 672,
                "short_name": "AQ"
            },
            {
                "id": 149,
                "name": "挪威",
                "country_id": 47,
                "short_name": "SJ"
            },
            {
                "id": 25,
                "name": "阿曼",
                "country_id": 968,
                "short_name": "OM"
            },
            {
                "id": 38,
                "name": "巴基斯坦",
                "country_id": 92,
                "short_name": "PK"
            },
            {
                "id": 151,
                "name": "帕劳",
                "country_id": 680,
                "short_name": "PW"
            },
            {
                "id": 41,
                "name": "巴拿马",
                "country_id": 507,
                "short_name": "PA"
            },
            {
                "id": 36,
                "name": "巴布亚新几内亚",
                "country_id": 675,
                "short_name": "PG"
            },
            {
                "id": 39,
                "name": "巴拉圭",
                "country_id": 595,
                "short_name": "PY"
            },
            {
                "id": 99,
                "name": "聚会岛",
                "country_id": 262,
                "short_name": "RE"
            },
            {
                "id": 132,
                "name": "秘鲁",
                "country_id": 51,
                "short_name": "PE"
            },
            {
                "id": 69,
                "name": "菲律宾",
                "country_id": 63,
                "short_name": "PH"
            },
            {
                "id": 50,
                "name": "波兰",
                "country_id": 48,
                "short_name": "PL"
            },
            {
                "id": 152,
                "name": "葡萄牙",
                "country_id": 351,
                "short_name": "PT"
            },
            {
                "id": 48,
                "name": "波多黎各",
                "country_id": 1787,
                "short_name": "PR"
            },
            {
                "id": 101,
                "name": "卡塔尔",
                "country_id": 974,
                "short_name": "QA"
            },
            {
                "id": 163,
                "name": "塞舌尔共和国",
                "country_id": 248,
                "short_name": "SC"
            },
            {
                "id": 117,
                "name": "罗马尼亚",
                "country_id": 40,
                "short_name": "RO"
            },
            {
                "id": 18,
                "name": "俄罗斯",
                "country_id": 7,
                "short_name": "RU"
            },
            {
                "id": 116,
                "name": "卢旺达",
                "country_id": 250,
                "short_name": "RW"
            },
            {
                "id": 167,
                "name": "圣卢西亚",
                "country_id": 1784,
                "short_name": "LC"
            },
            {
                "id": 169,
                "name": "圣皮埃尔和密克隆群岛",
                "country_id": 508,
                "short_name": "PM"
            },
            {
                "id": 159,
                "name": "萨摩亚，东部",
                "country_id": 684,
                "short_name": "AS"
            },
            {
                "id": 158,
                "name": "萨摩亚，西部",
                "country_id": 685,
                "short_name": "WS"
            },
            {
                "id": 168,
                "name": "圣马力诺",
                "country_id": 378,
                "short_name": "SM"
            },
            {
                "id": 166,
                "name": "圣多美和普林西比",
                "country_id": 239,
                "short_name": "ST"
            },
            {
                "id": 165,
                "name": "沙特阿拉伯",
                "country_id": 966,
                "short_name": "SA"
            },
            {
                "id": 161,
                "name": "塞内加尔",
                "country_id": 221,
                "short_name": "SN"
            },
            {
                "id": 160,
                "name": "塞拉利昂",
                "country_id": 232,
                "short_name": "SL"
            },
            {
                "id": 11,
                "name": "新加坡",
                "country_id": 65,
                "short_name": "SG"
            },
            {
                "id": 171,
                "name": "斯洛伐克",
                "country_id": 421,
                "short_name": "SK"
            },
            {
                "id": 172,
                "name": "斯洛文尼亚",
                "country_id": 386,
                "short_name": "SI"
            },
            {
                "id": 176,
                "name": "所罗门群岛",
                "country_id": 677,
                "short_name": "SB"
            },
            {
                "id": 177,
                "name": "索马里",
                "country_id": 252,
                "short_name": "SO"
            },
            {
                "id": 141,
                "name": "南非",
                "country_id": 27,
                "short_name": "ZA"
            },
            {
                "id": 198,
                "name": "西班牙",
                "country_id": 34,
                "short_name": "ES"
            },
            {
                "id": 170,
                "name": "斯里兰卡",
                "country_id": 94,
                "short_name": "LK"
            },
            {
                "id": 174,
                "name": "苏丹",
                "country_id": 249,
                "short_name": "SD"
            },
            {
                "id": 175,
                "name": "苏里南",
                "country_id": 597,
                "short_name": "SR"
            },
            {
                "id": 173,
                "name": "斯威士兰",
                "country_id": 268,
                "short_name": "SZ"
            },
            {
                "id": 155,
                "name": "瑞典",
                "country_id": 46,
                "short_name": "SE"
            },
            {
                "id": 156,
                "name": "瑞士",
                "country_id": 41,
                "short_name": "CH"
            },
            {
                "id": 202,
                "name": "叙利亚",
                "country_id": 963,
                "short_name": "SY"
            },
            {
                "id": 3,
                "name": "台湾地区",
                "country_id": 886,
                "short_name": "TW"
            },
            {
                "id": 179,
                "name": "坦桑尼亚",
                "country_id": 255,
                "short_name": "TZ"
            },
            {
                "id": 178,
                "name": "泰国",
                "country_id": 66,
                "short_name": "TH"
            },
            {
                "id": 62,
                "name": "多米尼加共和国",
                "country_id": 1809,
                "short_name": "DO"
            },
            {
                "id": 60,
                "name": "多哥",
                "country_id": 228,
                "short_name": "TG"
            },
            {
                "id": 188,
                "name": "托克劳岛",
                "country_id": 690,
                "short_name": "TK"
            },
            {
                "id": 180,
                "name": "汤加",
                "country_id": 676,
                "short_name": "TO"
            },
            {
                "id": 182,
                "name": "特立尼达和多巴哥",
                "country_id": 1868,
                "short_name": "TT"
            },
            {
                "id": 184,
                "name": "突尼斯",
                "country_id": 216,
                "short_name": "TN"
            },
            {
                "id": 186,
                "name": "土耳其",
                "country_id": 90,
                "short_name": "TR"
            },
            {
                "id": 187,
                "name": "土库曼斯坦",
                "country_id": 993,
                "short_name": "TM"
            },
            {
                "id": 181,
                "name": "特克斯和凯科斯",
                "country_id": 1649,
                "short_name": "TC"
            },
            {
                "id": 185,
                "name": "图瓦卢",
                "country_id": 688,
                "short_name": "TV"
            },
            {
                "id": 194,
                "name": "乌干达",
                "country_id": 256,
                "short_name": "UG"
            },
            {
                "id": 195,
                "name": "乌克兰",
                "country_id": 380,
                "short_name": "UA"
            },
            {
                "id": 24,
                "name": "阿联酋",
                "country_id": 971,
                "short_name": "AE"
            },
            {
                "id": 14,
                "name": "英国",
                "country_id": 44,
                "short_name": "GB"
            },
            {
                "id": 4,
                "name": "美国",
              "country_id": 1,
                "short_name": "US"
            },
            {
                "id": 196,
                "name": "乌拉圭",
                "country_id": 598,
                "short_name": "UY"
            },
            {
                "id": 197,
                "name": "乌兹别克斯坦",
                "country_id": 998,
                "short_name": "UZ"
            },
            {
                "id": 189,
                "name": "瓦努阿图",
                "country_id": 678,
                "short_name": "VU"
            },
            {
                "id": 192,
                "name": "委内瑞拉",
                "country_id": 58,
                "short_name": "VE"
            },
            {
                "id": 212,
                "name": "越南",
                "country_id": 84,
                "short_name": "VN"
            },
            {
                "id": 191,
                "name": "维珍群岛(英属)",
                "country_id": 1284,
                "short_name": "VG"
            },
            {
                "id": 190,
                "name": "维珍群岛(美属)",
                "country_id": 1340,
                "short_name": "VI"
            },
            {
                "id": 88,
                "name": "维克岛",
                "country_id": 1808
            },
            {
                "id": 153,
                "name": "瓦利斯群岛和富图纳群岛",
                "country_id": 1681,
                "short_name": "WF"
            },
            {
                "id": 205,
                "name": "也门",
                "country_id": 967,
                "short_name": "YE"
            },
            {
                "id": 142,
                "name": "南斯拉夫",
                "country_id": 381,
                "short_name": "RS"
            },
            {
                "id": 213,
                "name": "赞比亚",
                "country_id": 260,
                "short_name": "ZM"
            },
            {
                "id": 164,
                "name": "桑给巴尔岛",
                "country_id": 259
            },
            {
                "id": 98,
                "name": "津巴布韦",
                "country_id": 263,
                "short_name": "ZW"
            }
        ]
    }
}
```
</details>