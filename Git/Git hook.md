---
title:  Git hook
date: 2018-06-19 14:26:49
tags: [git,git hook]
---

>和其它版本控制系统一样，Git 能在特定的重要动作发生时触发自定义脚本。 有两组这样的钩子：**客户端**的和**服务器端**的。 
>客户端钩子由诸如提交和合并这样的操作所调用，而服务器端钩子作用于诸如接收被推送的提交这样的联网操作。 你可以随心所欲地运用这些钩子。

## 安装一个钩子

1. 钩子都被存储在 .git/hooks
2. 任何正确命名的可执行脚本都可以正常使用 —— 你可以用 Ruby 或 Python，或其它语言编写它们
3. 示例的名字都是以 .sample 结尾，如果你想启用它们，得先移除这个后缀

## 客户端钩子

>克隆某个版本库时，它的客户端钩子**并不** 随同复制。 如果需要靠这些脚本来强制维持某种策略，建议你在服务器端实现这一功能

### pre-commit

在输入提交信息前运行。 

**用途：**

1. 它用于检查即将提交的快照，例如，检查是否有所遗漏，确保测试运行，以及核查代码。 
2. 如果该钩子以非零值退出，Git 将放弃此次提交，不过你可以用 git commit --no-verify 来绕过这个环节。 
3. 你可以利用该钩子，来检查代码风格是否一致（运行类似 lint 的程序）、尾随空白字符是否存在（自带的钩子就是这么做的），或新方法的文档是否适当。

### prepare-commit-msg

启动提交信息编辑器之前，默认信息被创建之后运行。

1. 它允许你编辑提交者所看到的默认信息。 
2. 该钩子接收一些选项：存有当前提交信息的文件的路径、提交类型和修补提交的提交的 SHA-1 校验。 
3. 它对一般的提交来说并没有什么用；然而对那些会自动产生默认信息的提交，如提交信息模板、合并提交、压缩提交和修订提交等非常实用。 
4. 你可以结合提交模板来使用它，动态地插入信息。

### commit-msg
钩子接收一个参数，此参数即上文提到的，存有当前提交信息的临时文件的路径。

 1. 如果该钩子脚本以非零值退出，Git 将放弃提交，因此，可以用来在提交通过前验证项目状态或提交信息。 
 2. 在本章的最后一节，我们将展示如何使用该钩子来核对提交信息是否遵循指定的模板。
 
### post-commit
 钩子在整个提交过程完成后运行。 

1. 它不接收任何参数，但你可以很容易地通过运行 git log -1 HEAD 来获得最后一次的提交信息。 
2. 该钩子一般用于通知之类的事情。


### 电子邮件工作流钩子

>你可以给电子邮件工作流设置三个客户端钩子。 它们都是由 git am 命令调用的。

>如果你需要通过电子邮件接收由 git format-patch 产生的补丁，这些钩子也许用得上。

**一、applypatch-msg** 

1. 它接收单个参数：包含请求合并信息的临时文件的名字。 
2. 如果脚本返回非零值，Git 将放弃该补丁。 
3. 你可以用该脚本来确保提交信息符合格式，或直接用脚本修正格式错误。

**二、pre-applypatch**
  
1. 运行于应用补丁 之后，产生提交之前，所以你可以用它在提交前检查快照。 
2. 你可以用这个脚本运行测试或检查工作区。 如果有什么遗漏，或测试未能通过，脚本会以非零值退出，中断 git am 的运行，这样补丁就不会被提交。

**三、post-applypatch** 

1. 运行于提交产生之后，是在 git am 运行期间最后被调用的钩子。 
2. 你可以用它把结果通知给一个小组或所拉取的补丁的作者。
3.  但你没办法用它停止打补丁的过程。

##服务器端钩子

### pre-receive

1. 客户端推送操作时，最先被调用的脚本是 pre-receive。 
2. 它从标准输入获取一系列被推送的引用。如果它以非零值退出，所有的推送内容都不会被接受。 
3. 你可以用这个钩子阻止对引用进行非快进（non-fast-forward）的更新，或者对该推送所修改的所有引用和文件进行访问控制。

### update

1. update 脚本和 pre-receive 脚本十分类似，不同之处在于它会为每一个准备更新的分支各运行一次。
2.  假如推送者同时向多个分支推送内容，pre-receive 只运行一次，相比之下 update 则会为每一个被推送的分支各运行一次。 
3. 它不会从标准输入读取内容，而是接受三个参数：引用的名字（分支），推送前的引用指向的内容的 SHA-1 值，以及用户准备推送的内容的 SHA-1 值。
4. 如果 update 脚本以非零值退出，只有相应的那一个引用会被拒绝；其余的依然会被更新。

### post-receive

1. post-receive 挂钩在整个过程完结以后运行，可以用来更新其他系统服务或者通知用户。 
2. 它接受与 pre-receive 相同的标准输入数据。 
3. 它的用途包括给某个邮件列表发信，通知持续集成（continous integration）的服务器，或者更新问题追踪系统（ticket-tracking system） —— 甚至可以通过分析提交信息来决定某个问题（ticket）是否应该被开启，修改或者关闭。 
4. 该脚本无法终止推送进程，不过客户端在它结束运行之前将保持连接状态，所以如果你想做其他操作需谨慎使用它，因为它将耗费你很长的一段时间。


[Git-使用强制策略的一个例子](https://git-scm.com/book/zh/v2/自定义-Git-使用强制策略的一个例子#r_an_example_git_enforced_policy)

[使用Github的webhooks进行网站自动化部署](https://aotu.io/notes/2016/01/07/auto-deploy-website-by-webhooks-of-github/index.html)

