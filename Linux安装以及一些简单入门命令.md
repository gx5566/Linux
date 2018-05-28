### 一.linux 简介

>   Linux是一套免费使用和自由传播的类Unix操作系统，是一个多用户，多任务，支持多线程和多CPU的操作系统。
>
>   由林纳斯.托瓦兹在1991年10月5号推出
>
>   ##### 系统特点：
>
>   ```
>   开放
>   多用户
>   多任务
>   出色的速度性能
>   良好的用户界面
>   丰富的网络功能
>   可靠的系统安全
>   良好的移植性
>   具有标准兼容性
>   ```
>
>   ##### 应用领域
>
>   ```
>   服务器
>   云计算
>   嵌入式
>   政府
>   企业
>   影视
>   超算
>   桌面
>   ```
>
>   ##### 系统组成
>
>   ```
>   Linux内核:
>   	操作系统的心脏，运行程序和管理硬件设备的核心程序
>   Linux Shell:
>   	系统的用户界面，提供用户与内核进行交互操作的一种接口
>   Linux 文件系统:
>   	文件存储在磁盘等存储设备上的组织方法
>   Linux 应用程序
>   	标准的程序集，比如文本编辑，编程语言，Window，办公套件，Internet工具，数据库等
>   ```
>
>   ##### linux 版本
>
>   ```
>   Ubuntu
>   Centos
>   Fedora
>   RedHat
>   SUSE
>   Debian
>   Kali
>   ...
>   ```

### 二.Ubuntu

> Ubuntu（乌班图）是一个基于Debian的以桌面应用为主的Linux操作系统，据说其名称来自非洲南部祖鲁语或科萨语的“ubuntu”一词，意思是“人性”、“我的存在是因为大家的存在”，是非洲传统的一种价值观。
>
> Ubuntu的目标在于为一般用户提供一个最新同时又相当稳定，主要以自由软件建构而成的操作系统。Ubuntu目前具有庞大的社区力量支持，用户可以方便地从社区获得帮助。

#### 2.1 安装

> 在虚拟机上安装
>
> 虚拟机： vmware /VirtualBox ，mac下还可以使用： parallels  ， 其中VirtualBox是开源免费的。
>
> 使用vmware 安装（右击 - 以管理员身份运行）
>
> 安装虚拟机过程中会选择网络模式：
>
> ```
> 虚拟机的网络类型的简单理解： 
> 　　虚拟机是在我们的操作系统里使用软件模拟出来的，相当于虚拟机是寄宿在我们的真实的物理机的操作系统里的，虚拟机和物理机之间的关系是 寄宿与被寄宿的关系， 真实的物理机被称为宿主机。
> 　　1.  bridged（桥接模式） ：  我们的电脑在上网的时候都需要有一个网络地址（IP地址），通过这个地址可以确定我们的电脑在网络上的位置，桥接模式就是将我们虚拟机中的网卡的网络地址 放在我们真实的物理机的网卡上。 这样的话，我们的虚拟机就好像跟我们的宿主机所在的局域网中的一台机器一样。 桥接模式适合有路由器的情况，和真实的物理环境一样。
> 　　2. NAT（网络地址转换模式） ： 在宿主机上制作一个虚拟网卡，通过这个网卡，给虚拟机分配IP。宿主机在这里的角色相当于局域网中的路由器。NAT模式适合于没有路由器的情况，虚拟机通过宿主机去上网。　　
> 　　3.Host-Only（模式）： 和NAT模式很像，唯一的区别是，没有地址转换服务，所以该模式下虚拟机只能访问到主机。无法访问外网。
> ```

#### 2.2 安装虚拟机可能出现的问题

> 安装是出现的问题是 CPU 不支持虚拟化
>
> 解决：
>
> ```
> 1.首先需要确定计算机型号和菜谱，BIOS(基本输入输出系统)系统型号，因为过老的计算机是不支持虚拟机化的
> 2.检测方式：
> 	开机时按 F2，F12，DEL,ESC 等键就可以进到 BIOS[至于按哪个 看电脑品牌]
> 3.进入 BIOS 后，找到 Configuration 选项或者 Security选项， 然后选择 Virtualization或者 Intel Virtual Technology 就可以开始操作了
> 4.然后回车 讲至设置为 Enabled
> 5.保存 BIOS 设置重启计算机
> 6.进入操作系统 右键 选择任务管理器 - 性能 - CPU - 查看虚拟化设置(已启动表示设置成功了， 可以装虚拟机了)
> ```

#### 2.3 安装 iso 镜像时区的选择

> 选择上海
>
> 代表中国的共有5个城市，分别是哈尔滨、上海、重庆、乌鲁木齐和喀什
>
> 在1949年以前，5个时区分别以这5个城市为代表，分别是：长白时区GMT+8:30、中原标准时区GMT+8、陇蜀时区GMT+7、新藏时区GMT+6和昆仑时区GMT+5:30。这是1912年北京观象台制订，并在后来由内政部批准过的。

#### 2.4 将鼠标从虚拟机中移出

> CTRL+ALT
>
> 编辑 - 偏好设置 - 热键

#### 2.5 安装完镜像之后忘记密码

> 重启虚拟机 - 重启期间长按 shift - 按 e 进入编辑启动项
>
> ​	— 向下滑动找到
>
> ​		linux      /boot/vmlinuz-4.4.0-21-gegeric… ro quiet_splash $vt_handoff
>
> ​	修改：从 ro 开始 修改为
>
> ​		rw init=/bin/bash 
>
> ​	然后按 ctrl + x 或者 F10
>
> ​	接着输入 passwd  用户名
>
> ​	然后输入新的密码
>
> ​	然后重启虚拟机 就可以已新的密码登陆了

#### 2.6 设置分辨率(ubantu 18)

