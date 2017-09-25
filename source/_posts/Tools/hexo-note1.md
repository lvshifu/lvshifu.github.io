---
title: Hexo笔记1--Hexo注意事项
date: 2017-01-12 12:18:02
tags:
  - Hexo
categories:
---
# Hexo乱码问题
初始安装Hexo后，配置文件和示例post的编码不是UTF-8格式，写入中文字符后，生成静态文件会产生乱码。另存为UTF-8格式后，问题即可解决。

<!--more-->
# Hexo主题语言不对问题
按照官方文档的描述， <code>_config.yml</code> 里面 <code>language</code> 的默认值为 <code>en</code>，改成中文的的话，要改成的两个字母的代码，即为<code>zh</code>，这时应用主题时（Jacman）会发现主题的内容还是使用了英文，查看主题所在目录， 发现languages目录下有下面三个文件

    default.yml
    zh-CN.yml
    zh-TW.yml

尝试把 <code>language</code> 改成 <code>zh-CN</code> 后，主题的中文显示正常。

# hexo-filter-sequence插件
[hexo-filter-sequence](https://github.com/bubkoo/hexo-filter-sequence)v1.0.0的代码有错，直接沿用了hexo-filter-flowchart的代码，因此配置部分的

    sequence:
      # webfont:     # optional, the source url of webfontloader.js
      # snap:        # optional, the source url of snap.svg.js
      # underscore:  # optional, the source url of underscore.js
      # sequence:    # optional, the source url of sequence-diagram.js
      # css: # optional, the url for css, such as hand drawn theme
      options:
        theme:
        css_class:

应该改成

    flowchart:
      # webfont:     # optional, the source url of webfontloader.js
      # snap:        # optional, the source url of snap.svg.js
      # underscore:  # optional, the source url of underscore.js
      # sequence:    # optional, the source url of sequence-diagram.js
      # css: # optional, the url for css, such as hand drawn theme
      options:
        theme:
        css_class:

这样修改后和hexo-filter-flowchart的配置会混在一起，建议更改hexo-filter-sequence的代码，把里面的config.flowchart全部改成config.sequence即可。

v1.0.3错误还在。

另外js-sequence-diagrams从v2开始用 Snap.svg 替换了 raphael， 提示 raphael 出错时，配置里面改成

    sequence: https://bramp.github.io/js-sequence-diagrams/js/sequence-diagram-min.js

即可


# Hexo GitHub 发布问题
Hexo默认没有安装github插件
npm install hexo-deployer-git --save
