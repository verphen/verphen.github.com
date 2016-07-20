title: Eclipse Tasks
date: 2015-11-15 22:15:02
tags:
  - tools
  - eclipse
categories: tools
---
使用Eclipse开发中，难免出现很多需要当前标记的代码便于以后来完善，借助eclipse tasks来实现是最好不过了！

打开tasks面板： window -> show view -> other -> Tasks； 标记标签的具体含义如下

    . FIXME       # 表示注释的代码需要被修正(修复我)
    . TODO        # 尚未完成的待办事项(要做)
    . XXX         # 注释的代码虽然实现了功能，但是实现方案有待商榷，希望将来能改进
    . 自定义标签   # window -> preferences -> java -> compiler -> Task tags

那怎么来标记代码呢？你只需在待标记的代码处添添加注释行，将对应的标签写在注释行即可被Tasks面板收录；上述所有注释都会被eclipse task视图所收集。在项目发布前，检查一下task视图是一个很好的习惯。

当然，你还可以对标识设置优先权(proprity)