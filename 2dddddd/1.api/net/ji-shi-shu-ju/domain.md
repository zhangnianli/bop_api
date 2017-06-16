# 业务编号

net.domain.detaildata

# API请求地址

/net/domain/detaildata

# 请求参数：

| 参数名称 | 参数类型 | 是否必要填 | 实例值 | 参数说明 | 支持数据 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| statmainid | string | 是 | 10350505,10270801 | 查询的statmainid，多个id用“,”分隔 |  |
| monitortime | string | 是 | 1496250000,1496332800 | 查询时间起始时间，两个时间之间用“,”分隔，如果只有一个时间，则传递一个时间。 |  |
| field | string | 否 | STAT\_MAI\_ID,ERRORID,MONITOR\_TIME | 查询的字段集，字段之间用“,”分隔，如果没有不传递该值，表示查询所有字段。 | STAT\_DOMAIN\_ID,ROLE\_ID,DOMAIN,IP,ELEMENT\_NUM,ERR\_ELEMENT\_NUM,TCP\_CONN\_COUNT,ROUND\_TRIPS,DOWN\_SIZE,DOWN\_SPEED,ONEBYTES\_TIME,TOTLE\_TIME,T1,T2,T3,T4,T5,A1,A2,A3,A4,A5,ROLE\_CITYCOD,ROLE\_NETSERVICE,MONITOR\_TIME,C\_CITYCODE,C\_NETSERVICE\_ID,C\_CLIENT\_TYPE,C\_NETSPEED,CPU\_RATE,MEM\_RATE,CYCLE\_SPEED,PROCESS\_NUM,STAT\_MAIN\_ID,C\_DNS,C\_LAST\_IP,CLIENT\_NUM,IE\_VERSION,OS\_VERSION,DOMAIN\_CODE,MONITOR\_TIME\_CODE,HIJACKFLAG,CNAME,TRACERT\_CITYCODE,TRACERT\_NETSERVICEID,C\_GPS,ROLE\_CITYCODE |

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



