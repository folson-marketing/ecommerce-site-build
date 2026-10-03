# 各平台路线

G0 确定框架后读对应的一节。

## Shopify

### 开工前

- **先确认 Shopify 连接器已连上。** 没连就用连接器搜索 / 推荐工具提示用户连接；没有这类工具就直接告诉用户要装 Shopify 连接器（或 MCP）。说明需要的权限：读写产品、主题（`write_themes`）、内容（页面 / 博客）、文件、metafield / metaobject。
- **提前告诉用户哪些事 API 做不了、要他自己点**（以下是实际踩过的）：
  - 发布主题（也不要直接写正在发布的 MAIN 主题，先复制一份草稿主题）
  - 打开或关闭 app 嵌入（app embeds）、各 app 自己后台的设置
  - Customer Events 自定义像素（Agent 写代码，用户粘贴）
  - 法律政策页（缺 `write_legal_policies` 权限时）
  - 删除主题文件、登录后台（需要浏览器时由用户自己登录，Agent 不输入密码）
  - Search & Discovery 里的筛选器设置

### 实操备忘

- 主题文件用 Admin GraphQL `themeFilesUpsert` 写入；大文件先 `stagedUploadsCreate` 再引用。**只写复制出来的草稿主题。**
- 产品、metafield、metaobject 等数据操作按 **schema → validate → execute** 的顺序；大批量导出用 `bulkOperationRunQuery`。
- 改模板前先列出所有 app embed 和 app block，迁移后逐个确认还在。
- 主题自带的 `.rte a` 等链接样式会覆盖自定义组件，新组件的样式要提高优先级或单独命名空间。
- 博客、页面、产品描述里的联系邮箱、包邮门槛等全站信息，改一处要全站搜一遍。
- 预览链接格式：`https://<店铺域名>/?preview_theme_id=<主题 ID>`。
- 从复制主题到发布期间，对线上主题的改动会在发布后丢失，提醒用户这段时间别动线上主题。

## 纯 HTML / 其他框架（Next.js 等）

- **部署在哪**：Vercel / Netlify / GitHub Pages / 自有服务器；代码仓库在哪。改动先上 staging / 预览地址，生产发布由用户确认。
- **购物车和结账怎么解决**：静态站本身没有购物车，要选 Shopify Buy Button / Stripe Payment Links / Snipcart 等。这会影响页面设计，必须在 G0 先定。
- **表单、邮件订阅、统计代码**用什么服务（Formspree、Klaviyo、Mailchimp、GA4 等），G0 一并确认。

## WordPress / WooCommerce

- 用子主题和 staging 站点，不直接改线上。
- 改之前备份数据库和 `wp-content`；插件更新也在 staging 先试。

## Shopline、Shoplazza 等 SaaS 平台

- 先查平台有没有开放 API / MCP，以及主题能不能复制成草稿预览。
- 没有 API 的部分走浏览器（用户自己登录）或后台批量导入（CSV），同样遵守"先备份、改后回读"。
- 和 Shopify 一样，提前列出哪些事只能用户在后台手动做。
