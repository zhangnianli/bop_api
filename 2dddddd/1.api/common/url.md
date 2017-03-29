# 业务编号

base.data.url

# api请求地址

[http://api.bonree.com/base/data/](http://api.bonree.com/base/city)url

# 请求参数：

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string | 是 | xxxxxxxxxxxxx | 令牌 |
| params | string | 是 | {"lastModif":"20170201000000"} | 参数json |

# **params说明：**

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| urlcode | string | 123456,39285 | urlcode码，多个urlcode以逗号分隔 |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | string | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# result说明

| 名称 | 类型 | 示例值 | 描述 |
| :--- | :--- | :--- | :--- |
| citycode | Number | 1100101 | 城市编码 |
| cont | string | 亚洲 | 洲 |

# 请求示例

```
            httpclient = new DefaultHttpClient();
            String url = "http://192.168.4.137/url";
            HttpPost httppost = new HttpPost(url);
            System.out.println("请求: " + httppost.getRequestLine());
            // 创建参数队列
            List<NameValuePair> formparams = new ArrayList<NameValuePair>();
            formparams.add(new BasicNameValuePair("username", "aaa"));
            formparams.add(new BasicNameValuePair("token", "2CBFC800431FFCB0"));
            JSONObject params = new JSONObject();
            params.put("type", "json");
            params.put("urlcode", "111111,222222");
            System.out.println("params="+params.toString());
            formparams.add(new BasicNameValuePair("params", params.toString()));
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

\`\`\`

\`\`\`

