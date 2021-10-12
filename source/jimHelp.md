
```vimdoc

Patience !   Takes a few minutes to finish.
!pandoc --metadata=project:JIM --lua-filter doc/panvimdoc/scripts/skip-blocks.lua --lua-filter doc/panvimdoc/scripts/include-files.lua -t doc/panvimdoc/scripts/panvimdoc.lua % -o doc/jimHelp.txt

# ============================================
PURPOSE:    Render .md, .txt. .R, .Rmd files
USING:      pandoc, latex, knitr ....
Jump to this file:      |jim_knitr_pandoc_latex|
# ============================================

as of \today:  
    *  To mix latex and .md, must go with pdf, either pandoc or knit  
    *  Add r, knitr code to YAML?   then must render as .RMD file
    *  I do not know how to embed latex, produce html or md (github flavor).  
```

## jim_PDF                                                                    

 PDF   [ignores html, css; also ignores YAML header (pandoc & ::render()]

 To create pdf, just about everything works:  pandoc, markdown, latex, knitr..

  NOTE:   .tex uses a .sty which I do not have.  USE  knitr:: (with TinyTex
  to locate and install that .sty file)  

```vimdoc       
TODO: pandoc may think 2nd `%` is both relative directory and file name

!pandoc % -f markdown -o %.pdf

!pandoc % -f markdown  -t latex -H ../chapter_break.tex -V linkcolor:blue -V fontsize=11pt -V geometry:margin=0.3in -o ~/Downloads/print_and_delete/out.pdf
!pandoc % -f markdown  -t latex -H ../chapter_break.tex -V linkcolor:blue -V fontsize=11pt -V geometry:margin=0.3in -o out.pdf 
!pandoc % -f markdown  --pdf-engine xelatex -H chapter_break.tex -V linkcolor:blue -V fontsize=11pt -V geometry:margin=0.3in -o ~/Downloads/print_and_delete/out.pdf

!pandoc --metadata=project:JIM --lua-filter doc/panvimdoc/scripts/skip-blocks.lua --lua-filter doc/panvimdoc/scripts/include-files.lua  -t doc/panvimdoc/scripts/panvimdoc.lua % -o doc/source/jim_knitr_pandoc_latex.txt

```
    


## jim_HTML

  HTML [to produce HTML with pandoc, all latex is IGNORED.]  

 HTML is pain in ass and HUGE time waste.  Pandoc can handle markdown and
 small amounts of latex (math) b/c ppl have added filters or other widgets to
 pandoc.

 Avoid experiments:   will waste time.
 If using Latex, its packages, diagrams with Latex ... must go with PDF.


  *  !pandoc % -f markdown -V linkcolor:blue -V fontsize=11pt -V geometry:margin=0.3in -o out/out.html 


-H header  
-V or --variable  
--pdf-engine=xelatex  


*Create pdf from straight txt* 
(do not process any markdown)

pandoc balks at processing straight text if it things it sees markdown.
If lucky, !pandoc % -o file.pdf will work.

**BEST**  print_me.sh *.txt file;  then use browser to print and save as .pdf
*.R  - NOPE, Firefox chokes.



# writing_notes

*jim_writing_notes1*

Template for .md

http://www.terminally-incoherent.com/blog/2013/06/17/using-vim-for-writing-prose/

## hard wrap is friend  

a=automatic reformat
t=wrap at textwidth

setlocal formatoptions=ant
setlocal textwidth=80
setlocal wrapmargin=0
setlocal foldcolumn=3 		"trick, to set left margin	 


Long parapgarapja l;akdsjf asalkfjas d; asdfk;ladsjf  lk;adjf a;lkaf as;l
asdfjl; adsfl;kj d;as fasdj;lkj afds;lkj 

##	Turn off indents

(no c indents)

setlocal noautoindent  
setlocal nocindent  
setlocal nosmartindent  
setlocal indentexpr=  


# LUA
```vimdoc
!pandoc --metadata=project:JIM --lua-filter doc/panvimdoc/scripts/skip-blocks.lua --lua-filter doc/panvimdoc/scripts/include-files.lua  -t doc/panvimdoc/scripts/panvimdoc.lua % -o doc/jimlua.txt
```

JIM's LUA help notes
  


*lua*

In lua, nil or false evaluate to:  false
0 or '', evaluate to: true


*lua2*

The contents of this cheatsheet should be stored at 
`~/.config/nvim/plugged/vim-myhelp/doc/myhelp.txt`


# lua3
bottom



#   To Create Vimdoc

##  Level 2

This is level 2, has 2 hash marks.

### Level 3 

This is level 3, has 3 hash marks.

<!-- USAGE
pandoc --metadata=project:${PROJECT} --lua-filter scripts/skip-blocks.lua --lua-filter scripts/include-files.lua -t scripts/panvimdoc.lua ${INPUT} -o ${OUTPUT}

!pandoc --metadata=project:JIM --lua-filter doc/panvimdoc/scripts/skip-blocks.lua --lua-filter doc/panvimdoc/scripts/include-files.lua -t doc/panvimdoc/scripts/panvimdoc.lua % -o doc/to_create_vimdoc.txt
-->

# SOURCE md file

SOURCE markdown file to_create_vimdoc is located in jimHelp/source

# Resulting txt file.
The resulting txt file will be located in jimHelp/doc


# Topic 1 
As of 12 OCT, 2021;  run this pandoc you MUST be in directory:
~/code/jimHelp/

```vimdoc

!pandoc --metadata=project:JIM --lua-filter doc/panvimdoc/scripts/skip-blocks.lua --lua-filter doc/panvimdoc/scripts/include-files.lua  -t doc/panvimdoc/scripts/panvimdoc.lua % -o doc/to_create_vimdoc.txt
```

````
this is 4 backticks.
````

# Topic 2 

To do:   topic 2 has no content.



# Vim Notes

1. Reloading your vim configuration                       *myhelp-config-reload*

   - :so % : Reloads your vim configuration while editing.

===============================================================================

====
USAGE:     :h jimVimNotes  " Opens this file as read-only HELP file


HELPTAGS and Ctags are NOT related (do not confuse).

For helptags:
MUST use *.txt
MUST put in /doc folder of a plugin, here:  jimHelp/

To change file:  edit this file as regular file.
Dislike Highighting?   :set syntax=off
Add a tag:     surround new tag with * ; plus prose to describe tag
Add a hotlink:   ONLY in same file (I think) surround new tag with |

Run :helptags ALL to regenerate file called tags
/doc file (singular) :  should see this .txt file and tags file

restart vim
:h jimVimNotes
====

Tags in this file:
|jimVert|
|jim_vim_help|
|jim_common_tasks|
|jim_system_stuff|

To remove highlighting:   set syntax=off

*jimVert*

Following sets things up:
* open .R file
* start R (should be bottom)
* :vert h    (open help on right)

:h windows.txt
:h vert
:h splitright


:h new   " open new WINDOW
:h enew  " new buffer, in current window

*jim_system_stuff*
:view $VIMRUNTIME
:view $TEMPLATES

*jim_auto_commands*
:h autocmd
:h au



[all docs files](~/docs/)
[code files](~/code/)

*jim_freq_help*
**Help files**
:h abbreviation


:h help-summary
:h helphelp
:h help.txt
:h helpgrep
:h usr_toc.txt



:h startup
:h cmdline 
:h exe    (use cmd line to run normal cmds?)
:h startinsert


*jim_common_tasks*
####  Help for common tasks
:h :abbreviate
:h :augroup
:h :changes
:h :highlight
:h :syntax
:h :command
:h :file
:h :filetype
:h :messages
:h :options  :h options.txt  :h :set

:h :scriptnames


*jim_split*
:h :split
:vert help    " open help in vertical split


# Pandoc Notes

as of \today:  
    *  To mix latex and .md, must go with pdf, either pandoc or knit  
    *  Add r, knitr code to YAML?   then must render as .RMD file
    *  I do not know how to embed latex, produce html or md (github flavor).  

 ===    
  PDF   [ignores html, css; also ignores YAML header (pandoc & ::render()]
 ===  

  NOTE:   .tex uses a .sty which I do not have.  USE  knitr:: (with TinyTex
  to locate and install that .sty file)  

TODO: pandoc may think 2nd `%` is both relative directory and file name

!pandoc % -f markdown -o %.pdf

!pandoc % -f markdown  -t latex -H ../chapter_break.tex -V linkcolor:blue -V fontsize=11pt -V geometry:margin=0.3in -o ~/Downloads/print_and_delete/out.pdf
!pandoc % -f markdown  -t latex -H ../chapter_break.tex -V linkcolor:blue -V fontsize=11pt -V geometry:margin=0.3in -o out.pdf 
!pandoc % -f markdown  --pdf-engine xelatex -H chapter_break.tex -V linkcolor:blue -V fontsize=11pt -V geometry:margin=0.3in -o ~/Downloads/print_and_delete/out.pdf


 ====  
  HTML [ignores latex]  
 ====    

  *  !pandoc % -f markdown -V linkcolor:blue -V fontsize=11pt -V geometry:margin=0.3in -o out/out.html 


# LINUX/ZSH notes



To Jump to File Under Cursor
# ============================
gf   (goto file)

#
# USAGE:  :h jimLinux.txt   this file
#         :h jimlua.txt
#         :h jimhelp.txt
#         :h generic_help.txt
#         :h myhelp.txt (original plugin help)
#         :h tags
# 




STEP #1
add/modify helpfile ....  ~/.config/nvim/vim-plug/vim-myhelp/doc/*.txt

STEP #2 
To a tag, put the tag between two asteriks

STEP #3
in `tags` file,  add ..

STEP #4, finds all files in doc/ directory
```
helpt ~/.config/nvim/vim-plug/vim-myhelp/
```

You can create a `tags` file that allows you to then type 
`:h myhelp-cheatsheet` to quickly jump here. The command to do that is

# ============
#
#
*jim_Permissions*
u g o   (user group other)



*grep_vs_ls*
*Grep* always finds words that match a pattern and returns file names of
matches.

ls (+ glob) finds filenames that match a pattern.  Very differnt.
(same in vim)

*jim_GLOB_examples*
Mostly of form ls or ll or print -l    and **/*
example:   print -l ~/code/**/*.(R|Rmd)   # any level, return all .R and .Rmd
files

See my zsh GLOG handwritten notes (till typed in here)

*zle_widgets* (all commands)
Output from zle -al (~403 cmds)
.accept-and-hold
.accept-and-infer-next-history
.accept-and-menu-complete
.accept-line
.accept-line-and-down-history
.accept-search
.argument-base
.auto-suffix-remove
.auto-suffix-retain
.backward-char
.backward-delete-char
.backward-delete-word
.backward-kill-line
.backward-kill-word
.backward-word
.beep
.beginning-of-buffer-or-history
.beginning-of-history
.beginning-of-line
.beginning-of-line-hist
.bracketed-paste
.capitalize-word
.clear-screen
.complete-word
.copy-prev-shell-word
.copy-prev-word
.copy-region-as-kill
.deactivate-region
.delete-char
.delete-char-or-list
.delete-word
.describe-key-briefly
.digit-argument
.down-case-word
.down-history
.down-line
.down-line-or-history
.down-line-or-search
.emacs-backward-word
.emacs-forward-word
.end-of-buffer-or-history
.end-of-history
.end-of-line
.end-of-line-hist
.end-of-list
.exchange-point-and-mark
.execute-last-named-cmd
.execute-named-cmd
.expand-cmd-path
.expand-history
.expand-or-complete
.expand-or-complete-prefix
.expand-word
.forward-char
.forward-word
.get-line
.gosmacs-transpose-chars
.history-beginning-search-backward
.history-beginning-search-forward
.history-incremental-pattern-search-backward
.history-incremental-pattern-search-forward
.history-incremental-search-backward
.history-incremental-search-forward
.history-search-backward
.history-search-forward
.infer-next-history
.insert-last-word
.kill-buffer
.kill-line
.kill-region
.kill-whole-line
.kill-word
.list-choices
.list-expand
.magic-space
.menu-complete
.menu-expand-or-complete
.neg-argument
.overwrite-mode
.pound-insert
.push-input
.push-line
.push-line-or-edit
.put-replace-selection
.quote-line
.quote-region
.quoted-insert
.read-command
.recursive-edit
.redisplay
.redo
.reset-prompt
.reverse-menu-complete
.run-help
.select-a-blank-word
.select-a-shell-word
.select-a-word
.select-in-blank-word
.select-in-shell-word
.select-in-word
.self-insert
.self-insert-unmeta
.send-break
.set-local-history
.set-mark-command
.spell-word
.split-undo
.transpose-chars
.transpose-words
.undefined-key
.undo
.universal-argument
.up-case-word
.up-history
.up-line
.up-line-or-history
.up-line-or-search
.vi-add-eol
.vi-add-next
.vi-backward-blank-word
.vi-backward-blank-word-end
.vi-backward-char
.vi-backward-delete-char
.vi-backward-kill-word
.vi-backward-word
.vi-backward-word-end
.vi-beginning-of-line
.vi-caps-lock-panic
.vi-change
.vi-change-eol
.vi-change-whole-line
.vi-cmd-mode
.vi-delete
.vi-delete-char
.vi-digit-or-beginning-of-line
.vi-down-case
.vi-down-line-or-history
.vi-end-of-line
.vi-fetch-history
.vi-find-next-char
.vi-find-next-char-skip
.vi-find-prev-char
.vi-find-prev-char-skip
.vi-first-non-blank
.vi-forward-blank-word
.vi-forward-blank-word-end
.vi-forward-char
.vi-forward-word
.vi-forward-word-end
.vi-goto-column
.vi-goto-mark
.vi-goto-mark-line
.vi-history-search-backward
.vi-history-search-forward
.vi-indent
.vi-insert
.vi-insert-bol
.vi-join
.vi-kill-eol
.vi-kill-line
.vi-match-bracket
.vi-open-line-above
.vi-open-line-below
.vi-oper-swap-case
.vi-pound-insert
.vi-put-after
.vi-put-before
.vi-quoted-insert
.vi-repeat-change
.vi-repeat-find
.vi-repeat-search
.vi-replace
.vi-replace-chars
.vi-rev-repeat-find
.vi-rev-repeat-search
.vi-set-buffer
.vi-set-mark
.vi-substitute
.vi-swap-case
.vi-undo-change
.vi-unindent
.vi-up-case
.vi-up-line-or-history
.vi-yank
.vi-yank-eol
.vi-yank-whole-line
.visual-line-mode
.visual-mode
.what-cursor-position
.where-is
.which-command
.yank
.yank-pop
_bash_complete-word
_bash_list-choices
_complete_debug
_complete_help
_complete_tag
_correct_filename
_correct_word
_expand_alias
_expand_word
_history-complete-newer
_history-complete-older
_list_expansions
_most_recent_file
_next_tags
_read_comp
accept-and-hold
accept-and-infer-next-history
accept-and-menu-complete
accept-line
accept-line-and-down-history
accept-search
argument-base
auto-suffix-remove
auto-suffix-retain
backward-char
backward-delete-char
backward-delete-word
backward-kill-line
backward-kill-word
backward-word
beep
beginning-of-buffer-or-history
beginning-of-history
beginning-of-line
beginning-of-line-hist
bracketed-paste
capitalize-word
clear-screen
complete-word
copy-prev-shell-word
copy-prev-word
copy-region-as-kill
deactivate-region
delete-char
delete-char-or-list
delete-word
describe-key-briefly
digit-argument
down-case-word
down-history
down-line
down-line-or-history
down-line-or-search
emacs-backward-word
emacs-forward-word
end-of-buffer-or-history
end-of-history
end-of-line
end-of-line-hist
end-of-list
exchange-point-and-mark
execute-last-named-cmd
execute-named-cmd
expand-cmd-path
expand-history
expand-or-complete
expand-or-complete-prefix
expand-word
forward-char
forward-word
get-line
gosmacs-transpose-chars
history-beginning-search-backward
history-beginning-search-forward
history-incremental-pattern-search-backward
history-incremental-pattern-search-forward
history-incremental-search-backward
history-incremental-search-forward
history-search-backward
history-search-forward
infer-next-history
insert-last-word
kill-buffer
kill-line
kill-region
kill-whole-line
kill-word
list-choices
list-expand
magic-space
menu-complete
menu-expand-or-complete
neg-argument
overwrite-mode
pound-insert
push-input
push-line
push-line-or-edit
put-replace-selection
quote-line
quote-region
quoted-insert
read-command
recursive-edit
redisplay
redo
reset-prompt
reverse-menu-complete
run-help
select-a-blank-word
select-a-shell-word
select-a-word
select-in-blank-word
select-in-shell-word
select-in-word
self-insert
self-insert-unmeta
send-break
set-local-history
set-mark-command
spell-word
split-undo
transpose-chars
transpose-words
undefined-key
undo
universal-argument
up-case-word
up-history
up-line
up-line-or-history
up-line-or-search
vi-add-eol
vi-add-next
vi-backward-blank-word
vi-backward-blank-word-end
vi-backward-char
vi-backward-delete-char
vi-backward-kill-word
vi-backward-word
vi-backward-word-end
vi-beginning-of-line
vi-caps-lock-panic
vi-change
vi-change-eol
vi-change-whole-line
vi-cmd-mode
vi-delete
vi-delete-char
vi-digit-or-beginning-of-line
vi-down-case
vi-down-line-or-history
vi-end-of-line
vi-fetch-history
vi-find-next-char
vi-find-next-char-skip
vi-find-prev-char
vi-find-prev-char-skip
vi-first-non-blank
vi-forward-blank-word
vi-forward-blank-word-end
vi-forward-char
vi-forward-word
vi-forward-word-end
vi-goto-column
vi-goto-mark
vi-goto-mark-line
vi-history-search-backward
vi-history-search-forward
vi-indent
vi-insert
vi-insert-bol
vi-join
vi-kill-eol
vi-kill-line
vi-match-bracket
vi-open-line-above
vi-open-line-below
vi-oper-swap-case
vi-pound-insert
vi-put-after
vi-put-before
vi-quoted-insert
vi-repeat-change
vi-repeat-find
vi-repeat-search
vi-replace
vi-replace-chars
vi-rev-repeat-find
vi-rev-repeat-search
vi-set-buffer
vi-set-mark
vi-substitute
vi-swap-case
vi-undo-change
vi-unindent
vi-up-case
vi-up-line-or-history
vi-yank
vi-yank-eol
vi-yank-whole-line
visual-line-mode
visual-mode
what-cursor-position
where-is
which-command
yank
yank-pop
zle-line-finish
zle-line-init

*bindkey*  # results, all shortcuts

"^A"-"^C" self-insert
"^D" list-choices
"^E"-"^F" self-insert
"^G" list-expand
"^H" vi-backward-delete-char
"^I" expand-or-complete
"^J" accept-line
"^K" self-insert
"^L" clear-screen
"^M" accept-line
"^N"-"^P" self-insert
"^Q" vi-quoted-insert
"^R" redisplay
"^S"-"^T" self-insert
"^U" vi-kill-line
"^V" vi-quoted-insert
"^W" vi-backward-kill-word
"^X^R" _read_comp
"^X?" _complete_debug
"^XC" _correct_filename
"^Xa" _expand_alias
"^Xc" _correct_word
"^Xd" _list_expansions
"^Xe" _expand_word
"^Xh" _complete_help
"^Xm" _most_recent_file
"^Xn" _next_tags
"^Xt" _complete_tag
"^X~" _bash_list-choices
"^Y" self-insert
"^Z" backward-delete-word
"^[" vi-cmd-mode
"^[," _history-complete-newer
"^[/" _history-complete-older
"^[OA" up-line-or-history
"^[OB" down-line-or-history
"^[OC" vi-forward-char
"^[OD" vi-backward-char
"^[[1~" vi-beginning-of-line
"^[[200~" bracketed-paste
"^[[2~" overwrite-mode
"^[[3~" vi-delete-char
"^[[4~" vi-end-of-line
"^[[A" up-line-or-history
"^[[B" down-line-or-history
"^[[C" vi-forward-char
"^[[D" vi-backward-char
"^[~" _bash_complete-word
"^\\\\"-"~" self-insert
"^?" vi-backward-delete-char
"\M-^@"-"\M-^?" self-insert
# vim: filetype=help:ts=2



jim_xfce4_help.txt                                       25  SEP 2021

DO NOT DELETE


====
*jim_xfce4_help*  (hot links point to here)
USAGE:     :h jim_xfce4_help  " Opens this file as read-only HELP file

HELPTAGS and Ctags are NOT related (do not confuse).

For helptags:
MUST use *.txt
MUST put in /doc folder of a plugin, here:  jimHelp/

To change file:  edit this file as regular file.
Dislike Highighting?   :set syntax=off
Add a tag:     surround new tag with * ; plus prose to describe tag
Add a hotlink:   ONLY in same file (I think) surround new tag with |

Run :helptags ALL to regenerate file called tags
/doc file (singular) :  should see this .txt file and tags file

restart vim
:h jim_xfce4_help
====

Tags in this file:

|jim_xfce4_help| (link) to tag at top

To remove highlighting:   set syntax=off


#### xfce4
Shortcuts: https://docs.xfce.org/apps/terminal/start#keyboard_shortcuts
HELP:   https://docs.xfce.org/apps/terminal/4.12/start

Based on VTE Widget terminal (gnome uses)

ALT-F10  toggle bet min/max (NOPE!)

ALT-TAB  rotate through open windows?
:
