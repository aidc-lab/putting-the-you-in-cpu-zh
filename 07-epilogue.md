---
chapter: 7
title: 尾声
shortname: 尾声
original_title: Epilogue
source: https://cpu.land/epilogue
---

# 尾声

恭喜！我们终于把“你”牢牢地放进了 CPU。希望你玩得开心。

临别之际，我想再次强调：你刚刚学到的一切知识都是真实存在、正在运行的。下次你思考电脑如何同时运行多个应用时，希望你能想到定时器芯片和硬件中断。当你用某种花哨的编程语言写程序、遇到链接器报错时，希望你能想一想链接器到底在尝试做什么。

如果你对本文内容有任何问题（或勘误），可以发邮件到 [lexi@hackclub.com](mailto:lexi@hackclub.com)，或者在 [GitHub](https://github.com/hackclub/putting-the-you-in-cpu/) 上提交 issue 或 PR。

![完。](images/the-end.png)

……不过等等，还有彩蛋！

## 彩蛋：把 C 概念翻译成底层机制

如果你自己写过一些底层代码，大概知道栈（stack）和堆（heap）是什么，也用过 `malloc`。你可能没怎么想过它们是如何实现的！

首先，一个线程的栈是一块固定大小的内存，被映射到虚拟内存中较高的某个位置。在大多数（虽然[并非所有](https://stackoverflow.com/a/664779)）架构上，栈指针从栈内存的顶部开始，随着压栈向下移动。整块映射的栈空间并不会预先分配物理内存；相反，系统使用按需分页，在栈帧实际被访问时惰性地分配内存。

听到像 `malloc` 这样的堆分配函数不是系统调用，你可能会有点惊讶。堆内存管理其实是由 libc 实现提供的！`malloc`、`free` 等都是复杂的过程，libc 自己负责跟踪内存映射的细节。在底层，用户空间的堆分配器会使用 `mmap`（它不仅能映射文件）和 `sbrk` 等系统调用。

## 彩蛋：零碎趣闻

我找不到合适的地方安放这些内容，但又觉得挺有趣，所以一并放在这里。

> *大多数 Linux 用户大概都过着足够有趣的生活，没什么时间去想象页表在内核中是如何表示的。*
>
> *[Jonathan Corbet，LWN](https://lwn.net/Articles/106177/)*

硬件中断的另一种可视化方式：

![一张四格表情包漫画，画着一只停在树枝上的小鸟，对话气泡里是汇编指令。第二格里，画面外又冒出一个对话气泡，大喊：“你好，是我，键盘！”第三格里，喊话的来源现身在画面中，是一只大乌鸦，它喊道：“我有一条重要消息！”最后一格特写小鸟，一脸无语。画面外的乌鸦又冒出一个对话气泡，里面只有一个字母 E。](images/hardware-interrupt-meme.png)

补充一点：有些系统调用会使用一种叫 vDSO 的技术，而不是跳进内核空间。我没时间展开讲，但这相当有意思，推荐你[读一读](https://en.wikipedia.org/wiki/VDSO)[相关](https://man7.org/linux/man-pages/man7/vdso.7.html)[资料](https://0xax.gitbooks.io/linux-insides/content/SysCall/linux-syscall-3.html)。

最后，回应一下“这也太 Unix 了”的指控：我确实有点抱歉，很多与执行程序相关的细节都非常 Unix 专属。如果你用 macOS 或 Linux，那没关系；但这些内容不会让你更了解 Windows 如何执行程序或处理系统调用，尽管 CPU 架构部分是一样的。将来我很想写一篇覆盖 Windows 世界的文章。

## 致谢

写这篇文章时，我和 GPT-3.5、GPT-4 聊了不少。虽然它们经常骗我，大部分信息也没什么用，但有时在梳理问题上确实很有帮助。如果你了解它们的局限，并且对它们说的每句话都保持极度怀疑，LLM 的辅助总体上可以利大于弊。话虽如此，它们写文章真的很烂。别让它们替你写。

更重要的是，感谢所有帮我校对、鼓励我、陪我头脑风暴的人——特别是 Ani、B、Ben、Caleb、Kara、polypixeldev、Pradyun、Spencer、Nicky（[第 4 章](04-becoming-an-elf-lord.md)里那只可爱的精灵就是她画的），还有我亲爱的父母。

如果你是个青少年，喜欢计算机，而且还没加入 [Hack Club Slack](https://hackclub.com/slack)，那现在就加入吧。如果没有一群超棒的人可以分享想法和进展，我根本写不出这篇文章。如果你不是青少年，可以[给我们捐点钱](https://hackclub.com/philanthropy/)，让我们继续做酷东西。

本文所有平庸的画作都是用 [Figma](https://figma.com/) 画的。我使用 [Obsidian](https://obsidian.md/) 编辑，有时用 [Vale](https://vale.sh/) 跑 lint。文章的 Markdown 源码[在 GitHub 上](https://github.com/hackclub/putting-the-you-in-cpu/)，今后也欢迎挑刺；所有画作都发布在 [Figma 社区页面](https://www.figma.com/community/file/1260699047973407903)。

![一个有着可爱恳求表情的 CPU。](images/cpu-pleading-face.png)

---

上一章：[第 6 章：聊聊 Fork 与奶牛](06-lets-talk-about-forks-and-cows.md) · 返回[目录](README.md)
