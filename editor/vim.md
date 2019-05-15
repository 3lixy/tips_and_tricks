# VIM

##### show existing tab with 4 spaces width
```
" show existing tab with 4 spaces width
set tabstop=4
```

##### when indenting with '>', use 4 spaces width
```
" when indenting with '>', use 4 spaces width
set shiftwidth=4
```

##### On pressing tab, insert 4 spaces
```
" On pressing tab, insert value of tabstop as spaces
set expandtab
```

##### Each time a new or existing file is edited, Vim will try to recognize the type of the file and set the 'filetype' option. This will trigger the FileType event, which can be used to set the syntax highlighting, set options, etc.
```
filetype on
```

##### The result is that when a file is edited its plugin file is loaded (if there is one for the detected filetype).
```
filetype plugin on
```

##### The result is that when a file is edited its indent file is loaded (if there is one for the detected filetype). indent-expression
```
filetype indent on
```

##### Force vimdiff to wrap lines
```
au VimEnter * if &diff | execute 'windo set wrap' | endif
```



