---
title: Mac-Env
auther: yuran
date: 2022-05-11 00:53:57
categories:
tags:
---

# Start with Mac
第一次到实验室，拿到了实验室给准备的Mac  
于是要开始配置Mac了

# Homebrew
本科的时候听说Mac对开发者还挺友好的，而且Mac的terminal和Linux比较相似，那第一件事就是打开terminal  
一番ls/cd等无意义操作后，觉得首要事情是弄个包管理工具，搜索后发现homebrew用的比较多，Jo Ting也如此建议，英文互联网和中文互联网都有推荐，空白也附议  
于是敲定，就它了  
## Installation
进入官网，有自动提示的安装指令
```
% /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
安装完毕后
```
% brew -v
Homebrew 3.4.10
```
说明安装成功  
## Wget
既然包管理安装好了，作为测试，用它来装个wget罢  
```
% brew install wget
```
安装完毕后  
```
% wget -V
```
注意是大写哟
```
GNU Wget 1.21.3 built on darwin21.3.0
blablabla
```
说明安装成功  

# Git
想能在Win和Mac不同设备上共同用hexo编辑自己的博客，那显然要给Mac也整上Git  
## Installation
直接去Git官网，发现官网也推荐使用homebrew下载安装  
```
% brew install git
matthew@Qs-MacBook-Pro ~ % brew install git
Running `brew update --preinstall`...
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/core).
==> Updated Formulae
Updated 6 formulae.

==> Downloading https://ghcr.io/v2/homebrew/core/pcre2/manifests/10.40
######################################################################## 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/pcre2/blobs/sha256:18b810bc5ddba9960505488662ad3b122c898ded44461e2dfb871ee32abbe0fb
==> Downloading from https://pkg-containers.githubusercontent.com/ghcr1/blobs/sha256:18b810bc5ddba9960505488662ad3b122c898ded44461e2dfb871ee32abbe0fb?se=2022-05-10T17%3A25%3A00Z&sig=1i5xgA0kBSpoqCBk9Rn3
######################################################################## 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/git/manifests/2.36.1
######################################################################## 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/git/blobs/sha256:5941a1eb703ac9814c2f8ae7c78ff31630aed04ad90a6a3073e45f4748f96e25
==> Downloading from https://pkg-containers.githubusercontent.com/ghcr1/blobs/sha256:5941a1eb703ac9814c2f8ae7c78ff31630aed04ad90a6a3073e45f4748f96e25?se=2022-05-10T17%3A25%3A00Z&sig=idLuPp1AvjC9ow40Bqpg
######################################################################## 100.0%
==> Installing dependencies for git: pcre2
==> Installing git dependency: pcre2
==> Pouring pcre2--10.40.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/pcre2/10.40: 230 files, 6.1MB
==> Installing git
==> Pouring git--2.36.1.arm64_monterey.bottle.tar.gz
==> Caveats
The Tcl/Tk GUIs (e.g. gitk, git-gui) are now in the `git-gui` formula.
Subversion interoperability (git-svn) is now in the `git-svn` formula.

zsh completions and functions have been installed to:
  /opt/homebrew/share/zsh/site-functions

Emacs Lisp files have been installed to:
  /opt/homebrew/share/emacs/site-lisp/git
==> Summary
🍺  /opt/homebrew/Cellar/git/2.36.1: 1,545 files, 44.1MB
==> Running `brew cleanup git`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
==> Caveats
==> git
The Tcl/Tk GUIs (e.g. gitk, git-gui) are now in the `git-gui` formula.
Subversion interoperability (git-svn) is now in the `git-svn` formula.

zsh completions and functions have been installed to:
  /opt/homebrew/share/zsh/site-functions

Emacs Lisp files have been installed to:
  /opt/homebrew/share/emacs/site-lisp/git
```
## Generate SSH key
还是比较习惯用SSH方法登陆github而不是用账号密码，Mac和Linux实在是太一致了，几乎没什么需要修改的地方，指令都一模一样
```
matthew@dhcp82-160 ~ % ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/matthew/.ssh/id_rsa): 
Created directory '/Users/matthew/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/matthew/.ssh/id_rsa
Your public key has been saved in /Users/matthew/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:1f4I286yCydWUdM2U8FPQzXZwhqjw4znk1OqEHNKFLc matthew@dhcp82-160.vlab.nii.ac.jp
The key's randomart image is:
+---[RSA 3072]----+
|      ...   ooo=B|
|      .. . oo.B++|
|     .  E+o..= =o|
|      + o.*oo   .|
|     . =Soo=.    |
|      o  .*+ o   |
|       .+.ooo .  |
|       ..+.o     |
|          o+o    |
+----[SHA256]-----+

