# 部署到 Cloudflare

## 部署前准备

1. 安装依赖：`npm install`。
2. 登录 Wrangler：

   ```bash
   npx wrangler login
   ```

3. 确认 Cloudflare 账号拥有 Workers 和 D1 权限。
4. 准备一个 D1 数据库，并将其绑定到 Worker 的 `DB` 变量。

## 检查配置

项目的 `wrangler.jsonc` 已声明以下关键项：

```jsonc
{
  "name": "starlight-workers",
  "main": "src/index.ts",
  "d1_databases": [
    {
      "binding": "DB",
      "database_name": "sl-db",
      "database_id": "<your-database-id>"
    }
  ]
}
```

生产环境中请把 `database_id` 换成你自己账号下的 D1 数据库 ID。不要复用不属于自己的数据库，也不要把密钥写进源码。

## 发布 Worker

```bash
npm run build
npm run deploy
```

首次请求时，应用会执行数据库初始化逻辑。部署完成后，使用 Wrangler 输出的 Worker 地址访问首页，并依次检查注册、登录、文章列表和数据库读写。

## 部署后检查

- 首页和登录页能够打开。
- 新用户能够注册并登录。
- 文章创建、编辑和浏览正常。
- D1 中出现应用数据，且 Worker 日志没有异常。
- 管理员功能仅对授权账号开放。

!!! note
    具体域名、路由、D1 迁移策略和生产变量属于部署环境配置，不由文档站统一指定。每次升级前请先查看源码仓库的变更记录。