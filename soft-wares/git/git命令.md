# Git 常用命令 for idea Terminal


[简书 - Git 常用命令](https://www.jianshu.com/p/46ffff059092)

    git init                                                初始化仓库

    git config user.name gxin                             本地库用户名

    git config user.email guoamocker@163.com                本地库用户邮箱

    git config --global user.name gxin                    当前操作系统用户名

    git config --global user.email guoamocker@163.com       当前操作系统用户邮箱

    git status                                              查看工作区、暂存区状态

    git remote -v                                           查看当前所有远程地址别名

    git push [别名] [分支名]                                  推到远端

    git add [file name]                                     将文件添加到git版本控制


    git pull [别名][分支名]

    git commit -m "[commit message]" [file name]            暂存区文件提交到本地仓库

    git log                                                 历史提交记录
        1.HEAD@{2}                                          HEAD@{移动到当前版本需要多少步}

        输入字母 q 退出

    https://www.jianshu.com/p/0805b5d5d893




    git reset --hard [局部索引值]                             重置为某版本
        1.git reset --hard a6ace91

    git diff [file name]                                     将工作区中的文件和暂存区进行比较


    gitbash  ->  gitk  图形化界面

    git config --global --unset http.proxy                   设置代理 - 提交 git 失败时，timeout 可以尝试
----

##### 分支

    git branch [branch name]                                  创建分支

    git branch -v                                             查看分支

    git checkout [branch name]                                切换分支

    git merge [new file branch name]                          将有新内容的分支合并到当前分支

##### 拉取  pull = fetch + merge

    git fetch [远程库地址别名] [远程分支名]
    git merge [远程库地址别名/远程分支名]
    git pull [远程库地址别名] [远程分支名]

##### 冲突解决

    冲突的解决
        第一步：编辑文件，删除特殊符号
        第二步：把文件修改到满意的程度，保存退出
        第三步：git add [文件名]
        第四步：git commit -m "日志信息"  注意：此时 commit 一定不能带具体文件名


##### 检出

    git checkout -b branchname <commitId>


##### SSH 登录

     进入当前用户的家目录
        $ cd ~  删除.ssh 目录
        $ rm -rvf .ssh
     运行命令生成.ssh 密钥目录
        $ ssh-keygen -t rsa -C atguigu2018ybuq@aliyun.com
        [注意：这里-C 这个参数是大写的 C]
     进入.ssh 目录查看文件列表
        $ cd .ssh
        $ ls -lF
     查看 id_rsa.pub 文件内容
        $ cat id_rsa.pub
     复制 id_rsa.pub 文件内容，登录 GitHub，点击用户头像→Settings→SSH and GPG keys
     New SSH Key
     输入复制的密钥信息
     回到 Git bash 创建远程地址别名
        git remote add origin_ssh git@github.com:atguigu2018ybuq/huashan.git
     推送文件进行测试


##### 9 Gitlab 服务器搭建过程

    9.1官网地址
        首页：https://about.gitlab.com/
        安装说明：https://about.gitlab.com/installation/

    9.2安装命令摘录
        sudo yum install -y curl policycoreutils-python openssh-server cronie
        sudo lokkit -s http -s ssh
        sudo yum install postfix
        sudo service postfix start
        sudo chkconfig postfix on
        curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.rpm.sh | sudo bash
        sudo EXTERNAL_URL="http://gitlab.example.com" yum -y install gitlab-ee
      实际问题：yum 安装 gitlab-ee(或 ce)时，需要联网下载几百 M 的安装文件，非常耗时，所以应提前把所需 RPM 包下载并安装好。
      下载地址为：
        https://packages.gitlab.com/gitlab/gitlab-ce/packages/el/7/gitlab-ce-10.8.2-ce.0.el7.x86_64.rpm

    9.3调整后的安装过程
        sudo rpm -ivh /opt/gitlab-ce-10.8.2-ce.0.el7.x86_64.rpm
        sudo yum install -y curl policycoreutils-python openssh-server cronie
        sudo lokkit -s http -s ssh
        sudo yum install postfix
        sudo service postfix start
        sudo chkconfig postfix on
        curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | sudo bash
        sudo EXTERNAL_URL="http://gitlab.example.com" yum -y install gitlab-ce
      当前步骤完成后重启。

    9.4gitlab 服务操作
         初始化配置 gitlab
            gitlab-ctl reconfigure
         启动 gitlab 服务
            gitlab-ctl start
         停止 gitlab 服务
            gitlab-ctl stop

    9.5浏览器访问
        访问 Linux 服务器 IP 地址即可，如果想访问 EXTERNAL_URL 指定的域名还需要配置
        域名服务器或本地 hosts 文件。
        初次登录时需要为 gitlab 的 root 用户设置密码。
            root/atguigu2018good
        ※应该会需要停止防火墙服务：
            service firewalld stop








--------------
    https://www.zhihu.com/people/wenshaojin

-- merge：

    git merge dev
        发生冲突
    vi GitStudy.java
        编辑冲突行，保留所需
    git add GitStudy.java
    git commit -m ‘提交合并冲突’



-- Rebase：变基

    区别：Git 不会尝试确定要保留或不保留哪些文件。我们执行 rebase 的分支总是含有我们想要保留的最新近的修改！这样我们不会遇到任何合并冲突，而且可以保留一个漂亮的、线性的 Git 历史记录。

    git rebase master







-- cherry-pick  拣选

    git cherry-pick 76d12
    不想要整个 dev 分支，而只需要这个提交！



-- fetching  取回

    git pull 实际上是两个命令合成了一个：git fetch 和 git merge

-- reflog

    git reflog 是一个非常有用的命令，可以展示已经执行过的所有动作的日志。包括合并、重置、还原，基本上包含你对你的分支所做的任何修改。





--
git log --author="guoxin-2" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' -




















































































































