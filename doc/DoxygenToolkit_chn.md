## 描述：

目前为止已经定义了5个用途：

1. 快速生成许可注释，并且标签可以被修改；
2. 快速生成作者声明框架，标签可修改；
3. 快速为C/C++、Python函数或者类生成注释框架，此框架包含的元素有：@brief, @param(为每一个参数生成一个@param)和@return。
标签文本和注释块的头和尾都可以修改（因此，你可以有自己的简介，如果你原义，加上一点成就）；
4. 忽略在#ifdef...#endif(C/C++)块中代码碎片。给块命名的时候一定要考虑到其功能。
在所有文件中，所有有联系的块将会放在一个新的块 DOX_SKIP_BLOCK（或者用户定义的名称）。
你需要使用当前的新块名更新你的doxygen配置文件中的PREDEFINED变量。
而且你还需 要将ENABLE_PREPROCESSING设置为YES。
5. 快速生成一个注释集（开始或者结尾），标签可修改；

## 使用：

- 注释类型（C/C++/// 或者, Python：##和#）：
在vim中，默认C++注释为，但是如果你更喜欢使用///，只需要在你的配置文件.vimrc中添加如下语句：
let g:DoxygenToolkit_commentType="C++"。

- 许可：
在vim中，将光标放在将要写doxygen许可注释的那一行，然后，执行命令：DoxLic。
这将会生成许可注释并将光标放置在刚才那一行之后。

- 作者： 
在vim中，将光标放在想要添加doxygen作者注释的地方。然后执行命令：DoxAuthor。这将会生成一个框架，如果没有为其设置变量则将光标放置在@author标签之后，或者放在在框架之后。

- 函数/类注释：
在vim中，将光标放置在函数头部那一行（或者函数的返回变量）或者类。然后执行命令：Dox。
这将生成框架并且将光标放置在@brief标签后。

- 忽略代码片段（只有C/C++）：
在vim中，如果你想要忽略所有在块中的代码片段，类似 #ifdef DEBUG ... #endif
你只需要执行以下命令：DoxUndoc(DEBUG)!

- 组：
在vim中，执行命令：DoxBlock在后面的行中插入一个doxygen块。

## 限制：

1. 假设函数名（后面的左括号）至少在当前光标位置后的第三行；
2. 在注释块在写入之前不能再次更新；
3. 块分隔符（头部和尾部）只包含函数注释；
4. 假设已经使用了缩进；
5. 函数参数中得到注释还不支持；(像void foo(int bar ))
6. 定制输出脚本，在脚本文件中，在.vimrc中设置g: DoxygenToolkit_*变量：

 举例说明，在我的.vimrc中包含：

    let g:DoxygenToolkit_briefTag_pre="@Synopsis  " 
    let g:DoxygenToolkit_paramTag_pre="@Param " 
    let g:DoxygenToolkit_returnTag="@Returns   " 
    let g:DoxygenToolkit_blockHeader="--------------------------------------------------------------------------" 
    let g:DoxygenToolkit_blockFooter="----------------------------------------------------------------------------" 
    let g:DoxygenToolkit_authorName="Mathias Lorente" 
    let g:DoxygenToolkit_licenseTag="My own license"   <-- !!! Does not end with "\<enter>"

## 安装细节：
将DoxygenToolkit.vim拷贝至 '~/.vim/plugin' 目录。
