.. index:: ! installing

.. _installing-solidity:

################################
安装 Solidity 编译器
################################

版本控制
==========

Solidity 语言的版本请参阅 `语义版本控制 <https://semver.org>`_, 除了发行版之外, **nightly development builds** 也是可用的.
nightly builds（每日构建版）不保证能够正常工作, 尽管尽了最大的努力, 它们可能包含无正式文件的和 / 或重大的变更.
我们推荐使用最新版本.
下面的软件包安装程序将使用最新版本.

Remix
=====

*我们强烈推荐使用 Remix 来进行智能合约的开发, 以及快速学习 Solidity 语言*

`访问在线版本的 Remix <https://remix.ethereum.org/>`_, 你不需要安装任何东西.
如果你想在没有连接到互联网的情况下使用它, 请前往 https://github.com/ethereum/browser-solidity/tree/gh-pages, 然后下载如页面所述的 .ZIP 文件

在您的计算机上, 该页面详细的介绍了有关安装命令行版本的 Solidity 编译器软件的信息.
如果您正在处理大型合约或需要更多编译选项, 请选择命令行编译器.

.. _solcjs:

npm / Node.js
=============

使用 `npm` 这样的方式来安装 `solcjs`, 它是一个 Solidity 编译器.
`solcjs` 程序比本页面所有选项的功能更少.
我们的 :ref:`commandline-compiler` 文档假设你使用了 `全部特性` 的编译器 `solc`.
所以如果你从 `npm` 安装 `solcjs`, 那么建议你你停止阅读这里的文档, 然后请参阅 `solc-js <https://github.com/ethereum/solc-js>`_.


请注意: solc-js 项目是通过使用 Emscripten 来从 C++ `solc` 中诞生的.
`solc-js` 可以直接在 JavaScript 项目中使用（如 Remix）.
更多详情请参阅 `solc-js <https://github.com/ethereum/solc-js>`_ 仓库.

.. code:: bash

    npm install -g solc

.. note::

    命令行中的名字为 `solcjs`

    `solcjs` 的命令行选项与 `solc` 是不兼容的, 并且使用 `solc` 的行为的工具（如 `geth`）无法与 `solcjs` 配合使用.

Docker
======

我们为编译器提供了最新的 docker 版本.
``stable`` 仓库包含的发行版, 而 ``nightly`` 仓库在开发分支中包含可能不稳定的更改.

.. code:: bash

    docker run ethereum/solc:stable solc --version

目前, docker 镜像仅包含编译器可执行文件, 因此您必须执行一些额外的工作来链接源目录和输出目录.

二进制软件包
===============

Solidity 的二进制软件包可在 `solidity/releases <https://github.com/ethereum/solidity/releases>`_ 中获取. 

我们也为 Ubuntu 提供了 PPA. 针对最新的稳定版本执行如下命令.

.. code:: bash

    sudo add-apt-repository ppa:ethereum/ethereum
    sudo apt-get update
    sudo apt-get install solc

如果你想使用前沿的开发者版本.

.. code:: bash

    sudo add-apt-repository ppa:ethereum/ethereum
    sudo add-apt-repository ppa:ethereum/ethereum-dev
    sudo apt-get update
    sudo apt-get install solc
    
我们也发布了一个 `snap package <https://snapcraft.io/>`_, 它可以在所有 `支持 Linux distros <https://snapcraft.io/docs/core/install>`_ 上的系统上安装. 要安装 solc 的最新稳定版本:

.. code:: bash

    sudo snap install solc

或者, 如果您想帮助测试不稳定的 solc 以及来自开发分支的最新更改:

.. code:: bash

    sudo snap install solc --edge

Arch Linux 也有软件包, 尽管只限于最新的开发版本:

.. code:: bash

    pacman -S solidity

Homebrew is missing pre-built bottles at the time of writing,
following a Jenkins to TravisCI migration, but Homebrew
should still work just fine as a means to build-from-source.
We will re-add the pre-built bottles soon.

.. code:: bash

    brew update
    brew upgrade
    brew tap ethereum/ethereum
    brew install solidity
    brew linkapps solidity

如果您需要特定版本的 Solidity, 您可以直接从 Github 安装 Homebrew formula.

请参阅 `solidity.rb commits on Github <https://github.com/ethereum/homebrew-ethereum/commits/master/solidity.rb>`_.

查阅历史链接, 直到你找到一个特定的 ``solidity.rb`` 提交的原始文件链接.

使用 ``brew`` 来安装它:

.. code:: bash

    brew unlink solidity
    # Install 0.4.8
    brew install https://raw.githubusercontent.com/ethereum/homebrew-ethereum/77cce03da9f289e5a3ffe579840d3c5dc0a62717/solidity.rb

Gentoo Linux 还提供了一个可以使用 ``emerge`` 来安装的可靠软件包:

.. code:: bash

    emerge dev-lang/solidity

.. _building-from-source:

从源码构建
====================

克隆仓库
--------------------

要 clone 源代码, 执行以下命令:

.. code:: bash

    git clone --recursive https://github.com/ethereum/solidity.git
    cd solidity

如果你想帮助开发 Solidity,
你应该 fork Solidity, 然后添加你私人的 fork 作为第二个远程地址:

.. code:: bash

    cd solidity
    git remote add personal git@github.com:[username]/solidity.git

