# 🎓 Henry-Aru.github.io — 个人学术主页使用帮助

这个网站基于 [academic-homepage](https://github.com/luost26/academic-homepage) 模板构建，使用 Jekyll + GitHub Pages 自动部署。

---

## 📁 目录结构

```
Henry-Aru.github.io/
├── _config.yml            # 站点配置文件
├── index.html             # 首页
├── publications.html      # 论文列表页
├── blog.html              # 博客页
├── showcase.html          # 展示页（相册等）
├── _data/
│   ├── profile.yml        # 个人信息（姓名、简介、教育、奖项等）
│   ├── display.yml        # 显示设置（开关各模块）
│   ├── navigation.yml     # 导航栏设置
│   └── authors.yml        # 论文作者高亮设置
├── _publications/         # 论文文件夹
│   ├── 2022/
│   ├── 2023/
│   ├── 2024/
│   ├── 2025/
│   └── 2026/
├── _news/                 # 新闻动态文件夹
├── _posts/                # 博客文章文件夹
├── assets/
│   ├── images/
│   │   ├── photos/        # 头像照片
│   │   ├── covers/        # 论文封面图
│   │   ├── badges/        # 学校/机构 Logo
│   │   └── etc/           # 其他图片
│   └── css/
│       └── global.css     # 全局样式
└── _includes/
    └── widgets/           # 页面组件模板
```

---

## 一、修改个人信息

### 1.1 基本信息

打开 **`_data/profile.yml`**，修改以下字段：

```yaml
primary_name: "Pinxian Zeng"         # 你的姓名
secondary_name: ""                   # 备用名（可选）
navbar_name: "Pinxian Zeng"          # 导航栏显示的名字

email: "yc57911@um.edu.mo"           # 邮箱
gscholar: _XMG9esAAAAJ               # Google Scholar ID
github: Henry-Aru                    # GitHub 用户名

# 可选社交链接（去掉 # 取消注释）：
# twitter: your_twitter_id
# linkedin: your-linked-in-id
# orcid: 0000-0000-0000-0000
```

### 1.2 个人简介

在 `profile.yml` 中找到 `short_bio:`，用 HTML 写你的简介：

```yaml
short_bio: >-
  <p>
    Your name received his B.S. and M.ENG. degrees from XXX University. 
    He is currently a Ph.D. candidate in Computer Science at XXX. 
    His primary research interests focus on XXX.
  </p>
```

### 1.3 职位/单位

```yaml
positions:
- name: Ph.D. Candidate in Computer Science   # 你的职位
- name: University of Macau                   # 你的单位
  logo: /assets/images/badges/UM_logo.png     # 单位 Logo（可选）
```

### 1.4 教育经历

```yaml
education:
- name: University of Macau                     # 学校名
  logo: /assets/images/badges/UM_logo.png       # Logo（可选）
  position: >-
    Ph.D. in Computer Science and Technology     # 学位/专业
  date: 2025 - Present                           # 时间段
- name: Sichuan University
  position: M.ENG. in Artificial Intelligence
  date: 2022 - 2025
```

### 1.5 奖项

```yaml
awards:
- name: IEEE CIS/RAM Best Student Paper   # 奖项名称
  date: 2024                              # 年份
- name: Second-Prize Graduate Academic Scholarship
  date: 2024
```

---

## 二、修改头像和照片

1. **头像**：将你的照片放入 `assets/images/photos/` 目录，命名为 `photo.jpg`（或其他名字）
2. 在 `_data/profile.yml` 中修改：
   ```yaml
   portrait_url: /assets/images/photos/photo.jpg
   ```
3. 照片说明（可选）：
   ```yaml
   portrait_caption: >-
     你的名字
   ```

---

## 三、管理论文

### 3.1 添加论文

在 `_publications/` 下按年份分类，创建 `.md` 文件，文件名建议格式：`年份-会议缩写-关键词.md`

示例 `_publications/2026/2026-icassp.md`：

```markdown
---
title:          "论文标题"
date:           2026-05-01 00:01:00 +0800
selected:       true                          # true=显示在首页精选，false=仅在全部列表显示
pub:            "ICASSP 2026"                 # 发表会议/期刊
pub_date:       "2026"                        # 发表年份
abstract: >-
  论文简短摘要（1-2句话）
cover:          /assets/images/covers/cover1.jpg   # 封面图（可选）
authors:
  - P. Zeng                           # 你的名字（必须在 authors.yml 中有对应条目）
  - Other Author 1
  - Other Author 2
links:
  Paper: https://...                   # 论文链接
  Code: https://github.com/...         # 代码链接（可选）
  PDF: https://...                     # PDF 链接（可选）
---
```

### 3.2 设置作者高亮

在 **`_data/authors.yml`** 中添加你的名字使其加粗：

```yaml
"P. Zeng":
  bold: true

"Zeng, P.":
  bold: true
```

### 3.3 上传论文封面

将封面图片放到 `assets/images/covers/` 目录，然后在论文 front matter 中引用。

### 3.4 显示引用次数（可选）

在论文 front matter 中添加 Semantic Scholar ID：

```yaml
semantic_scholar_id: 204e3073870fae3d05bcbc2f6a8e263d9b72e776
```

---

## 四、管理新闻动态

在 `_news/` 目录下创建 `.md` 文件，按日期命名：

```markdown
---
title: >-
    新闻标题，支持 HTML 标签
    <a href="https://..." target="_blank">Read more <i class="fas fa-angle-double-right"></i></a>
date: 2026-06-15 10:00:00 +0800
---
```

新闻会自动按日期倒序排列，首页最多显示 `num_news` 条（在 `_data/display.yml` 中设置）。

---

## 五、管理博客文章

在 `_posts/` 目录下创建 `.md` 文件，**文件名必须为** `YYYY-MM-DD-标题.md` 格式：

```markdown
---
layout: blog_post
title: "博客标题"
date: 2026-06-15 10:00:00 +0800
---
博客正文，支持 Markdown 和 $\LaTeX$ 公式。
```

---

## 六、展示页面（Showcase）

用于展示图片、相册等。在 `_showcase/` 下创建文件夹和 `.md` 文件。查看示例了解格式。

---

## 七、显示设置

打开 **`_data/display.yml`**：

```yaml
homepage:
  show_experience: true                # 是否显示教育经历
  show_news: true                      # 是否显示新闻
  show_selected_publications: true     # 是否显示精选论文
  num_news: 10                         # 首页显示的最新新闻条数
```

---

## 八、导航栏

打开 **`_data/navigation.yml`**：

```yaml
pages:
- name: Home
  url: /
- name: Publications
  url: /publications
- name: Blog
  url: /blog
- name: Showcase
  url: /showcase
```

> `name` 必须与对应页面的 `navbar_title` 字段一致，否则导航栏高亮会失效。

---

## 九、本地预览

在仓库根目录运行：

```bash
bundle exec jekyll serve
```

然后浏览器打开 `http://localhost:4000` 即可预览。

---

## 十、部署到 GitHub Pages

1. 将修改 push 到 GitHub
2. 进入仓库 **Settings → Pages**
3. Source 选择 **Deploy from a branch**
4. Branch 选择 **main**，文件夹选择 **/(root)**
5. 等待几分钟，访问 `https://henry-aru.github.io`

---

## 十一、常见问题

### Q: 论文不显示？
检查：
- 文件是否有 front matter（`---` 包围的 YAML 头）
- 日期格式是否正确
- `selected` 字段是否有值

### Q: 头像不显示？
检查：
- 图片路径是否正确
- `portrait_url` 是否以 `/assets/images/...` 开头

### Q: 导航栏高亮不对？
确保 `navigation.yml` 中的 `name` 和页面中的 `navbar_title` 完全一致。

### Q: 公式不渲染？
模板内置了 KaTeX 支持，使用 `$...$` 行内公式或 `$$...$$` 块级公式即可。
