# 业务编号

custom.create

# api请求地址

[http://api.bonree.com/custom/create](http://api.bonree.com/custom/create)

# 请求方式

POST/GET

# 请求参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | myusername | 令牌 |
| params | string | 是 | {"pwd":"abcdabcd"} | params中包含所有其他参数 |
| token | string | 是 | systoken | 系统校验token |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 响应码说明 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求实例

curl

# 返回结果实例

```js
{
    "error_code":0,
    "reason":"创建成功",
    "result":{
        "usertoken":"usertoken"
    }
}
```

# FAQ



