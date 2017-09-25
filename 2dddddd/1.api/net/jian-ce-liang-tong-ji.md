# **业务编号**

net.task.monitorStat

# **api请求地址**

[http://api.bonree.com/net/task/monitorStat](http://api.bonree.com/net/task/monitorStat)

# **请求方式**

POST/GET

# **请求参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string | 是 | \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* | 令牌 |
| username | string | 是 | bonreetest | 用户名 |
| params | string | 是 | {"dTime":"20170901-20170910","dHeader":"MONITOR\_COUNT"} | 请求参数json |

## **param参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dTime | string | 是 | 20170906-20170907 | 时间范围,精确到天 |
| dHeader | string | 是 | MONITOR\_COUNT,MONITOR\_NET\_COUNT | 接口返回字段 |
| group | string | 否 | TASK\_ID | 分组条件,可以按照TASK\_ID,MONITOR\_FUN,FLAG,USERNAME等分组 |
| monitorFun | string | 否 | 3,4 | 任务类型\(多个","分割\)0-网络 3-浏览 4-传输 5-流媒体 6-元素组 7-协议 9-事务 10-推流  96-移动浏览 97-移动网络 98-移动协议 99-移动单元素 100-MAA95-BMTP |
| granule | string | 否 | STR\_DAY | 查询粒度,详细请看粒度表 |
| flag | string | 否 | 0,1 | 任务状态；0-禁用，1-正常，2-删除，9-结束，默认全部 |
| dType | string | 否 | json/csv | 导出的格式,默认json |
| region | int | 否 | 0 | 0-国内，1-国外，2-中国港澳台，3-中国大陆，默认全部 |
| monitorType | int | 否 | 0 | 0-全部，1-私有监测点,默认全部 |
| roleType | int | 否 | 0 | 0-常规任务，1-即时测试任务,默认常规任务 |
| search | string | 否 | bj-浏览任务 | 快速检索信息,匹配任务名称,URL |

### 时间频度字典表

| 值 | 描述 |
| :--- | :--- |
| STR\_DAY | 天 |
| STR\_WEEK | 周 |
| STR\_MONTH | 月 |
| STR\_YEAR | 年 |

# **dHeader说明**

| 名称 | 类型 | 示例值 | 描述 |
| :--- | :--- | :--- | :--- |
| ROLE\_NAME | string | 勿删长期测试qq | 任务名称 |
| URL | string | [http://www.qq.com](http://www.qq.com) | 任务地址 |
| USERNAME | string | bonreetest | 账户名称 |
| TASK\_ID | number | 170435 | 任务ID |
| MONITOR\_FUN | number | 3 | 任务类型 |
| FLAG | number | 1 | 任务状态 |
| START\_TIME | number | 1393603200000 | 任务起始时间 |
| END\_TIME | number | 1488211200000 | 任务结束时间 |
| MONITOR\_COUNT | number | 1234 | 监测次数\(BMTP类型为流量MB\) |
| MONITOR\_NET\_COUNT | number | 1000 | 网络监测次数\(BMTP类型为时长h\) |

# **返回参数说明**

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | Number | 错误码 |
| reason | string | 结果说明 |
| result | string | 查询结果 |

# **请求示例**

```
POST:
  HttpClient httpclient = new DefaultHttpClient();
  String url = "http://api.bonree.com/net/task/monitorStat";
  HttpPost httppost = new HttpPost(url);
  System.out.println("请求: " + httppost.getRequestLine());
  // 创建参数队列
  List<NameValuePair> formparams = new ArrayList<NameValuePair>();
  formparams.add(new BasicNameValuePair("username", "bonreetest"));
  formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
  formparams.add(new BasicNameValuePair("params", "{\"dTime\":\"20170904110000-20170908000000\",\"dHeader\":\"MONITOR_COUNT,MONITOR_NET_COUNT\",\"granule\":\"STR_DAY\"}"));
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

 GET:
  http://api.bonree.com/net/task/monitorStat?token=xxxxxxxxxx&username=bonreetest&param={"dTime":"20170904110000-20170908000000","dHeader":"MONITOR_COUNT,MONITOR_NET_COUNT","granule":"STR_DAY"}
```

# **返回结果示例**

```
{
    "errorCode": 0,
    "reason":"查询成功",
    "result: [
        ["STR_DAY","MONITOR_COUNT","MONITOR_NET_COUNT"],
        ["20170901","1234","981"],
        ["20170902","1221","972"],
        ["20170903","1220","968"],
        ["20170904","1243","980"]
    ]
}
```

# **api工具**

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# **FAQ**