> 设置 -devices -- displays - resolution - 设置分辨率
>
> 右击右上角的应用 保持设置即可（alt 加鼠标拖动页面）
>
> 另外一种设置方式：
>
> ​	安装 vmware tools 【保证两个系统文件可以共享】
>
> 步骤：
>
> ​	虚拟机/找到当前虚拟机右键点击 —> 安装 vmware tools 选项 —> 光盘出现 —>双击打开 ——> 双击vmwaretoiso —> 将其中的内容拖至桌面 —> 进入文件夹 ——> 右击在终端打开 —> 
>
> ​	命令：
>
> ​		./wmware-install.pl [回车]
>
> ​		权限不够
>
> ​		更改命令：
>
> ​		sudo ./wmware-install.pl
>
> ​		输入密码  【回车】
>
> ​		提示 no  —> 输入 yes
>
> ​		之后一直按照提示回车 遇到 yes 输入 yes即可
>
> ​		安装完成系统重启
>
> ​		

#### 2.7 目录结构

> 指令：
>
> ​	列出文件详细信息  ls -l  
>
> ​		在 linux 下所有东西都视作文件 【目录也视作文件】
>
> ​	查看根的信息 ls -l /
>
> ​		将/视作根  在根下有很多目录：			
>
> ```
> LInux目录结构： 
>
> / ： 所有目录都在
> /boot : boot 配置文件、内核和其它启动 时所需的文件
> /etc ： 存放系统配置有关的文件
> /home ： 存放普通用户目录
> 	 ls /home/ ----> xiaomu
> 	 每新增一个用户 都在 home 目录下增加一个普通用户名的目录
> /mnt ： 硬盘上手动 挂载的文件系统
> 	挂载： 把硬盘连接在文件系统上
> 		类似于大卡车挂在车头上一样
> 	mnt 默认是空的
> /media ： 自动挂载（加载）的硬盘分区以及类似CD、数码相机等可移动介质。
> 		设置 ---> cd 连接
> 		在 files ---> other ---> cumputer ---> media ---> xiaomu ---> 光盘
> /cdrom ： 挂载光盘 
> /opt ： 存放一些可选程序,如某个程序测试版本,安装到该目录的程序的所有数据,库文件都存在同个目录下
> /root ： 系统管理员的目录，对于系统来说，系统管理员好比上帝，他可以对系统做任何操作，比如删除你的文件，一般情况下不要使用root用户。
> 		管理员 根目录
> /bin ： 存放常用的程序文件（命令文件）。
> /sbin ： 系统管理命令，这里存放的是系统管理员使用的管理程序 
> /tmp ： 临时目录，存放临时文件，系统会定期清理该目录下的文件。
> /usr ： 在这个目录下，你可以找到那些不适合放在/bin或/etc目录下的额外的工具。比如游戏、打印工具等。/usr目录包含了许多子目录： /usr/bin目录用于存放程序;/usr/share用于存放一些共享的数据，比如音乐文件或者图标等等;/usr/lib目录用于存放那些不能直接 运行的，但却是许多程序运行所必需的一些函数库文件。/usr/local ： 这个目录一般是用来存放用户自编译安装软件的存放目录；一般是通过源码包安装的软件，如果没有特别指定安装目录的话，一般是安装在这个目录中。
> 　　　　/usr/bin/ 非必要可执行文件 (在单用户模式中不需要)；面向所有用户。
> 　　　　/usr/include/ 标准包含文件。
> 　　　　/usr/lib/ /usr/bin/和/usr/sbin/中二进制文件的库。
> 　　　　/usr/sbin/ 非必要的系统二进制文件，例如：大量网络服务的守护进程。
> 　　　　/usr/share/ 体系结构无关（共享）数据。
> 　　　　/usr/src/ 源代码,例如:内核源代码及其头文件。
> 　　　　/usr/X11R6/ X Window系统 版本 11, Release 6.
> 　　　　/usr/local/ 本地数据的第三层次， 具体到本台主机。通常而言有进一步的子目录， 例如：bin/、lib/、share/.
>
> /var ： 该目录存放那些经常被修改的文件，包括各种日志、数据文件；
>     /var/cache/ 应用程序缓存数据。这些数据是在本地生成的一个耗时的I/O或计算结果。应用程序必须能够再生或恢复数据。缓存的文件可以被删除而不导致数据丢失。
>     /var/lib/ 状态信息。 由程序在运行时维护的持久性数据。 例如：数据库、包装的系统元数据等。
>     /var/lock/ 锁文件，一类跟踪当前使用中资源的文件。
>     /var/log/ 日志文件，包含大量日志文件。
>     /var/mail/ 用户的电子邮箱。
>     /var/run/ 自最后一次启动以来运行中的系统的信息，例如：当前登录的用户和运行中的守护进程。现已经被/run代替[13]。
>     /var/spool/ 等待处理的任务的脱机文件，例如：打印队列和未读的邮件。
>     /var/spool/mail/ 用户的邮箱(不鼓励的存储位置)
>     /var/tmp/ 在系统重启过程中可以保留的临时文件。
> /lib : 目录是根文件系统上的程序所需的共享库，存放了根文件系统程序运行所需的共享文件。这些文件包含了可被许多程序共享的代码，以避免每个程序都包含有相同的子程序的副本，故可以使得可执行文件变得更小，节省空间。
> /lib32 : 同上
> /lib64 ： 同上
> /lost+found ： 该目录在大多数情况下都是空的。但当突然停电、或者非正常关机后，有些文件就临时存放在；
> /dev : 存放设备文件
> /run ： 代替/var/run目录，
> /proc : 虚拟文件系统，可以在该目录下获取系统信息，这些信息是在内存中由系统自己产生的，该目录的内容不在硬盘上而在内存里；
> 	cat /proc/cpuinfo
> /sys ： 和proc一样，虚拟文件系统，可以在该目录下获取系统信息，这些信息是在内存中由系统自己产生的，该目录的内容不在硬盘上而在内存里；
> ```
>
> 根体系：
>
> ​	![linux 根下的目录结构体系](/Users/liuyanan/Documents/python/笔记整理/linux 根下的目录结构体系.png)

#### 2.8 解决Ubuntu中vi命令的编辑模式下不能正常使用键盘问题

> 在Ubuntu中，进入vi命令的编辑模式，发现按方向键不能移动光标，会输出ABCD，以及退格键也不能正常删除字符。这是由于Ubuntu预装的是vim-tiny，而我们需要使用vim-full，解决方法很简单，只需要以下两步： 
> 　　步骤一，输入下述命令以卸载vim-tiny：
>
> ```
> sudo apt-get remove vim-common
> ```
>
> 　　步骤二，输入下述命令以安装vim-full：

