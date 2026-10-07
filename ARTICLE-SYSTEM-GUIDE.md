# 文章系统使用指南

## 📁 目录结构

```
clash-site/
├── blog/                          # 博客文章目录
│   ├── index.html                 # 文章列表页
│   ├── clash-mi-cross-platform-guide.html
│   ├── clashx-series-evolution.html
│   ├── clash-nyanpasu-lightweight.html
│   └── ... (更多文章)
```

---

## 📝 如何添加新文章

### 步骤 1: 创建文章 HTML 文件

在 `blog/` 目录下创建新的 HTML 文件,文件命名规范:

- **使用英文小写和连字符**: `clash-tun-mode-guide.html`
- **命名要有描述性**: `clash-rule-optimization.html`
- **避免使用中文**: ❌ `clash教程.html`

### 步骤 2: 复制文章模板

复制现有文章(如 `clash-mi-cross-platform-guide.html`)作为模板,修改以下内容:

#### A. `<head>` 部分 (SEO 关键)

```html
<title>文章标题 | 副标题或关键词 | 2026</title>
<meta name="description" content="150-160字的文章摘要,包含核心关键词">
<link rel="canonical" href="https://yoursite.com/blog/your-article.html">

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "文章标题",
  "description": "文章简介",
  "datePublished": "2026-10-07",  // 首次发布日期
  "dateModified": "2026-10-07",   // 最后修改日期(自动更新)
  "author": {
    "@type": "Organization",
    "name": "Clash 客户端指南"
  }
}
</script>
```

#### B. 面包屑导航

```html
<div class="breadcrumb">
    <a href="../index.html">首页</a> / 
    <a href="index.html">文章资讯</a> / 
    文章标题
</div>
```

#### C. 文章元信息

```html
<div class="article-meta">
    发布时间: 2026-10-07 | 
    更新时间: <span id="update-time"></span> | 
    阅读时间: X 分钟
    <div class="article-tags">
        <span class="tag">标签1</span>
        <span class="tag">标签2</span>
        <span class="tag">标签3</span>
    </div>
</div>
```

#### D. 内链部分 (非常重要!)

每篇文章末尾必须添加相关阅读模块:

```html
<div class="internal-links">
    <h3>📚 相关阅读</h3>
    <ul>
        <li>→ <a href="../windows.html">Windows 客户端对比</a> - 简短描述</li>
        <li>→ <a href="../macos.html">macOS 客户端推荐</a> - 简短描述</li>
        <li>→ <a href="another-article.html">相关文章</a> - 简短描述</li>
        <li>→ <a href="../clients.html">全平台客户端对比</a> - 简短描述</li>
    </ul>
</div>
```

**内链原则:**
- 每篇文章至少 5-6 个内链
- 链接到相关的产品页(windows.html, macos.html 等)
- 链接到相关的文章
- 使用描述性锚文本(不要只写"点击这里")

### 步骤 3: 更新文章列表页

在 `blog/index.html` 中添加新文章卡片:

```html
<div class="blog-card">
    <h3><a href="your-article.html">文章标题</a></h3>
    <div class="blog-meta">2026-10-07 | X 分钟阅读</div>
    <div class="blog-tags">
        <span class="tag">标签1</span>
        <span class="tag">标签2</span>
    </div>
    <p class="blog-excerpt">
        150-200字的文章摘要...
    </p>
    <a href="your-article.html" class="read-more">阅读全文 →</a>
</div>
```

**顺序:** 最新文章放在最前面。

### 步骤 4: 更新 sitemap.xml

在根目录的 `sitemap.xml` 中添加新文章:

```xml
<url>
    <loc>https://yoursite.com/blog/your-article.html</loc>
    <lastmod>2026-10-07</lastmod>
    <changefreq>weekly</changefreq>
    <priority>0.7</priority>
</url>
```

---

## 🔗 内链策略 (SEO 核心)

### 什么是内链?

内链是指从网站的一个页面链接到同一网站的另一个页面。内链对 SEO 极其重要!

### 为什么内链重要?

1. **帮助搜索引擎理解网站结构** - 告诉 Google 哪些页面重要
2. **传递页面权重** - 从高权重页面传递"PageRank"到其他页面
3. **降低跳出率** - 用户更容易找到相关内容,停留更久
4. **提升关键词排名** - 锚文本帮助 Google 理解页面主题

### 整站内链原则

#### 1. 核心页面(Hub Pages)

这些页面应该获得最多内链:

- `index.html` - 首页
- `windows.html` - Windows 客户端(高搜索量)
- `android.html` - Android 客户端(高搜索量)
- `macos.html` - macOS 客户端(高搜索量)
- `ios.html` - iOS 客户端(高搜索量)
- `clients.html` - 客户端对比(信息型查询)
- `tutorial.html` - 使用教程(新手入口)

**策略:** 每篇文章至少链接 2-3 个核心页面。

#### 2. 文章页面

每篇文章应该:

