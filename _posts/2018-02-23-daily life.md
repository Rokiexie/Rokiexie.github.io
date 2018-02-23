---
layout: post
title: 日常吐槽
categories: blog
description: 深度的努力焦虑症
keywords: daily life
---

讨厌现在的生活状态....



## 想想取啥标题

[test](http://www.youku.com)

![](/images/posts/vim/vim-markdown-outline.png)

## 实现啥

### 待编辑



1. 在 vimrc 文件里添加如下内容：

   ```viml
   Plugin 'majutsushi/tagbar'
   ```

2. 执行 `:so $MYVIMRC`

3. 执行 `:PluginInstall`

### 安装 Exuberant ctags



下载地址：<http://ctags.sourceforge.net/>。


tagbar 默认并不支持 Markdown 文件，但配置一下就好了。

1. 给 ~/.ctags 文件（Windows 下是 `C:\Users\<username>\.ctags` 里增加如下内容，没有这个文件就新建一个：

   ```viml
   --langdef=markdown
   --langmap=markdown:.md
   --regex-markdown=/^#{1}[ \t]*([^#]+.*)/. \1/h,heading1/
   --regex-markdown=/^#{2}[ \t]*([^#]+.*)/.   \1/h,heading2/
   --regex-markdown=/^#{3}[ \t]*([^#]+.*)/.     \1/h,heading3/
   --regex-markdown=/^#{4}[ \t]*([^#]+.*)/.       \1/h,heading4/
   --regex-markdown=/^#{5}[ \t]*([^#]+.*)/.         \1/h,heading5/
   --regex-markdown=/^#{6}[ \t]*([^#]+.*)/.           \1/h,heading6/
   ```

   这表示提取 Markdown 文件里的一到六级标题，并使用空格缩进表示层次。

2. 给你的 vimrc 文件里增加如下内容：

   ```viml
   let g:tagbar_type_markdown = {
           \ 'ctagstype' : 'markdown',
           \ 'kinds' : [
                   \ 'h:headings',
           \ ],
       \ 'sort' : 0
   \ }
   ```

   配置 tagbar 支持 Markdown。

### 更多自定义配置

1. 现在你可以使用 `:TagbarToggle<CR>` 来打开导航窗格了，但每次开关导航窗格都要敲这么长一串命令毕竟不够方便，配置快捷键来操作更顺手，在你的 vimrc 文件里增加一个映射：

   ```viml
   nnoremap <leader>tb :TagbarToggle<CR>
   ```

   现在你可以使用 `<leader>tb` 来随时开/关导航窗格了。

2. 导航窗格默认是在右边，如果你也像我一样喜欢它在左边，也想指定它的宽度，可以在你的 vimrc 文件里配置：

   ```viml
   let g:tagbar_width = 30
   let g:tagbar_left = 1
   ```

至此，大功告成了！
