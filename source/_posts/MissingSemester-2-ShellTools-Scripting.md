---
title: MissingSemester-2-ShellTools&Scripting
auther: yuran
date: 2021-09-11 18:09:59
categories:
    - 技术
    - Missing Semester
tags:
    - 技术
    - Missing Semester
    - Linux
---

### Define a variable
```shell
>>> foo=bar
>>> echo $foo
bar
>>> foo = bar
command not found: foo
>>> echo "Hello"
Hello
>>> echo 'World'
World
>>> echo "Value is $foo"
Value is bar
>>> echo 'Value is $foo'
Value is $foo 
```

<!--more-->

### Use functions in shell
```shell
>>> cat mcd.sh
mcd () {
    mkdir -p "$1"
    cd "$1"
}
>>> source mcd.sh
>>> pwd
/mnt/c/Users/Q_Mas/Desktop/missing-semester/2-shell
>>> mcd test
>>> pwd
/mnt/c/Users/Q_Mas/Desktop/missing-semester/2-shell/test
>>> cd ..
```

### Marks for replacing the previous command
```shell
>>> pwd
/mnt/c/Users/Q_Mas/Desktop/missing-semester/2-shell
>>> rmdir test
>>> mkdir test
>>> cd $_
>>> pwd
/mnt/c/Users/Q_Mas/Desktop/missing-semester/2-shell/test
>>> cd ..
>>> mkdir /mnt/new
mkdir: cannot create directory ‘/mnt/new’: Permission denied
>>> sudo !!
sudo mkdir /mnt/new
[sudo] password for matthew:
>>> 
```

|Syntax|Description                              |
|:----:|:----------------------------------------|
|$?    |The error code of the previous command   |
|$0    |The name of the script                   |
|$1    |The first argument                       |
|$2    |The second argument                      |
|$9    |The ninth argument                       |
|$_    |The last argument of the previous command|
|!!    |The last command                         |

### Error code and conditional statement
```shell
>>> echo Hello
Hello
>>> echo $?
0
>>> grep mkdir mcd.sh
    mkdir -p "$1"
>>> echo $?
0
>>> grep foobar mcd.sh
>>> echo $?
1
>>> true
>>> echo $?
0
>>> false
>>> echo $?
1
>>> false || echo "Oops fail"
Oops fail
>>> true || echo "Will not be printed"
>>> true && echo "Things went well"
Things went well
>>> false && echo "Will not be printed"
>>> false ; echo "This will always print"
This will always print
```

### Marks to replace command's output
```shell
>>> pwd
/mnt/c/Users/Q_Mas/Desktop/missing-semester/2-shell
>>> foo=$(pwd)
>>> echo $foo
/mnt/c/Users/Q_Mas/Desktop/missing-semester/2-shell
>>> echo "We are in $(pwd)"
We are in /mnt/c/Users/Q_Mas/Desktop/missing-semester/2-shell
>>> cat <(ls) <(ls ..)
2-shell.md
mcd.sh
test
1-overview
2-shell
3-vim
```

### Globbing and cartesian product
```ps
>>> ls
2-shell.md  mcd.sh  test
>>> ls *sh
mcd.sh
>>> mkdir project1 project2 project42
>>> mkdir project1/src project2/src
>>> ls project?
project1:
src

project2:
src
>>> touch image.png
>>> ls
2-shell.md  image.png  mcd.sh  project1  project2  project42  test
>>> convert image.png image.jpg
>>> ls
2-shell.md  image.jpg  mcd.sh  project1  project2  project42  test
>>> convert image.{jpg,png}
>>> ls
2-shell.md  image.png  mcd.sh  project1  project2  project42  test
>>> touch foo{,1,2,10}
>>> ls
2-shell.md  foo  foo1  foo10  foo2  image.png  mcd.sh  project1  project2  project42  test
>>> touch project{1,2}/src/test{1,2,3}.py
>>> ls project?/src
project1/src:
test1.py  test2.py  test3.py

project2/src:
test1.py  test2.py  test3.py
>>> mkdir fo bar
>>> ls
2-shell.md  bar  fo  foo  foo1  foo10  foo2  image.png  mcd.sh  project1  project2  project42  test
>>> touch {fo,bar}/{a..j}
>>> ls fo bar
bar:
a  b  c  d  e  f  g  h  i  j

fo:
a  b  c  d  e  f  g  h  i  j
>>> touch fo/x bar/y
>>> diff <(ls fo) <(ls bar)
11c11
< x
---
> y
```

### Combining bash scripts with other scripts(eg. python program)
```shell
>>> cat script.py
#!/usr/local/bin/python
import sys
for arg in reversed(sys.argv[1,]):
    print(arg)
# foobar
>>> python script.py a b c 
c
b
a
>>> ./script.py a b c
-bash: ./script.py: /usr/local/bin/python: bad interpreter: No such file or directory
>>> vim script.py
>>> cat script.py
#!/usr/bin/env python
import sys
for arg in reversed(sys.argv[1,]):
    print(arg)
# foobar
>>> ./script.py a b c
c
b
a
```
Shebang: A single line starts with '#!', telling the shell how to run this program


