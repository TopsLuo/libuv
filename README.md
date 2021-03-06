# libuv

[![Build Status](https://travis-ci.com/zhyingkun/libuv.svg)](https://travis-ci.com/zhyingkun/libuv)

---

## 基本介绍

1. 本工程是 libuv 及其 C 示例的构建工程，用于运行调试
2. 所有 libuv 源码来自[libuv 官方](https://libuv.org/)1.31.0 版本
3. 仅保留 Mac/Linux/Win 三个平台的源码，去除了其他平台特定代码（为了足够简单）
4. 增加了源码注释，支持 Debug/Release 编译模式
5. 整个工程 PC 端编译构建采用 cmake 来管理，支持跨平台（可以在树莓派上正常 cmake+make）

---

## 如何编译

#### 1. 在 Mac 上采用 Xcode 编译

```bash
cd libuv/
mkdir buildXcode && cd buildXcode
cmake -DCMAKE_INSTALL_PREFIX=./install -G "Xcode" ..
# cmake -DCMAKE_INSTALL_PREFIX=/usr/local/zyk/libuv -G "Xcode" ..
```

此时已经在 buildXcode 文件夹下生成了 Xcode 工程，直接打开并编译即可

#### 2. 直接命令行编译（支持 Mac 和 Linux）

```bash
cd libuv/
mkdir build && cd build
cmake -DCMAKE_INSTALL_PREFIX=./install .. # default is Debug
# for Debug: cmake -DCMAKE_BUILD_TYPE=Debug ..
# for Release: cmake -DCMAKE_BUILD_TYPE=Release ..
# cmake -DCMAKE_INSTALL_PREFIX=/usr/local/zyk/libuv -DCMAKE_BUILD_TYPE=Release ..
make
# for more details: make VERBOSE=1
make install
```

make 命令会自动编译好各个模块

#### 3. 在 Windows 上使用 Cygwin + Visual Studio 2017 进行编译

```bash
cd libuv/
mkdir buildVS && cd buildVS
cmake -DCMAKE_INSTALL_PREFIX=./install -G "Visual Studio 15 2017 Win64" ..
# cmake -DCMAKE_INSTALL_PREFIX=D:/Applications/zyk/libuv -G "Visual Studio 15 2017 Win64" ..
```

此时已经在 buildVS 文件夹下生成了 Visual Studio 工程，双击打开并编译即可

---

## 文件夹说明

1. demo：libuv 源码中相关组件的用法示例，以及其他应用构建
2. example：libuv 官方源码中附带的用法示例，做了一些小修改
3. libuv：libuv 官方源码，加了注释，编译出 libuv 动态链接库
