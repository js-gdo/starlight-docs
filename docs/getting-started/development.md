# 本地开发

## 环境要求

- Node.js 和 npm
- 一个可用的 Cloudflare 账号（部署时需要）
- Git

## 安装依赖

```bash
git clone https://github.com/js-gdo/starlight.git
cd starlight
npm install
```

## 启动开发服务器

```bash
npm run dev
```

`npm run start` 使用同一个 Wrangler 开发入口，也可以作为启动命令使用。默认情况下，Wrangler 会在本地提供访问地址；终端输出的地址才是当前端口的准确信息。

## 常用命令

| 命令 | 用途 |
| --- | --- |
| `npm run dev` | 启动 Wrangler 本地开发服务器 |
| `npm run start` | 启动开发服务器的别名 |
| `npm run build` | 用 esbuild 构建 Worker |
| `npm test` | 运行 Vitest 测试 |
| `npm run cf-typegen` | 根据 Cloudflare 配置生成类型定义 |
| `npm run deploy` | 使用 Wrangler 部署到 Cloudflare |

## 修改代码后的建议流程

1. 在 `src/routes` 或 `src/handlers` 中修改对应功能。
2. 使用 `npm run build` 验证构建。
3. 使用 `npm test` 运行测试。
4. 部署前检查 `wrangler.jsonc` 中的 Worker 名称和 D1 绑定。

!!! warning "不要提交本地状态文件"
    账号凭据、`.dev.vars` 以及本地生成的部署状态不应提交到 Git。需要的变量应通过 Wrangler 的本地或 Cloudflare 环境配置提供。