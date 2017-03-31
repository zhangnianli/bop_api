# **业务编号**

base.data.loadCustomHeader

# **api请求地址**

[http://api.bonree.com/base/data/loadCustomHeader](http://api.bonree.com/base/city)

# **请求参数**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string | 是 | xxxxxxxxxxxxx | 令牌 |
| params | string | 是 | {"dHeader":"ACCOUNT\_ID,COLUMN\_FIELDS,COLUMN\_LABELS,LASTMODIF"} | 参数json |

# **params说明**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| lastModif | string | 否 | 20170201000000 | 最后修改时间 |
| dHeader | String | 是 | ACCOUNT\_ID,COLUMN\_FIELDS,COLUMN\_LABELS,LASTMODIF | 接口返回字段,配置\*返回全部 |

# **dHeader说明**

| 名称 | 类型 | 示例值 | 描述 |
| :--- | :--- | :--- | :--- |
| ACCOUNT\_ID | Number | 1 |  |
| COLUMN\_FIELDS | string | responseTime,dnsTime,tcpTime | 表头字段 |
| COLUMN\_LABELS | string | 响应用时,DNS用时,TCP用时 | 表头对应描述 |
| BUSINESS\_TYPE | Number | 508 |  |
| LASTMODIF | Number | 1446307200000 | 最后修改时间 |

# **返回参数说明**

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# **请求示例**

```
    HttpClient httpclient = new DefaultHttpClient();
    String url = "http://api.bonree.com/base/data/loadCustomHeader";
    HttpPost httppost = new HttpPost(url);
    System.out.println("请求: " + httppost.getRequestLine());
    // 创建参数队列
    List<NameValuePair> formparams = new ArrayList<NameValuePair>();
    formparams.add(new BasicNameValuePair("username", "bonreetest"));
    formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
    formparams.add(new BasicNameValuePair("params", "{\"lastModif\":\"20170202000000\"}"));
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

# **返回结果示例**

```
{
    "errorCode": 0,
    "reason": "查询成功",
    "result": [
        ["ACCOUNT_ID","COLUMN_FIELDS","COLUMN_LABELS","BUSINESS_TYPE","LASTMODIF"],
        [1,"responseTime,dnsTime,tcpTime,sslTime,serverResponseTime,serverHandleTime,requestUrl,monitorTime",null,508,"20170321101456"],
        [1,"avgResponseTime,maxResponseTime,minResponseTime,totalResponseTime,avgServerHandleTime,requestCount,perminRequestCount,slowRequestCount,slowSpeedRate,roleSplit,domain",null,507,"20170321101506"]
    ]
}
```

# **api工具**

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# **FAQ**



