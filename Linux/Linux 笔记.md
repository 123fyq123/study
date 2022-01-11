# Linux 笔记

## <mark>1 常用文件管理命令</mark>

## <mark>1.1 常用命令介绍</mark>

**取消命令：`Ctrl + c`**

**补全：`Tab`**

**显示当前路径：`pwd`**

**进入XXX/上层目录：`cd XXX/cd ..`**

**列出当前目录下所有文件：`ls`**

**创建目录XXX：`mkdir XXX`**

**创建文件XXX：`touch XXX`**

**删除普通文件/文件夹：`rm XXX/rm XXX -r`**

**将XXX文件移动到YYY：`mv XXX YYY`**

**将XXX文件复制成YYY：`cp XXX YYY`**

**显示文件XXX内容：`cat XXX`**

**复制文本：`Ctrl + insert`**

**粘贴文本：`Shift + insert`**

## <mark>2 Tmux和Vim</mark>

### <mark>2.1 tmux结构</mark>

#### tmux->session0,1..->window0,1...->pane0,1...

### <mark>2.2 tmux常用指令</mark>

**新建session：`tmux`**

**打开之前的tmux：`tmux a`**

**左右分成两个pane：`ctrl+a后+%`**

**上下分成两个pane：`ctrl+a后+“`**

**退出Tmux：`ctrl+a后+d`**

**放大/取消某个pane：`ctrl+a后+z`**

**查看所有的session：`ctrl+a 后+s`**

**关闭当前pane：`ctrl+d`**

**在tmux中选中文本时，需要按住`shift`键(Linux和Windows系统可以，Mac不可)**

### <mark>2.3 Vim概念</mark>

**vim是命令行模式下的文本编辑器**

### <mark>2.4 Vim常用指令</mark>

#### vim 有三种模式：一般命令模式/编辑模式/命令行模式

**打开文件：`vim filename`**

**进入一般命令模式：`Esc`**

**进入编辑模式：`i`**

**进入命令行模式：一般命令模式下按`/`或`？`或`:`**

### <mark>2.5 Vim移动</mark>

**向右移动n个字符：`n<space>`**

**移动至本行开头：`0或[Home]`**

**移动至本行末尾：`$或[End]`**

**移动至最后一行：`G`**

**移动至第n行：`nG或:n`**

**移动至第一行：`gg`**

### <mark>2.6 Vim查找</mark>

**查找光标下第一个值位word的字符串：`/word`**

**查找光标上第一个值位word的字符串：`?word`**

**反复前一个查找操作：`n`**

**在n1行和n2行之间查找word1这个字符串，并将其替换为word2:**

**`:n1,n2s/word1/word2/g`**

**将全文的word1替换为word2：**

**`:1,$s/word1/word2/g`**

**将全文的word1替换位word2并需用户确认：**

**`:1,$s/word1/word2/gc`**

### <mark>2.7 Vim复制/粘贴</mark>

**选中文本：`v`**

**删除文本/当前行：`d/dd`**

**复制文本/当前行：`y/yy`**

**复制数据在光标下一行：`p`**

**撤销/取消撤销：`u/Ctrl + r`**

**设置/取消为粘贴模式，取消代码自动缩进：**

**`:set paste/:set nopaste`**

### <mark>2.8 Vim结束命令</mark>

**保存：`w`**

**强制保存：`!w`**

**退出：`q`**

**强制退出：`!q`**

**保存并退出：`wq`**

## <mark>3 Shell</mark>

### <mark>3.1 概论+运行</mark>

**shell是我们通过命令行与操作系统沟通的语言。Linux中常见的shell脚本有很多种。Linux系统中一般默认使用bash，所以接下来讲解bash中的语法。文件开头需要写`#! /bin/bash`，指明bash为脚本解释器。**

**使XXX脚本具有可执行权限：`chmod +x XXX`**

**当前路径下执行脚本XXX：`./XXX`**

**绝对路径下执行脚本XXX：例：`/home/acs/XXX`**

**家目录下执行脚本XXX：`~/XXX`**

### <mark>3.2 注释</mark>

**单行注释：`#+内容`**

**多行注释：**

`:<<EOF`

`第一行注释`

`第二行注释`

`EOF`

### <mark>3.3 变量</mark>

**分为局部变量和全局变量**

#### <mark>3.3.1 定义变量</mark>

`name1 = 'fyq' #单引号字符串`

`name2 = "fyq" #双引号定义字符串`

`name3 = fyq   #不加引号`

#### <mark>3.3.2 使用变量</mark>

**一般加上`${}`**

` echo ${name1}nb #输出fynb`

#### <mark>3.3.3 删除变量</mark>

**`unset`删除变量**

`unset name1`

#### <mark>3.3.4 字符串</mark>

**获取字符串长度：`echo ${#name1}$`**

**提取字串：`echo ${name1:0:5}`提取name1从0开始的5个字符**

#### <mark>3.3.5 默认变量</mark>

**例：当在当前目录下执行脚本XXX时 `./XXX 1 2 3 4`**

**第1,2,3...个参数：`$1 $2 $3...`**

**文件名XXX：`$0`**

