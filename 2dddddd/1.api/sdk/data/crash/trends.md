# 业务编号

sdk.data.crash.trends

# api请求地址

[http://api.bonree.com/sdk/report/data/crash/trends](http://api.bonree.com/sdk/report/data/crash/trends)

[https://api.bonree.com/sdk/report/data/crash/trends](https://api.bonree.com/sdk/report/data/crash/trends)

# 请求方式

POST／GET

# 请求参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string\(32\) | 是 | xxxxxxxx | 令牌 |
| dType | string | 是 | json/csv | 数据类型 |
| userName | string | 是 | bonree | 用户名 |
| params | string | 是 | {"dType":"json","sdkAppId":\[1111,2222\],"dTime":"20160101000000-20160102000000","dHeader":\[appid,granuleId,monitorTime,crashRate,startCount\],"filter":{"crashTypeCode":\["1111","2222"\]}} | 参数json |

### params参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json/csv | 数据类型 |
| sdkAppId | string | 是 | 1111,2222 | 应用id |
| dTime | string | 是 | 20160101000000-20160102000000 | 数据时间范围\(时间最长一个月\) |
| filters | string | 否 | "filter":{"crashTypeCode":\["1111","2222"\]} | 数据筛选条件 |
| dHeader | string | 是 | appid,granuleId,monitorTime,crashRate,startCount | 指标数据项 |

### filters参数

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| crashTypeCode | string | "crashTypeCode":\["1111","1231"\] | 崩溃类型code |

### dHeader指标

| 参数名称 | 参数类型 | 是否必选 | 返回值示例 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| sdkAppId | string | 否 | 1111 | sdk应用appId |
| granuledId | string | 是 | 1 | 时间刻度 |
| monitorTime | string | 是 | 201601010000 | 监测时间 |
| crashRate | string | 否 | 0.001 | 崩溃率 |
| crashType | string | 否 | NullPointerException | 崩溃类型 |
| crashTypeCode | string | 否 | "1111" | 崩溃类型code |
| crashCount | string | 否 | 200 | 崩溃次数 |
| startCount | string | 否 | 200 | sdk app启动次数 |
| userCount | string | 否 | 200 | 崩溃影响用户数 |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```java
HttpClient httpclient = new DefaultHttpClient();
String url = "https://api.bonree.com/sdk/report/data/crash/trends";
String params = "{\"dType\":\"json\",\"sdkAppId\":[1111,2222],\"dTime\":\"20160101000000-20160102000000\",\"dHeader\":[appid,granuleId,monitorTime,crashRate,startCount],\"filter\":{\"crashTypeCode\":[\"1111\",\"2222\"]}}";

HttpPost httppost = new HttpPost(url);
System.out.println("请求: " + httppost.getRequestLine());
// 创建参数队列
List<NameValuePair> formparams = new ArrayList<NameValuePair>();
formparams.add(new BasicNameValuePair("username", "girl"));
formparams.add(new BasicNameValuePair("password", "boy"));
fromparams.add(new BasicNameValuePair("params",params)
UrlEncodedFormEntity uefEntity = new UrlEncodedFormEntity(formparams,"UTF-8");
httppost.setEntity(uefEntity);
// 执行
HttpResponse response = httpclient.execute(httppost);
HttpEntity entity = response.getEntity();
System.out.println("----------------------------------------");
System.out.println("状态:" + response.getStatusLine());
if (entity != null) {
System.out.println("Response content length: "+ entity.getContentLength());
System.out.println("Response content :"+ EntityUtils.toString(entity, "UTF-8"));
}
// 关闭连接,释放资源
httpclient.getConnectionManager().shutdown();
```

# 返回示例

{"error\_code": 0,  
    "reason":"查询成功",  
    "result":\[  
        \["appid","granuleId","monitorTime","crashRate","startCount"\],  
        \["1111","1","20161101000000","0.01","1"\],  
        \["1111","2","20161101000100","0.01","1"\]  
    \]  
}  
\`\`\`

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：


