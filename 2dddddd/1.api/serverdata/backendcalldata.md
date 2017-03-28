# 业务编号

apm.data.backendcall.statdata

# api请求地址

[http://api.bonree.com/apm/data/backendcall/statdata](http://api.bonree.com/apm/backendcall/statdata)

# 请求参数：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string | 是 | xxxxxxxxxxxxx | 令牌 |
| params | string | 是 | {"dtype":"json","appId":"1035","dtime":"20170201000000-20170301000000"} | 参数json |

**params说明：**

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dtype | string | 是 | json | 数据类型\(csv、json\) |
| beAppId | string | 是 | 1035,1023,2023 | 后端应用ID |
| dtime | string | 是 | 20170201000000-20170301000000 | 查询时间范围 |
| betype | string | 否 | sql | 查询后端类型\(sql,rpc,nosql\) |
| dHeader | string | 是 | beAppId,backendId,backendName,clusterId,totalCalls,errorCalls,sumRespTime,sampleCount | 指标数据项 |

# dHeader字段说明：

| 字段 | 名称 |
| :--- | :--- |
| beAppId | 应用ID |
| backendId | 后端ID |
| backendName | 后端名称 |
| backendType | 后端类型（sql/rpc/nosql） |
| clusterId | 集群ID |
| totalCalls | 总调用数 |
| errorCalls | 错误调用数 |
| sumRespTime | 总耗时 |
| sampleCount | 样本数 |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码 |
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
    formparams.add(new BasicNameValuePair("params", "{\"dtype\":\"json\",\"beAppId\":\"1035,1023,2023\",\"dtime\":\"20170201000000-20170301000000\",\"dHeader\":\"beAppId,backendId,backendName,clusterId,totalCalls,errorCalls,sumRespTime,sampleCount\"}"));
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
        ["beAppId","backendId","backendName","clusterId","totalCalls","errorCalls","sumRespTime","sampleCount"],
        ["1035", "661208", "xxx", "101", "1021", "10","929","7"],
        ["1023", "661208", "xxx", "102", "2021", "20","930","7"],
        ["2023", "661208", "xxx", "103", "2021", "30","940","8"]
    ]
}
```



