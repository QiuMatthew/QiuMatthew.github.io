---
title: Nodejs and Revealjs
auther: yuran
date: 2022-03-03 00:44:29
categories:
tags:
---

## Install Node.js

- create a dirctory for nodejs
```
$ mkdir /mnt/c/Non-system/Linux/Node.js
$ cd $_
```

- download from nodejs.org
```
$ wget https://nodejs.org/dist/v16.14.0/node-v16.14.0-linux-x64.tar.xz
```

- unpatch and unzip

first patch with tar and then zip with xz, so we first unzip with xz and then unpatch with tar
```
$ xz -d node-v16.14.0-linux-x64.tar.xz
$ tar -xvf node-v16.14.0-linux-x64.tar
```

- now there are three executable files in directory `./node-v16.14.0-linux-x64/bin/`: `node`, `npm`, `npx`

- create softlinks
```
$ sudo ln -s /mnt/c/Non-system/Node/node-v16.14.0-linux-x64/bin/node /usr/local/bin/
$ sudo ln -s /mnt/c/Non-system/Node/node-v16.14.0-linux-x64/bin/npm /usr/local/bin/
$ sudo ln -s /mnt/c/Non-system/Node/node-v16.14.0-linux-x64/bin/npx /usr/local/bin/
```

- verify our installation
```
$ node -v
$ npm -v
$ npx -v
```
our installation is successful if we see the version

## Install Reveal.js

- install node.js
- clone github repository
```
$ cd /mnt/c/Non-system/Linux
$ git clone https://github.com/hakimel/reveal.js.git
```

- install dependencies
```
$ cd reveal.js
$ npm install
```

- run presentation
```
$ npm start
```
default port is 8000
if we want to select the port
```
$ npm start -- --port=8001
```
