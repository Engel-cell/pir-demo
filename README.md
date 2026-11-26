# PIR Demo — Static Preview

This is a static product preview using fictional demo data.
It does not provide live information collection, real user accounts, AI services, or backend synchronization.

---

## 这是什么

Personal Information Radar（PIR）的**静态界面预览版**，用于向受邀同学展示产品形态与交互设计。

- **全部数据为虚构演示数据**：所有信息标题均带 `【演示】` 前缀，来源链接仅指向 `example.com` 保留示例域名。
- **不连接任何后端**：没有服务器、没有数据库、没有真实账号、没有真实 AI 调用、没有 RSS 采集。
- **不是正式产品**：这不是 PIR 的正式上线版本，不提供任何真实信息服务。

## 目录结构

```text
.
├── README.md                 # 本文件（说明，不参与站点发布）
├── .github/workflows/
│   └── deploy-pages.yml      # 只发布 site/ 的 Pages 工作流（手动触发）
└── site/                     # 已审计的静态构建产物（发布内容）
    ├── index.html
    └── assets/*.js, *.css
```

本仓库**只包含构建产物**，不包含 PIR 的源代码、服务端、数据库、配置或任何密钥。

## 本地预览

```bash
# 任选其一
npx serve site
python3 -m http.server 8080 --directory site
```

因为资源路径以 `/pir-demo/` 为前缀（对应 GitHub Pages 的项目子路径），**直接双击 `index.html` 打开会 404**；本地预览请把 `site/` 挂到 `/pir-demo/` 路径下，例如：

```bash
mkdir -p /tmp/pv && ln -sfn "$PWD/site" /tmp/pv/pir-demo
python3 -m http.server 8080 --directory /tmp/pv
# 访问 http://localhost:8080/pir-demo/
```

## 发布方式

GitHub Pages（Source: GitHub Actions）。工作流仅允许手动触发（`workflow_dispatch`），不会因 push 自动发布。

## 已知边界

- 单页应用，无 URL 路由：刷新任意页面都回到首页（不会 404，但也不保留"当前在哪个详情页"）。
- 演示数据中的"AI 分析结果"为预置文本，标注了"演示数据，非实时 AI 分析结果"。
- 数据保存在浏览器内存中；刷新后演示数据恢复初始状态。
