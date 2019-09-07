# Code Review Developer Guide 代码审核指南

## 简介Introduction {#intro}

A code review is a process where someone other than the author(s) of a piece of
code examines that code.

代码审核指代码作者以外的人检查作者代码的一种程序（步骤？）。

At Google we use code review to maintain the quality of our code and products.

在Google，代码审核是用来维护代码质量的步骤。

This documentation is the canonical description of Google's code review
processes and policies.

这个文档是对Google代码审核程序和原则的标准化（统一？）描述。

这个页面是我们代码审核程序的概览。主要包含两大部分：

-   **[如何做代码审核](reviewer/)**: 一个面向代码审核者的详细指南。
-   **[The CL Author's Guide](developer/)**: A detailed guide for developers
    whose CLs are going through review.
-   **[CL作者指南](developer/)**: 一个面向代码被审核的开发者的详细指南。

## What Do Code Reviewers Look For?代码审核者应该审核什么? {#look_for}

Code reviews should look at: 代码审核者应该检查：

-   **设计**:  Is the code well-designed and appropriate for your system?
代码是否设计精良并且适合系统？
-   **功能性**: Does the code behave as the author likely intended? Is the way the code behaves good for its users?
代码是否表达作者意图？代码是否对用户友好？  
-   **复杂性**: Could the code be made simpler? Would another developer be
    able to easily understand and use this code when they come across it in the
    future?
    代码能否变得更简洁？ 其他开发者在未来能否很容易地理解并复用这段代码？
-   **测试**: Does the code have correct and well-designed automated tests?
     代码是否包含正确且设计良好的自动化测试？
-   **命名**: 开发者是否为变量，类，方法等起了明确的名字?
-   **注释**: 注释是否是明确的且有用的？
-   **风格**: 代码风格是否遵循
    [style guides](http://google.github.io/styleguide/)?
-   **文档**: 开发者是否更新相关文档？

更多详情请查看 **[如何做一个代码审核者](reviewer/)**

### Picking the Best Reviewers选择最好的审核者 {#best_reviewers}

In general, you want to find the *best* reviewers you can who are capable of
responding to your review within a reasonable period of time.
总的来说，你想要找你能找到的*最好的*审核者，他（她）们能在一段合理的时间内回复你的代码审查请求。

The best reviewer is the person who will be able to give you the most thorough
and correct review for the piece of code you are writing. This usually means the
owner(s) of the code, who may or may not be the people in the OWNERS file.
Sometimes this means asking different people to review different parts of the
CL.

最好的审核者应该是能够全面并正确检查你的代码的人。这通常意味着代码文件的所有者，包括但不限于在所有者(OWNER)文件列表上的人。有些情况下也指请求不同的人去检查cl的不同部分。


If you find an ideal reviewer but they are not available, you should at least CC
them on your change.
如果你找到一个理想的审核者，但是他（她）们没时间，你至少应该在你的更改提交中抄送(cc)他（她）们

### In-Person Reviews面对面审核  {#in_person}

If you pair-programmed a piece of code with somebody who was qualified to do a
good code review on it, then that code is considered reviewed.
如果你和某（些）人的结对编程完成了一段代码，并且他（她）们有资格对这段代码作出好的代码审核，那么，这些代码可以被认为是审核过的。
You can also do in-person code reviews where the reviewer asks questions and the
developer of the change speaks only when spoken to.
你也可以和审核者面对面，回答审核者提出的问题。

## 参见 {#seealso}

-   [如何做代码审核（Code Review）](reviewer/): 一个面向代码审核者的详细指南。
-   [CL作者指南](developer/): A detailed guide for developers whose
    CLs are going through review. 一个面向代码被审核的开发者的详细指南。