**传入参数个数：`$#`**

**用空格隔开的所有参数：`$*`**

**上一条命令的退出状态：`$?`**

**command命令的stdout：`$(command)`**

### <mark>3.4 数组</mark>

**下标从0开始**

**定义数组：`array = (1 abc "def" fyq)`**

**读取数组某个元素值：`${array[index]}`**

**读取整个数组：`${array[*]}`**

**获取数组长度：`${#array[*]}`**

### <mark>3.5 expr命令</mark>

**expr的stdout：1为真，0为假**

**expr的exit code：0为真，1为假**

#### <mark>3.5.1 字符串表达式</mark>

**字符串长度：``expr length "${str}"` #(注意`不是单引号)`**

#### <mark>3.5.2 整数表达式</mark>

**加减乘除：``expr $a + $b` #不是单引号`**

### <mark>3.6 read命令</mark>

**read用于从标准输入中读取单行数据**

**后面接提示信息：`-p`**

**后面接等待时间：`-t`**

**例：**

`read name`

`read -p "please input your name" -t 30 name`

### <mark>3.7 echo命令</mark>

#### <mark>3.7.1 显示普通字符串</mark>

`echo "Hello World"`

#### <mark>3.7.2 显示转义字符</mark>

`echo "\"Hello World\""`**若为单引号则不转义**

#### <mark>3.7.3 显示变量</mark>

`echo “My name is ${name}”`

#### <mark>3.7.4 显示换行/不换行</mark>

`-e开启转义`

`echo -e "Hi\n"`

`echo "fyq"`

**输出为**

`Hi`

`  `

`fyq`

`echo -e "Hi \c"`

`echo 'fyq'`

**输出为**

`Hi fyq`

#### <mark>3.7.5 显示结果定向至文件XXX.txt</mark>

`echo "Hello World" > XXX.txt`

### <mark>3.8 printf命令</mark>

**类似C/C++中的printf**

**例**

`printf "%10d.\n" 123 #占10位，右对齐`

`printf "-10.2f.\n" 123.123321 #占10位，输出两位小数，左对齐`

### <mark>3.9 test命令与[]判断符</mark>

**test 返回exit code，0表示真**

#### <mark>3.9.1 判断文件类型</mark>

**文件是否存在：`-e`**

**是否为文件：`-f`**

**是否为目录：`-d`**

**文件是否可读/可写/可执行/非空：`-r`/`-w`/`-x`/`-s`**

#### <mark>3.9.2 整数间比较</mark>

**a是否等于/不等于b：`-eq`/`-ne`**

**a是否大于b：`-gt`**

**a是否小于b：`-lt`**

**a是否大于等于b：`-ge`**

**a是否小于等于b：`-le`**

#### <mark>3.9.3 []判断符</mark>

**[]判断符主要用于if语句，返回exit code**

**注意:[]内的每一项都要用空格隔开，每个变量或常量用双引号括起来**

**例：**

```
[ 2 -lt 3 ]

echo $? #返回上个命令的返回值0
```

### <mark>3.10 判断语句</mark>

**if...then语句格式**

```bash
if condition
then 
    语句1
    语句2
    ...
elif condition
then
    语句1
    语句2
    ...
else
    语句1
    语句2
    ...
fi
```

### <mark>3.11 文件重定向</mark>

**将stdout/stdin重定向到file中：`command > file`/`command < file`**

**将stdout/stdin追加到file中：`command >> file`/`command << file`**

**例：**

**输入输出重定向：**

```bash
echo XXX > XXX.txt
echo XXX >> XXX.txt

read XXX < XXX.txt
```

**同时重定向stdin和stdout**

```bash
read a
read b

echo $(expr "$a" + "$b")
```

**执行命令**

```bash
chmod +x test.sh
./test.sh < input.txt > output.txt
```

**则input.txt中为**

```
3
4
```

**output.txt为**

```
7
```

### <mark>3.12 引入外部脚本</mark>

```bash
source filename
```

## <mark>4 SSH</mark>

### <mark>4.1 ssh登录</mark>

#### <mark>4.1.1 基本用法</mark>

**远程登录服务器：`ssh user@hosthome`**

**其中：`user`指用户名  `hostname`指ip地址或域名**

**首次登录一直回车后会将信息记录在`~/.ssh/known_hosts`中**

**输入密码即可登录远程服务器**

#### <mark>4.1.2 配置文件(使用别名登录服务器)</mark>

**首先创建文件`~/.ssh/config`**

**输入**

```vim
Host myserver1
    HostName IP
    User 用户名

Host myserver2
    HostName IP
    User 用户名
```

#### <mark>4.1.3 密钥登录</mark>

**创建密钥：`ssh-keygen`**

**结束后，`~/.ssh/`目录下会多两个文件**

`id_rsa`**：私钥**

`id_rsa.pub`**：公钥**

**若向免密登录myserver服务器，将公钥中的内容复制到`~/.ssh/authorized_keys`**

**也可以直接使用命令`ssh-copy-id myserver`**

### <mark>4.2 scp传文件</mark>

#### <mark>4.2.1 基本用法</mark>

