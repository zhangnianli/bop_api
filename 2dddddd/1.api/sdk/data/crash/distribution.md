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
| username | string | 是 | bonree | 用户名 |
| params | string | 是 |  | 参数json |

### params参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| taskId | string | 是 | "taskId":"10240,10240" | 应用id |
| dType | string | 是 | json/csv | 返回的数据类型 |
| dTime | string | 是 | "dTime":"20160101000000-20160102000000" | 数据时间范围\(时间最长一个月\) |
| filters | string | 否 | "filters":{"CRASH\_TYPE":\["NullPointerException"\]} | 数据筛选条件 |
| dHeader | string | 是 | "dHeader":"TASK\_ID,CRASH\_TYPE" | 指标数据项 |
| group | string | 是 | "group":"TASK\_ID,CRASH\_TYPE" | 分组条件 |
| order | string | 是 | "order":"CRASH\_COUNT ASC" | 排序条件 |
| top | int | 是 | "top":10 | 指标数量筛选 |

### filters参数

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| CRASH\_TYPE | string |  | 崩溃类型 |
| OS\_VERSION | string |  | 操作系统版本 |
| BRAND\_NAME | string |  | 设备型号 |

### dHeader参数

| 参数名称 | 参数类型 | 是否必选 | 参数说明 |
| :--- | :--- | :--- | :--- |
| TASK\_ID | int | 否 | sdk应用id |
| TASK\_VERSION\_ID | int | 否 | sdk应用版本 |
| CRASH\_TYPE | string | 否 | 崩溃类型 |
| OS\_VERSION | string | 否 | 操作系统 |
| BRAND\_NAME | string | 否 | 设备型号 |
| CRASH\_COUNT | int | 否 | 崩溃次数 |
| CRASH\_RATE | double | 否 | 崩溃率 |
| START\_COUNT | int | 否 | sdk启动次数 |
| USER\_COUNT | int | 否 | 影响用户数 |

### group参数

| 参数名称 | 参数说明 |
| :--- | :--- |
| TASK\_ID | sdk应用id |
| TASK\_VERSION\_ID | sdk应用版本id |
| CRASH\_TYPE | 崩溃类型 |
| OS\_VERSION | 操作系统 |
| BRAND\_NAME | 设备型号 |

### order参数

| 参数名称 | 参数说明 |
| :--- | :--- |
| CRASH\_RATE | 崩溃率 |
| CRASH\_COUNT | 崩溃次数 |

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



