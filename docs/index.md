# MkDocs

使用 Markdown 构建项目文档。

---

## 说明

本文档为 [MkDocs](https://github.com/mkdocs/mkdocs/) 项目的中文文档翻译，本站并非中文官方网站（事实上也并不存在所谓的中文官方网站）。这里仅出于个人爱好进行文档翻译，为中国开发者提供阅读方便，文档翻译内容将以翻译内容准确无误为第一准则，建议有一定英语基础的开发者或使用者进行英文阅读。

MkDocs 英文文档：[https://www.mkdocs.org](https://www.mkdocs.org)

MkDocs 中文文档：[https://mkdocs.writeup.top](https://mkdocs.writeup.top)

备用中文文档站点：[https://writeup007.github.io/mkdocs-cn](https://writeup007.github.io/mkdocs-cn)

Mkdocs 项目地址：[https://github.com/mkdocs/mkdocs](https://github.com/mkdocs/mkdocs)

---

## 概述

MkDocs 是一个 **快速**，**简单** 且 **非常华丽的** 一个静态网站生成器。因此它是非常适合用来构建项目文档。 项目文档使用 Markdown 进行书写，然后通过一个简单的 YAML 文件进行相关配置。 首先阅读下面的内容，然后查看用户使用指南来获取更多信息。

### 在任意地方托管

MkDocs 可以构建完全静态的 HTML 站点，以至于你可以托管在 GitHub pages，Amazon S3，或者你选择的[任意地方][deploy] 。

### 很棒的主题可使用

MkDocs 提供了非常多的漂亮[主题][themes]。可以在内置主题 [mkdocs][mkdocs] 和   [readthedocs][readthedocs] 进行选择，也可以在  [MkDocs 主题] [MkDocs Themes] 列表页面中进行选择一个第三方主题，或者构建[自己的主题][build your own]。

### 实时预览你的站点

内置的实时预览功能允许你在编写文档时进行预览站点内容。每当你保存更改时时，它甚至会自动重载并刷新你的浏览器。

### 易于个性化定制

通过自定义主题[theme]和/或安装一些插件[plugins]，让你的项目文档看起来如同你所期待的那样。

---

## 安装

### 使用软件包管理器进行安装

如果你拥有并软件包管理器（比如 [apt-get]，[dnf]，[homebrew]，[yum]，[chocolatey] 等等）在你的系统上安装软件包。那么你应该去搜索一个名叫 "MkDocs" 的软件包，如果存在最新的版本是可用的，那么用你的软件包管理器（详细信息请查看你的系统文档）来安装它。就是这样，你已经完成了！你可以直接跳到[开始页面](#开始)。

如果你的软件包管理器没有最近的 "MkDocs" 软件包，你仍然可以使用你的软件包管理器来安装 "Python" 和 "pip"。然后你就可以使用 pip 来[安装 MkDocs](#安装)。


[apt-get]: https://help.ubuntu.com/community/AptGet/Howto
[homebrew]: https://brew.sh/
[dnf]: https://dnf.readthedocs.io/en/latest/index.html
[yum]: http://yum.baseurl.org/
[chocolatey]: https://chocolatey.org/

### 手动安装

为了手动安装 MkDocs 你需要在你的系统上安装好 [Python] 以及 Python 包管理器 pip。你可以从命令行检查是否已经安装了它们：

```bash
$ python --version
Python 3.8.2
$ pip --version
pip 20.0.2 from /usr/local/lib/python3.8/site-packages/pip (python 3.8)
```

MkoDocs 支持 Python 3.5，3.6，3.7，3.8版本和 pypy3。

#### 安装 Python

通过从 [python.org] 下载一个适合你系统的安装程序并且运行它进行安装。

!!! Note

    如果你是在 Windows 上安装 Python，在安装程序提供了如下选项的情况下（默认情况下它是关闭的），请确保你选中该复选框以便将 Python 添加进环境变量。
    
    ![Add Python to PATH](img/win-py-install.png)

[python.org]: https://www.python.org/downloads/

#### 安装 pip

如果你正在使用最新版的 Python，那么这个 Python 软件包管理器 [pip] 在默认情况下是很有可能已经安装了的。尽管如此，你可能仍需要更新 pip 到最新的版本：

```bash
pip install --upgrade pip
```

如果你是第一次安装 [pip] 请下载 [get-pip.py] 然后执行如下命令进行安装：

```bash
python get-pip.py
```

#### 安装 MkDocs

使用 pip 安装 `mkdocs` 软件包:

```bash
pip install mkdocs
```

现在你的系统上应该已经安装了 `mkdocs` 命令。执行 `mkdocs --version` 来检查是否一切正常。

```bash
$ mkdocs --version
mkdocs, version 0.15.3
```

!!! Note
    如果您希望为 MkDocs 安装手册，[click-man] 工具可以为你生成并安装它们。只需执行如下两行命令即可：

        pip install click-man
        click-man --target path/to/man/pages mkdocs
    
    查看这个 [click-man documentation] 文档来了解为什么 pip 没有自动生成和安装这个手册。See the [click-man documentation] for an explanation of why manpages are
    not automatically generated and installed by pip.

[click-man]: https://github.com/click-contrib/click-man
[click-man documentation]: https://github.com/click-contrib/click-man#automatic-man-page-installation-with-setuptools-and-pip

!!! Note
    如果你正在使用 Windows，上面的一些命令可能无法立即使用。

    一个快速的解决办法是在每个 python 命令前加上 `python -m` 像这样：
    
        python -m pip install mkdocs
        python -m mkdocs
    
    要获得更永久的解决方案，你可能需要将 Python 的 `Scripts` 目录添加到 `PATH` 环境变量中。最新版的 Python 已经为你准备了一个小脚本工具。打开你的 Python 安装目录（例如 `C:\python38\`），打开 `Tools` 文件夹，然后打开 `Scripts` 文件夹，最后通过双击执行 `win_add2path.py` 来自动添加环境变量。或者你可以[下载][a2p]这个脚本然后执行它（`python win_add2path.py`）。

[a2p]: https://svn.python.org/projects/python/trunk/Tools/scripts/win_add2path.py

---

## 开始

开始入门是非常容易的。

```bash
mkdocs new my-project
cd my-project
```

花点时间查看一下为你创建的初始项目。

![The initial MkDocs layout](img/initial-layout.png)

那只有一个单独的 `mkdocs.yml` 配置文件和一个包含了你的源文件的 `docs` 文件夹。现在这个 `docs` 文件夹只包含一个 `index.md` 的文档页面。

MkDocs 带有内置的开发服务器，可让您在处理文档时预览文档。确保你和 `mkdocs.yml` 配置文件处于同一目录，然后通过执行 `mkdocs serve` 命令来启动这个服务：

```bash
$ mkdocs serve
INFO    -  Building documentation...
INFO    -  Cleaning site directory
[I 160402 15:50:43 server:271] Serving on http://127.0.0.1:8000
[I 160402 15:50:43 handlers:58] Start watching changes
[I 160402 15:50:43 handlers:60] Start detecting changes
```

在你的浏览器打开 `http://127.0.0.1/80000/`，然后你就能看到这个默认的主页：

![The MkDocs live server](img/screenshot.png)

内置的开发服务器还支持自动重载，并且只要配置文件，文档目录或主题目录中的任何文件发生改变，它都将自动重新生成站点内容。

用你的 txt 编辑器打开这个 `docs/index.md` 文档，将这个初始的默认标题改为 `MkLorum`，然后进行保存。你的浏览器将自动重新加载，你应该能够立刻看到更新后的文档。

仙子啊试着编辑这个配置文件：`mkdocs.yml`。将这个 [`site_name`][site_name] 设置项修改为 `MkLorum` 然后保存文件。

```yaml
site_name: MkLorum
```

你的浏览器应该会立即自动重新加载，然后你将看到你的新的站点名字已经生效了。

![The site_name setting](img/site-name.png)

## 添加页面

现在在文档中添加第二个页面：

```bash
curl 'https://jaspervdj.be/lorem-markdownum/markdown.txt' > docs/about.md
```

如果你想在我们的文档网站上添加一些导航标题，你可能需要编辑配置文件，然后通过添加[`导航`][nav]设置在导航标题中添加有关每个页面的顺序，标题和嵌套的一些信息：

```yaml
site_name: MkLorum
nav:
    - Home: index.md
    - About: about.md
```

保存所做的修改，然后你就能看到一个导航栏，左侧带有 `Home` 和 `About` 标签，右侧带有 `search` ，`Previous` 和 `Next` 标签。

![Screenshot](img/multipage.png)



尝试菜单项并在页面之间来回导航。 然后点击 `Search`，将出现一个搜索对话框，使您可以搜索任何页面上的任何文本。 请注意，搜索结果包括网站上搜索关键词的每一次出现，并直接链接到搜索词出现的页面部分。 您可以毫不费力地完成所有工作！

![Screenshot](img/search.png)

## 为我们的文档添加主题

现在我们通过更改配置文件的方式来更改主题，以此来改变文档的显示方式。编辑 `mkdocs.yml` 文件，然后新增一个 [`theme`][主题] 设置选项：

```yaml
site_name: MkLorum
nav:
    - Home: index.md
    - About: about.md
theme: readthedocs
```

保存所做的修改，然后你将会看到已经正在使用 ReadTheDocs 主题了。

![Screenshot](img/readthedocs.png)

## 修改 Favicon 图标

默认情况下，MkDocs 使用 [MkDocs favicon] 图标。想要使用不同的图标，请在你的 `doc_dir` 目录下创建一个 `img` 文件夹，然后复制你自定义的 `favicon.ico` 文件到该目录。MkDocs 将会自动检测然后使用该文件作为你的 favicon 图标。

[MkDocs favicon]: /img/favicon.ico

## 构建网站

看起来一切顺利。你已经准备好了第一次部署你的 `MkLorum` 站点了。首先构建文档：

```bash
mkdocs build
```

这将创建一个新的名为 `site` 的文件夹，看一下里面有什么：

```bash
$ ls site
about  fonts  index.html  license  search.html
css    img    js          mkdocs   sitemap.xml
```

可以看到你的源文档已经被生成并输出为两个 HTML 文件了，分别是 `index.html` 和 `about/index.html`。还有其他各种媒体文件，它们也作为文档主题的一部分被复制到了 `site` 目录。你甚至拥有一个 `sitemap.xml` 和 `mkdocs/search_index.json` 文件。

如果你使用的是 `git` 之类的源代码控制工具，你可能不想将你文档生成的站点上传到存储仓库上，只需要将 `site` 添加到你的 `.gitignore` 文件中即可。

```bash
echo "site/" >> .gitignore
```

如果你使用的是其他的源代码控制工具，那么你可能需要去查看相关文档，了解怎样去忽略特定的目录。

过一会儿，文件可能会从文档中删除，但是它们将会仍将保留在 `site` 目录内。想要移除这些文件，只需要执行 `mkdocs` 命令并带上 `--clean` 参数即可。

```bash
mkdocs build --clean
```

## 其他命令和选项

还有其他的各种命令和选项可用，使用 `--help` 参数查看完整的命令列表：

```bash
mkdocs --help
```

要查看给定命令的可用选项列表，请在该命令中使用 `--help` 参数。例如，要获取所有可用于 `build` 命令的选项列表，请执行以下命令：

```bash
mkdocs build --help
```

## Deploying

The documentation site that you just built only uses static files so you'll be
able to host it from pretty much anywhere. Simply upload the contents of the
entire `site` directory to wherever you're hosting your website from and
you're done. For specific instructions on a number of common hosts, see the
[Deploying your Docs][deploy] page.

## Getting help

To get help with MkDocs, please use the [discussion group], [GitHub issues] or
the MkDocs IRC channel `#mkdocs` on freenode.

[deploy]: user-guide/deploying-your-docs/
[mkdocs]: user-guide/styling-your-docs/#mkdocs
[readthedocs]: user-guide/styling-your-docs/#readthedocs
[theme]: user-guide/styling-your-docs/
[themes]: user-guide/styling-your-docs/
[plugins]: user-guide/plugins/
[MkDocs Themes]: https://github.com/mkdocs/mkdocs/wiki/MkDocs-Themes
[build your own]: user-guide/custom-themes/
[get-pip.py]: https://bootstrap.pypa.io/get-pip.py
[nav]: user-guide/configuration/#nav
[discussion group]: https://groups.google.com/forum/#!forum/mkdocs
[GitHub issues]: https://github.com/mkdocs/mkdocs/issues
[pip]: https://pip.readthedocs.io/en/stable/installing/
[Python]: https://www.python.org/
[site_name]: user-guide/configuration/#site_name
[theme]: user-guide/configuration/#theme
