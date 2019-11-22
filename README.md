# Git版本控制

* 起源

现在的软件项目通常是由一个研发小组共同分析、设计、维护以及测试的。
因此，团队开发需要解决以下问题：
  - 备份多个版本，费空间，费时间；
  - 解决代码问题（代码冲突、代码管理），难于追溯问题代码的修改人和修改时间。
  - 无法进行权限管理
  - 难于恢复以前正确版本

* 分布式源代码管理git
 
 - GIT是一款自由和开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目
 - 在世界上所有的分布式版本控制工具中，git是最快、最简单、最流行的
 - 是Linux之父李纳斯的第二个伟大作品
 
![image](https://upload-images.jianshu.io/upload_images/647982-6a9d0974b77621bc.png?imageMogr2/auto-orient/strip|imageView2/2/format/webp)


* 分布式和集中式的最大区别在于：
  - 在集中式下, 开发者只能将代码提交到服务器, 在分布式下, 开发者可以本地提交
  - 在集中式下, 只有远程服务器上有代码数据库, 在分布式下, 每个开发者机器上都有一个代码数据库

* git命令（个人开发）
 - git help：git指令帮助手册
 
 - `git init`:仓库初始化（个人仓库）
 
 - git config:配置信息
    - `git config user.name "用户名"`：配置用户名
    - `git config user.email "邮箱"`：配置邮箱
    - `git config -l`:查看配置信息
   
 - git status ：查文件的状态
    - 查看某个文件的状态 ：git status 文件ming
    - 查看当前路径所有文件的状态：`git status`
    
 - git add：将工作区的文件保持到暂缓区
    - 保存某个文件到暂缓区： git add 文件名
    - 保存当前路径的所有文件到暂缓区： `git add .`
    
 - git commit：将暂缓区的文件提交到当前分支
   - 提交某个文件到分支：git commit -m ”注释” 文件名
   - 保存当前路径的所有文件到分支：`git commit -m ”注释”`
   
 - git log: 查看文件的修改日志
    - 查看当前路径所有文件的修改日志：`git log`
 
 - git diff:查看文件最新改动的地方
    - 查看某个文件的最新改动的地方：git diff 文件名
    - 查看当前路径所有文件最新改动的地方：`git diff`
    
 - git rm：删除文件（删完之后要进行commit操作，才能同步到版本库）

 - git reset：版本回退（建议加上––hard参数，git支持无限次后悔）
    - 回退到上一个版本：git reset ––hard HEAD^
    - 回退到上上一个版本：git reset ––hard HEAD^^
    - 回退到上N个版本：git reset ––hard HEAD~N（N是一个整数）
    - 回退到任意一个版本：git reset ––hard 版本号（版本号用7位即可）

 - .gitignore配置
    ```
    #               表示此为注释,将被Git忽略
    *.a             表示忽略所有 .a 结尾的文件
    !lib.a          表示但lib.a除外
    /TODO           表示仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
    build/          表示忽略 build/目录下的所有文件，过滤整个build文件夹；
    doc/*.txt       表示会忽略doc/notes.txt但不包括 doc/server/arch.txt

    bin/:           表示忽略当前路径下的bin文件夹，该文件夹下的所有内容都会被忽略，不忽略 bin 文件
    /bin:           表示忽略根目录下的bin文件
    /*.c:           表示忽略cat.c，不忽略 build/cat.c
    debug/*.obj:    表示忽略debug/io.obj，不忽略 debug/common/io.obj和tools/debug/io.obj
    **/foo:         表示忽略/foo,a/foo,a/b/foo等
    a/**/b:         表示忽略a/b, a/x/b,a/x/y/b等
    !/bin/run.sh    表示不忽略bin目录下的run.sh文件
    *.log:          表示忽略所有 .log 文件
    config.php:     表示忽略当前路径的 config.php 文件

    被过滤掉的文件就不会出现在git仓库中（gitlab或github）了，当然本地库中还有，只是push的时候不会上传。
    ```
    
* git命令(团队开发)
  - git init --bare : 仓库初始化(共享仓库)
    注意: 不要直接在共享仓库中编写代码
    
  - git clone：下载远程仓库到本地
    - 下载远程仓库到当前路径：git clone 仓库的URL
    - 下载远程仓库到特定路径：git clone 仓库的URL 存放仓库的路径
    
  - git pull：下载远程仓库的最新信息到本地仓库
  
  - git push：将本地的仓库信息推送到远程仓库
    提交时如果远程仓库有其它人提交的最新代码, 必须先pull, 再提交
  - 冲突解决:
    当多个人同时修改了同一个文件时, 后提交的需要先从服务器pull代码到问题, 手动解决完冲突之后再push到远程服务器
    ```
      <<<<<<< HEAD
        你本地的新增的代码
      =======
          服务器上和你冲突的代码
      >>>>>>> e9609de28b65bf97539f94c6458cdebdf2711c9f
    ```


    
    
    
    
