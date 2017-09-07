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
| params | string | 是 | {"dTime":"20170901-20170910"} | 请求参数json |

## **param参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dTime | string | 是 | 20170906-20170907 | 时间范围,精确到天 |
| monitorFun | number | 否 | 3 | 任务类型\(多个","分割\)0-网络 3-浏览 4-传输 5-流媒体 6-元素组 7-协议 9-事务 96-移动浏览 97-移动网络 98-移动协议 95-BMTP |
| granule | string | 否 | STR\_DAY | 查询粒度,详细请看粒度表 |
| flag | number | 否 | 1 | 任务状态；0-禁用，1-启用，9-结束 |
| dHeader | string | 是 | ROLE\_NAME,MONITOR\_FUN,TASK\_ID | 接口返回字段,配置\*返回全部 |

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
| TASK\_ID | number | 170435 | 任务ID |
| MONITOR\_FUN | number | 3 | 任务类型 |
| FLAG | number | 1 | 任务状态 |
| START\_TIME | number | 1393603200000 | 任务起始时间 |
| END\_TIME | number | 1488211200000 | 任务结束时间 |
| MONITOR\_COUNT | number | 1234 | 监测次数 |
| MONITOR\_NET\_COUNT | number | 1000 | 网络监测次数 |

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
  String url = "http://api.bonree.com/net/task/loadTask";
  HttpPost httppost = new HttpPost(url);
  System.out.println("请求: " + httppost.getRequestLine());
  // 创建参数队列
  List<NameValuePair> formparams = new ArrayList<NameValuePair>();
  formparams.add(new BasicNameValuePair("username", "bonreetest"));
  formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
  formparams.add(new BasicNameValuePair("params", "{\"monitor_fun\":3}"));
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
  http://api.bonree.com/net/task/loadTask?token=asdas12312312ddwew5we5we5&username=bonreetest&param={"monitor_fun":3}
```

# **返回结果示例**

```
{
    "errorCode": 0,
    "reason":"查询成功",
    "result: [
        ["ROLE_NAME","URL","TASK_ID","MONITOR_FUN","FLAG","START_TIME","END_TIME","PARENT_ID","ROLE_TYPE","NETENV_MON"],
        ["勿删长期测试qq","http://www.qq.com",170435,3,1,1393603200000,1488211200000,340832,9,"111"],
        ["QQ任务组","http://",340832,3,0,1446307200000,1446307200000,0,0,"000"]
    ]
}
```

# **api工具**

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# **FAQ**



