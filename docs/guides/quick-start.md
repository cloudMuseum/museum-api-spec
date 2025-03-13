# 快速开始

## 简介

本指南将帮助您快速上手博物馆云平台API的使用。我们将介绍如何进行API认证、发起请求以及处理响应。

## 前置条件

在开始使用API之前，您需要：

1. 获取API访问凭证（Access Token）
2. 熟悉HTTP请求的基本概念
3. 准备好API调试工具（如Postman、cURL等）

## API文档使用

### 本地预览

1. 安装依赖
```bash
npm install -g @redocly/cli
```

2. 启动文档服务器
```bash
npx --yes @redocly/cli preview-docs openapi.yaml
```

### 在线文档

您可以通过GitHub Pages访问在线API文档：[博物馆云平台API文档](https://your-organization.github.io/museum-api-spec)

## 认证方式

所有API请求都需要在HTTP Header中包含认证信息：

```http
Authorization: Bearer your_access_token
```

## 请求示例

这里是一个使用curl发起API请求的示例：

```bash
curl -X GET \
  'https://api.museum-cloud.com/v1/exhibits' \
  -H 'Authorization: Bearer your_access_token'
```

## 响应格式

API响应采用JSON格式，一个成功的响应示例：

```json
{
  "code": 0,
  "message": "success",
  "data": {
    "items": [],
    "total": 0
  }
}
```

## 错误处理

当API请求失败时，您将收到一个包含错误信息的JSON响应：

```json
{
  "code": 400,
  "message": "Invalid parameters",
  "errors": [
    {
      "field": "name",
      "message": "名称不能为空"
    }
  ]
}
```

## 下一步

- 查看[API示例](../examples/api-examples.md)了解更多使用场景
- 参考[最佳实践](./best-practices.md)优化您的API使用
- 阅读[认证指南](./authentication.md)了解更多认证细节