**将`source`路径下的文件复制到destina中：**`scp source destination`

**复制文件夹：加上`-r`** 

**例：**

**<mark>4.2.1.1 本地复制到myserver</mark>**

`scp -r ~/tmp myserver:/home/acs/` **：将本地家目录的`tmp`文件夹复制到`myserver`的`/home/acs/`目录下**

**<mark>4.2.1.2 myserver复制到本地</mark>**

**`scp -r myserver:homework`：将myserver的homework文件夹复制到本地**

#### <mark>4.2.2 使用scp配置其他服务器的vim和tmux</mark>

`scp ~/.vimrc ~/.tmux.conf myserver:`

## <mark>5 Git</mark>

## 5.1 结构

**工作区：仓库的目录**

**暂存区：工作区完成后放入版本库的缓存区**

**版本库：存放所有提交到本地仓库的代码版本**



## <mark>5.2 常用命令</mark>

**将当前目录配置成git仓库：`git init`**

**将\*添加至暂存区：`git add *`  （全部为git  add  .）**

**将暂存区提交到当前分支：`git commit -m “自己定的备注”`**

**查看仓库状态：`git status`**

**回滚版本**

`git reset --hard  HEAD^`**(一个^指回滚1次)**

`git reset --hard 版本号`**（版本号可由git reflog或git log得到）**  

**将本地仓库关联到远程仓库：**`git  remote  add  origin  git@域名`

**将当前分支推送到远程仓库：`git push -u`（第一次需要-u，以后不需要）**

**将远程仓库的当前分支与本地当前分支合并：`git pull`**

**将branch__name分支合并到当前分支：`git merge branch_name`**

**查看分支：`git branch`**

**创建并切换到branch_name分支：`git checkout -b branch_name`**

**将远程仓库下载到当前目录：`git clone git@域名`**



## <mark>6 thrift</mark>

**注：client为客户端，server为服务端**

**实现match的server端以及client端，由于save的server端已有现成，只需实现save的client端**

**<mark>第一步</mark>：新建thrift文件夹用于存储接口，定义接口 *.thrift 文件**

**<mark>第二步</mark>：新建match__system文件夹用于存match的client端，新建src原文件夹，去thrift官网复制直接生成match的server端的代码，原始名字为gen-cpp，改名为match_server**

```
thrift -r --gen cpp   第一步*.thrift的路径
```

**<mark>第三步</mark>：在生成的文件中找出主函数并单独修改，编译并链接**

**编译**：`g++ -c *.cpp`                     

**链接**：`g++ *.o -o (生成的可执行文件名，如main) -lthrift` 

**<mark>第四步</mark>：生成game文件夹用于存match的server端和save的client端，新建src文件夹，去thrift官网复制直接生成match的client端的代码，用python实现，原始名字为gen-py，改名为match_client**

```
thrift -r --gen py 第一步*.thrift的路径
```

**<mark>第五步</mark>：在thrift官网复制client端的代码，进行修改**

**python 从标准输入中读取数据**：

`from sys import stdin`

`for line in stdin:`

`    op, user_id, username, score = line.split(' ')`

`    operator(op, int(user_id), username, int(score))` 

**<mark>第六步</mark>：修改match_server端，获得版本1.0，其中**

**<mark>主要内容：</mark>**

**1.Task（User，Type）**

**2.消费队列：**`Message_queue(queue<User> , mutex, condition_variable)`

**3.用户池：**`pool(public:add(),remove(),match(),save_result()   private:vector<User>)`

**4.消费任务：consume_task()函数**

**<mark>新概念：</mark>**

**生产者-消费者模型：生产者和消费者用消费队列维护**

**注：客户端为消费者？consume_task为消费者和生产者共同需完成的消费任务？依靠消费队列来维护？**

**引入锁的概念，线程在未得到锁时会被阻塞住**

**条件变量condition_variable的使用**

**建立单线程代码：** `thread matching_thread(consume_task)`

**锁住代码：** `unique_lock<mutex> lck(message_queue.m)`

**解锁代码：** `lck.unlock()`

**条件变量线程沉寂代码：** `message_queue.cv.wait(lck)`

**条件变量线程唤醒代码：** `message_queue.cv.notify_all()/notify_one()`

**若用到线程，链接代码为：**`g++ *.o -o main -lthrift -pthread`

**\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*至此最初match_server端实现**

**<mark>第七步</mark>：建立save.thrift存储端口，并直接生成save的client端**

```
thrift -r --gen cpp   第一步*.thrift的路径
```

**同之前操作改名为save_client，注意此时已有main函数，需删除其中server端的cpp文件**

**<mark>第八步</mark>：去thrift官网复制样例client端的代码，由于我们将数据存储在myserver服务器上，所以需将其中的localhost改为myserver的地址，并设置用户名以及密码的md5值**

**<mark>第九步</mark>：升级match函数，消费任务改为每隔1s都进行匹配一次，使用\<unistd.h\>的sleep()函数**

**<mark>第十步</mark>：将单线程改为多线程，在thrift官网的server处复制代码，主要复制main中的和factory工厂，修改Calculator和Share为Match，并添加头文件**
