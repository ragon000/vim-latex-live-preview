A Vim Plugin for Lively Previewing Pandoc PDF Output
===================================================

This plugin provides a live preview of the output PDF of your Pandoc file. The
display of the output PDF file will be updated lively as you type (just hold
the cursor and you will see the PDF file updated). Currently,
vim-pandoc-live-preview only support UNIX-like systems. 

Table of Contents
-----------------

- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)

Installation
------------

Before installing, you need to make sure your Vim version is later than 7.3,
and is compiled with `+python` feature.

### [vim-plug](https://github.com/junegunn/vim-plug)

Add the plugin in the vim-plug section of your `~/.vimrc`:

```vim
call plug#begin('~/.vim/plugged')
[...]
" A Vim Plugin for Lively Previewing Pandoc PDF Output
Plug 'ragon000/vim-pandoc-live-preview', { 'for': ['md', 'pandoc'] } 
" 'pandoc' if using the vim-pandoc plugin
[...]
call plug#end()
```

Then reload the config and install the new plugin. Run inside `vim`:

```vim
:so ~/.vimrc
:PlugInstall
```

### [Vundle](https://github.com/VundleVim/Vundle.vim)

Add the plugin in the Vundle section of your `~/.vimrc`:

```vim
call vundle#begin()
[...]
" A Vim Plugin for Lively Previewing Pandoc PDF Output
Plugin 'ragon000/vim-latex-live-preview'
[...]
call vundle#end()
```

Then reload the config and install the new plugin. Run inside `vim`:

```vim
:so ~/.vimrc
:PluginInstall
```

### Manually

Copy `plugin/pandoclivepreview.vim` to `~/.vim/plugin`.


Usage
-----

Simply execute `:LLPStartPreview` to launch the previewer. Then try to type in
Vim and you should see the live update. The updating time could be set by Vim's
['updatetime'][] option. If your pdf viewer crashes when updates happen, you can
try to set 'updatetime' to a higher value to make it update less frequently. The
suggested value of 'updatetime' is `1000`.

Configuration
-------------

### PDF viewer

By default, you need to have [mupdf][], [evince][] or [okular][] installed as pdf viewers.
But you can specify your own viewer by setting `g:livepreview_previewer`
option in your `.vimrc`:

```vim
let g:livepreview_previewer = 'your_viewer'
```

Please note that not every pdf viewer could work with this plugin. Currently
mupdf, evince and okular are known to work well.

- [mupdf][] works best as it can refresh the page without flickering

### Pandoc Arguments

If you want to use custom pandoc arguments, you can set them by setting `g:livepreview_arguments`
option in your `.vimrc`:

```vim
let g:livepreview_arguments = '-V pagesize=a4 --pdf-engine=pdflatex'
```


TODO
----

- [x] Make Pandoc arguments settable via a variable
- [ ] Make a gif to show usage

['updatetime']: http://vimdoc.sourceforge.net/htmldoc/options.html#%27updatetime%27
[evince]: http://projects.gnome.org/evince/
[okular]: http://okular.kde.org/
[mupdf]: https://mupdf.com/
