#<center>tmux

###operation
1. `tmux`:新建一个session
2. `tmux a`:打开最近挂起的session
3. `ctrl + a 、d`:挂起当前session
4. `ctrl + a 、%`:左边开启一个分屏
5. `ctrl + a 、"`:下面开一个分屏
6. `ctrl + d`:关闭当前窗口
7. `ctrl + a 、方向键`:转换窗口
8. `ctrl + a 、s`:选择窗口
9. `ctrl + a 、z`:放大窗口
10. `ctrl + a 、[`:复制
11. `ctrl + a 、[`:粘贴



#<center>vim

###operation
1. `i`:进入编辑模式
2. `esc`:进入一般命令模式
3. `n<space>`:光标移动到第n个字符后面
4. `0 或[home]`:光标移动到本行开头
5. `$或[end]`:光标移动到本行末尾
6. `G`:移动到最后一行
7. `nG 或:n`:移动到第n行
8. `gg`:移动到第一行
9. `n<enter>`:向后移动n行
10. `set nu\nonu`:行号
11. `/word`:向下寻找word
12. `?word`:向上寻找word
13. `n`:重复前一个查找操作
14. `N`:反向重复前一个查找操作
15. `:n1,n2s/word1/word2/g`:n1与n2之间的word1替换为word2
16. `:1,$s/word1/word2/gc`:n1与n2之间的word1替换为word2，加询问
17. `v`:选中文本
18. `d`:删除选中的文本
19. `y`:复制选中的文本
20. `dd`:删除本行
21. `yy`:复制本行
22. `p`:粘贴在下一行或者下一个位置
23. `u`:撤销
24. `ctrl + r`:取消撤销
25. `>`:向右缩进
26. `<`:向左缩进
27. `set paste`:粘贴模式
28. `set nopaste`:取消粘贴模式
29. `ggdG`:删除全文
30. `:noh`:取消高亮
31. `gg=G`:格式化全文