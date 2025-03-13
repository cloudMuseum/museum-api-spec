# API文档贡献指南

本指南将帮助您了解如何参与博物馆云平台API文档的编写和维护工作。

## 环境配置

1. 克隆仓库
```bash
git clone <repository_url>
cd museum-api-spec
```

2. 安装依赖
```bash
npm install -g @redocly/cli
```

## 文档结构

```
├── openapi.yaml     # OpenAPI主规范文件
├── docs/            # 补充文档
│   ├── guides/      # 使用指南
│   └── examples/    # 示例代码
└── schemas/         # 数据模型定义
```

## OpenAPI规范编写指南

### 基本规则

1. 使用YAML格式编写，保持良好的缩进
2. 遵循OpenAPI 3.0.3规范
3. 所有描述性文本使用中文编写
4. 代码示例应当简洁清晰

### 命名规范

1. 路径命名：使用kebab-case，例如：`/user-profiles`
2. 参数命名：使用camelCase，例如：`userId`
3. 模型命名：使用PascalCase，例如：`UserProfile`

### 文档注释

1. 每个API端点必须包含：
   - summary：简短描述
   - description：详细说明
   - parameters：参数说明
   - responses：返回值说明

2. 示例：
```yaml
/users/{id}:
  get:
    summary: 获取用户信息
    description: 根据用户ID获取详细的用户信息
    parameters:
      - name: id
        in: path
        required: true
        description: 用户ID
        schema:
          type: string
```

## 本地预览

1. 启动文档服务器
```bash
npx --yes @redocly/cli preview-docs openapi.yaml
```

2. 访问 http://localhost:8080 预览文档

## 提交流程

1. 创建分支
```bash
git checkout -b feature/update-api-docs
```

2. 修改文档
   - 更新openapi.yaml
   - 添加或修改指南文档
   - 更新示例代码

3. 提交变更
```bash
git add .
git commit -m "docs: 更新API文档"
```

4. 推送分支
```bash
git push origin feature/update-api-docs
```

5. 创建Pull Request
   - 填写清晰的PR描述
   - 说明修改内容和原因
   - 等待review和合并

## 文档质量检查

提交前请确保：

1. 文档格式正确，无语法错误
2. 描述清晰，用语准确
3. 示例代码可运行
4. 所有链接可访问
5. 本地预览正常

## 获取帮助

如果您在编写文档时遇到问题，可以：

1. 查看OpenAPI官方文档
2. 参考现有的API文档示例
3. 通过Issue提出问题

## 最佳实践

1. 保持文档的一致性
2. 定期更新文档
3. 添加详细的示例
4. 及时响应文档相关的Issue和PR
5. 遵循语义化版本控制