matthew@dhcp82-160 .ssh % cat id_rsa.pub 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDVzjPimLgla3p8JGB9aTw0x1BSn/rmTdvEUCW/JzDK3DFDh210hcaFuumsoEcLSeAZHfvB3PCwzz3U3DwKjFdutf1vjhh0sVU7TV5rvVzAoZJp2fbz7J0ai6wa1+gceGSYuDi08MsGnThxRlPytl1+LOCi1nS4RG/2YcmJc0y9wns2iaPcwsA4WCrM65ViJU10KK7G2z1+4LCn6xejjXAOIjMBcL8pSO7B1no+8LK6M44n/+LeuNK+a8l4HRh3yy0TbXuVPDHkgpDxDF7MR1KfG99t2wgEQF6Wv28bUTnpMoip4hz0ngGCURiGNjvQ5iF04SXF4ME1fIWUBdchy1EHYtEc9PdPzVpLE0espFWz+a/14tpsPPmd2TZHq1ufq2oh4PwsK8UBnkI8zC/aPB6USw6INYadC89+lYdg+mjfX7mJTnDnOIQvNUDAzsM2yL7MR6Zm//tZ0c1wKljGm6D8p1yCkUEpxPXenIzd6S4QJ7gUaiiNsMgB84EG16qmq68= matthew@dhcp82-160.vlab.labname.ac.jp
```
发现这个最后是实验室的host，以防出问题重新生成
```
matthew@dhcp82-160 .ssh % ssh-keygen -t rsa -C q_masio@outlook.com
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/matthew/.ssh/id_rsa): 
/Users/matthew/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/matthew/.ssh/id_rsa
Your public key has been saved in /Users/matthew/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:un4eTlP4UsdjywFpY4e8pfttM4GiIeP6qkXD0BsHIqo q_masio@outlook.com
The key's randomart image is:
+---[RSA 3072]----+
|. . .            |
|.. o .   . o     |
|. . o .   O o    |
|.  o +   + O     |
|E   =   S = *.   |
|   . .o..+.=.+.  |
|    ...o=oo.o  . |
|   .  .+o+ . .+  |
|  ..o=+oo   ...o |
+----[SHA256]-----+

matthew@dhcp82-160 .ssh % cat id_rsa.pub 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCpYnZx/WHi9DXUjk+by0RCmLDZTsER+kFf6T8UfkhxYu8prq9vAaQE4HIqiFQcDN+IB2Rjqu2jyUQ4Lcjsx8n2jz+JtAqzWB2QHum9IxCyo0VQsBwXlNl4Is4x0ExIr9X84+UrOJueSfmZ0vHMkZGvYfa1wzF/3cR2Mvkk7TIxKQLq4FoVx66lsG5/rmDD9wbQD3e+xxjMAJIheI5OLfvGKcYqqRoNrGxtyqmTiPne2ogeipVA3i29wPc2H9BqZPMCGgFjrhuGvNcV54g5PVh8OjsCQ+dSqJEVSznAuWIwfW0YyiThWZ7nIzpP8NNfx5eKosWub4KvZiAwEqbbxb5CG/hltlzstWnRHeUfbpIRbdsjPwibzWqjU8yMc4NaEr43TWNKvhUsn0E3proWY0O4xRG3LDKBSh9R/SxFfwnolRlyIxQYJNRZ9KemH9dOSl77mG7nEQZkghUrMsqdtjQz5gEA0sqskk7QfBKNDHoxD9viHiLzideiBWCc6fuimZM= q_masio@outlook.com
```
验证是否正常运行
```
matthew@dhcp82-160 .ssh % ssh -T git@github.com 
The authenticity of host 'github.com (52.69.186.44)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? y
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
Hi QiuMatthew! You've successfully authenticated, but GitHub does not provide shell access.
```
## Clone a repo using ssh authentication
用ssh方式clone的正确姿势，显然不能用直接复制网址到方式，因为那是https协议，我们要改成ssh协议，但有几个点要注意
只把https改成ssh是不行的
```
matthew@dhcp82-160 Desktop % git clone ssh://github.com/QiuMatthew/FileShare
Cloning into 'FileShare'...
matthew@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
```
在最后加.git还不够
```
Please make sure you have the correct access rights
and the repository exists.
matthew@dhcp82-160 Desktop % git clone ssh://github.com/QiuMatthew/FileShare.git
Cloning into 'FileShare'...
matthew@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
```
在网址前面加git@，成功
```
Please make sure you have the correct access rights
and the repository exists.
matthew@dhcp82-160 Desktop % git clone ssh://git@github.com/QiuMatthew/FileShare.git
Cloning into 'FileShare'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
```
## Try Git Operations
尝试进行一些git操作
```

