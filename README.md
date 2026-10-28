# 把“你”放进 CPU

《Putting the “You” in CPU》中文翻译。

> 当你在电脑上运行一个程序时，究竟发生了什么？本文会带你了解多任务处理、系统调用的本质、计算机如何借助硬件中断管理内存，以及 Linux 如何加载可执行文件。

原作者：[Lexi Mattick](https://kognise.dev/) 与 [Hack Club](https://hackclub.com/)  
原文发布于 2023 年 7 月：<https://cpu.land/>  
原文仓库：<https://github.com/hackclub/putting-the-you-in-cpu>

## 目录

- [序章](00-intro.md)
- [第 1 章：所谓“基础”](01-the-basics.md)
- [第 2 章：切分时间](02-slice-dat-time.md)
- [第 3 章：如何运行一个程序](03-how-to-run-a-program.md)
- [第 4 章：成为精灵领主](04-becoming-an-elf-lord.md)
- [第 5 章：你电脑里的翻译官](05-the-translator-in-your-computer.md)
- [第 6 章：聊聊 Fork 与奶牛](06-lets-talk-about-forks-and-cows.md)
- [第 7 章：尾声](07-epilogue.md)

## 翻译说明

- 本文档是面向中文读者的非官方翻译，以原文 2023 年 7 月发布的版本为准。文中的 Linux 内核代码、调度器参数等可能随版本更新而变化。
- 技术术语首次出现时通常附有英文原文，之后根据语境选用中文或英文。
- 代码、命令、路径、函数名和寄存器名保持原样；代码中的注释已译为中文。
- 原文章节插图保留英文标注，图片说明已译为中文。
- 原文中的链接、引用和延伸阅读均尽量保留。
- 原文以 MIT License 发布，本翻译同样遵循该许可，详见 [LICENSE](LICENSE)。

## 许可

原文及插图版权归 Lexi Mattick 与 Hack Club 所有。原项目采用 MIT License；本翻译作为其衍生作品分发。
