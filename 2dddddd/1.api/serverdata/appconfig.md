# 业务编号

apm.data.app.config

# api请求地址

[http://api.bonree.com/apm/data/app/config](http://api.bonree.com/apm/data/app/config)

# 请求参数：

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| username | string | bonreetest | \*用户名 |
| token | string | xxxxxxxxxxxxx | \*令牌 |
| params | string | {"dtype":"json","beAppId":"1035"} | \*参数json |

**params说明：**

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| dtype | string | json | \*数据类型\(csv、json\) |
| beAppId | string | 1035,1036,1037 | 后端应用ID |
| dHeader | string | beAppId,btThrshld,btThrshldSlowTimes,btThrshldVerySlowTimes,btThrshldStallTimes,sqlExeTimeThreshold,noSqlExeTimeThreshold,remoteCallExeTimeThreshold,updateTime | \*指标数据项 |

# dHeader字段说明：

| 字段 | 名称 |
| :--- | :--- |
| beAppId | 后端应用ID |
| btThrshld | 业务健康度阀值-健康 |
| btThrshldSlowTimes | 业务健康度阀值-较慢 |
| btThrshldVerySlowTimes | 业务健康度阀值-很慢 |
| btThrshldStallTimes | 业务健康度阀值-停滞 |
| sqlExeTimeThreshold | sql调用健康度阀值 |
| noSqlExeTimeThreshold | nosql调用健康度阀值 |
| remoteCallExeTimeThreshold | rpc调用健康度阀值 |
| updateTime | 更新时间 |

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
    formparams.add(new BasicNameValuePair("params", "{\"dtype\":\"json\",\"beAppId\":\"1035,1036,1037\",\"dHeader\":\"beAppId,btThrshld,btThrshldSlowTimes,btThrshldVerySlowTimes,btThrshldStallTimes,sqlExeTimeThreshold,noSqlExeTimeThreshold,remoteCallExeTimeThreshold,updateTime\"}"));
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
        ["beAppId","btThrshld","btThrshldSlowTimes","btThrshldVerySlowTimes","btThrshldStallTimes","sqlExeTimeThreshold","noSqlExeTimeThreshold","remoteCallExeTimeThreshold","updateTime"],
        ["1035","10","20","30","40","50","50","50","20170327120000"],
        ["1036","10","20","30","40","50","50","50","20170327120000"],
        ["1037","10","20","30","40","50","50","50","20170327120000"]
    ]
}
```