- **对外链接:** 至少 5-6 个内链(3-4 个核心页面 + 2-3 个相关文章)
- **接收链接:** 从其他相关文章和核心页面获得链接

**示例:**

```
文章: "Clash Mi 全平台指南"
↓ 链接到:
  - ios.html (iOS 客户端页面)
  - android.html (Android 客户端页面)
  - windows.html (Windows 客户端页面)
  - macos.html (macOS 客户端页面)
  - clash-subscription-management.html (订阅管理文章)
  - clients.html (客户端对比)
```

#### 3. 锚文本优化

**✅ 好的锚文本:**
- "iOS 完整客户端对比"
- "Windows 最强客户端"
- "TUN 模式深度解析"
- "订阅管理完全指南"

**❌ 差的锚文本:**
- "点击这里"
- "这个页面"
- "了解更多"
- 纯 URL

#### 4. 内链密度

- **文章正文:** 每 300-500 字出现 1-2 个内链
- **相关阅读模块:** 5-6 个内链(文章末尾)
- **面包屑导航:** 保持层级清晰

---

## 🏷️ SEO 标签优化清单

### 每个页面都必须有:

#### 1. Title 标签

```html
<title>主关键词 - 修饰词/卖点 | 品牌名 | 年份</title>
```

**规则:**
- 长度: 50-60 字符(中文约 25-30 字)
- 包含核心关键词
- 有吸引力(提升点击率)
- 每个页面 title 必须唯一

**示例:**
- ✅ "Clash Mi 全平台使用指南:一个客户端搞定所有设备 | 2026"
- ✅ "ClashX 系列完整演变史:从原版到 ClashFX 该选哪个? | macOS"
- ❌ "文章 | 网站"(太泛泛)
- ❌ "Clash Clash Clash 下载客户端"(关键词堆砌)

#### 2. Meta Description

```html
<meta name="description" content="150-160字的页面摘要,包含核心关键词,有吸引力的行动召唤">
```

**规则:**
- 长度: 150-160 字符(中文约 75-80 字)
- 包含核心关键词(自然出现,不堆砌)
- 描述页面内容和价值
- 吸引用户点击

**示例:**
```html
<meta name="description" content="Clash Mi 是唯一支持 iOS、Android、Windows、macOS、Linux 五大平台的完整 Clash 客户端。本文详细讲解各平台安装配置、多设备同步和常见问题解决。">
```

#### 3. Canonical 标签

```html
<link rel="canonical" href="https://yoursite.com/blog/your-article.html">
```

**作用:** 告诉搜索引擎这是内容的"正版"URL,避免重复内容问题。

#### 4. Schema.org 结构化数据

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "文章标题",
  "description": "文章简介",
  "datePublished": "2026-10-07",
  "dateModified": "2026-10-07",
  "author": {
    "@type": "Organization",
    "name": "Clash 客户端指南"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Clash 客户端指南"
  }
}
</script>
```

**作用:** 帮助搜索引擎理解内容类型,可能显示在搜索结果的"富媒体摘要"中。

#### 5. Open Graph 标签(社交媒体分享)

```html
<meta property="og:title" content="文章标题">
<meta property="og:description" content="文章摘要">
<meta property="og:url" content="https://yoursite.com/blog/your-article.html">
<meta property="og:type" content="article">
```

**作用:** 当文章被分享到社交媒体(微信、微博、Twitter)时,显示正确的标题和摘要。

---

## 📊 文章 SEO 优化技巧

### 1. 标题层级 (H1-H3)

```html
<h1>页面主标题</h1>              <!-- 只能有一个 H1 -->

<h2>章节标题</h2>                <!-- 主要内容区块 -->
  <h3>小节标题</h3>              <!-- 子区块 -->
  <h3>小节标题</h3>

<h2>章节标题</h2>
  <h3>小节标题</h3>