### Shellcheck
Command shellcheck helps us to check our bash script


### Manuals
man
tldr


### Search
```shell
>>> find . -name src -type d
./project1/src
./project2/src
>>> find . -path '**/project1/*.py' -type f
./project1/src/test1.py
./project1/src/test2.py
./project1/src/test3.py
>>> find . -path '**/project?/*.py' -type f
./project1/src/test1.py
./project1/src/test2.py
./project1/src/test3.py
./project2/src/test1.py
./project2/src/test2.py
./project2/src/test3.py
>>> find . -mtime -1
.
./2-shell.md
./bar
./bar/a
./bar/b
./bar/c
./bar/d
./bar/e
./bar/f
./bar/g
./bar/h
./bar/i
./bar/j
./bar/y
./fo
./fo/a
./fo/b
./fo/c
./fo/d
./fo/e
./fo/f
./fo/g
./fo/h
./fo/i
./fo/j
./fo/x
./foo
./foo1
./foo10
./foo2
./image.png
./project1
./project1/src
./project1/src/test1.py
./project1/src/test2.py
./project1/src/test3.py
./project2
./project2/src
./project2/src/test1.py
./project2/src/test2.py
./project2/src/test3.py
./project42
./script.py
./test
>>> find . -path '*/project1/*.py' -exec rm {} \;
>>> echo $?
0
>>> find . -path '*/project1/*.py'
>>> fd ".*py"
>>> locate 3-vim
/mnt/c/Users/Q_Mas/Desktop/missing-semester/3-vim
/mnt/c/Users/Q_Mas/Desktop/missing-semester/3-vim/3-vim.md
>>> grep foobar script.py
# foobar
>>> grep -R foobar .
./script.py:# foobar
>>> rg "import sys" -t py .
./script.py
2:import sys
>>> rg "import sys" -t py -C 10 .
./script.py
1-#!/usr/local/bin/python
2:import sys
3-for arg in reversed(sys.argv[1,]):
4-    print(arg)
5-# foobar
>>> rg -u --files-without-match "#!" -t sh
mcd.sh
>>> rg "import" --stats
script.py
2:import sys

1 matches
1 matched lines
1 files contained matches
39 files searched
23 bytes printed
135 bytes searched
0.002229 seconds spent searching
0.007077 seconds
>>> ack
>>> ag
```

|Argument for command find|Description                   |
|:-----------------------:|:-----------------------------|
|-name                    |Name of the file              |
|-type                    |Type of the file              |
|-path                    |Path of the file              |
|-mtime                   |Last modified time of the file|
|-exec                    |Do something to the file      |

|Argument for command rg|Description                   |Note                                  |
|:---------------------:|:-----------------------------|:-------------------------------------|
|-t                     |Type of the file              |d:directory                           |
|-C                     |Print nearby rows             |                                      |
|-u                     |Don't ignore hidden files     |                                      |
|--files-withou-match   |Do not match the given pattern|                                      |
|--stats                |Show the stats of the result  |Like how many results, time spent, etc|


### History
```shell
>>> history
  ...
  ...
  347  rg "import" --stats
>>> history 10
  339  sudo apt install fdclone
  340  rg "import sys" -t py .
  341  rg "import sys" -t py -C 10 .
  342  rg "import sys"
  343  rg -u --files-without-match
  344  rg -u --files-without-match "#!"
  345  rg -u --files-without-match "#!" -t sh
  346  rg "import" --stat
  347  rg "import" --stats
  348  history
>>> history | fzf
  ...
  ...
  3 cd Q_Mas/
  2 cd ..
  1 ls
```


### File structure
```shell
>>> ls -R
.:
2-shell.md  bar  fo  foo  foo1  foo10  foo2  image.png  mcd.sh  project1  project2  project42  script.py  test

./bar:
a  b  c  d  e  f  g  h  i  j  y

./fo:
a  b  c  d  e  f  g  h  i  j  x

./project1:
src

./project1/src:
test1.tmp  test2.tmp  test3.tmp

./project2:
src

./project2/src:
test1.py  test1.tmp  test2.py  test2.tmp  test3.py  test3.tmp

./project42:

./test:
>>> tree
.
├── 2-shell.md
├── bar
│   ├── a
│   ├── b
│   ├── c
│   ├── d
│   ├── e
│   ├── f
│   ├── g
│   ├── h
│   ├── i
│   ├── j
│   └── y
├── fo
│   ├── a
│   ├── b
│   ├── c
│   ├── d
│   ├── e
│   ├── f
│   ├── g
│   ├── h
│   ├── i
│   ├── j
│   └── x
├── foo
├── foo1
├── foo10
├── foo2
├── image.png
├── mcd.sh
├── project1
│   └── src
│       ├── test1.tmp
│       ├── test2.tmp
│       └── test3.tmp
├── project2
│   └── src
│       ├── test1.py
│       ├── test1.tmp
│       ├── test2.py
│       ├── test2.tmp
│       ├── test3.py
│       └── test3.tmp
├── project42
├── script.py
└── test
>>> broot
need rust environment
>>> nnn
something having interactive input using navigation arrows like File Explorer in Windows
```