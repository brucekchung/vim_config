# vim_config


execute pathogen#infect()
  
"map leader to comma
let mapleader=","


"CONTROLS ----------
"map jj to escape
imap jj <Esc>
imap jwj <Esc>:w<Enter>

"map o and O so they don't ener insert mode
nnoremap o o<Esc>
nnoremap O O<Esc>

"map c-o and c-i to to change commands
cnoremap <C-o> <Up>
cnoremap <C-i> <Down>

"map c-o and c-i to change buffers
map <C-o> :bn<cr>
map <C-i> :bp<cr>

"map space to search
nmap <space> /

"map vertical split, only window, close window, buffer delete, mru, toggle 
"hlsearch, ack search
nmap <leader>s :vsp<cr>
nmap <leader>o :only<cr>
nmap <leader>c :close<cr>
nmap <leader>d :bd<cr>
nmap <leader>m :MRU<cr>
nmap <leader>t :set hlsearch!<cr>
nnoremap <Leader>a :Ack!<Space>

"call numbertoggle
nnoremap <leader>l :call NumberToggle()<Cr>

"map H and L to start and end line; J and K to pageup and pagedown
nmap H 0
nmap L $
nmap J <PageDown>
nmap K <PageUp>

"map split navigation to omit 'w' from direction...
nnoremap <C-J> <C-W><C-J>
nnoremap <C-K> <C-W><C-K>
nnoremap <C-L> <C-W><C-L>
nnoremap <C-H> <C-W><C-H>

"nerdtree controls
map <C-n> :NERDTreeToggle<Cr>
map <C-f> :NERDTreeFind<Cr>
map <C-d> :NERDTreeCWD<Cr>


"CUSTOMIZED SETTINGS -----------
syntax on
filetype plugin indent on
filetype plugin on
set backspace=indent,eol,start
set complete-=i
syntax enable
set autoindent
set ruler
set wildmenu
set incsearch
set wildignore+=*.pyc,*.o,*.obj,*.svn,*.swp,*.class,*.hg,*.DS_Store,*.min.*

"line numbers
set nu

"mouse enabled
set mouse=n

"tab sizing
set tabstop=4 softtabstop=0 expandtab shiftwidth=2 smarttab

"ignore search case
nnoremap / /\c
nnoremap ? ?\c

"highlight all search matches
set hlsearch

"copy to system clipboard
set clipboard=unnamed

"set number of lines above and below cursor
set scrolloff=3

"MRU settings
let MRU_Max_Entries = 20

"Ack - don't auto open first search result
cnoreabbrev Ack Ack!


"APPEARANCE SETTING ----------
"doesn't show mode ie 'normal', 'visual', 'insert'
set noshowmode

"enables limelight statusbar
set laststatus=2

"omit '|' on vsp
set fillchars+=vert:\ 

"set display for oneline buffer
set display+=lastline

syntax enable
set background=dark
colorscheme solarized

"lightline config
let g:lightline = {
    \ 'active': {
    \   'left': [ [ 'mode', 'paste' ],
    \             [ 'gitbranch', 'readonly', 'filename', 'modified' ] ],
    \   'right': [ [ 'syntastic', 'lineinfo' ],
    \              [ 'percent' ]],
    \ },
    \ 'colorscheme': 'wombat',
    \ 'component_function': {
    \   'gitbranch': 'fugitive#head'
    \ }
    \ }


"CUSTOM FUNCTIONS -----------
function! NumberToggle()
  :exec &nu==0? "se nu!" : "se rnu!"
endfunction
