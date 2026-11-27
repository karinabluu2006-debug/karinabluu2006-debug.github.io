# Mochi 的房间 · 张贵洋

一个可以点开来看的个人网站：房间、作品、手记、留言。
不是简历页，更像我把自己住的地方摊开给人看——桌上有电脑，墙角有纸箱，门口有信箱，鼠标划过去会亮。

- 线上地址：https://guiyang-site.app.workbuddy.host/?sharecode=OZUX2NMDE2
- 备用镜像：https://karinabluu2026.github.io/ （GitHub Pages，纯静态）

## 怎么逛

1. **首页**：中间是「房间里的碎碎念」，按类型（碎碎念 / 快乐存档 / 光影捕手 / 白日梦 / 日常切片）筛选；左边是我的名片与房间 BGM，右边是最近的日子和时间线。
2. **房间**：一张可以探索的插画。鼠标划过家具会亮，点开能看这一角放了什么；找到的东西会记在本机，刷新不丢。
3. **作品**：八件东西，两列排开。顶部可按「游戏 / 影像 / 视觉 / 实验」筛选，每类后面带数量。
   - 鼠标悬停封面会轻微放大；点开是详细页，可以切换「整体 / 局部 / 细节」三个取景，键盘 ← → 换下一件，Esc 关闭。
4. **博客**：手记列表，点开读全文。
5. **留言**：不用登录，写一张便签「钉」到墙上。
6. **关于**：自述、学校专业年级、能力标签、技能栈、兴趣清单、简历 PDF。

右上角可以切白天 / 夜晚；手机上另一套布局，不是把桌面版缩小。

## 目录结构

```
room/
  index.html
  src/
    App.jsx              页面框架与路由（?space=home|room|works|blog|guest|about）
    data.js              作品、热点、自述、分类等静态内容
    contentStore.js      内容读取：先云端，取不到回落到打包底稿
    music.js / sfx.js    播放器与音效
    components/
      shell/             首页外壳：Banner、侧栏、作品墙、关于页、文章页
      worksArt.jsx       八件作品的封面插画（纯 SVG / 手绘感绘制）
      Mochi.jsx          那只猫
  public/
    images/ bg/ mochi/ audio/ fonts/   静态素材
```

## 技术

React 19 + Vite + Tailwind，动画用 framer-motion，主题靠 CSS 变量一套切到底。
所有插画、家具、猫都是 SVG 画的，没有一张位图（房间的网点稿除外，那是印刷效果）。

## 本地跑起来

```bash
cd room
npm install
npm run dev      # http://127.0.0.1:5178
npm run build    # 产物在 room/dist
```

## 部署

**主站**：WorkBuddy 托管，`room/dist` 直接发布，带云端数据库（留言、内容编辑）。

**GitHub Pages**：`room/dist` 即仓库根，推上去自动构建。

```bash
cd room && npx vite build --emptyOutDir false
cd dist && git add -A && git commit -m "deploy: update" && git push
```

> 因为素材在代码里都是 `images/...`、`bg/...` 这类**相对路径**，站点必须部署在域名根目录；
> 放在 `github.io/<repo>/` 子路径下会取不到图。

## 内容说明

页面上的经历、奖项、时间、数字都是真的，没有编造。AI 参与了代码与排版的打磨，
文案用的是自己的口吻和真实的日记素材。页脚也写了这句：

> 本网站在 AI 辅助下完成，内容均为本人真实经历。
