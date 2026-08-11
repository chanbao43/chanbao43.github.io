# 🗺️ 博客地图 —— chenbao

> 这份文档教你**看懂这个博客怎么运作**，以及**怎么指挥 AI 改它**。
> 你不需要会写代码，只需要照着"指挥话术"对 AI 说就行。

---

## 一、三句话看懂这个博客

1. **你的文章是 Markdown 文件**：`src/content/blog/` 里每个 `.md` 文件 = 一篇文章。
2. **构建生成网页**：Astro 把 Markdown 编译成静态 HTML，存到 `dist/`。
3. **自动上线**：把改动推送到 GitHub，GitHub Actions 自动构建并部署到 GitHub Pages。

```
你写文章 → 推送到 GitHub → 自动构建 → 网页更新
```

**日常你根本不用碰命令行**——用网页后台（Pages CMS）写文章、传图片、点保存就全自动完成了。

---

## 二、目录结构速查

| 路径 | 它是干什么的 | 需要改它时，对 AI 说 |
|---|---|---|
| `src/content/blog/*.md` | **你的文章**，一篇一个文件 | "帮我改 `xxx.md` 这篇文章" |
| `src/content/about.md` | 关于页的内容 | "帮我改关于页" |
| `src/config.ts` | **站点配置**：站名、描述、每页文章数、社交链接 | "帮我改站点标题/描述/每页文章数" |
| `src/components/Header.astro` | 顶部导航栏（首页/技术/生活/友链/关于） | "帮我加/改/删导航菜单" |
| `src/components/Footer.astro` | 页脚 | "帮我改页脚" |
| `src/components/PostCard.astro` | 文章列表里每张卡片的样子 | "帮我改文章卡片样式" |
| `src/components/TOC.astro` | 文章右侧的"目录"导航 | "帮我调文章目录" |
| `src/components/SearchModal.astro` | 站内搜索弹窗 | "帮我改搜索功能" |
| `src/components/ThemeToggle.astro` | 深色/浅色切换按钮 | "帮我改主题切换" |
| `src/components/GiscusComments.astro` | 评论区 | "帮我开/关评论" |
| `src/pages/index.astro` | 首页（文章列表 + 分页） | "帮我改首页布局" |
| `src/pages/posts/[slug].astro` | 单篇文章的详情页 | "帮我改文章页排版" |
| `src/pages/category/[cat].astro` | 分类页（技术/生活/随笔） | "帮我改分类页" |
| `src/pages/tag/[tag].astro` | 标签页 | "帮我改标签页" |
| `src/pages/friends.astro` | 友链页 | "帮我改友链页面" |
| `src/pages/404.astro` | 404 页面 | "帮我改 404 页" |
| `src/data/friends.json` | 友链数据（好友的链接） | "帮我加/改一个友链" |
| `src/styles/global.css` | **全站配色、字体、间距** | "帮我换主题色 / 改字体" |
| `src/content.config.ts` | 文章的字段规则（分类、标签等） | "帮我加一个文章字段 / 新分类" |
| `.pages.yml` | **网页后台（Pages CMS）的配置** | "帮我改后台上传功能" |
| `public/images/` | 你上传的图片都存这里 | "帮我处理图片" |
| `.github/workflows/deploy.yml` | 自动部署的流水线 | "帮我改部署流程" |

---

## 三、常见修改 · 指挥话术速查

> 直接把"你想干嘛"那句话丢给 AI 就行，比如：

| 我想… | 对 AI 说（示例话术） |
|---|---|
| 改博客名字 | "帮我把站点名改成「xxx」，在 `src/config.ts`" |
| 改首页一句话介绍 | "帮我改 `src/config.ts` 里的 description" |
| 导航加一个"项目"菜单 | "帮我在 `Header.astro` 的导航里加一个「项目」链接，指向 `/projects/`" |
| 换主题色 | "帮我把全站的强调色改成 xx 色，在 `global.css`" |
| 文章列表每行显示摘要 | "帮我在 `PostCard.astro` 里加上摘要显示" |
| 加一个友链 | "帮我在 `src/data/friends.json` 里加一个友链" |
| 每页显示 5 篇文章 | "帮我把 `config.ts` 的 postsPerPage 改成 5" |
| 新建一个页面 | "帮我新建一个 `src/pages/xxx.astro` 页面，和友链页风格一致" |
| 加个新分类"读书" | "帮我在 `content.config.ts` 加 category 枚举值，并加导航" |
| 文章里加"上一篇/下一篇" | "帮我在文章详情页加上一篇下一篇导航" |

> 💡 **原则**：对 AI 说话时，先说"改哪个文件"（看上面的表），再说"改成什么样"。
> 这样 AI 不会跑偏，你也能看懂它改了哪。

---

## 四、日常发文章（网页后台，推荐）

1. 打开 **https://app.pagescms.org** → 用 GitHub 账号登录 → 选择 `chanbao43.github.io` 仓库。
2. 点左边「**文章**」→「**新建文章**」。
3. 填标题、摘要、分类、标签，正文里粘贴内容、**拖拽图片**。
4. 点「**保存**」→ 自动提交到 GitHub → 自动重新构建 → 几分钟后文章上线。

> 首次使用会弹窗请求 GitHub 授权，点同意即可。只授权这个博客仓库。

## 五、日常发文章（本地文件，备用）

如果你更喜欢直接写文件（比如用 Obsidian / VS Code 写文章）：

1. 在 `src/content/blog/` 下新建一个 `.md` 文件，格式参考已有文章：
   ```
   ---
   title: "文章标题"
   date: 2026-08-11
   description: "一句话摘要"
   category: "tech"    # 可选：tech 技术 / life 生活 / essay 随笔
   tags: ["标签1", "标签2"]
   image: "/images/图片.jpg"   # 可选：封面图
   draft: false          # true 表示草稿，不会发布
   ---
   正文写在这里…
   ```
2. 图片放到 `public/images/` 文件夹。
3. 让 AI 帮你推送（或你自己提交），就自动发布了。

---

## 六、发布原理（懂了这条，你就真的"看懂"博客了）

```
 你写文章/图片
   │
   ▼
 GitHub 仓库  ──push──▶  GitHub Actions（云端自动构建）
   │
   └── 生成静态网页 ──▶  GitHub Pages（免费托管）
                                │
                                ▼
                           别人访问你的博客
```

- **文章** = Markdown 文件，不是数据库。这是这个架构的核心优点：**内容就是你文件夹里的文件**，永远不会丢，Git 帮你自动备份。
- **发文章** = 往仓库加一个 `.md` 文件并推送。
- **改博客** = 改 `src/` 里的代码文件并推送。
- **网页后台（Pages CMS）** = 一个网页工具，帮你完成"加文件 + 推送"，所以你不用记命令。

---

## 七、现状清单（2026-08-11）

| 功能 | 状态 |
|---|---|
| 博客框架 + 部署 | ✅ 已上线 |
| 文章/标签/分类/RSS/搜索/主题切换 | ✅ 已启用 |
| 网页后台（Pages CMS）上传文章和图片 | ✅ 已配置 |
| 友链页 | ✅ 已启用（数据在 `friends.json`） |
| 评论区（Giscus） | ⚠️ 有代码但**未配置完成**（`repo-id` 是占位符），需要时让 AI 帮你启用 |
| 自己的域名 | 暂用免费 `chanbao43.github.io`，想买再让 AI 帮你绑定 |

---

*这份地图由浮浮酱为你整理。想让我带你走一遍发第一篇文章吗？*
