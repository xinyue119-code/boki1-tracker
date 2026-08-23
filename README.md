# 簿記１級 学習進捗 — 部署到 GitHub Pages

这是一个可以真正安装、离线使用的 PWA（不是 claude.ai 里的 artifact）。数据保存在你手机浏览器本地，不联网也能用。

## 部署步骤（第一次，约 5 分钟）

1. 打开 https://github.com/new ，创建一个新仓库
   - Repository name 随便起，比如 `boki1-tracker`
   - 选 Public
   - 不要勾选任何初始化选项（README/gitignore 都不用）

2. 把这个文件夹里的所有文件（`index.html`、`manifest.json`、`sw.js`、`icons/` 整个文件夹）上传上去
   - 最简单方式：在仓库页面点 "Add file" → "Upload files"，把文件和 `icons` 文件夹一起拖进去，点 Commit

3. 开启 GitHub Pages
   - 进仓库的 Settings → 左侧 Pages
   - Source 选 "Deploy from a branch"，Branch 选 `main`，文件夹选 `/ (root)`，保存

4. 等 1-2 分钟，网址会出现在同一个页面，形如：
   `https://你的用户名.github.io/boki1-tracker/`

## 加到手机主屏幕

- **iPhone（Safari）**：打开上面的网址 → 点底部分享图标 → 「ホーム画面に追加」
- **安卓（Chrome）**：打开网址 → 右上角「⋮」→ 「ホーム画面に追加」/「アプリをインストール」

加完之后就是一个独立图标，打开是全屏无地址栏，断网也能用（因为 service worker 会把页面缓存到本地）。

## 以后想加内容/修改

直接在仓库里编辑 `index.html`，或者把新版本文件重新上传覆盖，GitHub Pages 会在几十秒内自动更新。数据本身存在用户浏览器本地（localStorage），跟代码更新无关，不会丢失。

## 文件说明

- `index.html` — 应用本体，簿記１級 四大科目的进度打卡表（可自己增删科目/项目）
- `manifest.json` — 告诉浏览器这是个可安装应用
- `sw.js` — 离线缓存逻辑
- `icons/` — 主屏幕图标（192px、512px）
