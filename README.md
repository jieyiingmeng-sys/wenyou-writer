# 文游写作助手 · 网页版

把桌面版「文游写作助手」搬进浏览器的单文件应用。整个应用就是这一个 `index.html`，
无构建、无外部依赖、不请求任何第三方服务；所有工程数据只存在访客自己浏览器的
IndexedDB / localStorage 里（IndexedDB 不可用时自动降级 localStorage），
不经过任何服务器。支持File System Access API 的浏览器（https 环境下的
Edge / Chrome）可以把工程存成真正的 `.wyx` 文件，与桌面版完全通用。

## 本地看效果

直接双击 `index.html` 即可；或起一个本地静态服务：

```
python -m http.server 8080
# 访问 http://127.0.0.1:8080/index.html
```

## 部署（Cloudflare Pages）

推送到 GitHub 后由 Cloudflare Pages 自动构建部署，无需构建步骤：

1. Cloudflare 后台 → Workers & Pages → Create → Pages → Connect to Git
2. 选本仓库，Framework preset 选 `None`，Build command 留空，
   Build output directory 填 `/`
3. Deploy。以后每次 `git push` 到 main 自动更新线上内容

## 更新线上版本

改完 `index.html` → commit → push，Cloudflare 自动重新部署，链接不变。
