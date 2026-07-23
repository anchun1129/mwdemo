---
layout: default
title: 指南
nav_order: 1 
---
## 一.个性化基础改进

1.在本地化仓库中的_sass文件家中设置基础外观套件，如果没有这个文件夹可以自己创建。

```bash
cd /d/anchun1129/mwdemo #仓库本地存储位置，先进入所在文件夹
```

### **步骤：**

1. 在仓库根目录创建文件夹 `_sass/color_schemes/`。
2. 在该文件夹里新建一个 `.scss` 文件，比如 `custom.scss`。
3. 写入以下内容（可自由修改变量值）：

```sass
// 自定义颜色方案
$body-background-color: #fafafa;      // 页面背景
$sidebar-color: #2c3e50;             // 侧边栏背景
$border-color: #e0e0e0;

$body-text-color: #333;              // 正文文字颜色
$body-heading-color: #1a73e8;        // 标题颜色
$nav-child-link-color: #555;
$link-color: #1a73e8;               // 链接颜色
$btn-primary-color: #1a73e8;        // 按钮颜色
```

1. 在 `_config.yml` 中启用它：

```yaml
color_scheme: custom #在yml中有color_scheme条目，更改即可
```

推送到 GitHub 后刷新，颜色就会全部改变。所有可用的变量在 Just the Docs 文档 中可以找到。

## 二、添加界面

### **1. 创建页面文件**

在你的仓库根目录（或任意子文件夹）新建一个 `.md` 文件，比如 `about.md`（关于页）、`guide.md`（指南页）等。

### **2. 写入 Front Matter + 正文**

打开文件，按以下格式写：

markdown

```
---
layout: default
title: 页面标题
nav_order: 1
---
# 页面标题
这里是页面正文内容，支持所有 Markdown 语法。
```

- `layout: default`：**必须写**，让 Just the Docs 正确渲染页面。
- `title`：这个标题会显示在侧边栏导航和页面顶部。
- `nav_order`：数字，控制该页面在侧边栏的排序（数字越小越靠前）。

### **3. 如果页面需要子页面（折叠菜单）**

先创建一个父页面（如 `guide.md`）：

markdown

```
---
layout: default
title: 使用指南
nav_order: 2
has_children: true
---
# 使用指南
这里写介绍文字（可选）。
```

再创建子页面（如 `guide/install.md`）：

markdown

```
---
layout: default
title: 安装说明
parent: 使用指南
nav_order: 1
---
# 安装说明
第一步：...
```

- `parent` 的值必须**完全匹配**父页面的 `title`。
- 子页面会自动折叠显示在父页面下方。

### **4. 如果不想让页面出现在导航里**

有时需要创建一个独立的页面（比如文章详情），只需不写 `nav_order`，或者设置：

yaml

```
nav_exclude: true
```

### **5. 提交推送**

创建好 `.md` 文件后，在 Git Bash 中执行：

bash

```
git add .
git commit -m "添加新页面"
git push
```

GitHub Pages 会自动构建，片刻后刷新网站，新页面就会出现在侧边栏中。