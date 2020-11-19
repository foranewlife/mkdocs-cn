# 编写文档

如何布局和编写Markdown源文件。

---

## 文件存储结构

你的源文档应该以常规的 MarkDown 文件形式编写（请参考下面的[用 Markdown 写作](#markdown)），并将其放在[文件目录](configuration.md#docs_dir)中。默认情况下，这个 `docs` 目录和 `mkdocs.yml` 配置文件一起位于项目的顶层。

Your documentation source should be written as regular Markdown files (see
[Writing with Markdown](#writing-with-markdown) below), and placed in the
[documentation directory](configuration.md#docs_dir). By default, this directory
will be named `docs` and will exist at the top level of your project, alongside
the `mkdocs.yml` configuration file.

您可以创建的最简单的项目如下所示：

```no-highlight
mkdocs.yml
docs/
    index.md
```

按照惯例，你的项目首页应该被命名为 `index.md`（有关详细信息，请参见下面的[索引页面](#_3)）。以下任何扩展名都可以用于 Markdown 源文件：`markdown`、 `mdown`、`mkdn`、`mkd`、 `md`。无论设置如何，文档目录中包含的所有的 Markdown 文件都将呈现在构建的站点中。



!!! note

    以点开头的文件和文件夹（例如：`.foo.md` 或 `.bar/baz.md`）都会被 Mkdocs 所忽略，这也与大多数 Web 服务器的行为相匹配。没有选项可以替代此行为。

你还可以通过创建几个 Markdown 文件的方法来创建多页文档：

```no-highlight
mkdocs.yml
docs/
    index.md
    about.md
    license.md
```

你使用的文件存储结构确定了用于生成页面的 URL。 根据上述布局，将生成以下 URL 页面：

```no-highlight
/
/about/
/license/
```

如果更适合你的文档存储结构，你还可以将 Markdown 文件包括在嵌套目录中。

```no-highlight
docs/
    index.md
    user-guide/getting-started.md
    user-guide/configuration-options.md
    license.md
```

嵌套目录中的源文件将导致产生 URL 嵌套页面，如下所示：

```no-highlight
/
/user-guide/getting-started/
/user-guide/configuration-options/
/license/
```

MkDocs 会将[文档目录](configuration.md#docs_dir)中未被标识为 Markdown 的文件（通过文件扩展名判断）的所有文件都原样复制到生成的站点中。 有关详情，请参见下面的[如何链接到图像和媒体](#linking-to-images-and-media)。

Any files which are not identified as Markdown files (by their file extension)
within the [documentation directory](configuration.md#docs_dir) are copied by
MkDocs to the built site unaltered. See
[how to link to images and media](#linking-to-images-and-media) below for details.

### 首页

默认情况下，请求网站目录时如果有索引文件的存在，大多数Web服务器将返回该目录中包含的索引文件（通常名为 `index.html`）。因此，上面所有示例中的首页都被命名为 `index.md`，MkDocs 在构建网站时会将其呈现为 `index.html`。

 许多资源库托管站点在浏览目录内容时通过显示 README 文件的内容来提供对 README 文件的特殊处理。因此，MkDocs 允许您将索引页命名为 `README.md` 而不是 `index.md`。这样，当用户浏览你的源代码时，资源托管站点可以显示该目录的索引页，因为它是 README 文件。然而，当MkDocs 渲染你的站点时，该文件将被重命名为 `index.html`，以便服务器将其作为一个适当的索引文件。

如果在同一目录中同时找到了 `index.md` 文件和 `README.md` 文件，则使用 `index.md` 文件，并忽略 `README.md` 文件。

### 配置页面和导航

`mkdocs.yml` 文件中的 [nav](configuration.md#nav) 配置项定义了全局站点导航菜单中包括的页面以及该菜单的结构。如果未提供导航，将通过[文档目录](configuration.md#docs_dir)中的所有的 Markdown 文件来自动创建导航。自动创建的导航配置将始终按文件名的字母数字顺序进行排序（除非索引文件始终始终在子部分中列出）。如果你希望导航菜单的排序方式不同，则需要手动定义导航配置。

一个最小的导航配置如下所示：

The [nav](configuration.md#nav) configuration setting in your `mkdocs.yml` file
defines which pages are included in the global site navigation menu as well as
the structure of that menu. If not provided, the navigation will be
automatically created by discovering all the Markdown files in the
[documentation directory](configuration.md#docs_dir). An automatically created
navigation configuration will always be sorted alphanumerically by file name
(except that index files will always be listed first within a sub-section). You
will need to manually define your navigation configuration if you would like
your navigation menu sorted differently.

A minimal navigation configuration could look like this:

```no-highlight
nav:
    - 'index.md'
    - 'about.md'
```

All paths in the navigation configuration must be relative to the `docs_dir`
configuration option. If that option is set to the default value, `docs`, the
source files for the above configuration would be located at `docs/index.md` and
`docs/about.md`.

The above example will result in two navigation items being created at the top
level and with their titles inferred from the contents of the Markdown file or,
if no title is defined within the file, of the file name. To override the title
in the `nav` setting add a title right before the filename.

```no-highlight
nav:
    - Home: 'index.md'
    - About: 'about.md'
```

Note that if a title is defined for a page in the navigation, that title will be
used throughout the site for that page and will override any title defined
within the page itself.

Navigation sub-sections can be created by listing related pages together under a
section title. For example:

```no-highlight
nav:
    - Home: 'index.md'
    - 'User Guide':
        - 'Writing your docs': 'writing-your-docs.md'
        - 'Styling your docs': 'styling-your-docs.md'
    - About:
        - 'License': 'license.md'
        - 'Release Notes': 'release-notes.md'
```

With the above configuration we have three top level items: "Home", "User Guide"
and "About." "Home" is a link to the homepage for the site. Under the "User
Guide" section two pages are listed: "Writing your docs" and "Styling your
docs." Under the "About" section two more pages are listed: "License" and
"Release Notes."

Note that a section cannot have a page assigned to it. Sections are only
containers for child pages and sub-sections. You may nest sections as deeply as
you like. However, be careful that you don't make it too difficult for your
users to navigate through the site navigation by over-complicating the nesting.
While sections may mirror your directory structure, they do not have to.

Any pages not listed in your navigation configuration will still be rendered and
included with the built site, however, they will not be linked from the global
navigation and will not be included in the `previous` and `next` links. Such
pages will be "hidden" unless linked to directly.

## 用 Markdown 写作

MkDocs pages must be authored in [Markdown][md], a lightweight markup language
which results in easy-to-read, easy-to-write plain text documents that can be
converted to valid HTML documents in a predictable manner.

MkDocs uses the [Python-Markdown] library to render Markdown documents to HTML.
Python-Markdown is almost completely compliant with the [reference
implementation][md], although there are a few very minor [differences].

In addition to the base Markdown [syntax] which is common across all Markdown
implementations, MkDocs includes support for extending the Markdown syntax with
Python-Markdown [extensions]. See the MkDocs' [markdown_extensions]
configuration setting for details on how to enable extensions.

MkDocs includes some extensions by default, which are highlighted below.

[Python-Markdown]: https://python-markdown.github.io/
[md]: https://daringfireball.net/projects/markdown/
[differences]: https://python-markdown.github.io/#differences
[syntax]: https://daringfireball.net/projects/markdown/syntax
[extensions]: https://python-markdown.github.io/extensions/
[markdown_extensions]: configuration.md#markdown_extensions

### Internal links

MkDocs allows you to interlink your documentation by using regular Markdown
[links]. However, there are a few additional benefits to formatting those links
specifically for MkDocs as outlined below.

[links]: https://daringfireball.net/projects/markdown/syntax#link

#### Linking to pages

When linking between pages in the documentation you can simply use the regular
Markdown [linking][links] syntax, including the *relative path* to the Markdown
document you wish to link to.

```no-highlight
Please see the [project license](license.md) for further details.
```

When the MkDocs build runs, these Markdown links will automatically be
transformed into an HTML hyperlink to the appropriate HTML page.

!!! warning
    Using absolute paths with links is not officially supported. Relative paths
    are adjusted by MkDocs to ensure they are always relative to the page. Absolute
    paths are not modified at all. This means that your links using absolute paths
    might work fine in your local environment but they might break once you deploy
    them to your production server.

If the target documentation file is in another directory you'll need to make
sure to include any relative directory path in the link.

```no-highlight
Please see the [project license](../about/license.md) for further details.
```

The [toc] extension is used by MkDocs to generate an ID for every header in your
Markdown documents. You can use that ID to link to a section within a target
document by using an anchor link. The generated HTML will correctly transform
the path portion of the link, and leave the anchor portion intact.

```no-highlight
Please see the [project license](about.md#license) for further details.
```

Note that IDs are created from the text of a header. All text is converted to
lowercase and any disallowed characters, including white-space, are converted to
dashes. Consecutive dashes are then reduced to a single dash.

There are a few configuration settings provided by the toc extension which you
can set in your `mkdocs.yml` configuration file to alter the default behavior:

`permalink`:

: Generate permanent links at the end of each header. Default: `False`.

    When set to True the paragraph symbol (&para; or `&para;`) is used as the
    link text. When set to a string, the provided string is used as the link
    text. For example, to use the hash symbol (`#`) instead, do:
    
        markdown_extensions:
            - toc:
                permalink: "#"

`baselevel`:

: Base level for headers. Default: `1`.

    This setting allows the header levels to be automatically adjusted to fit
    within the hierarchy of your HTML templates. For example, if the Markdown
    text for a page should not contain any headers higher than level 2 (`<h2>`),
    do:
    
        markdown_extensions:
            - toc:
                baselevel: 2
    
    Then any headers in your document would be increased by 1. For example, the
    header `# Header` would be rendered as a level 2 header (`<h2>`) in the HTML
    output.

`separator`:

: Word separator. Default: `-`.

    Character which replaces white-space in generated IDs. If you prefer
    underscores, then do:
    
        markdown_extensions:
            - toc:
                separator: "_"

Note that if you would like to define multiple of the above settings, you must
do so under a single `toc` entry in the `markdown_extensions` configuration
option.

```yml
markdown_extensions:
    - toc:
        permalink: "#"
        baselevel: 2
        separator: "_"
```

[toc]: https://python-markdown.github.io/extensions/toc/

#### Linking to images and media

As well as the Markdown source files, you can also include other file types in
your documentation, which will be copied across when generating your
documentation site. These might include images and other media.

For example, if your project documentation needed to include a [GitHub pages
CNAME file] and a PNG formatted screenshot image then your file layout might
look as follows:

```no-highlight
mkdocs.yml
docs/
    CNAME
    index.md
    about.md
    license.md
    img/
        screenshot.png
```

To include images in your documentation source files, simply use any of the
regular Markdown image syntaxes:

```Markdown
Cupcake indexer is a snazzy new project for indexing small cakes.

![Screenshot](img/screenshot.png)

*Above: Cupcake indexer in progress*
```

Your image will now be embedded when you build the documentation, and should
also be previewed if you're working on the documentation with a Markdown editor.

[GitHub pages CNAME file]: https://help.github.com/articles/using-a-custom-domain-with-github-pages/

#### Linking from raw HTML

Markdown allows document authors to fall back to raw HTML when the Markdown
syntax does not meets the author's needs. MkDocs does not limit Markdown in this
regard. However, as all raw HTML is ignored by the Markdown parser, MkDocs is
not able to validate or convert links contained in raw HTML. When including
internal links within raw HTML, you will need to manually format the link
appropriately for the rendered document.

### Meta-Data

MkDocs includes support for both YAML and MultiMarkdown style meta-data (often
called front-matter). Meta-data consists of a series of keywords and values
defined at the beginning of a Markdown document, which are stripped from the
document prior to it being processing by Python-Markdown. The key/value pairs
are passed by MkDocs to the page template. Therefore, if a theme includes
support, the values of any keys can be displayed on the page or used to control
the page rendering. See your theme's documentation for information about which
keys may be supported, if any.

In addition to displaying information in a template, MkDocs includes support for
a few predefined meta-data keys which can alter the behavior of MkDocs for that
specific page. The following keys are supported:

`template`:

: The template to use with the current page.

    By default, MkDocs uses the `main.html` template of a theme to render
    Markdown pages. You can use the `template` meta-data key to define a
    different template file for that specific page. The template file must be
    available on the path(s) defined in the theme's environment.

`title`:

: The "title" to use for the document.

    MkDocs will attempt to determine the title of a document in the following
    ways, in order:
    
    1. A title defined in the [nav] configuration setting for a document.
    2. A title defined in the `title` meta-data key of a document.
    3. A level 1 Markdown header on the first line of the document body.
       Please note that [Setext-style] headers are not supported.
    4. The filename of a document.
    
    Upon finding a title for a page, MkDoc does not continue checking any
    additional sources in the above list.

[Setext-style]: https://daringfireball.net/projects/markdown/syntax#header

#### YAML Style Meta-Data

YAML style meta-data consists of [YAML] key/value pairs wrapped in YAML style
deliminators to mark the start and/or end of the meta-data. The first line of
a document must be `---`. The meta-data ends at the first line containing an
end deliminator (either `---` or `...`). The content between the deliminators is
parsed as [YAML].

```no-highlight
---
title: My Document
summary: A brief description of my document.
authors:
    - Waylan Limberg
    - Tom Christie
date: 2018-07-10
some_url: https://example.com
---
This is the first paragraph of the document.
```

YAML is able to detect data types. Therefore, in the above example, the values
of `title`, `summary` and `some_url` are strings, the value of `authors` is a
list of strings and the value of `date` is a `datetime.date` object. Note that
the YAML keys are case sensitive and MkDocs expects keys to be all lowercase.
The top level of the YAML must be a collection of key/value pairs, which results
in a Python `dict` being returned. If any other type is returned or the YAML
parser encounters an error, then MkDocs does not recognize the section as
meta-data, the page's `meta` attribute will be empty, and the section is not
removed from the document.

#### MultiMarkdown Style Meta-Data

MultiMarkdown style meta-data uses a format first introduced by the
[MultiMarkdown] project. The data consists of a series of keywords and values
defined at the beginning of a Markdown document, like this:

```no-highlight
Title:   My Document
Summary: A brief description of my document.
Authors: Waylan Limberg
         Tom Christie
Date:    January 23, 2018
blank-value:
some_url: https://example.com

This is the first paragraph of the document.
```

The keywords are case-insensitive and may consist of letters, numbers,
underscores and dashes and must end with a colon. The values consist of anything
following the colon on the line and may even be blank.

If a line is indented by 4 or more spaces, that line is assumed to be an
additional line of the value for the previous keyword. A keyword may have as
many lines as desired. All lines are joined into a single string.

The first blank line ends all meta-data for the document. Therefore, the first
line of a document must not be blank.

!!! note

    MkDocs does not support YAML style deliminators (`---` or `...`) for
    MultiMarkdown style meta-data. In fact, MkDocs relies on the the presence or
    absence of the deliminators to determine whether YAML style meta-data or
    MultiMarkdown style meta-data is being used. If the deliminators are
    detected, but the content between the deliminators is not valid YAML
    meta-data, MkDocs does not attempt to parse the content as MultiMarkdown
    style meta-data.

[YAML]: http://yaml.org
[MultiMarkdown]: http://fletcherpenney.net/MultiMarkdown_Syntax_Guide#metadata
[nav]: configuration.md#nav

### Tables

The [tables] extension adds a basic table syntax to Markdown which is popular
across multiple implementations. The syntax is rather simple and is generally
only useful for simple tabular data.

A simple table looks like this:

```no-highlight
First Header | Second Header | Third Header
------------ | ------------- | ------------
Content Cell | Content Cell  | Content Cell
Content Cell | Content Cell  | Content Cell
```

If you wish, you can add a leading and tailing pipe to each line of the table:

```no-highlight
| First Header | Second Header | Third Header |
| ------------ | ------------- | ------------ |
| Content Cell | Content Cell  | Content Cell |
| Content Cell | Content Cell  | Content Cell |
```

Specify alignment for each column by adding colons to separator lines:

```no-highlight
First Header | Second Header | Third Header
:----------- |:-------------:| -----------:
Left         | Center        | Right
Left         | Center        | Right
```

Note that table cells cannot contain any block level elements and cannot contain
multiple lines of text. They can, however, include inline Markdown as defined in
Markdown's [syntax] rules.

Additionally, a table must be surrounded by blank lines. There must be a blank
line before and after the table.

[tables]: https://python-markdown.github.io/extensions/tables/

### Fenced code blocks

The [fenced code blocks] extension adds an alternate method of defining code
blocks without indentation.

The first line should contain 3 or more backtick (`` ` ``) characters, and the
last line should contain the same number of backtick characters (`` ` ``):

````no-highlight

```
Fenced code blocks are like Standard
Markdown’s regular code blocks, except that
they’re not indented and instead rely on
start and end fence lines to delimit the
code block.
```

````

With this approach, the language can optionally be specified on the first line
after the backticks which informs any syntax highlighters of the language used:

````no-highlight
​```python
def fn():
    pass
```
````  

Note that fenced code blocks can not be indented. Therefore, they cannot be
nested inside list items, blockquotes, etc.

[fenced code blocks]: https://python-markdown.github.io/extensions/fenced_code_blocks/

````