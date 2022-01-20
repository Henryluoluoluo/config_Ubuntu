#<center> SSH

##ssh登录  
`sh user@hostname`
* user:用户名
* hostname:IP地址或者域名
* 登录后服务器信息会保存在.ssh/known_hosts中

##配置文件
创建文件.ssh/config，在文件中输出:
```
Host servername
        HostName IP
        User username
        Port portid
```
##免密登录
创建密钥：
>ssh-keygen

将公钥复制到服务器的 *~/.ssh/authorized_keys*中
`ssh-copy-id servername`

##远程让服务器执行命令
`ssh servername command`

示例
```
# 单引号中的$i可以求值
# 双引号不可以求值
ssh myserver 'for ((i = 0; i < 10; i ++ )) do echo $i; done'
```

##scp传文件
命令格式
`scp [-r\-P 22] source destination`
示例
`scp ~/.vimrc ~/.tmux.conf myserver:`

