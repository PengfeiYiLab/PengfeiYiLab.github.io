# PengfeiYiLab Blog

Hexo-based personal blog with GitHub Pages auto deployment.

## Daily writing flow

1. Create a post:

```bash
npm run new "your-title"
```

2. Preview locally:

```bash
npm run server
```

3. Commit and push:

```bash
git add .
git commit -m "new post"
git push
```

GitHub Actions will build and publish automatically.

## Docs

- [Blog workflow guide](docs/blog-workflow.md)

## Content/logic separation

- Content: `source/_posts/` and `source/`
- Site config: `_config.yml`
- CI/CD: `.github/workflows/deploy-pages.yml`
