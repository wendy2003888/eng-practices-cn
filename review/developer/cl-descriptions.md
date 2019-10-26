# 撰写好的CL描述

CL的描述公开记录了变更 **内容** 以及 **原因** 。这个描述会永存于版本控制系统的记录中。在之后的时间里，它很可能会被上百人看到，而不只是你的审核者。

未来，其他开发者可以通过描述搜索你的CL。
某人可能模糊地记得这个CL有相关信息，但是不知道其具体的用途。
如果所有重要的信息在代码而不是在描述里，那么他们很难找到你的CL。

## 第一行 {#firstline}

*   简洁的总结CL的内容。
*   完整的祈使句。
*   留一行空行。

CL描述的 **第一行** 应该简洁地总结 *具体做了什么* **内容** ，并紧接一行空行。

未来，当其他开发者浏览版本控制系统的历史记录，大多数人会看到描述的第一行。所以第一行应该信息丰富，使他们不用读你的CL代码就能大致地知道这个CL真正 *做了什么*。

按照传统，CL描述的第一行应该是一个完整的祈使句。例如：

\"**Delete** the FizzBuzz RPC and **replace** it with the new system."

而非

\"**Deleting** the FizzBuzz RPC and **replacing** it with the new system."

你不必把描述的其余部分也写成祈使句。

## 详尽的正文 {#informative}

描述的其余部分应该是详尽的（信息丰富的）。它可能包括一段问题的简短描述，以及为什么这是最优的方法。如果这个方法有短板，那么把短板放到描述里。如果有相关的背景，也请放进描述，例如bug id，benchmark结果和设计文档的链接。

即使是小的CL也应该注意细节。把背景放进CL描述。

## 不好的CL描述 {#bad}

"Fix bug"(修bug) 是一个不充分的CL描述. 什么bug？你做了什么来修好它？
其他相似的不好的描述包括:

-   "Fix build."  （修build）
-   "Add patch."  （加补丁）
-   "Moving code from A to B."  （把代码从A移到B）
-   "Phase 1."  （第1阶段）
-   "Add convenience functions."  （添加便利的函数）
-   "kill weird URLs."  （杀掉奇怪的URL）

某些列子真实存在。它们的作者可能认为他（她）们提供了有用的信息，但是他（她）们没有遵照CL描述的目的去写。

## 好的CL描述 {#good}

以下是一些好的列子。

### 功能变更

> rpc: remove size limit on RPC server message freelist.
>
> Servers like FizzBuzz have very large messages and would benefit from reuse.
> Make the freelist larger, and add a goroutine that frees the freelist entries
> slowly over time, so that idle servers eventually release all freelist
> entries.

最开始的几个词描述了CL真正的内容。其余的部分描述这个CL在解决什么问题，为什么这是一种好的解决方案，以及一些具体的实现信息。

### 重构

> Construct a Task with a TimeKeeper to use its TimeStr and Now methods.
>
> Add a Now method to Task, so the borglet() getter method can be removed (which
> was only used by OOMCandidate to call borglet's Now method). This replaces the
> methods on Borglet that delegate to a TimeKeeper.
>
> Allowing Tasks to supply Now is a step toward eliminating the dependency on
> Borglet. Eventually, collaborators that depend on getting Now from the Task
> should be changed to use a TimeKeeper directly, but this has been an
> accommodation to refactoring in small steps.
>
> Continuing the long-range goal of refactoring the Borglet Hierarchy.

第一句总结了CL的内容和具有哪些新的变化。其余的部分解释具体实现，背景（解决方案并不是最优的），以及可能的未来方向。同时也解释了写这段代码的 *原因*

### 需要背景（上下文）的小CL

> Create a Python3 build rule for status.py.
>
> This allows consumers who are already using this as in Python3 to depend on a
> rule that is next to the original status build rule instead of somewhere in
> their own tree. It encourages new consumers to use Python3 if they can,
> instead of Python2, and significantly simplifies some automated build file
> refactoring tools being worked on currently.

第一句描述这个CL的内容。其余的部分解释了 *原因* 以及其背景。

## 在提交CL之前检查描述

在审核期间，CL的内容会发生重大的改变。在提交到代码库前再次检查描述，确保它仍旧反映CL的内容。

接下来: [小CL（Small CLs）](small-cls.md)
