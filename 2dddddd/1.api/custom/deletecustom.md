# ҵ����

custom.create

# api�����ַ

[http://api.bonree.com/custom/create](http://api.bonree.com/custom/create)

# ����ʽ

POST/GET

# �������

| �������� | �������� | �Ƿ��ѡ | ʾ��ֵ | ����˵�� |
| :--- | :--- | :--- | :--- | :--- |
| username | string | �� | myusername | ���� |
| params | string | �� | {"pwd":"abcdabcd"} | params�а�����������������pwdΪmd5 |
| token | string | �� | systoken | ϵͳУ��token |

# ���ز���˵��

| ���� | ���� | ���� |
| :--- | :--- | :--- |
| error\_code | int | ��Ӧ��˵�� |
| reason | string | ����˵�� |
| result | string | ���ؽ���� |

# ����ʵ��

curl [http://api.bonree.com/custom/create](#)?username=inusername&token=abcdabcdabcd&params={'pwd':'mypwdmd5'}

# ���ؽ��ʵ��

```js
{
    "error_code":0,
    "reason":"�����ɹ�",
    "type":"data",
    "result": {
        "username":"bonreetest",
        "v4Token":"42eb62ff35418c03"
    }

}
```

# FAQ



