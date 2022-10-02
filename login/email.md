# 获取公钥和盐值

> https://passport.bilibili.tv/x/intl/passport-login/web/key

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

| 字段名  | 类型  | 内容     | 备注  |
|------|-----|--------|-----|
| hash | str | 密码盐值   |     |
| key  | str | rsa 公钥 |     |

## 请求示例

**请求需要设置Host**

```shell
curl -L -X GET 'https://passport.bilibili.tv/x/intl/passport-login/web/key?s_locale=en_US&platform=web' \
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
        "hash": "e0f336d60d14ef12",
        "key": "-----BEGIN PUBLIC KEY-----\nMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDjb4V7EidX/ym28t2ybo0U6t0n\n6p4ej8VjqKHg100va6jkNbNTrLQqMCQCAYtXMXXp2Fwkk6WR+12N9zknLjf+C9sx\n/+l48mjUU8RqahiFD1XT/u2e0m2EN029OhCgkHx3Fc/KlFSIbak93EH/XlYis0w+\nXl69GV6klzgxW6d2xQIDAQAB\n-----END PUBLIC KEY-----\n"
    }
}
```
</details>

# 使用邮箱登录

> https://passport.bilibili.tv/x/intl/passport-login/web/login/password

请求方式：`POST`

是否需要登录：`否`

Content-Type：`application/x-www-form-urlencoded`

## URL参数

| 参数名      | 类型  | 必填  | 内容   | 备注                                |
|----------|-----|-----|------|-----------------------------------|
| s_locale | str |     | 语种代码 | 默认为英语<br/>[语言代码表](../language.md) |
| platform | str |     | 平台   |                                   |

## FORM参数

| 参数名      | 类型  | 必填  | 内容        | 备注  |
|----------|-----|-----|-----------|-----|
| username | str | √   | 用户名       |     |
| password | str | √   | 加密后的密码    |     |
| keep_me  | str |     | 是否勾选”记住我“ |     |

## Json回复

### 根对象

| 字段名     | 类型  | 内容   | 备注                                                        |
|---------|-----|------|-----------------------------------------------------------|
| code    | num | 响应码  | 0：成功<br/>-629：Incorrect account or password<br/>-662：-662 |
| message | str | 0    |                                                           |
| ttl     | num | 1    |                                                           |
| data    | obj | 信息本体 |                                                           |

### `data`对象

| 字段名          | 类型   | 内容   | 备注  |
|--------------|------|------|-----|
| mid          | num  | 用户id |     |
| is_new       | bool |      |     |
| go_url       | str  | `空串` |     |
| user_profile | obj  |      |     |

### `data`对象 -> `user_profile`对象

| 字段名                 | 类型   | 内容   | 备注  |
|---------------------|------|------|-----|
| is_userBlankProfile | bool |      |     |
| name                | str  | `空串` |     |
| face                | str  | `空串` |     |

## 请求示例

```shell
curl -L -X POST 'https://passport.bilibili.tv/x/intl/passport-login/web/login/password?s_locale=en_US&platform=web' \
-H 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'username=xxx' \
--data-urlencode 'password=xxx' \
--data-urlencode 'keep_me=true'
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
    "mid": 1294068111,
    "is_new": false,
    "go_url": "",
    "user_profile": {
      "is_userBlankProfile": false,
      "name": "",
      "face": ""
    }
  }
}
```
</details>

## 解析Cookie

**从响应返回的Header中获取`SESSDATA`、`bili_jct`和`DedeUserID`**

# 密码加密示例

## Java实现

```java
import cn.hutool.core.codec.Base64;

import javax.crypto.Cipher;
import java.security.KeyFactory;
import java.security.PublicKey;
import java.security.spec.X509EncodedKeySpec;

public class Test {
    public static void main(String[] args) throws Exception {
        //用户密码
        String password = "abcdef";
        //获取到的证书内容
        String key = "-----BEGIN PUBLIC KEY-----\nMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDjb4V7EidX/ym28t2ybo0U6t0n\n6p4ej8VjqKHg100va6jkNbNTrLQqMCQCAYtXMXXp2Fwkk6WR+12N9zknLjf+C9sx\n/+l48mjUU8RqahiFD1XT/u2e0m2EN029OhCgkHx3Fc/KlFSIbak93EH/XlYis0w+\nXl69GV6klzgxW6d2xQIDAQAB\n-----END PUBLIC KEY-----\n";
        //获取到的盐值
        String hash = "bb73382121594c46";
        String[] split = key.strip().split("\n");
        String newKey = split[1] + split[2] + split[3] + split[4];
        //进行加密
        KeyFactory keyFactory = KeyFactory.getInstance("RSA");
        X509EncodedKeySpec keySpec = new X509EncodedKeySpec(Base64.decode(newKey));
        PublicKey publicKey = keyFactory.generatePublic(keySpec);
        Cipher cipher = Cipher.getInstance(keyFactory.getAlgorithm());
        cipher.init(Cipher.PUBLIC_KEY, publicKey);
        byte[] bytes = cipher.doFinal((hash + password).getBytes());
        String encode = Base64.encode(bytes);
        System.out.println(encode);
    }
}
```