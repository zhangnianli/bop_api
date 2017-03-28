# 业务编号

sdk.data.crash.distribution

# api请求地址

[http://api.bonree.com/sdk/data/crash/distribution](http://api.bonree.com/sdk/report/data/crash/distribution)

[https://api.bonree.com/sdk/data/crash/distribution](https://api.bonree.com/sdk/report/data/crash/distribution)

# 请求方式

POST／GET

# 请求参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string\(32\) | 是 | xxxxxxxx | 令牌 |
| userName | string | 是 | bonree | 用户名 |
| params | string | 是 |  | 参数json |

### params参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json/csv | 数据类型 |
| sdkAppId | string | 是 | 1111,2222 | 应用id |
| dTime | string | 是 | 20160101000000-20160102000000 | 数据时间范围\(时间最长一个月\) |
| filters | string | 否 | {"crashType":\["1111"\]} | 数据筛选条件 |
| dHeader | string | 是 | appId,crashType,crashCount,userCount | 指标数据项 |
| groupField | string | 是 |  | 分组条件 |
| orderFlag | string | 是 |  | 排序条件 |
| hCountFilters | int | 是 | 10 | 指标数量筛选 |

### filters参数

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| crashType | string |  | 崩溃类型 |

### dHeader参数

| 参数名称 | 参数类型 | 是否必选 | 返回示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| sdkAppId | string | 否 | 1111 | sdk应用id |
| sdkAppVs | string | 否 | 1.0.1 | sdk应用版本 |
| crashType | string | 否 | NullPointerException | 崩溃类型 |
| osVersion | string | 否 | ios 9 | 操作系统 |
| brandName | string | 否 | iphone 5s | 设备型号 |
| crashCount | string | 否 | 100 | 崩溃次数 |
| crashRate | string | 否 | 0.01 | 崩溃率 |
| startCount | string | 否 | 1000 | sdk启动次数 |
| userCount | string | 否 | 1000 | 影响用户数 |

### groupfield参数

| 参数名称 | 参数说明 |
| :--- | :--- |
| sdkAppId | sdk应用id |
| sdkAppVs | sdk应用版本id |
| crashType | 崩溃类型 |
| osVersion | 操作系统 |
| brandName | 设备型号 |

### orderFlag参数

| 参数名称 | 参数说明 |
| :--- | :--- |
| crashRate | 崩溃率 |
| crashCount | 崩溃次数 |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```java
    HttpClient httpclient = new DefaultHttpClient();
    String url = "https://api.bonree.com/sdk/report/data/crash/distribution";
    String params = "{\"dType\":\"json\",\"sdkAppId\":[1111,2222],\"dTime\":\"20160101000000-20160102000000\",\"dHeader\":[\"appId\",\"crashTypeCode\",\"crashType\",\"crashCount\",\"userCount\"],\"filter\":{\"crashTypeCode\":[\"1111\"]},\"hCountFilters\":10}";

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
              ["appid",”crashTypeCode”,“crashType”,”crashCount”,”userCount”],
              ["1111",”2111”,“NullPointerException”,”10”,1”],
              ["1111",”2222”,“RunTimeException”,”8”,”1"]
]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



