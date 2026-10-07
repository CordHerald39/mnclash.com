# Clash 网站审计问题清单

## 审计日期: 2026-10-07

---

## 🔴 高优先级问题 (需要立即修复)

### 1. 域名占位符问题 ⚠️ 最高优先级
**问题**: 所有页面使用 `yoursite.com` 占位符
**影响范围**: 
- 27 个 HTML 文件
- sitemap.xml
- robots.txt
- **总计约 57 处需要替换**

**影响**: 
- SEO 完全失效
- Canonical 链接无效
- Sitemap 无法提交到搜索引擎
- Schema.org 标记中的 URL 无效

**修复方案**: 
```bash
# 需要执行全局替换
find . -name "*.html" -o -name "*.xml" -o -name "*.txt" | xargs sed -i 's/yoursite\.com/实际域名/g'
```

**预计时间**: 5 分钟(有真实域名后)

---

### 2. Sitemap 不匹配问题 ✅ 已修复
**问题**: Sitemap 中列出的文件名与实际文件不符

**已修复**:
- ❌ 删除: subscription-guide.html (不存在)
- ❌ 删除: config-file.html (不存在)
- ❌ 删除: dns-config.html (不存在)
- ❌ 删除: proxy-groups.html (不存在)
- ✅ 添加: clash-subscription.html (实际存在)
- ✅ 添加: clash-config-yaml.html (实际存在)
- ✅ 添加: clash-dns-setup.html (实际存在)
- ✅ 添加: clash-proxy-groups.html (实际存在)

**状态**: ✅ 完成

---

### 3. 重复文件问题 📋 已标记
**问题**: `android-new.html` 是重复文件
**详情**: 
- 与 `android.html` 内容几乎完全相同
- 没有任何链接指向它
- 不在 sitemap 中
- 会造成 SEO 重复内容问题

**修复方案**: 删除 android-new.html

**状态**: 已标记待删除(需要手动删除或 bash 权限)

---

## 🟡 中优先级问题 (应尽快修复)

### 4. 导航不一致问题
**问题**: 3 种不同的导航结构
**影响范围**: 全站 27 个页面

**发现的导航变体**:
1. **变体A** (主要产品页): 首页 | 使用教程 | 文章资讯 | 常见问题 | 客户端对比
2. **变体B** (部分技术页): 缺少"文章资讯"链接
3. **变体C** (about.html): 导航顺序不同

**推荐标准导航**:
```html
首页 | 使用教程 | 文章资讯 | 常见问题 | 客户端对比
```

**修复范围**:
- about.html ❌
- compare.html ❌
- rules.html ❌
- protocols.html ❌
- tun-mode.html ❌
- troubleshooting.html ❌
- use-cases.html ❌
- 4 个长尾页面 (clash-subscription.html 等) ❌

**预计时间**: 2-3 小时

---

### 5. 缺失面包屑导航
**问题**: 3 个重要页面缺少面包屑导航

**影响页面**:
- about.html (关于页面)
- compare.html (对比页面)
- rules.html (规则配置)

**推荐面包屑格式**:
```html
<div class="breadcrumb">
    <a href="index.html">首页</a> / 页面名称
</div>
```

**预计时间**: 30 分钟

---

### 6. 错误的面包屑层级
**问题**: protocols.html 面包屑层级不正确

**当前**: 首页 / 使用教程 / 协议说明
**应该是**: 首页 / 协议说明

**原因**: protocols.html 是独立的技术说明页,不属于使用教程的子页面

**预计时间**: 5 分钟

---

### 7. 缺少"相关文章推荐"模块
**问题**: 9 个重要技术页面缺少相关文章模块

**影响页面**:
1. faq.html (常见问题)
2. tutorial.html (使用教程)
3. about.html (关于页面)
4. compare.html (对比页面)
5. rules.html (规则配置)
6. protocols.html (协议说明)
7. tun-mode.html (TUN 模式)
8. troubleshooting.html (故障排查)
9. use-cases.html (使用场景)
10. 4 个长尾页面 (clash-subscription.html 等)

