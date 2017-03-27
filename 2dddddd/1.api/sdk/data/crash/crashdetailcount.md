# 业务编号

sdk.data.crash.detail

# api请求地址

[http://api.bonree.com/sdk/data/crash/detail](http://api.bonree.com/sdk/report/data/crash/detail)

[https://api.bonree.com/sdk/data/crash/detail](https://api.bonree.com/sdk/report/data/crash/detail)

# 请求方式

POST／GET

# 请求参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string\(32\) | 是 | xxxxxxxx | 令牌 |
| dType | string | 是 | json/csv | 数据类型 |
| userName | string | 是 | bonree | 用户名 |
| params | string | 是 |  | 参数json |

### params参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json/csv | 数据类型 |
| sdkAppId | string | 是 | "1111,2222" | 应用id |
| dTime | string | 是 | 20160101000000-20160102000000 | 数据时间范围\(时间最长一个月\) |
| pageNum | int | 是 | 1 | 页码 |
| pageRecorders | int | 是 | 50 | 每页条数 |
| filters | string | 否 |  | 数据筛选条件 |
| dHeader | string | 是 |  | 指标数据项 |
| orderFlag | string | 否 | sdkAppId | 排序依据 |
| groupfield | string | 是 | "sdkAppId,stackInfoCode" | 数据组合条件 |

### filters参数

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| osVersion | string | "osId":\["1111"\] | 操作系统 |
| brandName | string | "brandId":\["1111"\] | 设备型号 |
| crashType | string | "crashType":\["111"\] | 崩溃类型Code |

### dHeader参数

| 参数名称 | 参数类型 | 是否必选 | 返回示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| sdkAppId | string | 否 | 1111 | sdk应用id |
| minMonitorTime | string | 否 | 201601010000 | 首次发生时间 |
| maxMonitorTime | string | 否 | 201601020000 | 末次发生时间 |
| crashCount | string | 否 | 200 | 崩溃次数 |
| crashRate | string | 否 | 0.01 | 崩溃率 |
| startCount | string | 否 | 100 | sdk应用启动次数 |
| userCount | string | 否 | 100 | 崩溃影响用户数 |
| crashType | string | 否 | NullPoinerException | 崩溃类型 |
| keyFunction | string | 否 |  | 关键方法 |
| causeBy | string | 否 |  | causeby |

### groupField参数

| 参数名称 | 参数说明 |
| :--- | :--- |
| sdkAppId | sdk应用id |
| crashType | 崩溃类型 |
| stackInfoCode | 崩溃堆栈code |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```java
HttpClient httpclient = new DefaultHttpClient();
String url = "https://api.bonree.com/sdk/report/data/crash/detail";
String params = "{\"dType\":\"json\",\"sdkAppId\":[1111,2222],\"dTime\":\"20160101000000-20160102000000\",\"pageNum\":1,\"pageRecorders\":50,\"dHeader\":[\"sdkAppId\",\"osId\",\"brandId\",\"minMonitorTime\",\"maxMonitorTime\",\"crashCount\",\"crashRate\"],\"filter\":{\"osId\":[\"1111\"],\"brandId\":[\"1111\"]},\"orderFlag\":[\"appId\"],\"groupfield\":[\"appId\",\"stackInfoCode\"]}}";

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
              ["appId","osId","brandId",“appName”,”minMonitorTime”,”maxMonitorTime”,”crashCount”,”crashRate”,”userCount”],
              ["1111","1111","1111"“app1”,”20161100000100”,”20161101000100”,”100”,”0.01”,“1”]
]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



