# 业务编号

apm.data.app.config

# api请求地址

[http://api.bonree.com/apm/data/app/config](http://api.bonree.com/apm/data/app/config)

# 请求参数：

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| username | string | bonreetest | \*用户名 |
| token | string | xxxxxxxxxxxxx | \*令牌 |
| params | string | {"dtype":"json","appId":"1035","dtime":"20170201000000-20170301000000"} | \*参数json |

**params说明：**

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| dtype | string | json | \*数据类型\(csv、json\) |
| beAppId | string |  | 应用ID |
| dHeader | string | beAppId,btThrshld,btThrshldSlowTimes,btThrshldVerySlowTimes,btThrshldStallTimes,sqlExeTimeThreshold,noSqlExeTimeThreshold,remoteCallExeTimeThreshold,updateTime | \*指标数据项 |

# dHeader字段说明：

| 字段 | 名称 |
| :--- | :--- |
| startTime | 套餐开始时间 |
| endTime | 套餐结束时间 |
| agentNum | 探针数量 |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
    HttpClient httpclient = new DefaultHttpClient();
    String url = "http://api.bonree.com/apm/app/infodata";
    HttpPost httppost = new HttpPost(url);
    System.out.println("请求: " + httppost.getRequestLine());
    // 创建参数队列
    List<NameValuePair> formparams = new ArrayList<NameValuePair>();
    formparams.add(new BasicNameValuePair("username", "bonreetest"));
    formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
    formparams.add(new BasicNameValuePair("params", "{\"dtype\":\"json\",\"dHeader\":\"startTime,endTime,agentNum\"}"));
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
        ["startTime","endTime","agentNum"],
        ["2016-12-12", "2017-12-12", "100"]
    ]
}
```