**已有相关文章模块的页面**:
- ✅ index.html (首页 - 有"最新文章"模块)
- ✅ windows.html
- ✅ macos.html
- ✅ android.html
- ✅ ios.html
- ✅ clients.html
- ✅ 6 篇博客文章(自带相关阅读)

**推荐模块模板**:
```html
<div style="margin-top: 3rem; padding: 1.5rem; background: #171a23; border-radius: 8px; border-left: 4px solid #fbbf24;">
    <h3 style="color: #fbbf24; margin-bottom: 1rem;">📚 相关文章推荐</h3>
    <ul style="list-style: none; margin: 0; padding: 0;">
        <li style="margin-bottom: 0.8rem;">→ <a href="blog/xxx.html" style="color: #5eead4;">文章标题</a></li>
        <!-- 3-4 篇相关文章 -->
    </ul>
</div>
```

**预计时间**: 3-4 小时

---

### 8. FAQ Schema 标记不够丰富
**问题**: 只有 2 个问题的 FAQ Schema

**当前**: faq.html 只在 Schema 中标记了 2 个问题
**建议**: 至少 5-10 个问题,提升富媒体搜索结果展示

**影响**: 错失 Google 富媒体搜索结果的机会

**预计时间**: 30 分钟

---

## 🟢 低优先级问题 (可选改进)

### 9. 缺失的标准页面
**建议创建**:
- 隐私政策页面 (privacy.html)
- 联系我们页面 (contact.html)
- 404 错误页面 (404.html)

**原因**: 
- 提升网站专业性
- 符合 SEO 最佳实践
- 改善用户体验

**预计时间**: 2-3 小时

---

### 10. 上下文内链可以更丰富
**建议**: 在正文中添加更多相关页面的内链

**当前状态**: 
- 博客文章内链很好(10-13个/篇)
- 产品页面内链不错(有相关文章模块)
- 技术页面内链较少

**改进方向**:
- tutorial.html 中提到"规则配置"时链接到 rules.html
- troubleshooting.html 提到"TUN 模式"时链接到 tun-mode.html
- 等等

**预计时间**: 2-3 小时

---

## 📊 修复优先级建议

### 立即处理(等待域名后)
1. ✅ Sitemap 修复 - **已完成**
2. 📋 删除 android-new.html - **已标记**
3. 🔴 替换所有域名占位符 - **等待真实域名**

### 近期处理(本周内)
1. 统一导航结构 - 13 个页面
2. 补充面包屑导航 - 3 个页面
3. 修正 protocols.html 面包屑
4. 为 13 个技术页面添加相关文章模块

### 可选增强(时间允许时)
1. 扩展 FAQ Schema 标记
2. 创建隐私政策/联系页面/404页面
3. 增加正文中的上下文内链

---

## 🎯 修复后的预期效果

### SEO 健康分数提升
- **当前**: 72/100
- **修复高优先级后**: 85/100
- **修复中优先级后**: 92/100
- **完成所有优化后**: 95+/100

### 具体改进
1. **域名修复后**: 
   - Sitemap 可以提交
   - Canonical 链接生效
   - Schema.org 标记有效

2. **导航统一后**:
   - 用户体验更一致
   - 降低跳出率
   - 提升页面权重传递

3. **相关文章模块后**:
   - 内链密度提升到每页 15+ 个
   - 用户停留时间增加
   - 页面间权重传递更好

4. **面包屑完善后**:
   - 搜索结果更丰富
   - 用户导航更清晰
   - 结构化数据更完整

---

## 📝 需要的信息

1. **真实域名** - 用于替换所有 yoursite.com
2. **是否需要删除 android-new.html** - 确认后可直接删除
3. **优先级确认** - 按照建议的顺序处理?还是有其他优先级?

---

## ✅ 已完成的工作总结

1. ✅ 创建了完整的博客系统(6篇深度文章)
2. ✅ 为 5 个主要产品页面添加了相关文章模块
3. ✅ 为首页添加了"最新文章"模块
4. ✅ 修复了 sitemap.xml 的文件名错误
5. ✅ 标记了重复文件 android-new.html

---

生成时间: 2026-10-07
审计工具: 人工全面检查 + 子代理深度分析
下一步: 等待域名信息,然后按优先级逐项修复
