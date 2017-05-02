# 业务编号

custom.editpwd

# api请求地址

[http://api.bonree.com/custom/editpwd](http://api.bonree.com/custom/editpwd)

# 请求方式

POST/GET

# 请求参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | myusername | 令牌 |
| token | string | 是 | systomen | 系统校验token |
| params | string | 是 | params={"oldpwd":"aaa","newpwd":"mynewpwd"} | 其他参数放到params中，oldpwd、newpwd |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 响应码说明 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求实例

curl [http://api.bonree.com/custom/editpwd](#)?username=upduser&token=abcdabcd&params={"oldpwd":"oldpwd","newpwd":"mynewpwd"}

# 返回结果实例

```js
{
    "error_code":0,
    "reason":"修改成功",
    "result":{
        "usertoken":"usertoken"
    }
}
```

# FAQ



