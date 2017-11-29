# 业务编号

browser.data.app.config

# api请求地址

[http://api.bonree.com/browser/data/app/config](http://api.bonree.com/browser/data/app/config)

# 请求参数：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string | 是 | xxxxxxxxxxxxx | 令牌 |
| params | string | 是 | {"dtype":"json","username":"bonreetest"} | 参数json |

**params说明：**

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json | 数据类型\(csv、json\) |
| username | string | 是 | bonreetest | 用户名 |
| dHeader | string | 是 | APP\_ID,APP\_NAME,APP\_GUID | 指标数据项 |

# dHeader字段说明：

| 字段 | 名称 |
| :--- | :--- |
| APP\_ID | 应用ID |
| APP\_NAME | 应用名称 |
| APP\_GUID | 应用GUID |

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
        ["APP_ID","APP_NAME","APP_GUID"],
        ["1035","APP1","3cae7c0c-ad56-4b36-82a4-40ddc6d3513a"],
        ["1036","APP2","3cae7c0c-ad56-4b36-82a4-40ddc6d3513b"],
        ["1037","APP3","3cae7c0c-ad56-4b36-82a4-40ddc6d3513c"]
    ]
}
```



