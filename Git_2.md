## git命令（个人开发）
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