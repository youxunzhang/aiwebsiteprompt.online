部署到 GitHub Pages（使用自定义域 `www.aishort.top`）

1) 准备
- 确保仓库在 GitHub 上（例如 `youxunzhang/aiwebsiteprompt.online`）。
- 在你的 DNS 提供商处，把 `www` 子域的 CNAME 指向 `youxunzhang.github.io`（或使用 GitHub Pages 指示的地址）。

2) 已包含的文件
- `CNAME` — 内容：`www.aishort.top`，GitHub Pages 将自动识别。
- `.github/workflows/gh-pages.yml` — GitHub Actions workflow：每次 push 到 `main` 时自动把仓库根目录发布到 `gh-pages` 分支。

3) 推送到 GitHub（如果本地尚未关联远程仓库）：
```powershell
cd c:\Users\YOUXUN\Desktop\GITHUB\aiwebsiteprompt.online
git init
git add --all
git commit -m "Initial commit: rebrand to aishort.top and add GH Pages workflow"
git remote add origin https://github.com/<your-username>/aiwebsiteprompt.online.git
git branch -M main
git push -u origin main
```

4) 验证部署
- 在推送后，Actions 会触发，等待 Actions 完成（在 GitHub -> Actions 页面查看）。
- 部署完成后，GitHub Pages 将使用仓库根（published to `gh-pages` branch）并将 `CNAME` 应用为自定义域。
- 在 GitHub 仓库 Settings -> Pages 中确认自定义域是 `www.aishort.top`，并强制启用 HTTPS（如果可用）。

5) DNS 配置（重要）
- 在 DNS 管理面板中，添加 `CNAME` 记录：
  - 主机/名称：`www`
  - 值/目标：`your-github-username.github.io`（例如 `youxunzhang.github.io`）

6) 注意事项
- 如果你希望根域 `aishort.top` 也生效，需要设置 A 记录指向 GitHub Pages 的 IP（参考 GitHub Pages 文档）。
- 若使用 Cloudflare、CDN 或其他中间层，请确保 CNAME 未被代理（即 Cloudflare 的代理应为 "DNS only"）。

需要我替你做什么？
- 我可以帮你把仓库推送到 GitHub（需要你提供 GitHub 仓库 URL 或在本机完成授权）。
- 我可以把 workflow 调整为只在标签/发布时部署，或使用其它部署动作（如 `gh-pages` npm 包）。