> ```
> sudo apt-get install vim
> ```

#### 2.9 查看操作系统是否支持中文

> 语言环境
>
> 查看是否安装了中文支持
>
> ```
> locale -a 
> ```
>
> 如果有 zh_CN.utf8 则表示系统已经安装了中文locale，如果没有则需要安装相应的软件包。安装方式如下：
>
> sudo apt-get install language-pack-zh-hans language-pack-zh-hans-base
>
> #### 用户系统
>
> 1. 普通用户，就是我们自己创建的用户，平时尽量使用普通用户
> 2. 超级管理员，无敌的存在，可以摧毁系统中的任何东西，普通用户也可以调用超级管理员指令
>    - 使用sudo 指令 之后输入密码，调用超级管理员命令
>    - sudo !!   使用超级管理员执行上一条命令
>
>    ​

#### 2.10 安装软件

> 软件管理 apt ( Advanced Packaging Tool ) , 他可以自动下载、配置、安装软件包；简化了Linux系统上的。Debian及衍生版中都包含了apt [老版使用 apt-get]， RedHat系列的linux的则使用yum来进行管理，其中Fedora22中Centos7中开始使用dnf 来替代yum。
>
> ```
> apt-cache search package 搜索包
> apt-cache show package 获取包的相关信息，如说明、大小、版本等
> sudo apt-get install package 安装包
> sudo apt-get install package –reinstall 重新安装包
> sudo apt-get -f install 强制安装
> sudo apt-get remove package 删除包
> sudo apt-get remove package –purge 删除包，包括删除配置文件等
> sudo apt-get autoremove 自动删除不需要的包
> sudo apt-get update 更新源
> sudo apt-get upgrade 更新已安装的包
> sudo apt-get dist-upgrade 升级系统
> sudo apt-get dselect-upgrade 使用 dselect 升级
> apt-cache depends package 了解使用依赖
> apt-cache rdepends package 了解某个具体的依赖
> sudo apt-get build-dep package 安装相关的编译环境
> apt-get source package 下载该包的源代码
> sudo apt-get clean && sudo apt-get autoclean 清理下载文件的存档
> sudo apt-get check 检查是否有损坏的依赖
> ```
>
> apt的配置文件
>
> ```
> /etc/apt/sources.list 设置软件包的获取来源
> /etc/apt/apt.conf apt配置文件
> /etc/apt/apt.conf.d apt的零碎配置文件
> /etc/apt/preferences 版本参数
> /var/cache/apt/archives/partial 存放正在下载的软件包
> /var/cache/apt/archives 存放已经下载的软件包
> /var/lib/apt/lists 存放已经下载的软件包详细信息
> /var/lib/apt/lists/partial 存放正在下载的软件包详细信息
> ```
>
> dpkg是Debian软件包管理器的基础，被用于安装、卸载和供给和.deb软件包相关的信息。dpkg本身是一个底层的工具，本身并不能从远程包仓库下载包以及处理包的依赖的关系，需要将包从远程下载后再安装。DPKG常用命令：
>
> ```
> dpkg -i package.deb 安装包
> dpkg -r package 删除包
> dpkg -P package 删除包（包括配置文件）
> dpkg -L package 列出与该包关联的文件
> dpkg -l package 显示该包的版本
> dpkg –unpack package.deb 解开 deb 包的内容
> dpkg -S keyword 搜索所属的包内容
> dpkg -l 列出当前已安装的包
> dpkg -c package.deb 列出 deb 包的内容
> dpkg –configure package 配置包
> ```
>
> 

#### 2.11 简易常用命令

##### 快捷键

> ctrl-a ： 把光标移动到命令行最开始的地方。 
>
> ctrl+d: 退出终端
>
> ctrl-e ： 把光标移动到命令行末尾。 
> ctrl-u ： 清除命令行中光标所处位置之前的所有字符。 
> ctrl-k ： 清除从提示符所在位置到行末尾之间的字符
> ctrl-w ： 清除左边的字段 
> ctrl-y ： 将会贴上被ctrl-u 或者 ctrl-k 或者 ctrl-w清除的部分。 
> ctrl-r ： 将自动在命令历史缓存中增量搜索后面入的字符。 
> tab ： 命令行自动补全－自动补全当前的命令行。如果启用自动补全脚本命令参数和选项也可以自动补齐。ctrl-l ： 清屏

##### 命令

