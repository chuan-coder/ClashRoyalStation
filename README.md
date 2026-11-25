# 皇室战争 · 竞技情报站

Web 编程课程综合作业：以《皇室战争》为主题的竞技情报站。全站使用 HTML5 + CSS3 手写完成，**不使用 JavaScript**，轮播、吸顶、悬停、表单校验等交互都由 CSS 实现。

> 页面中的玩家、部落、分数、战绩、留言均为模拟数据，仅用于排版与课程展示。

## 一、页面与功能

| 页面 | 主要内容 |
| --- | --- |
| `index.html` 竞技场首页 | 三张图片的纯 CSS 轮播（箭头 + 圆点切换）、皇室👑要文八图相册、竞技场排名表、订阅版本资讯表单、右侧快捷导航与版本公告 |
| `signup.html` 数据采集 | 查询表单（玩家名 / ID / 赛季 / 查询条件）、示例结果表格、数据说明；查询表单右侧有「好运国王」贴纸，数据说明旁有蓝王浮动插图 |
| `news.html` 版本资讯 | 八条资讯列表（标题右侧有迷你皮卡插图）、编辑部精选图文卡、右侧赛事日历 |
| `news/` 新闻详情（8 篇） | 全宽新闻大图、向上重叠的白色版心卡片、面包屑、标题与来源时间、正文、八张相关推荐卡 |
| `about.html` 关于本站 | 站点介绍、目录结构表、皇室心得长文（速猪配图 / 野猪抠图 / 感谢动图）、留言板（标题旁有哭泣国王动图）与近期留言 |
| `gallery.html` 图鉴 | 开发中占位页：版心卡片 + 返回入口 + 统一底栏 |

新闻详情共 8 篇：觉醒之潮、小王子加强、全球锦标赛、分服机制、哥布林家族、冠军奖杯、史诗卡历史、新手攻略。

## 二、目录结构

```text
ClashRoyal/
├── index.html              竞技场首页
├── signup.html             数据采集
├── news.html               版本资讯中心
├── gallery.html            图鉴（建设中）
├── about.html              关于本站
├── news/                   八篇新闻详情页
│   ├── awakening.html      觉醒之潮
│   ├── prince.html         小王子加强
│   ├── crl.html            全球锦标赛
│   ├── server-split.html   分服机制
│   ├── goblin.html         哥布林家族
│   ├── trophy.html         冠军奖杯
│   ├── epic-cards.html     史诗卡历史
│   └── guide.html          新手攻略
├── css/
│   └── style.css           全站公共样式（按功能分区，附学生风格技术注释）
├── images/
│   ├── backgroud/          RedKing.jpg（底栏背景）、Fast2.6.jpg（皇室心得配图）、BlueKing.jpg（备用）
│   ├── banner/             三张轮播图：Cards / Champion / Victory
│   ├── cards/              预留卡牌目录（暂空）
│   ├── gif/                Mimimi.gif（感谢动图）、Gagaga.gif（留言板动图）
│   ├── icons/              Logo、Pig、Amethyst、BlueKing、GoodLuck、PiKa 等图标
│   ├── news/               八张新闻配图
│   ├── participant/        六张选手常用卡图标 favor1–favor6
│   └── list-side.png       订阅区右侧插图
├── ProjectDetail.txt       课程作业要求与修改记录
└── README.md               项目说明
```

部分图片为原始素材格式转换后的版本：`ClashRoyalImages2.webp` 保留原始 WebP 文件；`Respect.png`、`BlueKing.jpg` 目前未在页面中使用，留作备用素材。

## 三、配色（蓝白主题）

| 颜色 | 色值 | 用途 |
| --- | --- | --- |
| 深空蓝 | `#0b1030` / `#163a6b` | 页面标题、底栏压层、按钮文字 |
| 王者金 | `#f4c542` / `#ffd76e` | 标题装饰、分割线、按钮、当前导航 |
| 蓝宝石 | `#1e63b5` / `#2f7fff` | 链接、聚焦高亮、表格表头 |
| 紫水晶 | `#a45cff` / `#c79bff` | 稀有度、紫水晶分数 |
| 竞技红 | `#ff4d5a` | 强调色、链接按下状态 |
| 浅天蓝 | `#eaf1fa` / `#dfeaf8` | 页面空白、版心背板、内容分区 |
| 雾蓝 | `#bcd7f3` / `#d6e8fb` | 顶栏渐变背景 |
| 雾白 | `#ffffff` / `#f5f7fb` | 版心阅读区、侧栏卡片 |

样式表前半段保留基础深色样式，末尾用同名选择器覆盖为蓝白配色，布局部分保持不变。

## 四、布局说明

国字型布局：**吸顶顶栏 + 双栏主体 + 统一底栏**。

