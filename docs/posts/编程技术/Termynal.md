---
date:
    created: 2025-02-15
tags:
    - 编程技术
---

# Termynal：一个有趣的终端动画插件

搭建这个博客网站时看到[MkDocs Material 的文档](https://squidfunk.github.io/mkdocs-material/setup/setting-up-a-blog/#rss){target=_blank}中写着 Blog 支持 RSS 订阅。浏览了一下这个 RSS 插件的[文档网站](https://guts.github.io/mkdocs-rss-plugin/){target=_blank}，发现主页就有一个模拟 `pip install` 的终端动画，挺有意思的，于是顺藤摸瓜找到了这个插件，Termynal。

<!-- more -->

最早这个项目还没有封装成插件，最近的 commit 已经是 2018 年了。
见：:fontawesome-brands-github: [termynal.js](https://github.com/ines/termynal){target=_blank}

后来有人将其做成了 MkDocs 的插件，使用起来非常方便。见：:fontawesome-brands-github: [termynal.py](https://github.com/termynal/termynal.py){target=_blank}

## 安装

<!-- termynal -->

```bash
> pip install termynal
---> 100%
Installed
```

之后在 `mkdocs.yml` 中添加插件配置：

```yaml
plugins:
  - termynal
```

指定输入提示符：

```yaml
plugins:
  - termynal
    prompt_literal_start:
        - "$"
        - ">"
```

Then you're all set! :tada:

## 使用

在要展示的代码块前加上一行 HTML 注释 `<!-- termynal -->` 即可。

输入的内容以 `>` 或 `$` 开头（在 `mkdocs.yml` 中指定过），输出的内容直接写就行。

!!! example "示例"

    ````python
    <！-- termynal --> # (1)!

    ```bash
    > pip show termynal
    Name: termynal
    Version: 0.13.0
    Summary: A lightweight and modern animated terminal window
    Home-page: https://termynal.github.io/termynal.py/
    Author: Danil Akhtarov
    Author-email: daxartio@gmail.com
    （后略）
    ```
    ````

    1. 经多次尝试，在代码块里面的 `<!-- termynal -->` 也会被识别变成动画。为了展示只能把 `!` 改成全角字符 `！` 了。

    效果：

    <!-- termynal -->

    ```bash
    > pip show termynal
    Name: termynal
    Version: 0.13.0
    Summary: A lightweight and modern animated terminal window
    Home-page: https://termynal.github.io/termynal.py/
    Author: Danil Akhtarov
    Author-email: daxartio@gmail.com
    （后略）
    ```

### 显示进度条

```bash
> pip install termynal
---> 100%
```

输出的动画即[安装](Termynal.md#_1)一节中展示的效果。

### 窗口标题

在注释里加上 `title` 参数。

```markdown
<！-- termynal: {title: 安装 Termynal} -->

code here
```

## 配置

这个插件使用简单，不过相比原项目可调整的参数少很多。

总共有三个参数可以配置：

| 参数 | 说明 | 默认值 |
| :--: | :--: | :--: |
| `prompt_literal_start` | 输入提示符 | `["$"]` |
| `title` | 窗口标题 | `"bash"` |
| `buttons` | 窗口样式 | `"macos"` |

其中 `buttons` 可选值有 `"macos"` 和 `"windows"`。

如同上面[修改窗口标题](Termynal.md#_4)的方法，每个代码块的参数可以上方的注释中指定以覆盖全局配置。

!!! example "PowerShell"

    注释的一行这么写：

    `<!-- termynal: {"prompt_literal_start": ["$", ">>>", "PS >"], title: powershell, buttons: windows} -->`

    ```bash
    PS > python
    >>> import json
    ```

    效果：

    <!-- termynal: {"prompt_literal_start": ["$", ">>>", "PS >"], title: powershell, buttons: windows} -->

    ```bash
    PS > python
    >>> import json
    ```

## 结语

小而美的一个插件，希望功能还能进一步完善（更高程度的样式自定义、代码块内不渲染动画等）。

---

**参考资料/相关链接**：

- :fontawesome-brands-github: [termynal.js](https://github.com/ines/termynal){target=_blank}
- :fontawesome-brands-github: [termynal.py](https://github.com/termynal/termynal.py){target=_blank}
- :fontawesome-brands-github: [mkdocs-rss-plugin](https://github.com/Guts/mkdocs-rss-plugin){target=_blank}
- ![](https://guts.github.io/mkdocs-rss-plugin/assets/logo_rss_plugin_mkdocs.png){.logo-img-inline} [MkDocs RSS Plugin 文档站点](https://guts.github.io/mkdocs-rss-plugin/){target=_blank}
- :simple-materialformkdocs: [Termynal 文档站点](https://termynal.github.io/termynal.py/){target=_blank}
- Special thanks to [![Material for MkDocs](https://img.shields.io/badge/Material_for_MkDocs-526CFE?style=for-the-badge&logo=MaterialForMkDocs&logoColor=white){style="vertical-align: middle;"}](https://squidfunk.github.io/mkdocs-material/){target=_blank} that made all of these plugins and sites (including this blog) possible.