matthew@dhcp82-160 FileShare % git branch
* master
matthew@dhcp82-160 FileShare % mv ../README.md ./
matthew@dhcp82-160 FileShare % ls
Mac-Env.md	README.md
matthew@dhcp82-160 FileShare % git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.md

nothing added to commit but untracked files present (use "git add" to track)
matthew@dhcp82-160 FileShare % git add README.md 
matthew@dhcp82-160 FileShare % ls
Mac-Env.md	README.md
matthew@dhcp82-160 FileShare % git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   README.md

matthew@dhcp82-160 FileShare % git commit -m 'add README file'
[master f3ea1cf] add README file
 Committer: Q <matthew@Qs-MacBook-Pro.local>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 1 insertion(+)
 create mode 100644 README.md
matthew@dhcp82-160 FileShare % git push --set-upstream origin master
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 330 bytes | 82.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To ssh://github.com/QiuMatthew/FileShare.git
   86e6611..f3ea1cf  master -> master

```

# Start with hexo
## Start with Nodejs
There are two ways to use nodejs, we can install it with homebrew. But I decided to use nodebrew for version control.
```
matthew@Qs-MacBook-Pro FileShare % brew install nodebrew
Running `brew update --preinstall`...
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/core).
==> New Formulae
dotdrop             libabw              octosql             xcode-kotlin
glibc@2.13          lndir               release-it
==> Updated Formulae
Updated 501 formulae.

==> Downloading https://ghcr.io/v2/homebrew/core/nodebrew/manifests/1.2.0
######################################################################## 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/nodebrew/blobs/sha256:eed2aeff4
==> Downloading from https://pkg-containers.githubusercontent.com/ghcr1/blobs/sh
######################################################################## 100.0%
==> Pouring nodebrew--1.2.0.all.bottle.tar.gz
==> Caveats
You need to manually run setup_dirs to create directories required by nodebrew:
  /opt/homebrew/opt/nodebrew/bin/nodebrew setup_dirs

Add path:
  export PATH=$HOME/.nodebrew/current/bin:$PATH

To use Homebrew's directories rather than ~/.nodebrew add to your profile:
  export NODEBREW_ROOT=/opt/homebrew/var/nodebrew

zsh completions have been installed to:
  /opt/homebrew/share/zsh/site-functions
==> Summary
🍺  /opt/homebrew/Cellar/nodebrew/1.2.0: 8 files, 40.6KB
==> Running `brew cleanup nodebrew`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
matthew@Qs-MacBook-Pro FileShare % nodebrew -v
nodebrew 1.2.0

Usage:
    nodebrew help                         Show this message
    nodebrew install <version>            Download and install <version> (from binary)
    nodebrew compile <version>            Download and install <version> (from source)
    nodebrew install-binary <version>     Alias of `install` (For backward compatibility)
    nodebrew uninstall <version>          Uninstall <version>
    nodebrew use <version>                Use <version>
    nodebrew list                         List installed versions
    nodebrew ls                           Alias for `list`
    nodebrew ls-remote                    List remote versions
    nodebrew ls-all                       List remote and installed versions
    nodebrew alias <key> <value>          Set alias
    nodebrew unalias <key>                Remove alias
    nodebrew clean <version> | all        Remove source file
    nodebrew selfupdate                   Update nodebrew
    nodebrew migrate-package <version>    Install global NPM packages contained in <version> to current version
    nodebrew exec <version> -- <command>  Execute <command> using specified <version>
    nodebrew prune [--dry-run]            Uninstall old versions, keeping the latest version for each major version

