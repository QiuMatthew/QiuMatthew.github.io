---
title: MissingSemester-3-Vim
auther: yuran
date: 2021-09-16 15:05:09
categories:
    - 技术
    - Missing Semester
tags:
    - 技术
    - Missing Semester
    - Vim
---


### Modes
|Mode|Key|
|:---:|:---:|
|normal|\<esc\>|
|insert|i|
|replace|R|
|visual|v|
|visual-line|V|
|visual-block|\<C-V\>|
|command-line|:|

### Command-line Mode
|Key|Function|
|:---:|:---:|
|:w|save|
|:q|quit|
|:h|help|
|:sp|splite into two window|
|:tabnew|create a new tab|
|:qa|quit all|

### Normal Mode
|Key|Function|
|:---:|:---:|
|h|cursor left|
|j|cursor down|
|k|cursor up|
|l|cursor right|
|w|cursor a word ahead|
|b|cursor a word back|
|e|cursor to the end of the word|
|0|cursor to the beginning of the line|
|$|cursor to the end of the line|
|^|cursor to the first non space character of the line|
|\<C-U\>|cursor to a page up|
|\<C-D\>|cursor to a page down|
|G|cursor to the end of the file|
|gg|cursor to the beginning of the file|
|L|cursor to the lowest line that's shown on the screen|
|M|cursor to the middle line that's shown on the screen|
|H|cursor to the highest line that's shown on the screen|
|f+?|move the cursor forward until find the first ?|
|F+?|move the cursor backward until find the first ?|
|t+?|move the cursor forward to one character before first ?|
|T+?|move the cursor backward to one character after first ?|
|o|create a new line under the current cursor, into insert mode|
|O|create a new line above the current cursor, into insert mode|
|dw|delete the word|
|de|delete from the cursor to the end of the word|
|dd|delete the line|
|cw|change the word|
|ce|change from the cursor to the end of the word|
|cc|delete the line, into insert mode|
|x|delete a character|
|r|replace a character|
|u|undo|
|\<C-R\>|redo|
|yy|copy the current line|
|yw|copy a word|
|p|paste|
|~|flick the case of the selected characters|
|ci[|change things inside [] brackets|
|da(|delete all the things inside () brackets and the brackets itself at the same time|
|/|search things in the whole file|
|n|go to the next search example|
|.|repeat the previous command|

### Visual Mode
|Mode|Function|
|:---:|:---:|
|visual|select characters|
|visual-line|select lines|
|visual-block|select rectangular area|

### Counts
We can give vim a number to do a particular thing for some number of times
for normal mode

|Key|Function|
|:---:|:---:|
|4j|move the cursor 4 lines below|
|4k|move the cursor 4 lines up|

for visual mode

|Key|Function|
|:---:|:---:|
|3e|select from the current cursor to the end of the third following word|
|2b|select from the current cursor to 2 words back|

for editing commands

|Key|Function|
|:---:|:---:|
|7dw|delete 7 words|