Solidity 有 git submodules. 确保它们都正确加载了:

.. code:: bash

   git submodule update --init --recursive

前提条件 - macOS
---------------------

针对 macOS, 确保你已经安装了最新的 `Xcode <https://developer.apple.com/xcode/download/>`_ 版本.
它包含了 `Clang C++ 编译器 <https://en.wikipedia.org/wiki/Clang>`_,
`Xcode IDE <https://en.wikipedia.org/wiki/Xcode>`_ 以及在OS X 上构建 C ++ 应用程序所需的其他 Apple 开发工具.
如果您是第一次安装 Xcode, 或者刚刚安装了新版本, 那么在您执行命令行构建之前, 您需要同意该许可证:

.. code:: bash

    sudo xcodebuild -license accept

Our OS X builds require you to `install the Homebrew <http://brew.sh>`_
package manager for installing external dependencies.
Here's how to `uninstall Homebrew
<https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/FAQ.md#how-do-i-uninstall-homebrew>`_,
if you ever want to start again from scratch.

为了解决依赖问题, 我们的 OS X 构建需要你 `安装 Homebrew <http://brew.sh>`_ 软件包.
这里是如何去 `卸载 Homebrew
<https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/FAQ.md#how-do-i-uninstall-homebrew>`_ 的说明,
如果你想从头开始重新开始的话.

前提条件 - Windows
-----------------------

您需要为 Windows 版本的 Solidity 安装以下依赖:

+------------------------------+-------------------------------------------------------+
| Software（软件）                     | Notes（注意事项）                                                 |
+==============================+=======================================================+
| `Git for Windows`_           | Command-line tool for retrieving source from Github.  |
+------------------------------+-------------------------------------------------------+
| `CMake`_                     | Cross-platform build file generator.                  |
+------------------------------+-------------------------------------------------------+
| `Visual Studio 2015`_        | C++ compiler and dev environment.                     |
+------------------------------+-------------------------------------------------------+

.. _Git for Windows: https://git-scm.com/download/win
.. _CMake: https://cmake.org/download/
.. _Visual Studio 2015: https://www.visualstudio.com/products/vs-2015-product-editions


外部依赖
---------------------

我们现在有一个 "一键操作" 脚本, 可以在 macOS, Windows 和众多 Linux 发行版上安装所必须的外部依赖.
这曾经是一个多步手动过程, 但现在可以直接一把梭了:

.. code:: bash

    ./scripts/install_deps.sh

或者, 在 Windows 上:

.. code:: bat

    scripts\install_deps.bat


命令行构建
------------------

**确保在构建之前安装好外部的依赖（请参考上文）**

Solidity project uses CMake to configure the build.
Building Solidity is quite similar on Linux, macOS and other Unices:

Solidity 项目使用 CMake 来配置构建.
在 Linux, macOS 和其他 Unices 上, 构建 Solidity 的方法非常相似:

.. code:: bash

    mkdir build
    cd build
    cmake .. && make

甚至更容易:

.. code:: bash
    
    #note: this will install binaries solc and soltest at usr/local/bin
    ./scripts/build.sh

甚至在 Windows 上也可以:

.. code:: bash

    mkdir build
    cd build
    cmake -G "Visual Studio 14 2015 Win64" ..

后一组指令应该导致在该构建目录中创建 **solidity.sln** 文件.
双击该文件应该会导致 Visual Studio 启动.
我们建议构建 **RelWithDebugInfo** 配置，而不是做其它的操作.

或者， 您可以在命令行上为 Windows 来构建, 如下所示:

.. code:: bash

    cmake --build . --config RelWithDebInfo

CMake 选项
=============

如果你对 CMake 选项有兴趣, 可以运行 ``cmake .. -LH``.

version 字符串详解
============================

Solidity version 字符串包含 4 个部分:

- 版本号
- 预发布的标签, 通常设置为 ``develop.YYYY.MM.DD`` 或 ``nightly.YYYY.MM.DD``
- 以 ``commit.GITHASH`` 这样的格式来提交
- 平台具有任意数量的项目, 包含有关平台和编译器的详细信息

如果存在本地修改, 则提交将以 ``.mod`` 为后缀.

这些部件按照 Semver 的要求进行组合, 其中 Solidity 预发布标签等于 Semver 预发行版, 并且 Solidity 提交和平台组合了 Semver 构建元数据.

一个发行版示例: ``0.4.8+commit.60cc1668.Emscripten.clang``.

一个预发行版示例: ``0.4.9-nightly.2017.1.17+commit.6ecb4aa3.Emscripten.clang``

关于版本控制的重要信息
======================================

在发布一个版本后, 补丁版本的级别别提升了, 因为我们假设只有补丁级别会随着更改.
我更改被合并时, 版本应该根据 semver 和更改的程度来进行调整.
最后, 一个版本总是与当前的 nightly build（每日构建）的版本一起发布, 但没有 ``prerelease`` 说明符.

示例:

0. 发布 0.4.0 版本
1. 从现在开始, 逐日构建的版本为 0.4.1
2. 介绍了非重大性的更改 - 版本没有变化
3. 介绍了重大性的更改 - 版本提升到 0.5.0
4. 发布 0.5.0 版本

这种行为与 :ref:`version pragma <version_pragma>` 的协作很好.