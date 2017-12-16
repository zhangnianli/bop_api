# 业务编号

sdk.data.crash.count

# api请求地址

[http://api.bonree.com/sdk/data/crash/count](http://api.bonree.com/sdk/report/data/crash/distribution)

[https://api.bonree.com/sdk/data/crash/count](https://api.bonree.com/sdk/report/data/crash/distribution)

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
| taskId | string | 是 | "taskId":"10240,10241" | 应用id |
| dType | String | 是 | json/csv | 返回的数据类型 |
| dTime | string | 是 | "dTime":"20160101000000-20160102000000" | 数据时间范围 |
| filters | string | 否 | "filters":{"OS\_VERSION":\["android"\]} | 数据筛选条件 |
| dHeader | string | 是 | "dHeader":"TASK\_ID,CRASH\_RATE" | 指标数据项 |
| order | string | 否 | "order":"TASK\_ID DESC, CRASH\_TYPE ASC" | 排序依据 |
| group | string | 否 | "group":"TASK\_ID,CRASH\_TYPE" | 数据组合条件 |

### filters参数

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| OS\_VERSION | string | "OS\_VERSION":\["android","ios"\] | 操作系统id |
| BRAND\_NAME | string | "BRAND\_NAME":\["MI 2S","iphone"\] | 设备型号id |
| CRASH\_TYPE | string | "CRASH\_TYPE":\["NullPointerException","Exception"\] | 崩溃类型 |

### dHeaderℴ参数

| 参数名称 | 参数类型 | 是否必选 | 参数说明 |
| :--- | :--- | :--- | :--- |
| TASK\_ID | string | 否 | sdk应用id |
| MIN\_MONITORTIME | string | 否 | 首次发生时间 |
| MAX\_MONITORTIME | string | 否 | 末次发生时间 |
| CRASH\_COUNT | string | 否 | 崩溃次数 |
| CRASH\_RATE | string | 否 | 崩溃率 |
| START\_COUNT | string | 否 | sdk应用启动次数 |
| USER\_COUNT | string | 否 | 崩溃影响用户数 |
| CRASH\_TYPE | string | 否 | 崩溃类型 |

### group参数

| 参数名称 | 参数说明 |
| :--- | :--- |
| TASK\_ID | sdk应用id |
| CRASH\_TYPE | 崩溃类型 |

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
String url = "https://api.bonree.com/sdk/report/data/crash/count";
String params = "{\"dType\":\"json\",\"sdkAppId\":[1111,2222],\"dTime\":\"20160101000000-20160102000000\",\"dHeader\":[\"osId\",\"osVersion\",\"brandName\",\"brandId\"],\"filter\":{\"osId\":[\"1111\"],\"brandId\":[\"1111\"]},\"orderFlag\":[\"appId\"],\"groupfield\":[\"appId\",\"stackInfoCode\"]}}";

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