```

**规则:**
- 每页只有一个 `<h1>`(文章标题)
- H2 用于主要章节
- H3 用于次级小节
- 不要跳级(不要从 H2 直接跳到 H4)
- 标题中自然包含关键词

### 2. 关键词密度

- **目标关键词:** 在文章中出现 3-5 次
- **首段:** 必须出现 1 次目标关键词
- **正文:** 每 200-300 字出现 1 次
- **小标题:** 使用关键词变体

**示例:**

如果目标关键词是"Clash Mi",变体可以是:
- Clash Mi 客户端
- Clash Mi 应用
- Clash Mi 软件
- 这个全平台客户端(上下文指代)

**❌ 避免关键词堆砌:**
```
Clash Mi 是一个 Clash Mi 客户端,Clash Mi 支持全平台,下载 Clash Mi...
```

### 3. 内容长度

- **短文:** 800-1200 字(快速教程、简单对比)
- **中文:** 1500-2500 字(完整指南、深度分析)
- **长文:** 3000+ 字(全面教程、权威资源)

**原则:** 长度适合主题,不要为了凑字数而注水。

### 4. 多媒体元素

虽然目前网站是纯文本,但未来可以添加:

- **图片:** 截图、对比图、流程图(alt 属性必填)
- **表格:** 对比、参数、数据
- **列表:** 步骤、特点、优缺点

### 5. 内容更新

- **重要文章:** 每 1-3 个月更新一次
- **更新时:** 修改 `dateModified` 字段
- **更新内容:** 新版本、新功能、修正错误

---

## 🔄 文章更新流程

### 何时更新文章?

1. **客户端版本更新** - 新功能、界面变化
2. **发现错误** - 技术错误、链接失效
3. **用户反馈** - 缺少重要信息
4. **竞争对手分析** - 发现新的差异化内容
5. **SEO 优化** - 补充关键词、优化内链

### 如何更新?

1. 修改文章内容
2. 更新 Schema.org 中的 `dateModified` 字段
3. 页面底部的时间会自动更新(JavaScript)
4. 更新 sitemap.xml 中的 `<lastmod>`
5. 提交更新到 Google Search Console

---

## 📈 文章效果追踪

### 必须监控的指标:

1. **Google Search Console**
   - 展示次数(Impressions)
   - 点击次数(Clicks)
   - 点击率(CTR)
   - 平均排名(Average Position)

2. **Google Analytics**
   - 页面浏览量(Pageviews)
   - 平均停留时间(Avg. Time on Page)
   - 跳出率(Bounce Rate)

3. **关键词排名**
   - 使用工具: Ahrefs, Semrush, 或免费工具
   - 追踪目标关键词的排名变化

### 优化迭代:

- **上线后 2-4 周:** 不要修改(让 Google 稳定索引)
- **4-8 周:** 查看数据,识别问题
- **8周+:** 根据数据优化(标题、内链、内容)

---

## 🎯 文章主题建议

### 高优先级(应该写的)

1. **产品深度评测**
   - ✅ Clash Mi 全平台指南
   - ✅ ClashX 系列演变史
   - ✅ Clash Nyanpasu 轻量级神器
   - ⏳ Clash Verge Rev 完全指南
   - ⏳ FlClash 跨平台体验

2. **技术深度文章**
   - ⏳ Clash TUN 模式深度解析
   - ⏳ Clash 规则优化实战
   - ⏳ Clash 订阅管理完全指南
   - ⏳ Clash DNS 分流详解

3. **对比和选择**
   - ⏳ 2026 年最值得用的 5 个 Clash 客户端
   - ⏳ Clash vs V2Ray vs Sing-Box 该选哪个?
   - ⏳ 免费 vs 付费 iOS Clash 客户端对比

4. **问题解决**
   - ⏳ Clash 常见问题和解决方案合集
   - ⏳ Clash 连接失败的 10 种原因
   - ⏳ 如何优化 Clash 的速度和稳定性

### 中优先级(可以写)

- 各客户端版本更新资讯
- 用户投稿的使用技巧
- Clash 与特定应用的配合(游戏、开发工具等)

### 低优先级(暂时不写)

- 过于基础的内容(已在教程页面覆盖)
- 与 Clash 关联不大的泛泛代理知识
- 政治敏感或法律灰色地带的内容

---

## ✅ 发布前检查清单

每篇新文章发布前,检查:

- [ ] Title 标签唯一且包含关键词
- [ ] Meta Description 有吸引力且 150-160 字符
- [ ] Canonical 标签正确
- [ ] Schema.org 结构化数据完整
- [ ] 面包屑导航正确
- [ ] 文章标签(tags)准确
- [ ] 至少 5-6 个内链,锚文本描述性强
- [ ] 内链指向核心页面和相关文章
- [ ] 标题层级正确(只有一个 H1)
- [ ] 关键词自然出现,不堆砌
- [ ] 内容原创,有价值
- [ ] 语法和拼写正确
- [ ] 在 blog/index.html 中添加文章卡片
- [ ] 更新 sitemap.xml
- [ ] 移动端显示正常(响应式)

---

## 🚀 后续扩展建议

### 短期(1-2 个月)

1. 完成所有高优先级文章(10 篇)
2. 在每个产品页面添加"相关文章"模块
3. 创建文章分类页(按标签或主题)

### 中期(3-6 个月)

1. 添加文章评论系统(可选)
2. 添加"热门文章"模块
3. 制作信息图表和截图
4. 创建 RSS 订阅

### 长期(6个月+)

1. 视频教程(YouTube/B站)
2. 用户投稿系统
3. 多语言版本(英文)
4. 订阅邮件通知

---

## 📞 需要帮助?

如果在添加文章过程中遇到问题:

1. 参考现有文章作为模板
2. 查阅 SEO-STRATEGY.md 了解更多 SEO 知识
3. 使用 Google Search Console 验证 Schema 数据
4. 使用 PageSpeed Insights 测试页面性能

---

**最后更新:** 2026-10-07  
**文档版本:** 1.0