> ```python 
>
> 1. control + alt + t 快速打开终端
> 2. ls 列出当前目录中的文件
> 	格式：ls [选项] [目录名] 
>
>     -a 用于显示所有文件和子目录(保罗点文件)。
>
>     -l 除了文件名之外，还将文件的权限、所有者、文件大小等信息详细列出来。 (文件大小是字节)
>     -lh 与-l 类似  只不过文件大小显示的是 KB [默认是按照文件名的 abcd 排序的]
> 	-lht 与-l -lh 类似  排序是按照修改时间降序排的
>     -lhtr 按照时间升序排
>     -r 将目录的内容清单以英文字母顺序的逆序显示。
>
>     -t 按文件修改时间进行排序，而不是按文件名进行排序。
>
>     -A 同-a，但不列出“.”(表示当前目录)和“..”(表示当前目录的父目录)。
>
>     -F 在列出的文件名和目录名后添加标志。例如，在可执行文件后添加“*”，在目录名后添加“/”以区分不同的类型。
>
>     -R 如果目标目录及其子目录中有文件，就列出所有的文件。
>     	这个指令时将所有目录遍历一下。
>       	与其类似的有个 tree [如果没有安装 apt install tree]
>         	像树形图一样把文件结构显示出来
> 3.查看一个命令的详细信息：  man  
> 	例如 man ls
> 	这样做显示的太乱了  可以使用该链接实现在线命令查询：http://man.linuxde.net/
> 4. cd 目录操作  
>     - cd 目录名，进入某一目录
> 	- cd .. 返回上一级目录
> 	  cd - 返回上一次切换的目录
> 	  cd  # 回到当前用户的家目录
> 		一个点(.) ，在linux中代表当前目录，如果这个点在 文件名前，代表这个文件是一个隐藏文件
> 		两个点 (..)
> 5.pwd ： 查看当前的工作路径
> 6. mkdir  目录名   创建一个目录
> 	mkdir -p 多级目录
> 7. rmdir   目录名   删除一个目录（空目录）
> 8. rm 删除   
> 	rm -i  file 删除文件时会询问
> 	 rm -rf 目录名 循环强制删除，不提示，慎用
> 	 rm -f  file1 # 强制删除文件
>       rm -r  a/b/file1  # 删除指定目录及其下的所有文件和目录
>       rm -rf  a/b/file1  #  强制删除指定目录及其下的所有文件和目录
>
> 	# rm 命令太危险，不建议使用  rm -rf / [删除根 -- 会造成系统瘫痪]
>     
> 7. touch ： 改变文件或目录的时间，文件不存在时会创建一个空文件。
> 	  touch file1 # file1 不存在时被创建
>       touch -c file1 # 不创建文件
>       touch -r ref_file file1  更新file1.txt的时间戳和ref+file相同
>       touch -t 201210120505.25 file1
>
>       #  -t  time 使用指定的时间值 time 作为指定文件相应时间戳记的新值．此处的 # # time规定为如下形式的十进制数:      
>       #  [[CC]YY]MMDDhhmm[.SS]     
>       #   这里，CC为年数中的前两位，即”世纪数”；YY为年数的后两位，即某世纪中的年数．如果不给出CC的值，则touch   将把年数CCYY限定在1969--2068之内．MM为月数，DD为天将把年数CCYY限定在1969--2068之内．MM为月数，DD为天数，hh 为小时数(几点)，mm为分钟数，SS为秒数．此处秒的设定范围是0--61，这样可以处理闰秒．这些数字组成的时间是环境变量TZ指定的时区中的一个时 间．由于系统的限制，早于1970年1月1日的时间是错误的。
> 8. help 命令名 查看指定命令的帮助文档，命令 --help [一些指令的使用 help 是存在差异的 可以根据提示来完成]
> 9.文件类型
> 	ls -l 列出文件列表
>   			-rw------- 1 xiaomu xiaomu 1814528 五月 22 21:49 core
>               drwxr-xr-x 2 xiaomu xiaomu    4096 五月 23 16:50 Desktop
>               drwxr-xr-x 2 xiaomu xiaomu    4096 五月 14 21:18 Documents
>               drwxr-xr-x 2 xiaomu xiaomu    4096 五月 14 21:18 Downloads
>               -rw-r--r-- 1 xiaomu xiaomu    8980 五月 14 21:08 examples.desktop
>               drwxr-xr-x 2 xiaomu xiaomu    4096 五月 14 21:18 Music
>               drwxr-xr-x 2 xiaomu xiaomu    4096 五月 14 21:18 Pictures
>               drwxr-xr-x 2 xiaomu xiaomu    4096 五月 14 21:18 Public
>               drwxr-xr-x 2 xiaomu xiaomu    4096 五月 14 21:18 Templates
>              drwxr-xr-x 2 xiaomu xiaomu    4096 五月 14 21:18 Videos
>        ls -l /
>             drwxr-xr-x   2 root root      4096 五月 22 23:49 bin
>             drwxr-xr-x   3 root root      4096 五月 22 21:48 boot
>             drwxrwxr-x   2 root root      4096 五月 14 21:08 cdrom
>             drwxr-xr-x  19 root root      4060 五月 23 16:48 dev
>             drwxr-xr-x 129 root root     12288 五月 23 16:48 etc
>             drwxr-xr-x   3 root root      4096 五月 14 21:08 home
> 	ls -l /dev/
>     		crw-------  1 root root     10, 175 五月 23 16:48 agpgart
> 			crw-r--r--  1 root root     10, 235 五月 23 16:48 autofs
>      ls -l  /dev  # 可以查看字符设备文件和块设备文件
> 	ls -l  /run  #  可以找到socket文件 
> 	ls -l  /run/systemd/inhibit/ # 可以查看到管道文件
> 	列出文件列表后有-/d/c/l/p/s 开头的文件， 这些分别表示：
>     		-  普通文件
>               d  目录文件
>               b 块设备文件
>               c  字符设备文件
>               l  链接文件
>               p 管道文件
>               s  socket文件
> 10.文件权限
> 	文件类型后 main 跟随的 rwx 表示的是文件权限
>   	rwx r-x r-x 
>     	三个一组，这三个分别表示用户权限 所在组的权限  其他用户的权限
>       	r ： 表示可读, 可以用数字 4 来表示
>         w ： 标识可写 ，可以用数字 2 来表示
>         x ： 表示可执行 ， 可以用数字 1 来表示
>         - ：表示没有相应权限  可以用数字 0 来表示
>         
>         gedit -- 可以打开一个文本编辑器
>         	python + tab 可以查看 python 的版本
>         	执行 py 文件默认是 python2的环境
>           	所以要在 py 文件的头部添加 #!/usr/bin/env python3  [指名解释器所在的位置] linux 下必须声明
>         ./file --- 执行某个文件文件 [以这种方式执行文件 该文件必须是具有 x 权限的]
>         修改权限的方式：(+号是添加权限 -号是去除权限)
>         	  chmod o+w  file1
>               chmod g-w file1
>               chmod go-w file1
>               chmod u=rwx file1
>               chmod 755  file1  # -rwxr-xr-x (755) 只有所有者才有读，写，执行的权限，组群和其他人只有读和执行的权限
>               chmod 644  file #  -rw-r--r-- (644) 只有所有者才有读和写的权限，组群和其他人只有读的权限
>          
>               #  u 代表所有者（user）
>               #  g 代表所有者所在的组群（group）
>               #  o 代表其他人，但不是u和g （other）
>               #  a 代表全部的人，也就是包括u，g和o	
>         
> 9.mv  ： 移动或重命令文件或目录
> 	mv SOURCE DEST  # 
>         mv test.log test.txt  # 文件改名
>         mv test1.txt dir1/      #移动文件
>         mv test1.txt  test2.tx  test3.tx dir1/      #移动多个文件
> 10.cp ： 复制
> 		cp SOURCE DEST # 复制文件
>         cp -i  SOURCE DEST  #   如果遇到需要覆盖的情况，则提示
>     		cp -i ww.py ee.py
>       		cp -i ww.py ee.py [这个 ee 会被提示是否覆盖]
>       	
>         cp -r  dir1  dir2  # 若给出的源文件是一目录文件，此时cp将递归复制该目录下所有的子目录和文件。此时目标文件必须为一个目录名[复制目录]
> 11.stat : 查看文件相信信息
>   stat filename 
>     #  Access time(atime):是指取用文件的时间，所谓取用，常见的操作有：使用编辑器查看文件内容，使用cat命令显示文件内容，使用cp命令把该文件（即来源文件）复制成其他文件，或者在这个文件上运用grep sed more less tail head 等命令，凡是读取而不修改文件的操作，均衡改变文件的Access time.  
>     #  Modify time(mtime)：是指修改文件内容的时间，只要文件内容有改动（如使用转向输出或转向附加的方式）或存盘的操作，就会改变文件的Modify time,平常我们使用ls –l查看文件时，显示的时间就是Modify time  
>     #  Change time(ctime):是指文件属性或文件位置改动的时间，如使用chmod，chown,mv指令集使用ln做文件的硬是连接，就会改变文件的Change time.
> 12.cat : 链接文件后输出文件内容到屏幕上，其实就是查看文件内容    
> 11. reboot 重启
> 12. shutdown -h now 立刻关机
> 13. shutdown -r now 立刻重启
> 14. shutdown -h +1 一分钟后重启  
> 15. control + l 清屏
> 16. clear 清屏
> 17. control + c 中断执行
> 18. vi 编辑器 
>     - vi 路径 打开某一个文件
>     - i 在当前光标位置进行插入
>     - 输入完成在英文模式下按esc，输入冒号 (:) ，wq 保存并退出
> 19.date
> 	date //显示当前日期
>     # 日期格式化
>     #       %Y     year
>     #       %m     month (01..12)
>     #       %d     day of month (e.g., 01)
>     #       %H     hour (00..23)
>     #       %I     hour (01..12)
>     #       %M     minute (00..59)
>     #       %S     second (00..60)
>     date +"%Y%m%d %H%M%S"
>         20160824 223856
>     date +"%Y-%m-%d %H:%M:%S"
>         2016-08-24 22:39:07
>
>     date -s //设置当前时间，只有root权限才能设置，其他只能查看。
>     date -s 20061010 //设置成20061010，这样会把具体时间设置成空00:00:00
>     date -s 12:23:23 //设置具体时间，不会对日期做更改
>     date -s “12:12:23 2006-10-10″ //这样可以设置全部时间
>
>     # 注意： 重新设置时间后需要将时间捅不到硬件时钟。方式如下：
>     hwclock -w  
>  20.cal 显示一个日历
>  	cal  #  现实当前月份的日历
>     cal -y  # 显示当年的日历
>     cal 2016 #  # 显示指定年份的日历
> 21.设置时区 
> 	tzselect
>
> ```



