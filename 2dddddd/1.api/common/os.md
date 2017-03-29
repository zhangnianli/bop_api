# **业务编号**

base.data.loadOs

# **api请求地址**

[http://api.bonree.com/base/data/loadOs](http://api.bonree.com/basedata/loadOs)

# **请求方式**

POST/GET

# **请求参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string | 是 | \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* | 令牌 |
| username | string | 是 | bonreetest | 用户名 |
| params | string | 是 | {"lastModif":"20170201000000"} | 参数json |

# **params说明**

|  参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dHeader | String | 是 | OS_ID,OS_NAME,OS_VER_NAME | 接口返回字段,配置\*返回全部 |

# **dHeader说明**

# **dHeader说明**
| 名称 | 类型 | 示例值 | 描述 |
| :--- | :--- | :--- | :--- |
| OS_ID | Number | 1 | 操作系统ID |
| OS_NAME | string | Windows | 操作系统名称 |
| OS_VER_ID | Number | 101 | 版本ID |
| OS_VER_NAME | string | Win7 | 版本名称 |

# **返回参数说明**

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | Number | 错误码 |
| reason | string | 结果说明 |
| result | string | 查询结果 |

# **请求示例**

```
 POST:
  HttpClient httpclient = new DefaultHttpClient();
  String url = "http://api.bonree.com/base/data/loadOs";
  HttpPost httppost = new HttpPost(url);
  System.out.println("请求: " + httppost.getRequestLine());
  // 创建参数队列
  List<NameValuePair> formparams = new ArrayList<NameValuePair>();
  formparams.add(new BasicNameValuePair("username", "bonreetest"));
  formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
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
  http://api.bonree.com/base/data/loadOs?token=asdas12312312ddwew5we5we5&username=bonreetest
```

# **返回结果示例**

```
{
    "error_code": 0,
    "reason":"查询成功",
    "result: [
        ["osId","osName","osVerId","osVerName"],
        [1,"Windows",101,"Win7"],
        [1,"Windows",102,"Win Vista"]
    ]
}
```

# **api工具**

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# **FAQ**



