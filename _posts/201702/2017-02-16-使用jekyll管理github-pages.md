---
layout: post

title: "使用jekyll来管理你的github pages"
date: 2017-02-16 10:20:01 +0800

categories: post
tags: [github, jekyll, blog]
---

>本人环境配置
```
Ubuntu: 16.10
git: 2.9.3
```

1. 在 **github** 创建个人pages,并将 github pages **clone** 到本地
    ```bash
    $ git clone https://github.com/itaken/itaken.github.io.git
    ```

1. 进入你本地的github pages目录, 使用`jekyll new`创建你的博客.
    ```bash
    cd itaken.github.io
    $ jekyll new .
    ```
    >报错, 提示文件夹不为空:
    ```
    Conflict: /path/to/itaken.github.io exists and is not empty.
    ```
    可以使用`--force`, 强制新建一个jekyll项目. (**\*注意**: 使用force将_清空_原文件夹文件)
    ```bash
    $ jekyll new . --force
    ```

1. 开启jekyll服务 [^1], 打开 [http://127.0.0.1:4000/](http://127.0.0.1:4000/) 即可看到blog页面了.

    ```shell
    $ jekyll serve
    ```

1. 开始使用`markdown`书写你的blog吧.
    >也许今天天气不错, 是时候来段代码提提神了.

1. 提交到 `github`
    ```bash
    $ git add .
    $ git commit -m "提交信息"
    $ git push origin master
    ```

---
### 更多阅读
- [jekyll quick start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)
- [jekyll markdown internal links](http://stackoverflow.com/questions/4629675/jekyll-markdown-internal-links)
- [Jekyll: How to get markdown parsing inside blocks using Kramdown?](http://stackoverflow.com/questions/22291211/jekyll-how-to-get-markdown-parsing-inside-blocks-using-kramdown)

---
### 索引

[^1]: [jekyllrb usage](https://jekyllrb.com/docs/usage/)
