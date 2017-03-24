# 业务编号

net.task.loadTask

# api请求地址

[http://api.bonree.com/net/task/loadTask](http://api.bonree.com/net/task/loadTask)

# 请求方式

POST/GET

# 请求参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string | 是 | \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* | 令牌 |
| username | string | 是 | bonreetest | 用户名 |
| params | string | 是 | {"monitor\_fun":3} | 请求参数json |

## param参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| monitorFun | Number | 是 | 3 | 任务类型0-网络 3-浏览 4-传输 5-流媒体 6-元素组 7-协议 9-事务 96-移动浏览 97-移动网络 98-移动协议 95-BMTP |
| taskId | Number | 否 | 170435 | 任务ID |
| flag | Number | 否 | 1 | 任务状态；0-禁用，1-启用，9-结束 |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | Number | 错误码 |
| reason | string | 结果说明 |
| result | string | 查询结果 |

# 请求示例

```
 POST:
  HttpClient httpclient = new DefaultHttpClient();
  String url = "http://api.bonree.com/net/task/loadTask";
  HttpPost httppost = new HttpPost(url);
  System.out.println("请求: " + httppost.getRequestLine());
  // 创建参数队列
  List<NameValuePair> formparams = new ArrayList<NameValuePair>();
  formparams.add(new BasicNameValuePair("username", "bonreetest"));
  formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
  formparams.add(new BasicNameValuePair("params", "{\"monitor_fun\":3}"));
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

 GET:
  http://api.bonree.com/net/task/loadTask?token=asdas12312312ddwew5we5we5&username=bonreetest&param={"monitor_fun":3}
```

# 返回结果示例

```
{
    "error_code": 0,
    "reason":"查询成功",
    "result: [
        ["roleName","url","taskId","monitorFun","flag","startTime","endTime","parentId","roleType","netenvMon"],
        ["勿删长期测试qq","http://www.qq.com",170435,3,1,1393603200000,1488211200000,340832,9,"111"],
        ["QQ任务组","http://",340832,3,0,1446307200000,1446307200000,0,0,"000"]
    ]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：


