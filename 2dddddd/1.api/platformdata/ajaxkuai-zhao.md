# 业务编号

platform.data.snapshots.data

# api请求地址

[https://api.bonree.com/platform/data/snapshots/data](https://api.bonree.com/platform/data/snapshots/data)

# 请求方式

POST／GET

# 请求参数

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string（32） | 是 | xxx | 令牌 |
| params | string | 是 | {“type”:2,"taskId":123456} | 请求参数 |

params说明：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| rowkeys | string | 是 | 1492081200:6d6f0839-4700-4482-4856-68e32d8b4cec,1492081201:6d6f0839-4700-4482-4856-68e32d8b4cec | ajax快照的rowkey,多个用逗号分隔 |
| dType | string | 是 | json/csv | 返回数据格式 |

field列表：

| 字段英文名称 | 字段中文名称 | 字段描述 |
| :--- | :--- | :--- |
| ROWKEY | 请求的rowkey | 请求条件里面的rowkey |
| RESULT | 结果 | 快照是否存在 0-不存在;1-存在 |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | int | 错误码，0表示成功查询 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
        HttpClient httpclient = new DefaultHttpClient();
        String url = "https://api.bonree.com/platform/data/snapshots/data";
        HttpPost httppost = new HttpPost(url);
        System.out.println("请求: " + httppost.getRequestLine());
        // 创建参数队列
        List<NameValuePair> formparams = new ArrayList<NameValuePair>();
        formparams.add(new BasicNameValuePair("username", "bonreetest"));
        formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
        formparams.add(new BasicNameValuePair("params", "{\"token\":\"*******\",\"dType\":\"json\",\"rowkeys\":\"1492081200:6d6f0839-4700-4482-4856-68e32d8b4cec\"}"));
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

# 返回结果示例

```
{
    "errorCode": 0,
    "reason": "查询成功",
    "result": [
        [ROWKEY,"RESULT"],
        ["1492081200:6d6f0839-4700-4482-4856-68e32d8b4cec", 0]
    ]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



