# 项目简介

## StarLight 是什么

StarLight 是面向社区交流的全栈应用。它将页面渲染、业务接口和数据访问集中在 Cloudflare Worker 中，通过 D1 保存应用数据。

项目使用 TypeScript 编写，入口文件为 `src/index.ts`。仓库按职责划分为路由、处理器、数据库初始化、工具函数和多语言资源，适合在 Cloudflare 平台上部署和迭代。

## 主要能力

- 账号注册、登录、个人资料与设置
- 文章发布、编辑、浏览和分享
- 短内容动态、评论、点赞、关注和通知
- 站内私信与消息中心
- 签到、成就、积分兑换和排行榜
- 竞赛、题目浏览、代码提交与评测记录
- 团队创建、成员申请和团队设置
- 工单、举报和后台管理
- 多语言界面资源

## 技术栈

| 层次 | 技术 |
| --- | --- |
| 运行时 | Cloudflare Workers |
| 语言 | TypeScript |
| 数据库 | Cloudflare D1 |
| 构建 | esbuild |
| 测试 | Vitest 与 `@cloudflare/vitest-pool-workers` |
| 本地工具 | Wrangler |

## 仓库结构

```text
src/
  db/          数据库初始化
  handlers/    API 和业务处理器
  routes/      页面路由与 HTML 渲染
  locales/     多语言资源
  utils/       公共工具
  index.ts     Worker 入口
test/          Worker 测试
wrangler.jsonc Cloudflare 配置
```

!!! note
    StarLight 不是内容审核、攻击测试或私人纠纷处理平台。使用社区前请阅读[社区使用边界](../about/starlight-is-not-what.md)及[用户协议](../about/user-agreement.md)。