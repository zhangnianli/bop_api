# 业务编号

apm.data.healthdata

# api请求地址

[http://api.bonree.com/apm/data/healthdata](http://api.bonree.com/apm/ma/healthdata)

# 请求参数：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string | 是 | xxxxxxxxxxxxx | 令牌 |
| params | string | 是 | {"dtype":"json","appId":"1035","dtime":"20170201000000-20170301000000"} | 参数json |

**params说明：**

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json | 数据类型\(csv、json\) |
| beAppId | string | 是 | 1035,1023,2023 | 后端应用ID |
| dTime | string | 是 | 20170201000000-20170301000000 | 查询时间范围 |
| dHeader | string | 是 | BE\_APP\_ID,TOTAL\_MA,ERROR\_MA,TOTAL\_VM,ERROR\_VM | 指标数据项 |

# dHeader字段说明：

| 字段 | 名称 |
| :--- | :--- |
| BE\_APP\_ID | 应用ID |
| TOTAL\_MA | 主机总数 |
| ERROR\_MA | 不健康主机数 |
| TOTAL\_VM | 容器总数 |
| ERROR\_VM | 不健康容器数 |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
    HttpClient httpclient = new DefaultHttpClient();
    String url = "http://api.bonree.com/apm/backendcall/statdata";
    HttpPost httppost = new HttpPost(url);
    System.out.println("请求: " + httppost.getRequestLine());
    // 创建参数队列
    List<NameValuePair> formparams = new ArrayList<NameValuePair>();
    formparams.add(new BasicNameValuePair("username", "bonreetest"));
    formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
    formparams.add(new BasicNameValuePair("params", "{\"dType\":\"json\",\"beAppId\":\"1035,1023,2023\",\"dTime\":\"20170201000000-20170301000000\",\"dHeader\":\"BE_APP_ID,TOTAL_MA,ERROR_MA,TOTAL_VM,ERROR_VM\"}"));
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
        ["BE_APP_ID","TOTAL_MA","ERROR_MA","TOTAL_VM","ERROR_VM"],
        ["1035", "100", "5", "100", "8"]
    }]
}
```



