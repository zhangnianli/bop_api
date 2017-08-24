# 业务编号

net.nav.detaildata

# API请求地址

/net/nav/detaildata

# 请求参数：

| 参数名称 | 参数类型 | 是否必要填 | 实例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string | 是 | XXXXXXXXXXXX | token值 |
| params | string | 否 | {“statmainid”:“1212323”,“monitortime":1496988449”,"filed":”stat\_main\_id,errorid“} | 其中包含statmainid、monitortime、filed参数的json字符串，其中，statmainid和monitortime为必须的 |

# 请求参数示例：返回参数说明：

| 参数名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| code | int | 状态码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 返回结果示例：

```
{
    "code": 0,
    "reason": "success",
    "result": [
        ["STAT_MAIN_ID","ERRORID","MONITOR_TIME","BYTES_RECEIVED"],
        ["10350505","200","1496988449","100"],
        ["10350501","400","1496988449","100"],
        ["10350502","500","1496988449","100"]
    ]
}
```



