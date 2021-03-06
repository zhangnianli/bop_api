# **业务编号**

base.data.loadApp

# **api请求地址**

[http://api.bonree.com/base/data/loadApp](http://api.bonree.com/basedata/loadApp)

# **请求方式**

POST/GET

# **请求参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string | 是 | \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* | 令牌 |
| username | string | 是 | bonreetest | 用户名 |
| params | string | 是 | {"userId":1} | 请求参数json |

# **params参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| userId | Number | 否 | 1 | 用户id |
| appId | Number | 否 | 1 | appId |
| dHeader | String | 是 | APPID,APPNAME,KEY\_FLAG | 接口返回字段,配置\*返回全部 |

# **dHeader说明**

| 名称 | 类型 | 示例值 | 描述 |
| :--- | :--- | :--- | :--- |
| APPID | Number | 1 | AppID |
| APPNAME | string | fdf | App名称 |
| USER\_ID | Number | 1 | 用户ID |
| KEY\_FLAG | Number | 1 | 是否为关键业务 0-不是 1-是 |
| B1 | Number | 1 | 健康阈值：性能体验阈值（s） |
| B2 | Number | 90 | 健康阈值：请求错误率 |
| B3 | Number | 100 | 健康阈值：任务可用性 |
| B4 | Number | 58 | 健康阈值：崩溃率 |
| B5 | Number | 67 | 健康阈值：JS错误率 |
| B6 | Number | 40 | 健康阈值 慢速比 |
| STATUS | Number | 2 | 1:正常 2：删除 3：禁用 |

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
  String url = "http://api.bonree.com/base/data/loadApp";
  HttpPost httppost = new HttpPost(url);
  System.out.println("请求: " + httppost.getRequestLine());
  // 创建参数队列
  List<NameValuePair> formparams = new ArrayList<NameValuePair>();
  formparams.add(new BasicNameValuePair("username", "bonreetest"));
  formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
  formparams.add(new BasicNameValuePair("params", "{\"userId\":3}"));
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
  http://api.bonree.com/base/data/loadApp?token=asdas12312312ddwew5we5we5&username=bonreetest&param={"userId":3}
```

# **返回结果示例**

```
{
    "errorCode": 0,
    "reason":"查询成功",
    "result: [
        ["APPID","APPNAME","USER_ID","KEY_FLAG","B1","B2","B3","B4","B5","B6","STATUS"],
        [1,"fdf",1,1,2,2,2,2,2,2,2],
        [2,"'test'",1,0,0,0,0,0.1,0.1,0,2]
    ]
}
```

# **api工具**

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# **FAQ**



