# 业务编号

base.data.loadCustomHeader

# api请求地址

[http://api.bonree.com/base/data/loadCustomHeader](http://api.bonree.com/base/city)

# 请求参数：

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| username | string | bonreetest | 用户名 |
| token | string | xxxxxxxxxxxxx | 令牌 |
| params | string | {"lastModif":"20170201000000"} | 参数json |

**params说明：**

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| lastModif | string | 20170201000000 | 最后修改时间 |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

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

# 返回结果示例：

```
{
    "error_code": 0,
    "reason": "查询成功",
    "result": [
        [["accountId","columnFields","columnLabels","businessType","lastModif"],
        [1,"responseTime,dnsTime,tcpTime,sslTime,serverResponseTime,serverHandleTime,requestUrl,monitorTime",null,508,"20170321101456"],
        [1,"avgResponseTime,maxResponseTime,minResponseTime,totalResponseTime,avgServerHandleTime,requestCount,perminRequestCount,slowRequestCount,slowSpeedRate,roleSplit,domain",null,507,"20170321101506"]
    ]
}
```



