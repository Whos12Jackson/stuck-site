# stuck-site 维护说明

这个仓库是 Stuck 卡词的 GitHub Pages 镜像站，用于 Chrome / Edge 商店审核（Google 的验证服务器访问不到中国大陆的 www.stuck12.com）。

## 两个站点的关系

| 站点 | 域名 | 用途 |
|---|---|---|
| 阿里云主站 | www.stuck12.com | 正式官网（带 ICP 备案号）+ API |
| GitHub Pages 镜像 | site.stuck12.com | 商店审核用的首页和隐私政策（无 ICP） |

## 隐私政策同步规则

**改隐私政策时，两边必须一起更新：**

1. 在 `Stuck` 仓库 `release/1.0` 分支修改 `docs/上架材料/隐私政策.md`
2. 用 `build-privacy.mjs` 重新生成 `stuck-waitlist/privacy.html`
3. 把生成的 HTML 复制到本仓库 `privacy/index.html`（去掉 ICP 备案号行）
4. 两个仓库分别 commit + push
5. 重新打包 `stuck-waitlist.tar.gz` 并部署到服务器

## 商店链接

审核通过后，更新 `index.html` 中的商店安装按钮 `href`：
- 搜索 `id="link-edge"` 和 `id="link-chrome"`（页面顶部的按钮）
- 搜索 `data-mirror="edge"` 和 `data-mirror="chrome"`（页面底部的按钮）
