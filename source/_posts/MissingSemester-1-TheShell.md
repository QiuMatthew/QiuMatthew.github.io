---
title: MissingSemester-1-TheShell
auther: yuran
date: 2021-08-28 20:24:19
categories:
    - 技术
    - Missing Semester
tags:
    - 技术
    - Missing Semester
    - Linux
---

### Basics
```shell
>>> date
Wed Sep 15 17:57:06 CST 2021
>>> echo hello
hello
>>> echo Hello\ World
Hello World
>>> echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/mnt/c/Windows/system32:/mnt/c/Windows:/mnt/c/Windows/System32/Wbem:/mnt/c/Windows/System32/WindowsPowerShell/v1.0/:/mnt/c/Windows/System32/OpenSSH/:/mnt/c/Program Files (x86)/NVIDIA Corporation/PhysX/Common:/mnt/c/Program Files/NVIDIA Corporation/NVIDIA NvDLISR:/mnt/c/WINDOWS/system32:/mnt/c/WINDOWS:/mnt/c/WINDOWS/System32/Wbem:/mnt/c/WINDOWS/System32/WindowsPowerShell/v1.0/:/mnt/c/WINDOWS/System32/OpenSSH/:/mnt/c/Non-system/Node.js/:/mnt/c/Non-system/Git/cmd:/mnt/c/Users/Q_Mas/AppData/Local/Microsoft/WindowsApps:/mnt/c/Non-system/Microsoft VS Code/bin:/mnt/c/Users/Q_Mas/AppData/Roaming/npm:/snap/bin
>>> which echo
/usr/bin/echo 
>>> pwd
/mnt/c/Users/Q_Mas/Desktop/missing-semester
>>> cd /home
>>> pwd
/home
>>> cd ..
>>> pwd
/
>>> cd ./home
>>> pwd
/home
>>> cd ./home
-bash: cd: ./home: No such file or directory
>>> cd /mnt/c/Users/Q_Mas/Desktop/missing-semester/
>>> ../../../../../../bin/echo world
world
>>> pwd
/mnt/c/Users/Q_Mas/Desktop/missing-semester
>>> ls
1-overview.md  2-shell.md  3-vim.md  test
>>> cd test
>>> ls ..
1-overview.md  2-shell.md  3-vim.md  test
>>> cd ..
>>> pwd
/mnt/c/Users/Q_Mas/Desktop/missing-semester
>>> cd ~
>>> pwd
/home/matthew
>>> cd -
/mnt/c/Users/Q_Mas/Desktop/missing-semester
>>> ls --help
>>> ls -a
.  ..  1-overview.md  2-shell.md  3-vim.md  test
>>> ls -l
total 0
-rwxrwxrwx 1 matthew matthew    0 Sep 15 23:34 1-overview.md
-rwxrwxrwx 1 matthew matthew    0 Sep 15 23:34 2-shell.md
-rwxrwxrwx 1 matthew matthew    0 Sep 15 23:35 3-vim.md
drwxrwxrwx 1 matthew matthew 4096 Sep 15 23:35 test
>>> mv 3-vim.md 3-vim-renamed.md
>>> ls
1-overview.md  2-shell.md  3-vim-renamed.md  test
>>> mv 3-vim-renamed.md 3-vim.md
>>> cp 3-vim.md ./test/3-vim-copy.md
>>> ls ./test
3-vim-copy.md
>>> rm ./3-vim-copy.md
>>> touch ./test/1
>>> rmdir test
rmdir: failed to remove 'test': Directory not empty
>>> rm -r test
>>> ls
1-overview.md  2-shell.md  3-vim.md
>>> mkdir "My Photos"
>>> man ls
```
For a directory rather than a file, 
read means you can list stuffs inside it
write means you can change the file name, make a new file or remove one
execute means you can get into the directory

<!--more-->

### Combining different programs
```shell
>>> echo hello > hello.txt
>>> cat hello.txt
hello
>>> cat < hello.txt
hello
>>> cat < hello.txt > hello2.txt
>>> cat hello2.txt
hello
>>> cat < hello.txt >> hello2.txt
>>> cat hello2.txt
hello
hello
>>> tail -n1 hello2.txt
hello
>>> ls -l
total 0
-rwxrwxrwx 1 matthew matthew    0 Sep 15 23:34  1-overview.md
-rwxrwxrwx 1 matthew matthew    0 Sep 15 23:34  2-shell.md
-rwxrwxrwx 1 matthew matthew    0 Sep 15 23:35  3-vim.md
drwxrwxrwx 1 matthew matthew 4096 Sep 15 23:53 'My Photos'
-rwxrwxrwx 1 matthew matthew    6 Sep 15 23:57  hello.txt
-rwxrwxrwx 1 matthew matthew   12 Sep 15 23:59  hello2.txt
>>> ls -l | tail -n1
-rwxrwxrwx 1 matthew matthew   12 Sep 15 23:59 hello2.txt
>>> ls -l | tail -n2 > ls.txt
>>> cat ls.txt
-rwxrwxrwx 1 matthew matthew   12 Sep 15 23:59 hello2.txt
-rwxrwxrwx 1 matthew matthew    0 Sep 16 00:03 ls.txt
```

### Root User
User ID is 0
```shell
>>> echo 500 > /sys/class/backlight/intel_backlight/brightness
-bash: brightness: Permission denied
>>> sudo echo 500 > /sys/class/backlight/intel_backlight/brightness
-bash: brightness: Permission denied
>>> sudo su
[sudo] password for matthew:
# echo 500 > /sys/class/backlight/intel_backlight/brightness
# exit
>>> echo 1060 | sudo tee brightness
1060
>>> cd /sys/class/leds/input4\:\:scrolllock
>>> cat brightness
0
>>> echo 1 | sudo tee brightness
1
```

### Others
```shell
>>> xdg-open lectures.html
```