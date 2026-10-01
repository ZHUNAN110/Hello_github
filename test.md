# Markdown 语法展示文档

本文档演示常用 Markdown 语法与样式写法，包含**文字颜色设定**。
不同渲染器（GitHub、Typora、VS Code、Obsidian、语雀等）支持程度不同，文中已逐项标注。

---

## 一、标题

# 一级标题 H1
## 二级标题 H2
### 三级标题 H3
#### 四级标题 H4
##### 五级标题 H5
###### 六级标题 H6

> 快捷键：VS Code 中 `Ctrl+Shift+P` 后可格式化；Typora 中 `Ctrl+1~6` 直接切换级别。

另一种写法（Setext 风格，仅支持 H1/H2）：

主标题
======

副标题
------

---

## 二、文字样式

### 2.1 基础样式

| 样式 | 语法 | 效果 |
| --- | --- | --- |
| 加粗 | `**文字**` | **加粗文字** |
| 斜体 | `*文字*` | *斜体文字* |
| 粗斜体 | `***文字***` | ***粗斜体文字*** |
| 删除线 | `~~文字~~` | ~~删除线文字~~ |
| 行内代码 | `` `代码` `` | `inline code` |
| 下划线 | `<u>文字</u>` | <u>下划线文字</u> |
| 高亮 | `==文字==` | ==高亮文字==（⚠️ 仅 Obsidian、Typora 等支持） |
| 下标 | `H~2~O` | H~2~O（⚠️ 部分支持） |
| 上标 | `x^2^` | x^2^（⚠️ 部分支持） |

### 2.2 换行与分段

- 段落之间：空一行。
- 行内换行：行尾加 **两个空格**，或直接写 `<br>`。

第一行（行尾两个空格）  
第二行。

---

## 三、文字颜色设定 ⭐

> **核心结论**：标准 Markdown 语法**没有**颜色定义。
> 所有颜色效果都依赖内嵌 HTML，能否生效取决于渲染器是否允许 raw HTML。

### 3.1 推荐写法：`<span style>`

支持：GitHub、VS Code（需开启预览）、Typora、Obsidian、语雀、Jupyter 等。

<span style="color:red;">这是红色文字</span>  
<span style="color:#FF8C00;">这是橙色文字（十六进制）</span>  
<span style="color:rgb(0,128,255);">这是蓝色文字（RGB）</span>  
<span style="color:green; font-weight:bold;">绿色 + 加粗</span>  
<span style="background:yellow; color:black;">黄底黑字（背景色 + 前景色）</span>

### 3.2 兼容写法：`<font color>`

老式标签，兼容性最广，但已被 HTML5 废弃，部分现代渲染器会忽略。

<font color="red">红色</font> / <font color="green">绿色</font> / <font color="#9932CC">紫色</font>

### 3.3 常用颜色速查

| 名称 | 写法 | 预览 |
| --- | --- | --- |
| 红 | `color:red` | <span style="color:red;">■ 红色</span> |
| 橙 | `color:orange` | <span style="color:orange;">■ 橙色</span> |
| 金 | `color:goldenrod` | <span style="color:goldenrod;">■ 金色</span> |
| 绿 | `color:green` | <span style="color:green;">■ 绿色</span> |
| 青 | `color:teal` | <span style="color:teal;">■ 青色</span> |
| 蓝 | `color:blue` | <span style="color:blue;">■ 蓝色</span> |
| 紫 | `color:purple` | <span style="color:purple;">■ 紫色</span> |
| 灰 | `color:gray` | <span style="color:gray;">■ 灰色</span> |

### 3.4 在表格与列表中上色

| 状态 | 说明 |
| --- | --- |
| <span style="color:green;">✅ 通过</span> | 测试全部通过 |
| <span style="color:orange;">⚠️ 警告</span> | 存在非阻塞问题 |
| <span style="color:red;">❌ 失败</span> | 需要立即修复 |

- 列表项也可上色：<span style="color:#1E90FF;">蓝色条目</span>
- 加粗 + 颜色：**<span style="color:red;">红色加粗</span>**

### 3.5 注意事项

1. **必须留空行**：HTML 块级元素（如 `<div>`）前后需空行，否则会被当作代码。
2. **行内标签可行内写**：`<span>` 属于行内元素，可直接嵌入句子中。
3. **GitHub 白名单**：GitHub 只允许部分标签与属性，`style` 中的 `color` 可用，但 `class`、`id`、`onclick` 等会被过滤。
4. **不可用场景**：纯 Markdown 阅读器（如部分终端工具、`pandoc` 默认输出）会原样显示标签或直接剥离。
5. **`<font>` 已废弃**：新文档建议统一用 `<span style="color:...">`。

---

## 四、列表

### 4.1 无序列表

- 项目一
- 项目二
  - 嵌套项 A
  - 嵌套项 B
    - 更深一层
- 项目三

> 符号可用 `-`、`*`、`+`，同一层级请保持一致。

### 4.2 有序列表

1. 第一步
2. 第二步
   1. 子步骤 1
   2. 子步骤 2
3. 第三步

### 4.3 任务列表

- [x] 已完成任务
- [ ] 未完成任务
- [ ] 待办事项

> ⚠️ 任务列表需 GitHub / VS Code / Obsidian 等支持。

---

## 五、引用

