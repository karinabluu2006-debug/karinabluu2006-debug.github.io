# Mochi 的房间 · 张贵洋

个人网站「Mochi 的房间」的 GitHub Pages 部署仓库。

- 线上地址：https://karinabluu2006-debug.github.io/
- 主站（带云端能力）：https://guiyang-site.app.workbuddy.host/?sharecode=OZUX2NMDE2

## 这个仓库是什么

仓库根目录即是网站的**构建产物**（Vite build 输出），由本地 `room/dist` 推送而来，不含源码。

> 图片、字体、音频、视频在代码里都是 `/images/...`、`/fonts/...` 这类根路径，
> 所以必须放在账号根仓库（`<user>.github.io`）下，子路径部署会让素材全部 404。

## 与主站的区别

GitHub Pages 只能跑静态文件，读不到云端数据库，因此：

| 能力 | 主站 | 这里 |
| --- | --- | --- |
| 房间 / 作品墙 / 关于 / 文章 | 正常 | 正常 |
| 文章列表 | 按云端状态（3 篇） | 取打包底稿（6 篇） |
| 留言墙 | 所有人可见 | 只存在本机浏览器 |
| 编辑中心 | 改动进云端 | 改动只留本机 |

## 更新方式

```bash
cd room && npx vite build --emptyOutDir false
cd dist && git add -A && git commit -m "deploy: update" && git push
```

Pages 会自动重新构建，通常 1–2 分钟生效。