#### 指令

##### 文件指令

```
wc   :统计指定文件中字节数、字数、行数，并将统计结果显示输出
	-c 统计字节数。
	-l 统计行数。
	-m 统计字符数。这个标志不能与 -c 标志一起使用。 
	-w 统计字数。一个字被定义为由空白、跳格或换行字符分隔的字符串
```

```
sort ： 排序
	sort [-fbMnrtuk] [file or stdin]
    选项与参数：
    -f  ：忽略大小写的差异，例如 A 与 a 视为编码相同；
    -b  ：忽略最前面的空格符部分；
    -n  ：使用『纯数字』进行排序(默认是以文字型态来排序的)；
    -r  ：反向排序；
    -u  ：就是 uniq ，相同的数据中，仅出现一行代表；
    -t  ：分隔符，默认是用 [tab] 键来分隔；
    -k  ：以那个区间 (field) 来进行排序的意思	
```

```python
xiaomu@xiaomu-virtual-machine:~/Desktop$ cat abc.txt
1245134
68752
4678934
affjhs
grege
fssd
dsc
xiaomu@xiaomu-virtual-machine:~/Desktop$ sort abc.txt 
1245134
4678934
68752
affjhs
dsc
fssd
grege

xiaomu@xiaomu-virtual-machine:~/Desktop$ cat abc.txt 
1245134:ghjh:yeuw
68752:euwhud:nda
3156132:duewi:ew
930194:adjks:fe
xiaomu@xiaomu-virtual-machine:~/Desktop$ sort -t ':' -k 2 abc.txt 
930194:adjks:fe
3156132:duewi:ew
68752:euwhud:nda
1245134:ghjh:yeuw
```

```
uniq ： 忽略或报告重复行
	uniq [-icu]
    选项与参数：
    -i   ：忽略大小写字符的不同；
    -c  ：进行计数
    -u  ：只显示唯一的行
```

```
cut命令可以从一个文本文件或者文本流中提取文本列
	选项与参数：
    -d  ：后面接分隔字符。与 -f 一起使用；
    -f  ：依据 -d 的分隔字符将一段信息分割成为数段，用 -f 取出第几段的意思；
    -c  ：以字符 (characters) 的单位取出固定字符区间；( -连接区间  ,取的是和的意思)
    
    xiaomu@xiaomu-virtual-machine:~/Desktop$ cat a.txt 
    ahfshfdfhsjkfa
    jfasdhfjsd
    djsbchjsab

    xiaomu@xiaomu-virtual-machine:~/Desktop$ cut -d 'f' -f 1 a.txt 
    ah
    j
    djsbchjsab
    
    xiaomu@xiaomu-virtual-machine:~/Desktop$ cut -c 1 a.txt 
    a
    j
    d
    
    xiaomu@xiaomu-virtual-machine:~/Desktop$ cut -c 1,3 a.txt 
    af
    ja
    ds
	
    xiaomu@xiaomu-virtual-machine:~/Desktop$ cut -c 1-3 a.txt 
    ahf
    jfa
    djs

```

