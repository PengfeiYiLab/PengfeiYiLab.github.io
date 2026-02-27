# 博客操作手册（Hexo）

这份手册覆盖你日常需要的操作：

- 新增/发布/修改/删除文章
- 在文章中插入 PNG 与 draw.io 图
- 调整分类与标签
- 本地预览与线上发布检查

## 1. 一次性准备

```bash
npm ci
```

## 2. 本地预览（重点）

日常只看效果，执行这一条就够了：

```bash
npm run server
```

默认地址：`http://localhost:4000`

预览草稿（包含 `source/_drafts/`）：

```bash
npx hexo server --draft
```

发布前做一次构建检查（和线上构建一致）：

```bash
npm run build
```

停止预览：在终端按 `Ctrl + C`。

## 3. 新增文章

```bash
npm run new "文章标题"
```

会在 `source/_posts/` 下生成一个 Markdown 文件。

推荐 Front Matter：

```md
---
title: 文章标题
date: 2026-02-27 10:00:00
tags:
  - Tech
categories:
  - Engineering
---
```

## 4. 草稿 -> 发布（可选）

创建草稿：

```bash
npm run new -- draft "草稿标题"
```

预览草稿：

```bash
npx hexo server --draft
```

发布草稿（从 `source/_drafts/` 移到 `source/_posts/`）：

```bash
npx hexo publish "草稿标题"
```

## 5. 修改文章

1. 编辑 `source/_posts/` 里的目标文件
2. 本地预览确认（`npm run server`）
3. 提交并推送

## 6. 删除文章

```bash
rm source/_posts/你的文章文件.md
```

然后提交并推送即可。

## 7. 插入 PNG/JPG/SVG 图片

建议存放路径：

`source/images/<主题>/your-image.png`

Markdown 引用方式：

```md
![示意图](/images/主题/your-image.png)
```

## 8. 插入 draw.io 图

推荐流程：

1. 保留可编辑源文件（便于后续维护）
   - `drawio/xxx.drawio`
2. 在 draw.io 中导出为 `PNG` 或 `SVG`
3. 导出文件放到 `source/images/...`
4. 在文章里引用

```md
![架构图](/images/architecture/agent-flow.svg)
```

如果你还想让读者下载原始 `.drawio` 文件：

1. 放到 `source/files/xxx.drawio`
2. 在文章里加链接

```md
[下载 draw.io 源文件](/files/xxx.drawio)
```

## 9. 分类与标签

在文章 Front Matter 中设置：

```md
---
tags:
  - AI
  - Agent
categories:
  - Architecture
---
```

如果你想有独立的分类/标签页面（可选）：

```bash
npx hexo new page categories
npx hexo new page tags
```

编辑 `source/categories/index.md`：

```md
---
title: categories
date: 2026-02-27 10:00:00
type: categories
---
```

编辑 `source/tags/index.md`：

```md
---
title: tags
date: 2026-02-27 10:00:00
type: tags
---
```

## 10. 预览与发布

本地预览：

```bash
npm run server
```

构建检查（与线上部署一致）：

```bash
npm run build
```

发布到公网：

```bash
git add .
git commit -m "update blog"
git push
```

推送到 `main` 后，GitHub Actions 会自动部署到：

`https://pengfeiyilab.github.io`

## 11. 查看线上部署状态

1. 打开仓库 `Actions`
2. 找到 `Deploy Hexo to GitHub Pages`
3. 看最新一次是否为绿色成功

## 12. 常用命令速查

```bash
# 新建文章
npm run new "post-title"

# 新建草稿
npm run new -- draft "draft-title"

# 本地预览（不含草稿）
npm run server

# 本地预览（含草稿）
npx hexo server --draft

# 构建静态文件到 public/
npm run build
```
