Solidity
========

.. image:: logo.svg
    :width: 120px
    :alt: Solidity logo
    :align: center

Solidity 是一个 contract-oriented（面向合约的）, 为实现 smart contracts（智能合约）而创建的高级语言.
它受到 C++, Python 和 JavaScript 语言的影响, 所以其设计的目的是可以在以太坊虚拟机 (EVM) 上来运行使用.

Solidity 是静态类型的语言, 支持继承, 相关库和复杂的用户定义类型, 以及一些其它特性.

正如你所看到的那样, 可以用于创建 voting（投票）, crowdfunding（众筹）, blind auctions（秘密竞价/盲拍）, multi-signature wallets（多重签名钱包）等等的这样的合约.

.. note::
    目前尝试使用 Solidity 的最佳方式是使用 Remix `Remix <https://remix.ethereum.org/>`_ （可能需要一段时间才能加载, 请耐心等待）.
    Remix 是一个基于 Web 浏览器的 IDE, 可以让您编写 Solidity 智能合约, 然后部署和运行它（智能合约）.

.. warning::
    由于软件是由人类所编写的, 因此它可能存在 BUG.
    因此, 智能合约也应该遵循着众所周知的软件开发最佳实践.
    这包括 code review（代码审查）, testing（测试）, audits（审计）和 correctness proofs（正确性证明）.
    另请注意, 用户有时比其作者对代码更有信心.
    最后, 区块链也有它们自己的注意事项, 所以请参阅一下 :ref:`security_considerations` 这个部分.

翻译
------------

本文档由社区志愿者翻译成多种语言, 但是英语版本作为主要参考.

* `简体中文版 <http://solidity-cn.readthedocs.io>`_ (进行中)
* `西班牙语版 <https://solidity-es.readthedocs.io>`_
* `俄语版 <https://github.com/ethereum/wiki/wiki/%5BRussian%5D-%D0%A0%D1%83%D0%BA%D0%BE%D0%B2%D0%BE%D0%B4%D1%81%D1%82%D0%B2%D0%BE-%D0%BF%D0%BE-Solidity>`_ (已过时)


友情链接
------------

* `以太坊官网 <https://ethereum.org>`_

* `变更日志 <https://github.com/ethereum/solidity/blob/develop/Changelog.md>`_

* `Story Backlog <https://www.pivotaltracker.com/n/projects/1189488>`_

* `源代码 <https://github.com/ethereum/solidity/>`_

* `以太坊技术栈交流社区 <https://ethereum.stackexchange.com/>`_

* `Gitter Chat <https://gitter.im/ethereum/solidity/>`_

可用的 Solidity 集成
-------------------------------

* `Remix <https://remix.ethereum.org/>`_
    基于浏览器的 IDE, 集成了编译器和 Solidity 运行时环境, 并且不需要服务端的组件.

* `IntelliJ IDEA plugin <https://plugins.jetbrains.com/plugin/9475-intellij-solidity>`_
    IntelliJ IDEA 的 Solidity 插件（可用于其它所有的 JetBrains IDEs）

* `Visual Studio Extension <https://visualstudiogallery.msdn.microsoft.com/96221853-33c4-4531-bdd5-d2ea5acc4799/>`_
    Microsoft Visual Studio 的 Solidity 插件, 它包含了 Solidity 编译器.

* `Package for SublimeText — Solidity language syntax <https://packagecontrol.io/packages/Ethereum/>`_
    SublimeText 编辑器的语法高亮包.

* `Etheratom <https://github.com/0mkara/etheratom>`_
    Atom 编辑器的插件, 其特性是语法高亮, 可编译的和可运行的环境（后端节点 & 虚拟机兼容的）.

* `Atom Solidity Linter <https://atom.io/packages/linter-solidity>`_
    Atom 编辑器的插件, 提供 Solidity 语言的 Lint 检查（静态检查）.

* `Atom Solium Linter <https://atom.io/packages/linter-solium>`_
    Atom 的可配置的 Solidty 静态检查器, 它是基于 Solium 来使用的.