- **顶栏**：Logo + 五个一级导航（竞技场首页 / 数据采集 / 版本资讯 / 图鉴 / 关于本站）+ 装饰性搜索框，`position: sticky` 吸顶，当前页用金色高亮。
- **版心**：外层浅蓝背板 + 内层白色阅读区，背板左上角用 `::before` 绘制一个半悬在卡片外的金色错位小方块。
- **主体双栏**：`main` 主内容 + 右侧 `aside` 侧栏；除图鉴占位页和新闻详情页外，每个内页保留两张统一格式卡片——快捷导航（本页目录 + 其他页面）+ 本页专属卡片（首页版本公告、采集页采集帮助、资讯页赛事日历、关于本站站点信息）。
- **首页**：Banner 轮播 → 皇室👑要文相册 → 竞技场排名表 → 订阅表单；排名表使用 `table-layout: fixed` 固定六列宽度，长玩家名和部落名自动换行，所有数据行统一高度，避免表格撑出版心。
- **新闻详情**：顶栏下是全宽 520px 新闻大图，1280px 白色版心卡片向上重叠 92px；新闻大图按图片主体单独设置 `object-position`，让人物脸部保持在画面内（觉醒之潮、小王子、史诗卡三张做了重点调整，其余保持居中）。
- **装饰图标**：数据说明右侧的蓝王使用 `float` 让正文环绕；查询表单空白处的好运国王用 `position: absolute` 定位；留言板与资讯列表的动图 / 皮卡图标通过 `flex` 与标题左右排列。
- **底栏**：RedKing 背景图 + 深色渐变压层，左侧 Logo 与站名，右侧四个圆形联系方式徽章，下方作者 / 版本 / 主题信息与版权层。
- **返回顶部**：固定在版心右侧空白处的圆形箭头，`position: fixed` + `#top` 锚点。

## 五、技术点

- **语义化标签**：`header`、`nav`、`main`、`article`、`section`、`aside`、`footer`、`form`、`table` 等。
- **选择器与链接四态**：元素 / 类 / id / 后代 / 子代 / 属性 / 伪类选择器；链接按 **L-V-H-A** 顺序书写。
- **盒模型**：`box-sizing: border-box`，margin / padding / border / 圆角 / 阴影。
- **flex 布局**：顶栏、主体双栏、侧栏卡片、表单左右分栏、相关推荐卡片。
- **浮动**：表单里用 `float` 让标签和输入框并排，再用 `overflow: hidden` 清除浮动；心得区的野猪图也用浮动实现文字环绕。
- **定位**：`relative` + `absolute` 做金色错位块、Banner 文字 / 箭头 / 圆点、新闻页重叠卡片和装饰贴纸；`fixed` 做返回顶部；`sticky` 做吸顶顶栏与侧栏。
- **纯 CSS 轮播**：隐藏 `radio`，用 `:checked ~` 兄弟选择器切换 Banner 图片，`label` 圆点和左右箭头都能点击切图，全程不用 JavaScript。
- **伪元素**：`::before` 画版心左上角金色方块和侧栏顶部金条；`::after` 给新闻大图和底栏加渐变压层。
- **渐变与图片表现**：`linear-gradient` / `radial-gradient` 背景、`object-fit: cover` 裁图、`object-position` 调整新闻大图取景、`transform: scale()` 做相册悬停放大、`rotate()` 做心得配图小幅倾斜。
- **表格**：`border-collapse` 合并边框、`nth-child` 斑马纹、`tr:hover` 行高亮；图片直接放在 `td` / `th` 单元格里当图标，配合固定宽高、`object-fit`、`border-radius` 和 `vertical-align` 对齐。
- **表格适配**：`table-layout: fixed` + 百分比列宽控制整体宽度；名称列允许换行，`inline-block` 固定名字宽度让第二行从名字起始处折行，`overflow-wrap: anywhere` 处理长外文 ID。
- **表单**：`fieldset` / `legend` 分组、`label for` 关联、radio / checkbox / select / textarea、`pattern` 校验、`:focus` 高亮。
- **无障碍**：表格 `caption`、`thead` / `tbody` / `tfoot`、`scope="col|row"`；图片有 `alt`，装饰图使用空 `alt`。
- **媒体查询**：窄屏时收紧版心左上角方块、把返回顶部按钮挪回屏幕右下角。
- **无 JavaScript**：全站交互只使用 HTML + CSS。

## 六、CSS 注释约定

`css/style.css` 按功能分区，每个分区开头使用：

```css
/* ========== 分区名称 ========== */
/* ===== 用到：这一块主要用了什么技术 ===== */
```

注释用比较口语、学生作业式的写法，例如 Banner 区会写“position 绝对定位叠文字 / 箭头 / 圆点、隐藏 radio + :checked 切图、label 点击、overflow 裁圆角”，方便对照课程笔记复习。

## 七、运行方式

- 直接用浏览器打开 `index.html`；
- 或在 VS Code 中安装 Live Server 插件，右键 `index.html` 选择 “Open with Live Server”。

建议使用较新的 Chrome / Edge / Firefox 浏览器，以正常显示 `position: sticky`、`object-fit`、`object-position` 等效果。

## 八、更新记录

- **2026-11-25**：重写 README；新闻大图按主体位置调整 `object-position`，修复人物脸部被裁切；排名表改为固定列宽、长名字换行与统一行高，解决表格超出内容框；新增蓝王、好运国王、哭泣国王动图、迷你皮卡等分区装饰图标；CSS 分区补充“用到”技术注释。

## 九、作者与说明

- 作者：川-Coder
- GitHub：<https://github.com/chuan-coder>
- 本站为 Web 编程课程综合作业，所有数据均为模拟示例，仅供学习交流；页面中的游戏图片版权归 Supercell 所有。
