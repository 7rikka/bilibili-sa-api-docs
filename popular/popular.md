# 获取趋势热点视频列表

> https://www.bilibili.tv/en/popular

请求方式：`GET`

是否需要登录：`否`

获取到页面源码进行解析，获取其中的`window.__initialState`方法，执行之后获取对象，再转换为Json字符串即可。

## Json回复

### 根对象

| 字段名     | 类型  | 内容  | 备注  |
|---------|-----|-----|-----|
| global  | obj |     |     |
| common  | obj |     |     |    
| user    | obj |     |     |   
| ugc     | obj |     |     |  
| ogv     | obj |     |     |  
| popular | obj |     |     | 

### `global`对象

| 字段名         | 类型   | 内容      | 备注                      |
|-------------|------|---------|-------------------------|
| fallback    | bool | `false` |                         |
| sLocale     | str  | 当前语言代码  | [语言代码表](../language.md) |
| useBstation | bool | `false` |                         |
| largeScreen | bool | `false` |                         |
| uiMode      | num  | `0`     |                         |

### `common`对象

| 字段名          | 类型   | 内容      | 备注  |
|--------------|------|---------|-----|
| configs      | obj  |         |     |
| userInfo     | obj  | 当前用户信息  |     |
| isFetching   | bool | `false` |     |
| popupInfo    |      | `null`  |     |
| popupVisible | bool | `false` |     |

#### `common`对象 -> `configs`对象

| 字段名         | 类型   | 内容     | 备注  |
|-------------|------|--------|-----|
| can_buy_vip | bool | `true` |     |

#### `common`对象 -> `userInfo`对象

| 字段名      | 类型   | 内容     | 备注  |
|----------|------|--------|-----|
| is_login | bool | 当前是否登录 |     |
| mid      | str  | 用户id   |     |
| nickname | str  | 用户名    |     |
| avatar   | str  | 头像     |     |
| sign     | str  | 个人签名   |     |
| vip_info | obj  | 会员信息   |     |
| birth    | obj  | 生日信息   |     |

##### `common`对象 -> `userInfo`对象 -> `vip_info`对象

| 字段名      | 类型   | 内容         | 备注  |
|----------|------|------------|-----|
| is_vip   | bool | 当前用户是否开通会员 |     |
| due_date | str  | 会员过期时间     |     |

##### `common`对象 -> `userInfo`对象 -> `birth`对象

| 字段名   | 类型  | 内容   | 备注         |
|-------|-----|------|------------|
| date  | str | 生日日期 | yyyy-MM-dd |
| toast | str | `空串` |            |

### `user`对象

| 字段名           | 类型  | 内容    | 备注  |
|---------------|-----|-------|-----|
| updatedFollow | obj | `空对象` |     |
| profileParams | obj |       |     |

### `profileParams`对象

| 字段名      | 类型  | 内容   | 备注         |
|----------|-----|------|------------|
| face     | str | 头像   |            |
| name     | str | 用户名  |            |
| sign     | str | 个人签名 |            |
| birthday | str | 生日日期 | yyyy-MM-dd |

### `ugc`对象

| 字段名         | 类型  | 内容     | 备注  |
|-------------|-----|--------|-----|
| aid         | str | `空串`   |     |
| archive     |     | `null` |     |
| errorTagUgc | num | `0`    |     |

### `ogv`对象

| 字段名                | 类型    | 内容     | 备注  |
|--------------------|-------|--------|-----|
| epId               | str   | `空串`   |     |
| season             |       | `null` |     |
| series             | array | `空数组`  |     |
| errorTagOgv        | num   | `0`    |     |
| activeSectionTitle | str   | `空串`   |     |
| sectionsList       | array | `空数组`  |     |

### `popular`对象

| 字段名     | 类型    | 内容      | 备注  |
|---------|-------|---------|-----|
| total   | array | 信息本体    |     |
| list    | array | 信息本体    |     |
| loading | bool  | `false` |     |
| params  | obj   |         |     |
| hasMore | bool  | `true`  |     |

### `popular`对象 -> `total`数组中的对象

| 字段名          | 类型   | 内容          | 备注      |
|--------------|------|-------------|---------|
| type         | str  | `ugc`       |         |
| aid          | num  | av号         |         |
| card_type    | str  | `ugc_video` |         |
| title        | str  | 标题          |         |
| cover        | str  | 封面          |         |
| view         | str  | 观看量         |         |
| duration     | str  | 时长          |         |
| author       | obj  | 作者信息        |         |
| view_at      | str  | `空串`        |         |
| view_history |      | `null`      |         |
| live         | obj  | 直播间信息(?)    | 可能为null |
| unavailable  | bool | `false`     |         |

#### `popular`对象 -> `total`数组 -> `author`对象

| 字段名      | 类型  | 内容   | 备注  |
|----------|-----|------|-----|
| mid      | str | 用户id |     |
| avatar   | str | 头像   |     |
| nickname | str | 用户名  |     |

#### `popular`对象 -> `total`数组 -> `live`对象

| 字段名     | 类型  | 内容    | 备注  |
|---------|-----|-------|-----|
| room_id | num | 直播间id |     |
| state   | num | `0`   |     |

### `popular`对象 -> `list`数组中的对象

| 字段名      | 类型  | 内容    | 备注  |
|----------|-----|-------|-----|
| type     | str | `ugc` |     |
| id       | num | av号   |     |
| title    | str | 标题    |     |
| cover    | str | 封面    |     |
| url      | str | 播放页地址 |     |
| maskText | str | 时长    |     |
| user     | obj | 作者信息  |     |
| desc     | str | 观看量   |     |

### `popular`对象 -> `list`数组 -> `user`对象

| 字段名          | 类型   | 内容      | 备注  |
|--------------|------|---------|-----|
| avatar       | str  | 头像      |     |
| nickname     | str  | 用户名     |     |
| hideNickname | bool | `false` |     |
| link         | str  | 个人页面地址  |     |
| newWindow    | bool | `false` |     |
| pendant      | str  | `空串`    |     |

### `popular`对象 -> `params`对象

| 字段名 | 类型  | 内容   | 备注  |
|-----|-----|------|-----|
| pn  | num | `0`  |     |
| ps  | num | `50` |     |