```python
tee ： 读取标准输入的数据，并将其内容输出成文件。
	  tee file1  # 读取文件，并生成file1文件
      tee - a file1   # 读取文件 ，并追加，
      tee  file1 file2 向多个文件中输出内容 形成文件
      
xiaomu@xiaomu-virtual-machine:~/Desktop$ tee a.txt
1234
1234
adda
adda
dsf
dsf
cdc
cdc
^C
xiaomu@xiaomu-virtual-machine:~/Desktop$ cat a.txt
1234
adda
dsf
cdc

```

```python
history ： 查看执行过的命令。
	history  # 显示最近1000条历史命令
    history 5   # 显示最后5条命令
    !number# number为history之后命令前的序号：执行该条命令
    	每条命令前都有编号  可以通过编号执行对应的命令
    	xiaomu@xiaomu-virtual-machine:~/Desktop$ !426
          cat b.txt
          456
          fasf
          cxzc

    !命令 # 执行最后一条以指定命令开头的命令
    	xiaomu@xiaomu-virtual-machine:~/Desktop$ !cat
        cat b.txt
        456
        fasf
        cxzc
```

```python
命令不会一直都存放下去  最多只会显示1000条  查看信息如下：
xiaomu@xiaomu-virtual-machine:~/Desktop$ cat ~/.bashrc |grep -i hist
    # don't put duplicate lines or lines starting with space in the history.
    HISTCONTROL=ignoreboth
    # append to the history file, don't overwrite it
    shopt -s histappend
    # for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
    HISTSIZE=1000 #最多显示
    HISTFILESIZE=2000 #执行的命令都放在一个文件中 这个文件中最多放置2000条
    alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
```

```
命令存放的位置：
xiaomu@xiaomu-virtual-machine:~/Desktop$ ls -a ~/.bash*
/home/xiaomu/.bash_history  /home/xiaomu/.bashrc
/home/xiaomu/.bash_logout

打开存放命令的文件
xiaomu@xiaomu-virtual-machine:~/Desktop$ gedit /home/xiaomu/.bash_history 
```

```
more ：   查看文件内容
	当内容较多时 不会全部显示 最后会有更多提示语
	按着空格 一页一页的翻滚显示
	按回车 一行一行的翻滚显示
less  ： 查看文件内容
	与 more 类似
head 输出文件的开始的部分， 可以指定行数 , 默认显示10行
	head -n 5 file 
tail  ：   查看文件尾部的内容。默认显示最后10行
	tail file1
	tail -n 5 file1
	tail -f file1  # 动态监控文件的更新
	
		可以配合 echo 想文件中输入内容结合使用
```

```
which #查找其他命令的位置
	which ls
```

##### 用户管理

> linux使用文件保存用户信息 ：
>
> /etc/passwd 用户账户信息。
>
> /etc/shadow 安全用户账户信息。
>
> /etc/group 组账户信息。
>
> /etc/gshadow 安全组账户信息。
>
> /etc/default/useradd 账户创建的默认值。
>
> /etc/skel/ 包含默认文件的目录。
>
> /etc/login.defs Shadow 密码套件配置。
>
> **man 5 文件  —— 查看文件中的信息的作用**

```
chown ： 更改文件的所有者和所有组
    chown root:root  file
    chown root   file  
    chown :root   file
```

```python
useradd：  添加用户(通过管理员身份添加)
	# -c 备注 加上备注。并会将此备注文字加在/etc/passwd中的第5项字段中         
    #  -d 用户主文件夹。指定用户登录所进入的目录，并赋予用户对该目录的的完全控制权        
    #  -e 有效期限。指定帐号的有效期限。格式为YYYY-MM-DD，将存储在/etc/shadow         
    #  -f 缓冲天数。限定密码过期后多少天，将该用户帐号停用       
    #  -g 主要组。设置用户所属的主要组  www.cit.cn           
    #  -G 次要组。设置用户所属的次要组，可设置多组         
    # -M 强制不创建用户主文件夹         
    #  -m 强制建立用户主文件夹，并将/etc/skel/当中的文件复制到用户的根目录下         
    #  -p 密码。输入该帐号的密码         
    #  -s shell。用户登录所使用的shell         
    #  -u uid。指定帐号的标志符user id，简称uid

    useradd user1 # 添加用户 user1
    useradd  -d /home/userTT user2 
```

```python
#创建用户[普通用户是在 home 目录下的]
xiaomu@xiaomu-virtual-machine:~/Desktop$ sudo useradd user1
#检测 home 目录下是否有 user1用户
xiaomu@xiaomu-virtual-machine:/home$ ls -l
#没有的创建的新用户的解决方案： 在 home 目录下创建一个与用户名一致的文件夹
xiaomu@xiaomu-virtual-machine:/home$ sudo mkdir /home/user1
xiaomu@xiaomu-virtual-machine:/home$ ls -l
  total 8
  drwxr-xr-x  2 root   root   4096 5月  24 22:35 user1
  #但是此时用户的所有者与所属组都是超级管理员的
  drwxr-xr-x 19 xiaomu xiaomu 4096 5月  24 21:54 xiaomu
#修改目录的所有者与所有组的权限
xiaomu@xiaomu-virtual-machine:/home$ sudo chown user1:user1 /home/user1
xiaomu@xiaomu-virtual-machine:/home$ ls -l
    total 8
    drwxr-xr-x  2 user1  user1  4096 5月  24 22:35 user1
    drwxr-xr-x 19 xiaomu xiaomu 4096 5月  24 21:54 xiaomu
```

```python
#设置新用户的密码
xiaomu@xiaomu-virtual-machine:/home$ sudo passwd user1
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
```

```python
#登陆新用户
xiaomu@xiaomu-virtual-machine:/home$ su - user1
Password: 
$ 
```

**注意：**

​	在新的用户的前提下 输入指令的界面与原始用户不一致：

​		原始用户：xiaomu@xiaomu-virtual-machine:/home$

​		新的用户： $

**原因：**	

​	在新用户下缺少配置文件

​	先看原始用户下的配置文件：

```
$ ls -a /home/xiaomu/.bash*
	/home/xiaomu/.bash_history  /home/xiaomu/.bashrc
	/home/xiaomu/.bash_logout	
```

**解决方案：**

​	需要将.bashrc 和 .bash_logout 拷贝到当前用户

