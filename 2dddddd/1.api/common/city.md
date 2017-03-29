# 业务编号

base.data.city

# api请求地址

[http://api.bonree.com/base/data/city](http://api.bonree.com/base/city)

# 请求参数：

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string | 是 | xxxxxxxxxxxxx | 令牌 |
| params | string | 是 | {"lastModif":"20170201000000"} | 参数json |

# **params说明：**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| lastModif | string |  | 20170201000000 | 最后修改时间 |
| dHeader | String | 是 | CITYCODE,CITY,LASTMODIF | 接口返回字段,配置\*返回全部 |

# result说明

| 名称 | 类型 | 示例值 | 描述 |
| :--- | :--- | :--- | :--- |
| CITYCODE | Number | 1100101 | 城市编码 |
| CONT | string | 亚洲 | 洲 |
| COUNTRY | string | 中国 | 国家 |
| DISTRICT | string | 北京 | 地区 |
| CITY | string | 北京市 | 城市 |
| CITYEN | string | Beijing | 城市英文 |
| LASTMODIF | Number | 1446307200000 | 最后修改时间 |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
    HttpClient httpclient = new DefaultHttpClient();
    String url = "http://api.bonree.com/base/data/city";
    HttpPost httppost = new HttpPost(url);
    System.out.println("请求: " + httppost.getRequestLine());
    // 创建参数队列
    List<NameValuePair> formparams = new ArrayList<NameValuePair>();
    formparams.add(new BasicNameValuePair("username", "bonreetest"));
    formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
    formparams.add(new BasicNameValuePair("params", "{\"lastModif\":\"20170202000000\"}"));
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
        ["citycode","cont","country","district","city","cityEn","lastModif"],
        ["1100101","亚洲","中国","北京","北京市","Beijing","20170201000000"],
        ["1100705","亚洲","中国","广西","北海市","Beihai","20170201000000"]
    ]
}
```



