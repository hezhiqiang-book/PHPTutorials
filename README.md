# PHPTutorials

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