```python
#拷贝文件的位置
$ ls -a /etc/skel/
.  ..  .bash_logout  .bashrc  examples.desktop	.profile
#将以.bash 开头的文件全部拷贝到当前目录下
$ cp /etc/skel/.bash* .
#查看当前用户下是否有该文件
$ ls -a
.  ..  .bash_logout  .bashrc
#ctrl + d 退出当前用户
#打开编辑 etc 下的 passwd 文件
 sudo vi /etc/passwd
为新建的用户后面添加/bin/bash
退出编辑
重新登录新用户即可
```

**另外一种创建用户的方式**	:这种创建方式弥补了刚才还需要设置配置文件的缺失

```python
xiaomu@xiaomu-virtual-machine:/home$ sudo useradd -m -s /bin/bash user2
xiaomu@xiaomu-virtual-machine:/home$ ls
	user1  user2  xiaomu
xiaomu@xiaomu-virtual-machine:/home$ ls -l
    total 12
    drwxr-xr-x  2 user1  user1  4096 5月  24 22:57 user1
    drwxr-xr-x  2 user2  user2  4096 5月  24 23:16 user2
    drwxr-xr-x 19 xiaomu xiaomu 4096 5月  24 23:09 xiaomu
```

```python
userdel : 删除用户
	sudo userdel user2
		#这个删除只是在/etc/passwd 将用户信息删除了 但是在家目录中的用户信息还没有删除
	sudo userdel -r user2
		#既可以删除/etc/passwd 中的用户信息 以及家目录下的都会被删除
```

```python
usermod : 修改用户信息
    #　-c<备注> 　修改用户帐号的备注文字。 
    #　-d登入目录> 　修改用户登入时的目录。 
    #　-e<有效期限> 　修改帐号的有效期限。 
    #　-f<缓冲天数> 　修改在密码过期后多少天即关闭该帐号。 
    #　-g<群组> 　修改用户所属的群组。 
    #　-G<群组> 　修改用户所属的附加群组。 
    #　-l<帐号名称> 　修改用户帐号名称。 
    #　-L 　锁定用户密码，使密码无效。 
    #　-s<shell> 　修改用户登入后所使用的shell。 
    #　-u<uid> 　修改用户ID。 
    #　-U 　解除密码锁定。
    sudo usermod -G staff user2  # 将 newuser2 添加到组 staff 中 
    sudo usermod -l newuser1 newuser  # 修改 newuser 的用户名为 newuser1 
    sudo usermod -L newuser1  # 锁定账号 newuser1
    sudo suermod -p 密码  账户 #设置账户密码 [不建议使用这种 不安全 ]
    sudo usermod -U newuser1  # 解除对 newuser1 的锁定
id ---> 显示当前用户的信息
```

```
groupadd : 添加组
	groupadd group1 
	groupadd -g  1000 group1  # 指定gid
```

```
groupdel ： 删除组
	groupdel group1 # 删除组
```

```
su与 sudo
	 su  : 切换用户，没有参数时，默认切换为root用户；
	 	su -   # 切换为root 并加载user1的环境配置
		su -  user1 # 切换为user1 并加载user1的环境配置
     sudo ：   让当前用户暂时以管理员的身份root来执行命令。
		Ubuntu 默认没有启用root用户， 普通用户执行一些特殊的操作时，使用sudo就可以让普通用户以root用户的身份执行命令
sudo有一个配置文件： /etc/sudoers  ;  通过修改配置文件可以让指定用户使用sudo命令
```

```python
man sudoers # 查看man手册
看下面几行： 
# Host alias specification # 配置Host_Alias：就是主机的列表 
Host_Alias      HOST_FLAG = hostname1, hostname2, hostname3
# User alias specification # 配置User_Alias：就是具有sudo权限的用户的列表 
User_Alias USER_FLAG = user1, user2, user3 

# Cmnd alias specification # 配置Cmnd_Alias：就是允许执行的命令的列表，命令前加上!表示不能执行此命令.命令一定要使用绝对路径，避免其他目录的同名命令被执行，造成安全隐患 ,因此使用的时候也是使用绝对路径! 
Cmnd_Alias      COMMAND_FLAG = command1, command2, command3 ，!command4

# 配置Runas_Alias：就是用户以什么身份执行（例如root，或者oracle）的列表 
Runas_Alias RUNAS_FLAG = operator1, operator2, operator3 


# User privilege specification  
# 配置权限的格式如下： 
#  USER_FLAG HOST_FLAG=(RUNAS_FLAG) COMMAND_FLAG 

root    ALL=(ALL:ALL) ALL
如果不需要密码验证的话，则按照这样的格式来配置 
USER_FLAG HOST_FLAG=(RUNAS_FLAG) NOPASSWD: COMMAND_FLAG 


格式为：用户名(用户别名) 主机名(主机别名)=[(运行用户或是Runas_Alias)可选] [tag可选]  可以执行的命令(或Cmmd_Alias)  这样描述语法很生硬，不易理解，举例子
user1  host1 = /bin/kill　# user1 可以在host1上使用命令/bin/kill
user1  host1 = NOPASSWD: /bin/kill　# user1 可以在host1上使用命令/bin/kill 同时可以不必输入密码(这里就是使用了NOPASSWD　# 这个tag，默认是PASSWD)
user1  host1 = NOPASSWD: /bin/kill , PASSWORD: /bin/ls　# user1 可以在host1上使用命令/bin/kill无需输入密码，但是使用/bin/ls则需要输入密码
user1  host1 = (opterator) /bin/kill　# user1 可以在host1上使用命令/bin/kill但是必须是以operator用户运行这个命令，等价于# su -u opertor /bin/kill
user1  host1 = (:group_name) /bin/kill　# user1 可以在host1上使用命令/bin/kill,且必须以group_name这个用户群组里面的用户来运行。
%group_name host1 = /bin/kill　# 所有group_name里面的用户都可以在host1上执行/bin/kill(Linux中一般代表整个用户群组用# %group_name)
再举个实际例子，我之前对sudo su这个命令不理解，为什么我可以直接就su到root用户了呢，连密码都不需要？查看了一下sudoers文件才知道原来里面有这么一行：
xxx     ALL=NOPASSWD: /bin/su
```

