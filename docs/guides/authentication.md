# 认证指南

## 认证概述

博物馆云平台API使用基于Token的认证机制，所有的API请求都需要包含有效的访问令牌（Access Token）。

## 获取访问令牌

1. 登录博物馆云平台管理后台
2. 进入API密钥管理页面
3. 创建新的API密钥
4. 保存生成的Access Token（请注意安全保管，该Token只显示一次）

## 使用访问令牌

在发起API请求时，需要在HTTP Header中添加Authorization头：

```http
Authorization: Bearer your_access_token
```

### 示例

使用curl：
```bash
curl -X GET \
  'https://api.museum-cloud.com/v1/exhibits' \
  -H 'Authorization: Bearer your_access_token'
```

使用Python requests：
```python
import requests

headers = {
    'Authorization': 'Bearer your_access_token'
}

response = requests.get('https://api.museum-cloud.com/v1/exhibits', headers=headers)
```

## Token有效期

- Access Token的有效期为30天
- Token过期后需要重新获取
- 建议在Token过期前进行更新

## 安全建议

1. 妥善保管Access Token，不要泄露给他人
2. 不要在客户端代码中硬编码Token
3. 定期轮换Token以提高安全性
4. 在检测到安全问题时及时禁用Token

## 常见问题

### 1. Token无效

如果收到401错误响应，可能的原因：
- Token已过期
- Token格式不正确
- Token已被禁用

### 2. Token权限不足

如果收到403错误响应，说明当前Token没有访问该API的权限。

## 相关资源

- [快速开始](./quick-start.md)
- [API示例](../examples/api-examples.md)
- [最佳实践](./best-practices.md)