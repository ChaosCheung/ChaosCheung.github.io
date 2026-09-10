# 个人学术主页编辑指南

这个网站使用 Hugo Blox Academic CV 模板，适合部署到 GitHub Pages。日常更新不需要重新设计网站，只需要编辑几个文字文件。

## 最常编辑的文件

| 想修改的内容 | 编辑文件 |
|---|---|
| 姓名、职称、个人简介、单位、研究方向 | `data/authors/me.yaml` |
| 首页栏目、论文和基金项目文字 | `content/_index.md` |
| 网站主色、辅色、背景和文字颜色 | `data/themes/uestc.yaml` |
| 顶部导航栏目与顺序 | `config/_default/menus.yaml` |
| 网站标题和 GitHub Pages 地址 | `config/_default/hugo.yaml` |
| 个人照片 | `assets/media/authors/me.png` |

## 直接在 GitHub 网页中修改

1. 打开网站仓库。
2. 找到需要编辑的文件。
3. 点击右上角的铅笔图标。
4. 修改内容，点击 `Commit changes` 保存。
5. GitHub Pages 会自动重新生成网站。

编辑 YAML 文件时，请保留每行开头的空格和英文冒号。

## 修改个人资料

打开 `data/authors/me.yaml`，常用字段如下：

```yaml
name:
  display: 张三

role: 教授

bio: |
  在这里填写个人简介。可以写教育经历、研究重点和主要学术贡献。

affiliations:
  - name: 电子科技大学网络空间安全学院

interests:
  - 网络安全
  - 系统安全
  - 数据与人工智能安全
```

## 更换个人照片

准备一张正方形或接近正方形的照片，建议不小于 600×600 像素，然后将其命名为 `me.png`，替换：

`assets/media/authors/me.png`

## 修改配色

打开 `data/themes/uestc.yaml`，修改 `light` 下的颜色：

```yaml
light:
  colors:
    primary: "#0a2342"   # 深海军蓝
    secondary: "#c8a45d" # 学术金
    neutral: "#151d2a"   # 正文颜色
```

推荐配色示例：

| 风格 | primary | secondary | neutral |
|---|---|---|---|
| 当前深蓝金色 | `#0a2342` | `#c8a45d` | `#151d2a` |
| 电子科大蓝 | `#155a9c` | `#2aa8c7` | `#172033` |
| 墨绿学术 | `#176b5b` | `#6aa98f` | `#1d2926` |

## 调整首页结构

打开 `content/_index.md`。`sections:` 下的每个 `- block:` 都是一个页面栏目。当前顺序是：

1. 个人简介
2. 研究方向
3. 发表论文
4. 科研项目

移动一个完整的 `- block:` 段落，就可以改变栏目顺序；删除完整段落，就可以隐藏该栏目。

顶部导航栏在 `config/_default/menus.yaml` 中设置。`weight` 越小，菜单越靠前。

## 添加或修改论文

在 `content/_index.md` 中找到 `publication-list`。复制一整个 `publication-item`，然后修改论文信息：

```html
<article class="publication-item">
  <h3>Paper Title</h3>
  <p class="publication-authors">Author One, <strong class="author-self">Your Name</strong>, Author Three</p>
  <p class="publication-venue">Conference or Journal · Year <span class="paper-rank">CCF A</span></p>
</article>
```

每篇论文固定显示三行：第一行是题目，第二行是作者，第三行是期刊/会议、年份和等级。

需要加粗哪个作者，就只把该姓名放进
`<strong class="author-self">...</strong>` 中；该姓名可以位于作者列表的任意位置，不要求是第一作者。

需要强调论文等级时，把 `CCF A`、`CCF B` 或中科院分区等文字放入
`<span class="paper-rank">...</span>`，网页会显示为红色文字，并跟在期刊/会议后面。

## 修改基金项目

在 `content/_index.md` 中搜索“青年科学基金项目”，然后替换项目名称、批准号和执行期限。

## 发布前需要修改

在 `config/_default/hugo.yaml` 中，将：

```yaml
baseURL: 'https://username.github.io/'
```

替换为自己的 GitHub 用户名，例如：

```yaml
baseURL: 'https://zhangsan.github.io/'
```
