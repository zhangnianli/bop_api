# 业务编号

browser.data.app.config

# api请求地址

[http://api.bonree.com/browser/data/app/config](http://api.bonree.com/apm/data/app/config)

# 请求参数：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string | 是 | xxxxxxxxxxxxx | 令牌 |
| params | string | 是 | {"dtype":"json","appId":"1035"} | 参数json |

**params说明：**

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json | 数据类型\(csv、json\) |
| appId | string | 是 | 1035,1036,1037 | 应用ID |
| dHeader | string | 是 | BE\_APP\_ID,BT\_THRSHLD,BT\_THRSHLD\_SLOW\_TIMES,BT\_THRSHLD\_VERYSLOW\_TIMES,BT\_THRSHLD\_STALL\_TIMES,SQL\_EXETIME\_THRESHOLD,NOSQL\_EXETIME\_THRESHOLD,REMOTECALL\_EXETIME\_THRESHOLD,UPDATE\_TIME | 指标数据项 |

# dHeader字段说明：

| 字段 | 名称 |
| :--- | :--- |
| BE\_APP\_ID | 后端应用ID |
| BT\_THRSHLD | 业务健康度阀值-健康 |
| BT\_THRSHLD\_SLOW\_TIMES | 业务健康度阀值-较慢 |
| BT\_THRSHLD\_VERYSLOW\_TIMES | 业务健康度阀值-很慢 |
| BT\_THRSHLD\_STALL\_TIMES | 业务健康度阀值-停滞 |
| SQL\_EXETIME\_THRESHOLD | sql调用健康度阀值 |
| NOSQL\_EXETIME\_THRESHOLD | nosql调用健康度阀值 |
| REMOTECALL\_EXETIME\_THRESHOLD | rpc调用健康度阀值 |
| UPDATE\_TIME | 更新时间 |
| IP\_COUNT | 外网主机统计个数 |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | int | 错误码 |
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
    formparams.add(new BasicNameValuePair("params", "{xxx}"));
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
    "errorCode": 0,
    "reason": "查询成功",
    "result": [
        ["BE_APP_ID","BT_THRSHLD","BT_THRSHLD_SLOW_TIMES","BT_THRSHLD_VERYSLOW_TIMES","BT_THRSHLD_STALL_TIMES","SQL_EXETIME_THRESHOLD","NOSQL_EXETIME_THRESHOLD","REMOTECALL_EXETIME_THRESHOLD","UPDATE_TIME"],
        ["1035","10","20","30","40","50","50","50","20170327120000"],
        ["1036","10","20","30","40","50","50","50","20170327120000"],
        ["1037","10","20","30","40","50","50","50","20170327120000"]
    ]
}
```



