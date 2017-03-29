# 业务编号

platform.data.performance.statdata

# api请求地址

[https://api.bonree.com/](https://[api.bonree.com/net/report/taskdata]\(http://api.bonree.com/net/report/taskdata\)[platform/data/performance/statdata](https://[api.bonree.com/net/report/taskdata]\(http://api.bonree.com/net/report/taskdata)

# 请求方式

POST／GET

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
| appId | string | 否 | 123456 | 应用ID |
| dtime | string | 是 | 20161101000000-20161102000000 | 数据时间范围，（时间最长一个月） |
| monitors | string | 是 | ALL/IDC/LM/PP/IDC | 监测点类型 |
| dateFM | string | 否 | 默认是yyyy-MM-dd HH:mm:ss | 数据时间类型 |
| filters | string | 否 | \[{“filed”:”CPU\_RATE”, “condo”:”&gt;=”,”value”:”6”}\] | 字段值筛选条件 |
| group | string | 否 | city,netservice | 分组条件，字段顺序为分组顺序 |
| granule | string | 否 | 5 | 时间频度 |
| dHeader | string | 是 | city,netservice | 指标查询结果，可以指定计算哪些指标 |
| order | string | 否 | city desc/nerservice asc,city desc | 排序条件，字段顺序就是排序顺序 |

field列表：

| 字段英文名称 | 字段中文名称 | 字段描述 |
| :--- | :--- | :--- |
| APPID | 应用ID | 应用ID |
| TASKID | TASKID | ROLE\_ID |
| CITYCODE | 城市 | 监测点城市 |
| NETSERVICEID | 运营商 | 监测点运营商 |
| ACCESSMODE | 接入方式 | 监测点接入方式 |
| BROWSER | 浏览器 | 浏览器类型 |
| ERRRATE | 请求错误率 | 请求错误次数/请求次数 |
| SLOWRATE | 慢速比 | 慢请求次数/请求次数 |
| REQUESTNUM | 请求次数 | 总请求次数 |
| BLOCKTIME | block时间 | block时间均值 |
| BLOCKTIME1 | block时间 | block时间均值，健康请求 |
| BLOCKTIME2 | block时间 | block时间均值，慢请求 |
| DNSTIME | dns时间 | dns时间均值，所有请求 |
| DNSTIME1 | dns时间 | dns时间均值，健康请求 |
| DNSTIME2 | dns时间 | dns时间均值，慢请求 |
| TCPTIME | tcp时间 | tcp时间均值 |
| TCPTIME1 | tcp时间 | tcp时间均值，健康请求 |
| TCPTIME2 | tcp时间 | tcp时间均值，慢请求 |
| SSLTIME | ssl时间 | ssl时间均值 |
| SSLTIME1 | ssl时间 | ssl时间均值，健康请求 |
| SSLTIME2 | ssl时间 | ssl时间均值,慢请求 |
| CLIENTRESPONSETIME | response时间 | response均值,所有请求的。 |
| CLIENTRESPONSETIME1 | response时间 | response均值,健康请求的 |
| CLIENTRESPONSETIME2 | response时间 | response均值，不健康请求的,不健康请求指慢请求 |
| DTIME | 整体性能 | 整体性能时间均值 |
| SERVERRESPONSETIME | 服务器处理时间 | 服务器处理时间均值 |
| SERVERRESPONSETIME1 | 服务器处理时间 | 服务器处理时间均值，健康请求的 |
| SERVERRESPONSETIME2 | 服务处理时间 | 服务器处理时间均值，不健康请求的 |
| ERRORID | 错误码 | 错误类型码 |
| MONITOR\_TIME\_CODE | 时间频度码 | 按时间频度划分的时间频度值 |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码，0表示成功查询 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
        HttpClient httpclient = new DefaultHttpClient();
        String url = "https://api.bonree.com/platform/performance/statdata";
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
        [APPID,"ERRORID"],
        [1,"123"]
    ]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



