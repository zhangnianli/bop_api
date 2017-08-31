# 业务编号

net.data.report.statdata

# api请求地址

[https://api.bonree.com/net/report/statdata](https://api.bonree.com/net/element/]%28https://[api.bonree.com/net/report/taskdata]%28http://api.bonree.com/net/report/taskdata%29statdata]%28https://api.bonree.com/net/element/]%28https://[api.bonree.com/net/report/taskdata]%28http://api.bonree.com/net/report/taskdata%29statdata)

# 请求方式

POST／GET

# 请求参数

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string（32） | 是 | xxx | 令牌 |
| params | string | 是 | {“dType”:2,"taskId":123456} | 请求参数 |

params说明：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json/csv | 数据类型 |
| taskId | string | 是 | 170435,170436 | 任务ID |
| dTime | string | 是 | 20161101000000-20161102000000 | 数据时间范围，（时间最长一个月） |
| weekTime | string | 否 | {"staerWeek":"1", "endWeek":"7","startHour":"00:00","endHour":"23:05"} |  |
| dateFM | string | 否 | 默认是yyyy-MM-dd HH:mm:ss | 数据时间类型 |
| filters | string | 否 |  | 字段值筛选条件,详见筛选条件列表 |
| group | string | 是 | city,netservice | 分组条件，字段顺序为分组顺序 |
| dHeader | string | 是 | city,netservice | 指定计算哪些指标，并作为查询结果返回 |
| pageNum | string | 否 | 1 | 分页索引，第几页 |
| pageRecorders | string | 否 | 50 | 分页查询时，单页总条数 |
| granule | string | 否 | 5 | 查询数据的时间频度，单位为分钟，当传时间频度的时候，group参数必填 |
| order | string | 否 | \[\["city","desc"\],\["netservice","asc"\]\] | 排序条件 |
| user | string | 是 | bonreetest | V4用户名 |
|  |  |  |  |  |

filters字段

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| monitors | string | 否 | {"idc": {"selected": "in","agents": \["1100101\_1","1100101\_2" \]},"lm": {"selected": "all","agents": \[\]},"mb": {"selected": "ex","agents": \["1100503\_16"\]},"bmtp": {"selected": "all","agents": \[\]},"pp": {"selected": "all","agents": \[\]}} | 监测点类型,selected表示选中类型,all:为全部选中;in:选中agents里面的值,ex:排除agents里面的值;agents为数组,里面的值为字符串,citycode\_netserverid |
| access | string | 否 | \["1","2"\] | 接入方式,仅支持wap与bmtp |
| agentSpeed | string | 否 | \["1","2","3"\] | 监测点带宽,1:\[0, 512Kb\];2:\(512Kb, 2Mb\];3:\(2Mb, 4Mb\];4:\(4Mb, 10Mb\];5:\(10Mb, 20Mb\];6:\(20Mb, ∞\) |
| browser | string | 否 | \["1","2","3"\] | 监测点浏览器版本,1: IE6; 2: IE7; 3: IE8; 4:IE9; 5:IE10; 6:IE11; 100:chrome\(WebKit\); 101:chrome\(blink\); -1:其它 |
| os | string | 否 | \["2","3","4","5"\] | 监测点操作系统版本: 2:WIN2003; 3:WINXP; 4:WINVISTA; 5:WIN7; 6:WIN8; 9:WIN10; -1:其它 |
| clientIds | string | 否 | {"selected":"in", "ids":\["123", "456"\]} | 客户端ID,selected表示选中类型,in:选中ids里面的值,ex:排除ids里面的值 |
| clientIPs | string | 否 | {"selected":"in", "ips":\["1.1.1.1", "8.8.8.8"\]} | 客户端IP,selected表示选中类型,in:选中ips里面的值,ex:排除ips里面的值 |
| clientDNS | string | 否 | {"selected":"in", "ips":\["1.1.1.1", "8.8.8.8"\]} | 客户端DNS,selected表示选中类型,in:选中ips里面的值,ex:排除ips里面的值 |
| targetIPs | string | 否 | {"selected":"in", "ips":\["1.1.1.1", "8.8.8.8"\]} | 目标IP,selected表示选中类型,in:选中ips里面的值,ex:排除ips里面的值 |
| CPURate | string | 否 | {"min":"48", max:"60"} | 客户端CUP占用率 |
| memoryRate | string | 否 | {"min":"48", max:"60"} | 客户端内存占用率 |
| processNum | string | 否 | {"min":"48", max:"60"} | 客户端进程数量 |
| cycleSpeed | string | 否 | {"min":"1000", max:"2000"} | 周期平均速度,单位:KB/s |
| cycleSpeedWeigh | int | 否 | 2 | 整体速度大于几倍的平均周期速度 |
| tracertMatching | int | 否 | 0 | 是否匹配出口ip 0:否;1:是 |
| errorIds | string | 否 | \["302","404"\] | 错误ID,默认包含0 |
| performanceIndex | string | 否 | {"type":"0","inde":"D\_TIME","min":"0.5",""mark":"0"} | 指标筛选,type:筛选样式,0:指定值;1:指标百分比;2:样本数; inde:指标; min:最小值; max:最大值; mark:标识,0:与\(保留\);1:或\(排除\) |
| hijack | int | 否 | 0 | 是否排除劫持数据;0:不排除;1排除 |
| domain | string | 否 | \["www.bonree.com"\] | 域名筛选 |
|  |  |  |  |  |

时间频度字典表

| 值 | 含义 |
| :--- | :--- |
| STR\_MINUTE5 | 5分钟频度 |
| STR\_MINUTE30 | 30分钟频度 |
| STR\_HOUR | 1小时频度 |
| STR\_DAY | 1天频度 |

# dHeader字典表：

| 字段英文名称 | 字段中文名称 |
| :--- | :--- |
| TASKID | TASKID |
| COUNTRY | 国家 |
| CITY\_CODE | 城市 |
| NETSERVICE | 运营商 |
| BROWSER | 浏览器 |
| ROLE\_USEABLE | 总任务可用性\(%\) |
| USEABLE | 任务可用性\(%\) |
| ERRNUM | 任务错误次数\(次\) |
| ERRORTYPE | 错误类型 |
| FIRST\_TIME | 首次发生时间 |
| LAST\_TIME | 末次发生时间 |
| ALLNUM | 总检测次数 |
| ALLNUM\_ERR | 总错误次数 |
| ERRRATE\_ROLE | 任务错误占比 |
| ERRRATE | 错误率 |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | int | 错误码,0表示查询正常 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
        HttpClient httpclient = new DefaultHttpClient();
        String url = "https://api.bonree.com/net/element/statdata";
        HttpPost httppost = new HttpPost(url);
        System.out.println("请求: " + httppost.getRequestLine());
        // 创建参数队列
        List<NameValuePair> formparams = new ArrayList<NameValuePair>();
        formparams.add(new BasicNameValuePair("username", "bonreetest"));
        formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
        formparams.add(new BasicNameValuePair("params", "{\"token\":\"*******\",\"dtype\":\"json\",\"taskId\":\"1035\",\"dtime\":\"20170201000000-20170301000000\"}"));
        UrlEncodedFormEntity uefEntity = new UrlEncodedFormEntity(formparams, "UTF-8");
        httppost.setEntity(uefEntity);
        // 执行
        HttpResponse response = httpclient.execute(httppost);
        HttpEntity entity = response.getEntity();
        System.out.println("----------------------------------------");
        System.out.println("状态:" + response.getStatusLine());
        if (entity != null) {
            System.out.println("Response content length: " + entity.getContentLength());
            System.out.println("Response content :" + EntityUtils.toString(entity, "UTF-8"));
        }
        // 关闭连接,释放资源
        httpclient.getConnectionManager().shutdown();
```

# 返回结果示例

```
{
    "error_code": 0,
    "reason": "查询成功",
    "result": [
        [
            "role_id",
            "domain"
        ],
        [
            "1035",
            "www.baidu.com"
        ],
        [
            "1023",
            "www.bonree.com"
        ]
    ]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



