# 业务编号

net.nav.detaildata

# API请求地址

/net/nav/detaildata

# 请求参数：

| 参数名称 | 参数类型 | 是否必要填 | 实例值 | 参数说明 | 支持数据 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| statmainid | string | 是 | 10350505,10270801 | 查询的statmainid，多个id用“,”分隔 |  |
| monitortime | string | 是 | 1496250000,1496332800 | 查询时间起始时间，两个时间之间用“,”分隔，如果只有一个时间，则传递一个时间。 |  |
| field | string | 否 | STAT\_MAI\_ID,ERRORID,MONITOR\_TIME | 查询的字段集，字段之间用“,”分隔，如果没有不传递该值，表示查询所有字段。 | FIELDS, timestamp=1497605591087, value=ALLELEMENT\_ID,STAT\_MAIN\_ID,ROLE\_ID,USERNAME,ROLE\_IP,DOWN\_SIZE,MIME\_TYPE,STATUS\_CODE,MONITOR\_TIME,URL,HEADER,S\_TIME,B1,B2,B3,B4,B5,B6,B7,B8,TCPNUM,URL\_CODE,FIRST\_FLAG,MONITOR\_TIME\_CODE,REQ\_METHOD,REQHEADER,ASYNC\_ELE,HIJACKFLAG |

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



