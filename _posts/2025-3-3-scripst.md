---
layout: post
title:  "Scripst：A versatile scripting template for Typst typesetting. "
image: ''
date:   2025-3-3 00:00:00
tags:
- typst
- scripst
description: ''
categories:
- Markup
---

在使用了一段时间的[typst](https://typst.app/)之后，它逐渐成为了我排版的首选工具。

在任何场合，只要手头边有一个模板包，我便可以像写 Markdown 一样，用轻量化的标记快速排版。

但不像 LaTeX 那样，typst 不提供默认模板，这使得我在使用 typst 时，需要自己维护一套模板。

在经过不断的调优和迭代之后，我终于有了一套自己的 typst 模板，我称之为 Scripts。

<figure class="foto-legenda">
	<img src="{{ "/assets/img/posts/2025-3-3-scripst/thumbnail.png"}}" alt="">
	<figcaption> <p>Scripst</p>
	</figcaption>
</figure>


## Scripst 模板

**Scripst** 是一个基于 **Typst** 的模板包，提供了一套简约高效的文档模板，适用于日常文档、作业、笔记、论文等场景。

我想把这个模板做的看起来轻量简洁，同时又不失优雅。不使用过多的样式，只使用最基本的排版元素，使其能适用于严肃的场合，也能在日常使用中保持舒适的阅读体验。

### 特性

- 高扩展性：模块化设计，便于对模板进行扩展
  - 对于常用的排版元素，提供了模块化的设计，方便后期的维护和扩展
  - 可以引用这些模块，组合出新的模板样式
- 多语言设计：针对不同语言进行本地化设计
  - 提供了四十多种语言的本地化支持，便于多语言文档的排版
- 新增模块`countblock`：这是一个可以自定义名称和颜色的模块，内置一个计数器，并且可以在文中随时引用；可以用来做定理、问题、注记等模块
  - **该模块是我日常使用最多的模块，也是最值得宣传的模块**，尤其是在数学、物理的笔记和作业之中，通过封装计数器，可以方便的引用和管理
  - 提供了定义任意 block 的接口，对不同类的交叉引用提供了支持

### 使用 Scripst

#### 引入 Scripst 模板

在 Typst 文件开头引入模板：

```typst
#import "@local/scripst:1.1.0": *
```

#### 创建 `article` 文档

```typst
#show: scripst.with(
  title: [Scripst 的使用方法],
  info: [这是文章的模板],
  author: ("作者1", "作者2", "作者3"),
  time: datetime.today().display(),
  abstract: [摘要内容],
  keywords: ("关键词1", "关键词2", "关键词3"),
  contents: true,
  content-depth: 2,
  matheq-depth: 2,
  lang: "zh",
)
```

### 🔧 模板参数

| 参数 | 类型 | 默认值 | 说明 |
| --- | --- | --- | --- |
| `template` | `str` | `"article"` | 选择模板 (`"article"`, `"book"`, `"report"`) |
| `title` | `content`, `str`, `none` | `""` | 文档标题 |
| `info` | `content`, `str`, `none` | `""` | 文档副标题或补充信息 |
| `author` | `array` | `()` | 作者列表 |
| `time` | `content`, `str`, `none` | `""` | 文档时间 |
| `abstract` | `content`, `str`, `none` | `none` | 文档摘要 |
| `keywords` | `array` | `()` | 关键词 |
| `preface` | `content`, `str`, `none` | `none` | 前言 |
| `font-size` | `length` | `11pt` | 字体大小 |
| `contents` | `bool` | `false` | 是否生成目录 |
| `content-depth` | `int` | `2` | 目录深度 |
| `matheq-depth` | `int` | `2` | 数学公式编号深度 |
| `lang` | `str` | `"zh"` | 语言 (`"zh"`, `"en"`, `"fr"` 等) |


更多详细内容请查看[Scripst 的主页](https://an-314.github.io/scripst/zh)以及[Scripst 的 GitHub 仓库](https://github.com/An-314/scripst)

期待你的使用和反馈！