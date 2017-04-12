# 业务编号

sdk.data.webview.count

# api请求地址

[http://api.bonree.com/sdk/data/webview/count](http://api.bonree.com/sdk/report/data/crash/distribution)

[https://api.bonree.com/sdk/data/webview/count](https://api.bonree.com/sdk/report/data/crash/distribution)

# 请求方式

POST／GET

# 请求参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string\(32\) | 是 | xxxxxxxx | 令牌 |
| username | string | 是 | bonree | 用户名 |
| params | string | 是 |  | 参数json |

### params参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json/csv | 数据类型 |
| taskId | string | 是 | "taskId":"10240,10241" | 应用id |
| dTime | string | 是 | "dTime":"20160101000000-20160102000000" | 数据时间范围 |
| dHeader | string | 是 | "dHeader":"TASK\_ID" | 指标数据项 |
| group | string | 否 | "group":"TASK\_ID" | 数据组合条件 |

### filters参数

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |


### dHeader参数

| 参数名称 | 参数类型 | 是否必选 | 参数说明 |
| :--- | :--- | :--- | :--- |
| TASK\_ID | string | 否 | sdk应用id |
| WEBVIEW\_ERROR\_RATE | string | 否 | 错误率 |
| WEBVIEW\_ERROR\_COUNT | string | 否 | 发生错误的访问数 |
| WEBVIEW\_COUNT | string | 否 | 访问数 |

### group参数

| 参数名称 | 参数说明 |
| :--- | :--- |
| TASK\_ID | sdk应用id |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | int | 错误码 |
| reason | string | 返回说明 |
| type | string | 返回数据类型 |
| result | string | 返回结果集 |

# 请求示例

```java
HttpClient httpclient = new DefaultHttpClient();
String url = "http://api.bonree.com/sdk/report/data/webview/count";
String params = "{\"dType\":\"json\",\"appId\":\"1111,2222\",\"dTime\":\"20160101000000-20160102000000\"}";

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

```
{“error_code”: 0,
    “reason”:”查询成功”,
     result: [
              [”appId”,“appName”,”webviewErrorRate”],
              [”02”,”bonree01”,”0.01”],
              [”03”,“bonree02”,”0.01”]
]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



