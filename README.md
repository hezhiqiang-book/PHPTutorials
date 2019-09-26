# 接口开发

## 封装通信接口数据方法

### 通信数据标准格式

- code： 自定义状态码(200, 400等)
- message：提示信息（邮箱格式不正确；数据返回成功等）
- data：返回数据

```json
{
  code: 200,
  message: "数据返回成功",
  data: {
    id: 1,
    name: "wovert"
  }
}
```


#### php封装 JSON 数据标准格式

```php
/**
 * @param int $code 自定义状态码
 * @param string $message 提示信息
 * @param array $data 数据
 * @return string
 */
function apiJson($code, $message, $data = array()) {
  if (!is_numeric($code)) {
    return '';
  }
  
  $result = array(
    'code' => $code,
    'message' => $message,
    'data' => $data
  );
  return json_encode($result);
}

$arr = array(
  'id' => 1,
  'name' => 'wovert'
);

apiJson(200, '数据返回成功', $arr);
```

#### PHP 生成XML数据

- 组装字符串

```php
function apiXml() {
  $xml = "<?xml version="1.0" encoding="UTF-8"?>";
  $xml .= "<root>";
  $xml .= "<code>200</200>";
  $xml .= "<message>数据返回成功</message";
  $xml .= "<data>";
  $xml .= "<id>1</id>";
  $xml .= "<name>wovert</name>";
  $xml .= "</data>";
  $xml .= "</root>";
  
  return $xml;
}

apiXml();
```

- 系统类
  - DomDocument
  - XMLWriter
  - SimpeXML

```
