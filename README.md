# 黑白测评组官网

当前版本：P1 公开网页样刊。技术栈遵循已确认 P0：Next.js / TypeScript / Tailwind；后续接入 Supabase Auth、PostgreSQL、Storage、Cron。

**只看页面：**此前的 P1 源码交付包另附 `preview/index.html`，解压后可直接打开。这是构建导出的只读版；链接可浏览，搜索、筛选、弹窗在只读版停用。GitHub 仓库保存源码；完整交互请按下方步骤运行应用。

## 启动

需要 Node.js 22.13+（已在 Node 24.19 验证依赖安装和构建）。在本项目根目录执行：

```bash
npm ci
npm run dev
```

浏览器打开 `http://localhost:3000/zh`；英文页为 `http://localhost:3000/en`。根路径跳转中文。当前不需要 `.env` 或后端凭据。

生产构建检查及本地运行：

```bash
npm run check
npm test
npm run build
npm run verify:build
npm start
```

`npm start` 只在你自己的环境启动本地服务，不是公开部署。若使用 `.next/standalone/server.js`，须按 Next.js 独立产物要求同时携带 `public/` 与 `.next/static/`；本阶段优先使用上面的标准启动步骤。

## 页面与交互

- `/zh`、`/en`：首页；`/reviews`：搜索、类型、平台、最低评分和三种排序；测评详情包含官方/玩家分离、黑白点和原文语言回退。
- `/news`：分类与详情；`/activities`：招募/抽奖分区、状态筛选、活动详情和脱敏结果示例。
- `/about`、`/business`：理念、团队资料待核实说明、合作形式及案例公开授权说明。
- `/search`：测评、资讯、活动搜索；`/account` 和页脚法律/联系页说明当前可用范围。
- 顶部切换语言保留当前页面路径。稿件缺少英文时显示原中文，并明确提示；文章 ID 不随语言变化。
- 账号、评分、收藏、评论、认证、招募、抽奖与商务提交尚未实现。相关入口只显示未开放说明，不收集信息，不保存成功状态。

## 示例数据与素材

`src/data/demo.ts` 是四款虚构游戏、示例稿件和活动的唯一演示数据源。示例没有真实商业意义，不应直接导入正式数据库。品牌的 100万+ / 2000+ 来自需求文件，页面注明口径待核对且非实时。团队、合作对象和分众组数量不虚构。

`public/images/imagined-worlds.png` 为本项目生成的原创概念拼图，使用 SVG 视窗显示四个场景，保持颜色及比例。不是实际游戏截图。提示词和来源记录见 `docs/ASSETS.md`。

当前无 Supabase 客户端、数据库、云资源、真实邮件、用户资料或第三方分析代码。预览默认 noindex。

## 验收状态

详见 `docs/P1_ACCEPTANCE.md`。构建、纯逻辑与静态 HTML 检查不能替代真实浏览器交互、390px/1440px 视觉、键盘/读屏和部署后验收；未执行的项目必须继续标记待验收。

## 接续开发与版本

先读 `PROGRESS.md`，再读相关代码和 V1 段落。需求源为 `docs/requirements/WORK_HANDOFF_V1.md`；技术决策为 `docs/P0_DECISION.md`。

代码仓库：https://github.com/obedientdem/white-and-black 。本次通过 GitHub 接口导入源码，远程提交记录从导入开始；原始本地历史保存在 `history/P1_HISTORY.bundle`，包含 P0、P1、此前的同步阻塞记录及 `p1-implementation-v1` 标签。

常规开发直接克隆本仓库。如需单独恢复原始历史，在仓库外的新目录执行：

```bash
git clone /absolute/path/to/white-and-black/history/P1_HISTORY.bundle blackwhite-review-original
```

历史文件仅作恢复存档，后续开发继续使用本仓库的 `main`。实际同步验证状态见 `PROGRESS.md`。
