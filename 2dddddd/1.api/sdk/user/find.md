# 业务编号

sdk.user.find

# api请求地址

[http://api.bonree.com/sdk/user/find](http://api.bonree.com/sdk/report/user/find)

[https://api.bonree.com/sdk/user/find](https://api.bonree.com/sdk/report/user/find)

# 请求方式

POST／GET

# 请求参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string\(32\) | 是 | xxxxxxxx | 令牌 |
| dType | string | 是 | json/csv | 数据类型 |
| username | string | 是 | bonree | 用户名 |
| params | string | 是 |  | 参数json |

### params参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json/csv | 数据类型 |
| userName | string | 否 |  | 用户名 |
| dHeader | string | 是 |  | 指标数据项 |

### filter参数

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| USERNAME | string | "userName":\["admin"\] | 用户名 |

### dHeader参数

| 参数名称 | 参数类型 | 是否必选 | 返回示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| USERNAME | string | 是 | bonree | 用户名 |
| START\_VALID\_TIME | string | 否 | 20160101000000 | 有效期开始时间 |
| END\_VALID\_TIME | string | 否 | 20160102000000 | 有效期结束时间 |
| REMAIN\_DEVICE\_COUNT | string | 否 | 1000 | 剩余活跃设备数 |
| ACTIVE\_DEVICE\_COUNT | string | 否 | 10000 | 活跃设备数 |
| USER\_STATUE | string | 否 | false | 用户状态信息 |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码 |
| reason | string | 返回说明 |
| type | string | 返回数据类型 |
| result | string | 返回结果集 |

# 请求示例

```java
HttpClient httpclient = new DefaultHttpClient();
String url = "http://localhost/HttpsDemo/";
String params = "{\"dType\":\"json\"}";

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
{"error_code": 0,
    "reason":"查询成功",
    "result":[
        ["username","isOpen","validFrom","validTo","availableDeviceCount"],
        ["bonree","true","20160101000000","20170101000000","20000"],
    ]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



