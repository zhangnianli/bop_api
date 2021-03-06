# 业务编号

sdk.version.find

# api请求地址

[http://api.bonree.com/sdk/version/find](http://api.bonree.com/sdk/report/task/find)

[https://api.bonree.com/sdk/version/find](https://api.bonree.com/sdk/report/task/find)

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
| dType | string | 是 | json | 数据类型 |
| filters | string | 否 | "filters":{"TASK\_VERSION\_ID":\["59015"\]} | 数据筛选条件 |
| dHeader | string | 是 | "dHeader":"SDK\_VERSION" | 指标数据项 |

### filters参数

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| TASK\_VERSION\_ID | string | "TASK\_VERSION\_ID":\["59015"\] | sdk应用版本ID |

### dHeader参数

| 参数名称 | 参数类型 | 是否必选 | 参数说明 |
| :--- | :--- | :--- | :--- |
| TASK\_VERSION\_ID | string | 否 | sdk应用版本ID |
| SDK\_VERSION | string | 否 | sdk版本 |
| TASK\_VERSION\_NAME | string | 否 | sdk应用版本名称 |

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
String url = "http://api.bonree.com/sdk/version/find";
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
        ["username","appName","appId"],
        ["bonree","bonreeApp","1111"],
    ]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



