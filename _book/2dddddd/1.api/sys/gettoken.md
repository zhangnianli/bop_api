\# 业务编号

sys.getToken

# api请求地址

[[http://api.bonree.com/sys/g](http://api.bonree.com/custom/check)etToken](http://api.bonree.com/sys/getToken)

# 请求方式

POST/GET

# 请求参数

无

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 响应码说明 |
| reason | string | 返回说明 |
| result | string | 返回结果集，token数组\[\] |

# 请求实例

curl [[http://api.bonree.com/sys/g](#)etToken](#)

# 返回结果实例

```js
{
    "error_code":0,
    "reason":"成功",
    "result":[
        {"token":"abcd","bizId":1}, ...
    ]
}
```

# FAQ



