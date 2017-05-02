# 业务编号

custom.check

# api请求地址

[http://api.bonree.com/custom/check](http://api.bonree.com/custom/check)

# 请求方式

POST/GET

# 请求参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | myusername | 令牌 |
| token | string | 是 | systomen | 系统校验token |

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
	"reason":"校验成功",
	"result":{
		"usertoken":"usertoken"
	}
}
```

# FAQ




