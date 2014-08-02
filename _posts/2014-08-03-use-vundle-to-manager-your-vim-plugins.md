---
layout: article
categories: [vim]
tags: [vim]
title: 使用 Vundle 来管理你的 Vim 插件
---

开始接触某个技术的时间比较早有个坏处，那就是容易养成一些“过时”的习惯。比如我至今都不会用 [CPAN Minus][]，也很不习惯 [Sublime Text][]，
虽然明知道它们是好东西。

所幸最近这个情况略微有了一些改观，那就是我开始学会了用 Vundle 来管理我的 vim 插件。

在用 Vundle 来管理我的 vim 插件之前，我通常的做法是到 [Vim 官网][vim] 上去搜索我想要的插件。找到了之后，点击里面的下载链接，下载一个压缩包下来，
然后解压到 <kbd>$HOME/.vim</kbd> 目录。

如果运气好的话，这个插件就可以满足我的预期。否则可能还要把它解压产生的那些文件都删掉，然后换另一个插件试试。
好不容易全部都调试满意了，我可能还有其它几台主机也需要做同样的设置。这其中还包括 Windows，而有些插件可能在 Windows 下不能很好地工作，需要禁止。

等把所有这一切都做完之后，一段时间之后某些插件更新了，其中可能修复了某个重要的 BUG，或者提供了某个重要的 feature，又得折腾一遍。
如果遇上插件重构目录结构都和原来不一样的情况下，真是太痛苦了。

如果你也正在经历这样的痛苦的话，那么我强烈推荐你用 Vundle 来管理自己的插件。

[Vundle 的官网][Vundle]提供了它的特性介绍和安装使用方法。
简单来说，它有以下几个作用：

*   **它可以一键安装、一键清理、一键升级大多数的插件。**

    笔者的 .vimrc 里面有下面的内容：

    >       flw@debian:~$ grep ^Plugin ~/.vimrc-flw
    >       Plugin 'gmarik/Vundle.vim'
    >       Plugin 'godlygeek/tabular'
    >       Plugin 'gabrielelana/vim-markdown'
    >       Plugin 'vimwiki/vimwiki'
    >       Plugin 'yegappan/mru'
    >       Plugin 'jlanzarotta/bufexplorer'
    >       Plugin 'mbbill/VimExplorer'
    >       Plugin 'nsf/gocode'
    >       Plugin 'taglist.vim'
    >       flw@debian:~$

    然后如果我有一个崭新的工作环境的话，只需要 checkout 一下我的 vimrc，然后 PluginInstall 就可以一次性安装所有上面的这些插件了。

*   **它通过维护 vim 的 runtime path 设置来让每个接受它管理的插件都呆在一个单独的目录。**
    
    这意味着即使想要手工管理插件也会变得更加容易。就像这样：

    >       flw@debian:~$ ls -l ~/.vim/bundle/
    >       总用量 36
    >       drwxr-xr-x  5 flw flw 4096 8月   2 22:45 bufexplorer
    >       drwxr-xr-x 11 flw flw 4096 8月   3 02:50 gocode
    >       drwxr-xr-x  4 flw flw 4096 8月   2 22:24 mru
    >       drwxr-xr-x  7 flw flw 4096 8月   3 02:15 tabular
    >       drwxr-xr-x  5 flw flw 4096 8月   2 22:17 taglist.vim
    >       drwxr-xr-x  5 flw flw 4096 8月   2 22:45 VimExplorer
    >       drwxr-xr-x 10 flw flw 4096 8月   2 23:16 vim-markdown
    >       drwxr-xr-x  8 flw flw 4096 8月   2 22:00 vimwiki
    >       drwxr-xr-x  6 flw flw 4096 8月   2 21:30 Vundle.vim
    >       flw@debian:~$ ls -l ~/.vim/bundle/vimwiki/
    >       总用量 24
    >       drwxr-xr-x 3 flw flw 4096 8月   2 22:00 autoload
    >       drwxr-xr-x 2 flw flw 4096 8月   2 22:00 doc
    >       drwxr-xr-x 2 flw flw 4096 8月   2 22:00 ftplugin
    >       drwxr-xr-x 2 flw flw 4096 8月   2 22:00 plugin
    >       -rw-r--r-- 1 flw flw 3941 8月   2 22:00 README.md
    >       drwxr-xr-x 2 flw flw 4096 8月   2 22:00 syntax
    >       flw@debian:~$

[CPAN Minus]: https://metacpan.org/pod/distribution/App-cpanminus/bin/cpanm (CPAN 官网推荐的安装 CPAN 模块的方法)
[Sublime Text]: http://www.sublimetext.com/ (著名的 Mac 程序员编辑器 TextMate 的克隆，提供 Windows 版的下载)
[vim-scripts]: http://vim-scripts.org/ (一个时尚的 Vim 脚本集散地)
[Vundle]: https://github.com/gmarik/Vundle.vim
[vim]: http://www.vim.org/
