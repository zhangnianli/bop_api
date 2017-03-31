# **业务编号**

base.data.loadKeyele

# **api请求地址**

[http://api.bonree.com/base/data/loadKeyele](http://api.bonree.com/base/data/loadKeyele)

# **请求方式**

POST/GET

# **请求参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string | 是 | \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* | 令牌 |
| username | string | 是 | bonreetest | 用户名 |
| params | string | 是 | {"appId":1} | 请求参数json |

## **params参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| appId | Number | 否 | 1 | appId |
| dHeader | String | 是 | ERROR\_ID,ERROR\_NAME | 接口返回字段,配置\*返回全部 |

# **dHeader说明**

| 名称 | 类型 | 示例值 | 描述 |
| :--- | :--- | :--- | :--- |
| KEY\_ID | Number | 1 | 关键元素ID |
| APPID | Number | 1 | 应用ID |
| KEY\_FLAG | Number | 1 | 匹配规则1-完全匹配 2-通配符 |
| URL | string | [http://www.baidu.com](http://www.baidu.com) |  |
| STATUS | Number | 2 | 关键元素状态 1-正常 2-禁用，3-删除 |

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
  String url = "http://api.bonree.com/base/data/loadKeyele";
  HttpPost httppost = new HttpPost(url);
  System.out.println("请求: " + httppost.getRequestLine());
  // 创建参数队列
  List<NameValuePair> formparams = new ArrayList<NameValuePair>();
  formparams.add(new BasicNameValuePair("username", "bonreetest"));
  formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
  formparams.add(new BasicNameValuePair("params", "{\"appId\":3}"));
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
  http://api.bonree.com/base/data/loadKeyele?token=asdas12312312ddwew5we5we5&username=bonreetest&param={"appId":3}
```

# **返回结果示例**

```
{
    "errorCode": 0,
    "reason":"查询成功",
    "result: [
        ["KEY_ID","APPID","KEY_FLAG","URL","STATUS"],
        [1,1,1,"3",3],
        [2,1,2,"3",3]
    ]
}
```

# **api工具**

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# **FAQ**



