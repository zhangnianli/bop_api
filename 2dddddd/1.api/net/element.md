# 业务编号

net.data.element.statdata

# api请求地址

[https://api.bonree.com/net/data/element/](https://[api.bonree.com/net/report/taskdata]\(http://api.bonree.com/net/report/taskdata)statdata

# 请求方式

POST／GET

# 请求参数

# 请求参数

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string（32） | 是 | xxx | 令牌 |
| params | string | 是 | {“type”:2,"taskId":123456} | 请求参数 |

params说明：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| type | string | 是 | json/csv | 数据类型 |
| taskId | string | 否 | 170435,170436 | 任务ID |
| dtime | string | 是 | 20161101000000-20161102000000 | 数据时间范围，（时间最长一个月） |
| monitors | string | 是 | ALL/IDC/LM/PP/IDC | 监测点类型 |
| dateFM | string | 否 | 默认是yyyy-MM-dd HH:mm:ss | 数据时间类型 |
| filters | string | 否 | \[\["OR","D\_TIME","&gt;=",0.1\],\["AND","ERRORID","=",0\]\] | 字段值筛选条件,详见筛选条件列表 |
| group | string | 否 | city,netservice | 分组条件，字段顺序为分组顺序； |
| dHeader | string | 是 | city,netservice | 指定计算哪些指标，并作为查询结果返回，详见dHeader字典表 |
| pageNum | string | 否 | 1 | 分页索引，第几页 |
| pageRecorders | string | 否 | 50 | 分页查询时，单页总条数 |
| granule | string | 否 | STR\_DAY | 查询数据的时间频度，请查看时间频度字典表 |
| order | string | 否 | \[\["city","desc"\],\["netservice","asc"\]\] | 排序条件 |

时间频度字典表

| 值 | 含义 |
| :--- | :--- |
| STR\_MINUTE5 | 五分钟频度 |
| STR\_MINUTE30 | 30分钟频度 |
| STR\_HOUR | 1小时频度 |
| STR\_DAY | 1天频度 |



dHeader字典表：

| 字段英文名称 | 字段中文名称 |
| :--- | :--- |
| TASKID | roleid |
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
| error\_code | int | 错误码,0表示查询正常 |
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