Example:
    # install
    nodebrew install v8.9.4

    # use a specific version number
    nodebrew use v8.9.4

```
nodebrew安装完成，试图用nodebrew安装最新版nodejs（v16.15.0）
```
matthew@Qs-MacBook-Pro ~ % nodebrew install-binary v16.15.0
Fetching: https://nodejs.org/dist/v16.15.0/node-v16.15.0-darwin-arm64.tar.gz
Warning: Failed to create the file 
Warning: /Users/matthew/.nodebrew/src/v16.15.0/node-v16.15.0-darwin-arm64.tar.g
Warning: z: No such file or directory
                                                                            0.0%curl: (23) Failure writing output to destination

download failed: https://nodejs.org/dist/v16.15.0/node-v16.15.0-darwin-arm64.tar.gz
```
去官网看了，明明是存在`https://nodejs.org/dist/v16.15.0/node-v16.15.0-darwin-arm64.tar.gz`这个文件的  
怀疑是本地存储路径不存在
```
matthew@Qs-MacBook-Pro ~ % cd /Users/matthew 
matthew@Qs-MacBook-Pro ~ % ls
Desktop		Documents	Downloads	Library		Movies		Music		OneDrive	Pictures	Public
matthew@Qs-MacBook-Pro ~ % ll 
zsh: command not found: ll
matthew@Qs-MacBook-Pro ~ % ls -a
.			.DS_Store		.cisco			.ssh			.vscode			.zsh_sessions		Downloads		Music			Public
..			.Trash			.cups			.swiftpm		.zprofile		Desktop			Library			OneDrive
.CFUserTextEncoding	.anyconnect		.lesshst		.viminfo		.zsh_history		Documents		Movies			Pictures
matthew@Qs-MacBook-Pro ~ % cd .nodebrew 
cd: no such file or directory: .nodebrew
matthew@Qs-MacBook-Pro ~ % mkdir .nodebrew
matthew@Qs-MacBook-Pro ~ % cd .nodebrew 
matthew@Qs-MacBook-Pro .nodebrew % ls
matthew@Qs-MacBook-Pro .nodebrew % nodebrew install-binary v16.15.0
Fetching: https://nodejs.org/dist/v16.15.0/node-v16.15.0-darwin-arm64.tar.gz
Warning: Failed to create the file 
Warning: /Users/matthew/.nodebrew/src/v16.15.0/node-v16.15.0-darwin-arm64.tar.g
Warning: z: No such file or directory
curl: (23) Failure writing output to destination

download failed: https://nodejs.org/dist/v16.15.0/node-v16.15.0-darwin-arm64.tar.gz
matthew@Qs-MacBook-Pro .nodebrew % mkdir src                       
matthew@Qs-MacBook-Pro .nodebrew % cd src 
matthew@Qs-MacBook-Pro src % nodebrew install-binary v16.15.0
Fetching: https://nodejs.org/dist/v16.15.0/node-v16.15.0-darwin-arm64.tar.gz
######################################################################################################################################################################################################################################################### 100.0%
Installed successfully
```
成功，检查是否正常安装，并开始使用刚刚安装的版本的node
```
matthew@Qs-MacBook-Pro ~ % nodebrew ls  
v16.15.0

current: none
matthew@Qs-MacBook-Pro ~ % nodebrew use v16.15.0
use v16.15.0
```
尝试确认
```
matthew@Qs-MacBook-Pro ~ % node -v  
zsh: command not found: node
matthew@Qs-MacBook-Pro ~ % npm -v
zsh: command not found: npm
```
原因应该是没有加入PATH当中，先寻找nodejs安装在哪  
我是用nodebrew安装的，所以应该在
```
~/.nodebrew/current/bin
```
因此添加这个路径到PATH当中，先判断自己是zsh还是bash
```
% echo $SHELL
/bin/zsh
```
我是zsh，因此要修改的文件是`~/.zshrc`  
先看看这个文件存不存在  
```
% ls -a ~ | grep zshrc
```
如果不存在就`touch`新建一下这个文件，然后在最后追加内容  
```
% echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.zshrc
```
应用修改
```
% exec $SHELL -l
```
验证是否修改成功
```
% node --version
v16.15.0
```
显示版本说明修改成功

