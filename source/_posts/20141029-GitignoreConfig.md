title: gitignore配置
date: 2014-10-30 07:35:22
categories: tools
tags: [tools,git]
---
Git管理项目，将某些文件或目录不纳入git的管理，则需要配置忽略文件 `.gitignore`，在项目根目录下创建该文件:

    # 创建然后编辑文件
    $ touch .gitignore
    $ vi .gitignore
    or
    # 直接创建并且编辑
    $ vi .gitignore

配置忽略文件规则：
    
    空行不匹配任何内容
    # 表示该行为注释行
    / 表示目录
    \ 转义字符("\!"意为匹配"!")
    * 表示通配符
    ? 表示匹配单个字符
    ! 表示忽略该文件或目录

skills

- 通常一条忽略规则或注释单独一行; 忽略规则行尾不允许在使用注释语句

-  git对忽略文件是从上到下进行匹配；如前面的规则范围较大，则后面的规则将不生效

-  忽略规则只对未加入git管理的文件生效;若需要忽略文件已经加入git管理，需要先使用 `git rm [-r]  - -cached filename` 将文件移除git的管理；参数[-r]表示递归移除目录下的文件和目录，filename表示待忽略的完整文件名（目录）