# 业务编号

net.user.loadUser

# api请求地址

[http://api.bonree.com/net/user/loadUser](http://api.bonree.com/net/user/loadUser)

# 请求方式

POST/GET

# 请求参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| token | string | 是 | \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* | 令牌 |
| username | string | 是 | bonreetest | 用户名 |
| params | string | 是 | {"username":"bonreetest"} | 请求参数json |

# params参数

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 否 | bonreetest | 查询用户名（请求参数中username为系统用户时，该字段必填） |
| dHeader | String | 是 | USERNAME,MONITOR_COUNT_SET,MONITOR_COUNT_USED | 接口返回字段,配置*返回全部 |

# result说明

| 名称 | 类型 | 示例值 | 描述 |
| :--- | :--- | :--- | :--- |
| USERNAME | string | bonreetest | 用户名 |
| MONITOR_COUNT_SET | Number | 9999999 | 传统互联网监测量权限 |
| MONITOR_COUNT_USED | Number | 238 | 传统互联网已使用监测量 |
| START_DATE | Number | 1420041600000 | 套餐开始时间 |
| END_DATE | Number | 1514736000000 | 套餐结束时间 |
| MOBMONITOR_COUNT_SET | Number | 10000000 | 移动互联网监测量权限 |
| MOBMONITOR_COUNT_USED | Number | 32 | 移动互联网已使用监测量 |
| MONITOR_MODE | Number | 0 | 计费方式0-按监测量 1-按任务 |
| APPHUIFANG_TIME_SET | Number | 60000 | BMTP回放时间权限（单位s） |
| APPHUIFANG_TIME_USED | Number | 56 | BMTP回放时间已使用时长（单位s） |
| APPHUIFANG_FLOW_SET | Number | 1024 | BMTP回放流量权限（单位KB） |
| APPHUIFANG_FLOW_USED | Number | 56 | BMTP已使用回放流量（单位KB） |
| URLNUM_SET | Number | 9999 | 传统互联网配置任务权限 |
| URLNUM_USED | Number | 22 | 传统互联网已配置任务数 |
| APPLUZHI_TIME_SET | Number | 1000 | BMTP录制时长权限 |
| APPMONITOR_COUNT_USED | Number | 67 | BMTP已使用监测量 |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | Number | 错误码 |
| reason | string | 结果说明 |
| result | string | 用户权限信息 |

# 请求示例

```
 POST:
  HttpClient httpclient = new DefaultHttpClient();
  String url = "http://api.bonree.com/net/user/loadUser";
  HttpPost httppost = new HttpPost(url);
  System.out.println("请求: " + httppost.getRequestLine());
  // 创建参数队列
  List<NameValuePair> formparams = new ArrayList<NameValuePair>();
  formparams.add(new BasicNameValuePair("username", "bonreetest"));
  formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
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
  http://api.bonree.com/net/user/loadUser?token=asdas12312312ddwew5we5we5&username=bonreetest
```

# 返回结果示例

```
{
    "error_code": 0,
    "reason":"查询成功",
    "result: [
        ["username","monitorCountSet","monitorCountUsed","startDate","endDate","mobMonitorCountSet","mobMonitorCountUsed","monitorMode","appHuifangTimeSet","appHuifangTimeUsed","appHuifangFlowSet","appHuifangFlowUsed","urlnumSet","urlnumUsed"],
        ["bonreetest",99999999,23,1420041600000,1514736000000,10000000,0,0,60000,0,1024,0,9999,22]
    ]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