## Install Hexo
有了git和nodejs，现在安装hexo，遵循hexo官网 https://hexo.io 的操作  
```
% npm install -g hexo-cli

added 60 packages, and audited 61 packages in 5s

14 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
npm notice 
npm notice New minor version of npm available! 8.5.5 -> 8.11.0
npm notice Changelog: https://github.com/npm/cli/releases/tag/v8.11.0
npm notice Run npm install -g npm@8.11.0 to update!
npm notice 

```
顺手更新一下npm
```
% npm install -g npm@8.11.0

removed 6 packages, changed 74 packages, and audited 202 packages in 1s

11 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

## Get source codes
我们现在已经安装好了hexo，接下来要把windows的hexo源文件复制到mac上  
之后为了方便同步源文件，统一使用git完成，每次无论在Windows还是在mac上，都先pull一下源文件，编辑过后再push和deploy  
我们deploy的网页在github的main分支，源文件在github的hexo分支  
首先是把win上的源文件提交到hexo分支  
```
# 进入hexo博客文件夹
$ cd /mnt/c/Non-system/GitRepositories/HexoBlog
# 这个文件夹hexo是不会帮我们建立成git仓库的，因此需要初始化本地仓库，但由于我clone过主题，因此需要先找到主题文件夹里面的 `.git` 文件夹，将其删除，否则就会仓库套仓库导致报错，这里假设已经删除完毕，初始化仓库并添加所有内容到仓库
$ git init
$ git add *
$ git commit -m 'source code of blog'
# 和远程仓库建立连接，给远程仓库起名为origin
$ git remote add origin https://github.com/QiuMatthew/QiuMatthew.github.io.git
# 查看远程连接和本地分支
$ git remote -v
$ git branch
# 尝试push，将本地master分支push到远程的hexo分支
$ git push --set-upstream origin master:hexo
# 发现需要密码，想起来改用ssh放弃https
$ git remote rm origin
$ git remote add origin ssh://git@github.com/QiuMatthew/QiuMatthew.github.io.git
$ git push --set-upstream origin master:hexo
# 发现被远程仓库拒绝了，因为本地比远程版本落后，先pull
$ git pull origin hexo:master
$ git push origin master:hexo
# 还是不行，commit对不上号，只好强制push
$ git push -f origin hexo:master
```
成功提交，然后在mac里直接把整个repo克隆下来  
```
% cd ~/Hexo/
% git clone https://github.com/QiuMatthew/QiuMatthew.github.io
# 进入并查看本地分支，发现是main，main是我们用来放网页的分支，hexo是我们用来存源文件的分支
% cd QiuMatthew.github.io
% git branch
* main
# 因此改成hexo分支
% git checkout hexo
```

## Use Hexo
在这个目录下，我们有了生成网页所需的源文件，接下来就需要用hexo了，先初始化  
```
% hexo init
ERROR Cannot find module 'hexo' from '/Users/matthew/Hexo/QiuMatthew.github.io'
ERROR Local hexo loading failed in ~/Hexo/QiuMatthew.github.io
ERROR Try running: 'rm -rf node_modules && npm install --force'
% npm install --force
npm WARN using --force Recommended protections disabled.
npm WARN old lockfile 
npm WARN old lockfile The package-lock.json file was created with an old version of npm,
npm WARN old lockfile so supplemental metadata must be fetched from the registry.
npm WARN old lockfile 
npm WARN old lockfile This is a one-time fix-up, please be patient...
npm WARN old lockfile 
npm WARN deprecated source-map-url@0.4.1: See https://github.com/lydell/source-map-url#deprecated
npm WARN deprecated source-map-resolve@0.5.3: See https://github.com/lydell/source-map-resolve#deprecated
npm WARN deprecated urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
npm WARN deprecated resolve-url@0.2.1: https://github.com/lydell/resolve-url#deprecated

added 198 packages, and audited 199 packages in 5s

15 packages are looking for funding
  run `npm fund` for details

11 vulnerabilities (3 moderate, 5 high, 3 critical)

To address issues that do not require attention, run:
  npm audit fix

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.
```
好家伙一堆bug，姑且试试能不能用  
```
% hexo clean
% hexo g
% hexo d
```
还真的能用，起飞！
