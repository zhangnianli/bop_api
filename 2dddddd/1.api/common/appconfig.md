# **业务编号**

base.data.loadAppConfig

# **api请求地址**

[http://api.bonree.com/base/data/loadAppConfig](http://api.bonree.com/base/data/loadAppConfig)

# **请求方式**

POST/GET

# **请求参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string | 是 | \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* | 令牌 |
| username | string | 是 | bonreetest | 用户名 |
| params | string | 是 | {"appId":1} | 请求参数json |

# **params参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| appId | Number | 否 | 1 | appId |
| taskId | Number | 否 | 1 | 任务ID |
| taskType | Number | 否 | 1 | 1:v4   2:SDK 3:BROWSER 4:SERVER |
| monitorFun | Number | 否 | 1 | 检测任务类型： V4：（监测功能（0网络环境监测、2网页浏览监测、3网页元素监测、4下载监测,5流媒体，6元素组，7端口测试，9事务测试,99-移动单元素，98移动私有协议，97移动网络，96移动全元素、100-MAA）\)，95：BMTP，151：sdk,152：browser,153：server |
| dHeader | String | 是 | APPID,TASK\_TYPE,TASK\_ID | 接口返回字段,配置\*返回全部 |

# **dHeader说明**

| 名称 | 类型 | 示例值 | 描述 |
| :--- | :--- | :--- | :--- |
| APPID | Number | 3 | 应用ID |
| ID | Number | 1 |  |
| TASK\_TYPE | Number | 1 | 1-v4 2-SDK 3-BROWSER 4-SERVER |
| MONITOR\_FUN | Number | 6 | 检测任务类型V4：（监测功能（0网络环境监测、2网页浏览监测、3网页元素监测、4下载监测,5流媒体，6元素组，7端口测试，9事务测试,99-移动单元素，98移动私有协议，97移动网络，96移动全元素、100-MAA）\)，95：BMTP，151：sdk,152：browser,153：server |
| TASK\_ID | Number | 170435 | 任务ID |
| URL | string | [http://www.baidu.com](http://www.baidu.com) | 任务地址 |
| URL\_MERGE\_RULE | Number | 3 | 请求地址合并（1:完全匹配，2：通配符，3：正则表达式） |

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
  String url = "http://api.bonree.com/base/data/loadAppConfig";
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
  http://api.bonree.com/base/data/loadAppConfig?token=asdas12312312ddwew5we5we5&username=bonreetest&param={"appId":3}
```

# **返回结果示例**

```
{
    "errorCode": 0,
    "reason":"查询成功",
    "result: [
        ["APPID","ID","TASK_TYPE","MONITOR_FUN","TASK_ID","URL","URL_MERGE_RULE"],
        [3,50,1,6,8,"0",null],
        [3,51,4,153,11,"0",null]
    ]
}
```

# **api工具**

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# **FAQ**