> 这是一段引用。
>
> > 这是嵌套引用。
>
> 引用内也可以有**加粗**、`代码`、<span style="color:teal;">颜色</span>。

> **提示**
> 引用常用于标注注意事项。

---

## 六、代码

### 6.1 行内代码

使用 `print("hello")` 输出内容。

### 6.2 代码块

```python
def greet(name: str) -> str:
    """返回问候语。"""
    return f"Hello, {name}!"


print(greet("world"))
```

```bash
# 查看文件
ls -la /home/zhunan/文档/report
```

```json
{
  "name": "report",
  "color": "#FF8C00",
  "enabled": true
}
```

> 围栏用三个反引号，首行写语言名即可高亮。

---

## 七、链接与图片

### 7.1 链接

- 行内式：[Markdown 官方指南](https://www.markdownguide.org/)
- 带标题：[Claude](https://claude.ai "访问 Claude")
- 引用式：[Claude Code][cc]
- 裸链接：<https://claude.ai/code>
- 锚点跳转：[回到颜色章节](#三文字颜色设定-)

[cc]: https://claude.ai/code "Claude Code 官网"

### 7.2 图片

```markdown
![替代文本](图片路径 "可选标题")
```

![示例图片](https://via.placeholder.com/300x100?text=Demo "示例")

> 图片语法只是在链接前加 `!`，同样支持引用式写法。

---

## 八、表格

### 8.1 基础表格

| 左对齐 | 居中 | 右对齐 |
| :--- | :---: | ---: |
| A | B | C |
| 数据 | 数据 | 100 |
| 内容 | 内容 | 200 |

### 8.2 含样式的表格

| 项目 | 结果 | 说明 |
| :--- | :---: | :--- |
| 语法检查 | <span style="color:green;">✅ 通过</span> | `markdownlint` 无告警 |
| 链接检查 | <span style="color:orange;">⚠️ 警告</span> | 1 个外链超时 |
| 渲染检查 | <span style="color:red;">❌ 失败</span> | `==高亮==` 不被支持 |

---

## 九、分隔线

三种写法等效：

```markdown
---
***
___
```

实际效果：

---

***

___

---

## 十、脚注

Markdown 支持脚注语法[^1]，颜色标签的兼容性也常被讨论[^color]。

[^1]: 脚注内容会渲染在文档底部。

[^color]: 脚注中同样可以写 <span style="color:red;">彩色文字</span>。

---

## 十一、折叠块（details）

<details>
<summary>点击展开更多内容</summary>

这里是折叠区域内部。

- 可放列表
- 可放 <span style="color:purple;">彩色文字</span>

</details>

---

## 十二、转义字符

以下字符需要使用反斜杠 `\` 转义：

```markdown
\   反斜杠
`   反引号
*   星号
_   下划线
{}  花括号
[]  方括号
()  圆括号
#   井号
+   加号
-   减号
.   句点
!   感叹号
|   竖线
```

示例：`\*这不是斜体\*` → \*这不是斜体\*

---

## 十三、Emoji

短代码写法（需渲染器支持）：

```markdown
:smile: :rocket: :white_check_mark: :warning:
```

直接粘贴：😄 🚀 ✅ ⚠️

---

## 十四、其他扩展语法

### 14.1 定义列表（部分支持）

```markdown
术语
: 术语的解释
```

### 14.2 数学公式（需 MathJax / KaTeX）

```markdown
行内：$E = mc^2$
块级：$$\int_a^b f(x)\,dx$$
```

行内效果：$E = mc^2$

### 14.3 目录

- 部分编辑器支持 `[TOC]` 自动生成目录。
- VS Code 可安装 `Markdown All in One` 插件，用命令生成。

---

## 十五、最佳实践

1. **标题层级连续**：不要从 H1 跳到 H3。
2. **标题前后空行**：兼容性最好。
3. **颜色统一**：用同一套色板，避免整篇花花绿绿。推荐：
   - 成功 `green` / `#22863a`
   - 警告 `orange` / `#b08800`
   - 错误 `red` / `#d73a49`
   - 提示 `#0969da`
4. **颜色之外留冗余**：颜色在纯文本环境会丢失，重要信息应同时用 ✅/⚠️/❌ 等符号表达。
5. **不写死颜色依赖**：深色模式下 `color:black` 会看不见，建议用具体色值，或避免纯黑纯白。

---

## 附录：语法速查表

| 功能 | 语法 |
| --- | --- |
| 标题 | `# H1` ~ `###### H6` |
| 加粗 | `**粗体**` |
| 斜体 | `*斜体*` |
| 删除线 | `~~删除~~` |
| 高亮 | `==高亮==` |
| 下划线 | `<u>下划线</u>` |
| 颜色 | `<span style="color:red;">文字</span>` |
| 背景色 | `<span style="background:yellow;">文字</span>` |
| 行内代码 | `` `code` `` |
| 代码块 | ```` ```lang ... ``` ```` |
| 链接 | `[文字](url)` |
| 图片 | `![alt](url)` |
| 引用 | `> 引用` |
| 无序列表 | `- 项` |
| 有序列表 | `1. 项` |
| 任务列表 | `- [x] 完成` |
| 表格 | `\| 表头 \| ... \|` |
| 分隔线 | `---` |
| 换行 | 行尾两个空格 或 `<br>` |
| 转义 | `\*` |
