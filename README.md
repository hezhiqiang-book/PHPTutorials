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


- php封装通信数据标准格式

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