##### 其他指令

```python
alias : 给命令起别名
	alias ll='ls -alF'
    alias la='ls -A'
    alias l='ls -CF'
如果需要别名永久生效，需要保存到 .bashrc 文件
	xiaomu@xiaomu-virtual-machine:~$ gedit .bashrc
```

```
配置环境变量 PATH
	类似于 windows 想再任意目录下执行一个命令 需要把该命令对应的bin路径【凡是可执行的文件一般都是房子啊 bin 目录下的】添加在 环境变量的 path 字段下
	在 linux 下如何配置环境变量呢？
		切换到对应的用户下  执行 vi ~/.profile文件  [~表示当前用户]
			添加 PATH = '..../BIN:$PATH'   [:$PATH --- 是拼接上其他设置的环境变量  $是获取原有变量的值]
查看当前设置的环境变量
	env
		PATH 下的字段 有很多 bin 路径

```

```
echo
	会将输入的字符串送往标准输出。输出的字符串间以空白字符隔开并在最后加上换行号。
	-n 不要在最后自动换行
```

```
管道符
	就是 |  ：他的作用是 将前一个命令的结果 交给后一个命令使用
	cat -n qq.py |sort -rn
		将前面命令的结果作用于后面的命令
```

```
重定向  

>   重定向，如果的文件存在，则覆盖文件内容，文件不存在时创建文件
		>ww.txt
		cat ww.txt [原内容清空]
>> 重定向，如果的文件存在，则向文件追加内容，文件不存在时创建文件
		>>ww.txt
		cat ww.txt
1>  标准正确输出，同上
		cat qq.py 1> mm
			将 qq.py的内容添加到 mm 文件中[mm 文件有内容的话会被清空]
1>> 标准正确输出，同上  
		追加不清空
2> 标准错误输出，同上
		可以将不存在的文件 写入到文件 如果正常写入的话 会提示错误
		但是如果使用错误输出的话 会将错误信息输出到文件中
		如果使用错误输出的话 将存在文件写入到指定文件中会写不进去的
2>> 标准错误输出，同上

&> 标准正确输出和标准错误输出，同上
	将1和2结合在一起了
```

##### 查找的指令

```
locate 查找文件
	locate 关键字 全局查找含有关键字的内容
	locate /etc/sh   # 搜索路径中有/etc/sh开头的文件。 
	locate ~/a   # 搜索用户主目录下，所有以a开头的文件。 
	locate -i ~/a   # 搜索用户主目录下，所有以a开头的文件，并且忽略大小写。
    
 locate 是在数据库中进行查找的 如果数据没有在数据库中是无法查找到了(每天晚上更新)
 例如 新建一个文件
 	touch abc
 使用 locate abc [如果数据库没有更新 可能是查不到的]
 #更新数据库
 sudo upatedb
 #在进行查找
 locate dd

```

```python
find [在目录中遍历查找 不是在数据库中]
	使用方法： 
    find   path   -option   [-print ]   [ -exec  -ok  command ]  {} \;

    ######  根据文件名查找：在指定路径下根据文件名查找 #######
    find / -name filename 再根目录里面搜索文件名为filename的文件
    find /home -name "*.txt"
    find /home -iname "*.txt"  # 忽略大小写


    ######  根据文件类型查找 在指定路径下根据文件类型查找 #######
    find path -type 类型参数
        f 普通文件
        l 符号连接 
        d 目录 
        c 字符设备 
        b 块设备 
        s 套接字 
        p Fifo


    ######  根据目录深度查找 #######
    find path -maxdepth 3 -type f  # 最大深度为3
    find path -mindepth 2 -type f  # 最小深度为2

    #########   根据文件的权限或者大小名字类型进行查找 ###########
    find path -type f -size (+|-)文件大小 # +表示大于 -表示小于 
        b —— 块（512字节） 
        c —— 字节 
        w —— 字（2字节） 
        k —— 千字节 
        M —— 兆字节 
        G —— 吉字节


    #########   按照时间查找  ############
    -atime（+|-）n  # 此选项代表查找出n天以前被读取过的文件。
    -mtime（+|-）n  # 此选项代表查找出n天以前文件内容发生改变的文件。
    -ctime（+|-）n  # 此选项代表查找出n天以前的文件的属性发生改变的文件。
    -newer file  # 此选项代表查找出所有比file新的文件。
    -newer file1 ! –newer file2  # 此选项代表查找比file1文件时间新但是没有file2时间新的文件。

    # 注意：   
    #  n为数字，如果前面没有+或者-号，代表的是查找出n天以前的，但是只是一天之内的范围内发生变化的文件。
    #  如果n前面有+号，则代表查找距离n天之前的发生变化的文件。如果是减号，则代表查找距离n天之内的所有发生变化的文件。
    #  -newer file1 ! –newer file2中的!是逻辑非运算符

    #########   按照用户/权限查找  ############
    -user 用户名：根据文件的属主名查找文件。
    -group 组名：根据文件的属组名查找文件。
    -uid n：根据文件属主的UID进行查找文件。
    -gid n：根据文件属组的GID进行查找文件。
    -nouser：查询文件属主在/etc/passwd文件中不存在的文件。
    -nogroup：查询文件属组在/etc/group文件中不存在的文件
    -perm 777： 查询权限为777的文件

    来自: http://man.linuxde.net/find

    ########  查找时指定多个条件   ############
    -o：逻辑或，两个条件只要满足一个即可。
    -a：逻辑与，两个条件必须同时满足。

    find  /etc -size +2M -a -size -10M

    #########  对查找结果进行处理  #############
    -exec  shell命令  {}  \;
    -ok  shell命令  {}  \;
    其中-exec就是代表要执行shell命令，后面加的是shell指令，再后面的“{}”表示的是要对前面查询到的结果进行查询，最后的“\；”表示命令结束。需要注意的是“{}”和“\”之间是要有空格的。而-ok选项与-exec的唯一区别就是它在执行shell命令的时候会事先进行询问，-print选项是将结果显示在标准输入上

find /home -name  “*.txt” -ok ls -l {} \;
find /home -name  “*.txt” -ok rm {} \;
```

