# 博物馆云平台 API 文档

这是博物馆云平台的API规范文档仓库，使用OpenAPI 3.0.3规范编写。

## 项目结构

```
├── openapi.yaml     # OpenAPI主规范文件
├── docs/            # 补充文档
│   ├── guides/      # 使用指南
│   └── examples/    # 示例代码
└── schemas/         # 数据模型定义
```

## 本地预览

1. 安装依赖
```bash
npm install -g @redocly/cli
```

2. 启动文档服务器
```bash
npx --yes @redocly/cli preview-docs openapi.yaml
```

## API版本控制

我们使用语义化版本控制（Semantic Versioning）来管理API版本：

- 主版本号（MAJOR）：不兼容的API修改
- 次版本号（MINOR）：向下兼容的功能性新增
- 修订号（PATCH）：向下兼容的问题修正

## 集成指南

1. 基础URL
   - 生产环境：https://api.museum-cloud.com/v1
   - 测试环境：https://api-staging.museum-cloud.com/v1

2. 认证
   所有API请求都需要在Header中携带JWT Token：
   ```
   Authorization: Bearer <your_token>
   ```

3. 错误处理
   API使用标准HTTP状态码，并在响应体中提供详细的错误信息：
   ```json
   {
     "code": "INVALID_PARAMETER",
     "message": "展品名称不能为空"
   }
   ```

## 贡献指南

1. Fork本仓库
2. 创建特性分支
3. 提交变更
4. 推送到分支
5. 创建Pull Request

## 自动部署

本仓库配置了GitHub Actions自动部署流程：

- 当代码推送到main/master分支时，自动构建API文档
- 构建完成后自动部署到GitHub Pages
- 可在 `https://<org>.github.io/museum-api-spec` 访问在线文档

## 许可证

本项目采用MIT许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。