* `Solium <https://github.com/duaraghav8/Solium/>`_
    一种静态检查器, 识别和修复 Solidity 语言中的风格以及安全问题.
    
* `Solhint <https://github.com/protofire/solhint>`_
    一种静态检查器, 提供安全和风格指南以及智能合约验证的最佳实践规则.

* `Visual Studio Code extension <http://juan.blanco.ws/solidity-contracts-in-visual-studio-code/>`_
    Microsoft Visual Studio Code 插件, 包含语法高亮和 Solidity 编译器.

* `Emacs Solidity <https://github.com/ethereum/emacs-solidity/>`_
    Emacs 编辑器的插件, 提供语法高亮和编译错误报告.

* `Vim Solidity <https://github.com/tomlion/vim-solidity/>`_
    Vim 编辑器的插件, 提供语法高亮.

* `Vim Syntastic <https://github.com/scrooloose/syntastic>`_
    Vim 编辑器的插件, 提供编译检查.

停止使用:

* `Mix IDE <https://github.com/ethereum/mix/>`_
    基于 Qt 的 IDE, 可以设计, 调试和测试 Solidity 语言的智能合约.

* `Ethereum Studio <https://live.ether.camp/>`_		
    Specialized web IDE that also provides shell access to a complete Ethereum environment.
    专门的网页 IDE, 它也提供一个 shell 脚本访问完整的以太坊环境.

Solidity 工具列表
-----------------

* `Dapp <https://dapp.readthedocs.io>`_
    Solidity 语言的构建工具, 包管理器以及部署助手.

* `Solidity REPL <https://github.com/raineorshine/solidity-repl>`_
    一个命令行控制台, 可以立刻尝试使用 Solidity 语言.

* `solgraph <https://github.com/raineorshine/solgraph>`_
    可视化的 Solidity 控制流, 并能标明潜在的安全漏洞.

* `evmdis <https://github.com/Arachnid/evmdis>`_
    EVM 反汇编程序, 它可以执行字节码的静态分析, 能提供比 EVM 操作更高级的抽象.

* `Doxity <https://github.com/DigixGlobal/doxity>`_
    Solidity 语言的文档生成器.

第三方的 Solidity 解析器和语法
-----------------------------------------

* `solidity-parser <https://github.com/ConsenSys/solidity-parser>`_
    针对 JavaScript 的 Solidity解析器

* `Solidity Grammar for ANTLR 4 <https://github.com/federicobond/solidity-antlr4>`_
    针对 ANTLR 4 解析器生成器的 Solidity 语法

Solidity 语言文档
----------------------

在下面的页面中, 我们首先会看到一个使用 Solidity 来编写的 :ref:`简单智能合约 <simple-smart-contract>`,
随后开始讲解 :ref:`区块链基础 <blockchain-basics>`,
然后再是 :ref:`以太坊虚拟机（EVM） <the-ethereum-virtual-machine>`.

接着下一节将会通过给出有用的 :ref:`合约示例 <voting>` 来解释几个 Solidity 语言方面的特性, 需要提醒一下的是,
你都可以在 `你的浏览器 <https://remix.ethereum.org>`_ 中尝试运行这些合约.

最后, 也是最长的一节将会深入讲解 Solidity 的各个方面.

如果还有问题, 你可以尝试在搜索引擎中获取答案,
或在 `Ethereum Stackexchange <https://ethereum.stackexchange.com/>`_ 上提问,
或者到我们的 `gitter channel <https://gitter.im/ethereum/solidity/>`_ 中来。
随时欢迎改善 Solidity 或本文档的想法!

目录
========

:ref:`关键词索引 <genindex>`, :ref:`搜索网页 <search>`

.. toctree::
   :maxdepth: 2

   introduction-to-smart-contracts.rst
   installing-solidity.rst
   solidity-by-example.rst
   solidity-in-depth.rst
   security-considerations.rst
   using-the-compiler.rst
   metadata.rst
   abi-spec.rst
   julia.rst
   style-guide.rst
   common-patterns.rst
   bugs.rst
   contributing.rst
   frequently-asked-questions.rst
