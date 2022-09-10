---
layout: post
title:  "在Mac上安装JDK"
category: dev
---

使用`homebrew`安装opnjdk
```
brew install openjdk
```

For the system Java wrappers to find this JDK, symlink it with
```
sudo ln -sfn /opt/homebrew/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```
openjdk is keg-only, which means it was not symlinked into /opt/homebrew, because macOS provides similar software and installing this software in parallel can cause all kinds of trouble.

If you need to have openjdk first in your PATH, run:
```
echo 'export PATH="/opt/homebrew/opt/openjdk/bin:$PATH"' >> ~/.zshrc
```
For compilers to find openjdk you may need to set:
```
export CPPFLAGS="-I/opt/homebrew/opt/openjdk/include"
```
