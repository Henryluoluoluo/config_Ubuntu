#<center> shell常用命令

###基本命令
1. `ctrl + c`:取消命令，且换行
2. `ctrl + u`:清空本行命令
3. `tab`:补全
4. `ls`:
5. `pwd`:
6. `cd xx`:
7. `cp xx yy`:
8. `mv xx yy`:
9. `mkdir xx`:
10. `touch xx`:
11. `cat xx`:
12. `rm [-r]`:
13. `history`:查看历史命令,保存在~/.bash_history

###系统状况
1. `top`:查看所有进程的信息
    * 输入M：按使用内存排序
    * 输入P：按使用CPU排序
    * 输入q：退出
2. `df -h`:查看硬盘使用情况
3. `free -h`:内存使用情况
4. `du -sh`:查看当前目录的硬盘空间
5. `ps aux`:查看所有进程
6. `kill -9 pid`:杀死编号为pid的进程
    * 传递某个具体的信号：`kill -s SIGTERM pid`
7. `netstat -nt`:查看所有网络连接
8. `w`:列出当前登录的用户
9. `ping www.baidu.com`：检查是否连网

###文件权限
1.`chmod`:修改文件权限
* `chmod +x xxx`
* `chmod -x xxx`
* `chmod 777 xxx`
* `chmod 777 xxx -R`:递归修改整个文件夹权限
  
###文件检索
1. `find path -name '*.py'`:搜索路径下的文件
2. `grep xxx`:从stdin中读入若干行输出有xxx的行
3. `wc`:统计行数，单词数，字节数
   * 可以在*stdin*中直接读入内容，也可以在*命令行参数*中传入文件名列表
   * `wc -l`:统计行数
   * `wc -w`:统计单词数
   * `wc -c`:统计字节数
4. `tree`:显示文件目录结构
   * `tree -a`:可显示隐藏文件
5. `ag xxx`:当前目录下检索xxx字符串
6. `cut`:分割一行内容
   * 从stdin中读入多行数据
   * `echo $PATH | cut -d ':' -f 3,5` :输出分割后第3、5列数据
   * `echo $PATH | cut -d ':' -f 3-5` :输出分割后第3~5列数据
   * `echo $PATH | cut -c 3,5`:输出PATH的第3、5个字符
   *  `echo $PATH | cut -c 3-5`:输出PATH的第3~5个字
7. `sort`:将每行内容按字典序排序
   * 可以从*stdin*中读取多行数据
   * 可以从命令行参数中读取文件名列表


###查看文件内容
1. `head -3 xxx`:展示xxx的前三行内容
2. `tail -3 xxx`:展示xxx的后三行内容

###管道
 会忽略stderr
> 1. `find . -name '*.py' | xargs cat | wc -l` 
* 统计当前文件中python文件的行数
  * find . -name '*.py'用来查找文件，作为cat参数
   然后用wc来统计行数

###工具
1. `md5sum`:计算md5哈希值
   * 可以从*stdin*读入内容
   * 也可以在命令行参数中传入文件名列表
2. `time command`:统计command命令执行时间
3. `watch -n  0.1 command` :每0.1秒执行一次command指令
4. `diff xxx yyy`:查找文件xxx与yyy的不同点
5. `tar`:压缩文件
   * `tar -zcvf xxx.tar.gz /path/to/file/*` :压缩
   * `tar -zxvf xxx.tar.gz`:解压缩