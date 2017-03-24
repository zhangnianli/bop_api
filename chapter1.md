# 业务编号

net.data.nav.statdata

# api请求地址

[http://api.bonree.com/net/report/taskdata](http://[api.bonree.com/net/report/taskdata](http://api.bonree.com/net/report/taskdata)

[https://api.bonree.com/net/report/taskdata](https://[api.bonree.com/net/report/taskdata](http://api.bonree.com/net/report/taskdata)

# 请求参数：

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| token | string | xxxxxxxx | 令牌 |
| dtype | string | json | 数据类型 |
| taskId | string | 170435,170436 | 任务ID |
| dtime | string | 20161101000000-20161102000000 | 数据时间范围 |
| monitors | string | all，IDC，LM，PP，1100101\_2\_1-1100102\_2\_1 | 监测点[http://www.baidu.com](http://www.baidu.com "title") |
| dateType | string | BeijingTime,GMT | 数据时间类型 |
| filters | string | \[{“filed”:”CPU\_RATE”, “condo”:”&gt;=”,”value”:”6”}\] | 数据条件过滤 |
| dHeader | string | taskId,taskName,taskUrl | 指标数据项；查看所有指标项[/www.baidu.com](/chapter1.md "eeeee") |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
TaobaoClient client = new DefaultTaobaoClient(url, appkey, secret);
OpenAccountIndexFindRequest req = new OpenAccountIndexFindRequest();
req.setIndexType(1L);
req.setIndexValue("138581292221");
OpenAccountIndexFindResponse rsp = client.execute(req);
System.out.println(rsp.getBody());
```

# 返回结果示例：

```
{
    “error_code”: 0,
    “reason”:”查询成功”,
    “result”:[{
        “header”:{“taskId”,”taskName”,”taskUrl”,”errInfo”},
        “value” :[
        “170435”,”qq task”,”www.qq.com”,”0”,
        “170435”,”qq task”,”www.qq.com”,”0”
        }
    ]
}
```

# api工具：

api测试工具， 错误码查询工具，监测点查询工具，指标查询工具

# FAQ：

[/33333](/33333 "eeeeee")

