# 业务编号

browser.data.js.error.statdata

# api请求地址

[http://api.bonree.com/browser/data/js/error/statdata](http://api.bonree.com/browser/data/js/error/statdata)

# 请求参数：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string | 是 | xxxxxxxxxxxxx | 令牌 |
| params | string | 是 | {"dtype":"json","appId":"1035,1036,1037"} | 参数json |

**params说明：**

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json | 数据类型\(csv、json\) |
| appId | string | 是 | 1035,1036,1037 | 应用ID |
| dTime | string | 是 | 20170428000000-20170429000000 | 时间范围 |
| group | string | 否 | APP\_ID | 为空时APP\_ID返回0 |
| dHeader | string | 是 | APP\_ID,ERROR\_TATE,ERROR\_NUM, | 指标数据项 |

# dHeader字段说明：

| 字段 | 名称 |
| :--- | :--- |
| APP\_ID | 应用ID |
| ERROR\_TATE | 错误率 |
| ERROR\_NUM | 发生js错误的页面次数 |
| TOTAL\_NUM | 总的页面次数 |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
    HttpClient httpclient = new DefaultHttpClient();
    String url = "http://api.bonree.com/apm/app/infodata";
    HttpPost httppost = new HttpPost(url);
    System.out.println("请求: " + httppost.getRequestLine());
    // 创建参数队列
    List<NameValuePair> formparams = new ArrayList<NameValuePair>();
    formparams.add(new BasicNameValuePair("username", "bonreetest"));
    formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
    formparams.add(new BasicNameValuePair("params", "{xxx}"));
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
    "errorCode": 0,
    "reason": "查询成功",
    "result": [
        ["APP_ID","ERROR_RATE","ERROR_NUM","TOTAL_NUM"],
        ["1035","0.2","20","100"],
        ["1036","0.2","20","100"],
        ["1037","0.2","20","100"]
    ]
}
```



