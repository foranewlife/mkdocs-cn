# 说明

本文档为 MkDocs 项目的中文文档翻译，为中国开发者提供阅读方便，本站并非官方中文站点（事实上也并不存在所谓的官方中文站点）这里仅处于个人爱好进行文档翻译，文档翻译内容将以翻译内容准确无误为第一准则，建议有一定英语基础的开发者使用者进行英文阅读。

MkDocs 英文文档：[https://www.mkdocs.org](https://www.mkdocs.org)

MkDocs 中文文档：[https://mkdocs.writeup.top](https://mkdocs.writeup.top)

# MkDocs

使用 Markdown 构建项目文档。

---

## 概述

MkDocs 是一个 **快速**, **简单** 且 **非常华丽的** 一个静态网站生成器。因此它是非常适合用来构建项目文档。 项目文档使用 Markdown 进行书写，然后通过一个简单的 YAML 文件进行相关配置。 首先阅读下面的内容，然后查看用户使用指南来获取更多信息。

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

If you're using a recent version of Python, the Python package manager, [pip],
is most likely installed by default. However, you may need to upgrade pip to the
lasted version:

```bash
pip install --upgrade pip
```

If you need to install [pip] for the first time, download [get-pip.py].
Then run the following command to install it:

```bash
python get-pip.py
```

#### Installing MkDocs

Install the `mkdocs` package using pip:

```bash
pip install mkdocs
```

You should now have the `mkdocs` command installed on your system. Run `mkdocs
--version` to check that everything worked okay.

```bash
$ mkdocs --version
mkdocs, version 0.15.3
```

!!! Note
    If you would like manpages installed for MkDocs, the [click-man] tool can
    generate and install them for you. Simply run the following two commands:

        pip install click-man
        click-man --target path/to/man/pages mkdocs
    
    See the [click-man documentation] for an explanation of why manpages are
    not automatically generated and installed by pip.

[click-man]: https://github.com/click-contrib/click-man
[click-man documentation]: https://github.com/click-contrib/click-man#automatic-man-page-installation-with-setuptools-and-pip

!!! Note
    If you are using Windows, some of the above commands may not work
    out-of-the-box.

    A quick solution may be to preface every Python command with `python -m`
    like this:
    
        python -m pip install mkdocs
        python -m mkdocs
    
    For a more permanent solution, you may need to edit your `PATH` environment
    variable to include the `Scripts` directory of your Python installation.
    Recent versions of Python include a script to do this for you. Navigate to
    your Python installation directory (for example `C:\Python38\`), open the
    `Tools`, then `Scripts` folder, and run the `win_add2path.py` file by double
    clicking on it. Alternatively, you can [download][a2p] the script and run it
    (`python win_add2path.py`).

[a2p]: https://svn.python.org/projects/python/trunk/Tools/scripts/win_add2path.py

---

## Getting Started

Getting started is super easy.

```bash
mkdocs new my-project
cd my-project
```

Take a moment to review the initial project that has been created for you.

![The initial MkDocs layout](img/initial-layout.png)

There's a single configuration file named `mkdocs.yml`, and a folder named
`docs` that will contain your documentation source files. Right now the `docs`
folder just contains a single documentation page, named `index.md`.

MkDocs comes with a built-in dev-server that lets you preview your documentation
as you work on it. Make sure you're in the same directory as the `mkdocs.yml`
configuration file, and then start the server by running the `mkdocs serve`
command:

```bash
$ mkdocs serve
INFO    -  Building documentation...
INFO    -  Cleaning site directory
[I 160402 15:50:43 server:271] Serving on http://127.0.0.1:8000
[I 160402 15:50:43 handlers:58] Start watching changes
[I 160402 15:50:43 handlers:60] Start detecting changes
```

Open up `http://127.0.0.1:8000/` in your browser, and you'll see the default
home page being displayed:

![The MkDocs live server](img/screenshot.png)

The dev-server also supports auto-reloading, and will rebuild your documentation
whenever anything in the configuration file, documentation directory, or theme
directory changes.

Open the `docs/index.md` document in your text editor of choice, change the
initial heading to `MkLorum`, and save your changes. Your browser will
auto-reload and you should see your updated documentation immediately.

Now try editing the configuration file: `mkdocs.yml`. Change the
[`site_name`][site_name] setting to `MkLorum` and save the file.

```yaml
site_name: MkLorum
```

Your browser should immediately reload, and you'll see your new site name take
effect.

![The site_name setting](img/site-name.png)

## Adding pages

Now add a second page to your documentation:

```bash
curl 'https://jaspervdj.be/lorem-markdownum/markdown.txt' > docs/about.md
```

As our documentation site will include some navigation headers, you may want to
edit the configuration file and add some information about the order, title, and
nesting of each page in the navigation header by adding a [`nav`][nav]
setting:

```yaml
site_name: MkLorum
nav:
    - Home: index.md
    - About: about.md
```

Save your changes and you'll now see a navigation bar with `Home` and `About`
items on the left as well as `Search`, `Previous`, and `Next` items on the
right.

![Screenshot](img/multipage.png)

Try the menu items and navigate back and forth between pages. Then click on
`Search`. A search dialog will appear, allowing you to search for any text on
any page. Notice that the search results include every occurrence of the search
term on the site and links directly to the section of the page in which the
search term appears. You get all of that with no effort or configuration on your
part!

![Screenshot](img/search.png)

## Theming our documentation

Now change the configuration file to alter how the documentation is displayed by
changing the theme. Edit the `mkdocs.yml` file and add a [`theme`][theme] setting:

```yaml
site_name: MkLorum
nav:
    - Home: index.md
    - About: about.md
theme: readthedocs
```

Save your changes, and you'll see the ReadTheDocs theme being used.

![Screenshot](img/readthedocs.png)

## Changing the Favicon Icon

By default, MkDocs uses the [MkDocs favicon] icon. To use a different icon, create
an `img` subdirectory in your `docs_dir` and copy your custom `favicon.ico` file
to that directory. MkDocs will automatically detect and use that file as your
favicon icon.

[MkDocs favicon]: /img/favicon.ico

## Building the site

That's looking good. You're ready to deploy the first pass of your `MkLorum`
documentation. First build the documentation:

```bash
mkdocs build
```

This will create a new directory, named `site`. Take a look inside the
directory:

```bash
$ ls site
about  fonts  index.html  license  search.html
css    img    js          mkdocs   sitemap.xml
```

Notice that your source documentation has been output as two HTML files named
`index.html` and `about/index.html`. You also have various other media that's
been copied into the `site` directory as part of the documentation theme. You
even have a `sitemap.xml` file and `mkdocs/search_index.json`.

If you're using source code control such as `git` you probably don't want to
check your documentation builds into the repository. Add a line containing
`site/` to your `.gitignore` file.

```bash
echo "site/" >> .gitignore
```

If you're using another source code control tool you'll want to check its
documentation on how to ignore specific directories.

After some time, files may be removed from the documentation but they will still
reside in the `site` directory. To remove those stale files, just run `mkdocs`
with the `--clean` switch.

```bash
mkdocs build --clean
```

## Other Commands and Options

There are various other commands and options available. For a complete list of
commands, use the `--help` flag:

```bash
mkdocs --help
```

To view a list of options available on a given command, use the `--help` flag
with that command. For example, to get a list of all options available for the
`build` command run the following:

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
