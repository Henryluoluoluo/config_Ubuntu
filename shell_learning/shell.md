#<center> shell语法

####脚本示例
```
#! /bin/bash
echo "hello world"
```
####运行方式
1. 
```
chmod +x xxx.sh
./xxx.sh
```
2. 
```
bash xxx.sh
```

###注释
```
    # 这是注释
    echo "hello world"
    :<<xx
    这是多行
    注释
    xx

```

###变量
```
name1='yxc'  # 单引号定义字符串
name2="yxc"  # 双引号定义字符串
name3=yxc    # 也可以不加引号，同样表示字符串
echo ${name1}   #输出变量
delare -r name1  #定义只读变量
unset name1 #删除变量
```
**自定义变量**:*子进程不能访问*
**环境变量**:*子进程可以访问的变量*
```
declare -x name #自定义变量变成全局变量
declare +x name #全局变量变成自定义变量
```
**字符串**
*单引号不会转义，双引号会*
```
name=yxc  # 不用引号
echo 'hello, $name \"hh\"'  # 单引号字符串，输出 hello, $name \"hh\"
echo "hello, $name \"hh\""  # 双引号字符串，输出 hello, yxc "hh"
```
*获取字符串长度*
```
name = 'lh'
echo ${#name} #输出2
```
提取字串
```
name = lh
echo ${name:0:1}  #提取从0开始的一个字符
```

### 默认变量
```
#! /bin/bash

echo "文件名："$0
echo "第一个参数："$1
echo "第二个参数："$2
echo "第三个参数："$3
echo "第四个参数："$4
```

| 参数  | 说明                                                |
| ----- | --------------------------------------------------- |
| `$#`  | 参数个数                                            |
| `$*`  | `"$1 $2 $3 $4"`                                     |
| `$@`  | `"$1" "$2" "$3" "$4"`                               |
| `$$`  | 当前进程的ID                                        |
| `$？` | 上一条命令的退出状态。0表示正常退出，其他值表示错误 |

### 数组

1. `array=(1 abc "def" yxc)`

2. ```
    array[0]=1
    array[1]=abc
    array[2]="def"
    array[3]=yxc
   ```
**数组输出**
`echo ${array[0]}`

**读取整个数组**
`echo ${array[*]}`

**数组长度**
`echo ${#array[*]}`

### expr命令

**字符串处理**
```
str="hello world"
echo `expr length "$str"`  # ``不是单引号，表示执行该命令，输出12
echo `expr index "$str" aWd`  # 输出7，下标从1开始
echo `expr substr "$str" 2 3`  # 输出 ell
```

**运算**
```
a=3
b=4

echo `expr $a + $b`  # 输出7
echo `expr $a - $b`  # 输出-1
echo `expr $a \* $b`  # 输出12，*需要转义
echo `expr $a / $b`  # 输出0，整除
echo `expr $a % $b` # 输出3
echo `expr \( $a + 1 \) \* \( $b + 1 \)`  # 输出20，值为(a + 1) * (b + 1)
```

**逻辑关系表达式**
```
a=3
b=4

echo `expr $a \> $b`  # 输出0，>需要转义
echo `expr $a '<' $b`  # 输出1，也可以将特殊字符用引号引起来
echo `expr $a '>=' $b`  # 输出0
echo `expr $a \<\= $b`  # 输出1

c=0
d=5

echo `expr $c \& $d`  # 输出0
echo `expr $a \& $b`  # 输出3
echo `expr $c \| $d`  # 输出5
echo `expr $a \| $b`  # 输出3
```

### read 命令
`read -p "Please input your name: " -t 30 name` 
> -p:后面加提示
> -t 后面加等待时间

### echo命令
**换行**
`echo -e "hi\n" #换行`
`echo -e "hi\c" #不换行`

**显示结果定向到文件**
`echo "hello world" > output.txt`

显示命令执行的结果
```
echo `date`
```

### printf
```
printf "%10d.\n" 123  # 占10位，右对齐
printf "%-10.2f.\n" 123.123321  # 占10位，保留2位小数，左对齐
printf "My name is %s\n" "yxc"  # 格式化输出字符串
printf "%d * %d = %d\n"  2 3 `expr 2 \* 3` # 表达式的值作为参数
```

### test & []
> 用来判断文件是否存在或者变量比较

示例
```
test 2 -lt 3  # 为真，返回值为0
echo $?  
```
判断文件是否存在
```
test -e test.sh && echo "exist" || echo "Not exist"
```
**文件类型判断**
| 参数 | 代表意义     |
| ---- | ------------ |
| -e   | 文件是否存在 |
| -f   | 是否为文件夹 |
| -d   | 是否为目录   |

**文件权限判断**
| 参数 | 代表意义   |
| ---- | ---------- |
| -r   | 是否可读   |
| -w   | 是否可写   |
| -x   | 是否可执行 |
| -s   | 是否为空   |

**整数间的比较**
`test $a -eq $b  # a是否等于b`
| 参数 | 代表意义   |
| ---- | ---------- |
| -lt  | a是否小于b |
| -gt  | a是否大于b |
| ...  | ....       |


**多重条件判断**
`test $a -eq $b -a -x filename`
| 参数 | 代表意义 |
| ---- | -------- |
| -a   | and      |
| -o   | or       |
| !    | not      |


用法类似
`[ -e test.sh ] && echo "exist" || echo "Not exist"`
```
[ $name == "acwing yxc" ]  # 错误，等价于 [ acwing yxc == "acwing yxc" ]，参数太多
[ "$name" == "acwing yxc" ]  # 正确
```


### 判断语句

**单层if**
```
if condition
then
    语句1
    语句2
    ...
fi
```
示例:
```
a=3
b=4

if [ "$a" -lt "$b" ] && [ "$a" -gt 2 ]
then
    echo ${a}在范围内
fi
```

**单层if-else**
```
if condition
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
示例:
```
a=3
b=4

if ! [ "$a" -lt "$b" ]
then
    echo ${a}不小于${b}
else
    echo ${a}小于${b}
fi
```

多层if-elif-elif-else
```
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
elif condition
then
    语句1
    语句2
else
    语句1
    语句2
    ...
fi
```
示例:
```
a=4

if [ $a -eq 1 ]
then
    echo ${a}等于1
elif [ $a -eq 2 ]
then
    echo ${a}等于2
elif [ $a -eq 3 ]
then
    echo ${a}等于3
else
    echo 其他
fi
```

### 循环语句

**for...in...do...done**

示例1
```
for i in a 2 cc
do
    echo $i
done
```
示例2，输出文件名
```
for file in `ls`
do
    echo $file
done
```
示例3，输出1-10
```
for i in ${1..10}
do
    echo $i
done
```
示例4，输出a-z
```
for i in ${a..z}
do
    echo $i
done
```
示例5,C语言格式
```
for((i=1;i<=10;i++))
do
    echo $i
done
```

**while...do...done**
```
while read name
do
    echo $name
done
```
**until...do...done**
当条件为真时返回
```
until [ "${word}" == "yes" ] || [ "${word}" == "YES" ]
do
    read -p "Please input yes/YES to stop this program: " word
done
```
###函数
```
#! /bin/bash

func() {
    name=henry
    echo "hello $name"
    return 1
}                                                                                                                                                           
output=$(func)
ret=$?
echo "output = $output"
echo "return = $ret"
```
> 输出:output = hello henry
       return = 1


**函数内的局部变量**
`local 变量名=变量值`
> return 和exit的区别
> return 结束函数，exit结束整个shell脚本

### 文件重定向
```
echo -e "Hello \c" > output.txt  # 将stdout重定向到output.txt中
echo "World" >> output.txt  # 将字符串追加到output.txt中

read str < output.txt  # 从output.txt中读取字符串

echo $str  # 输出结果：Hello World
```
**bash脚本**
```
#! /bin/bash

read a
read b

echo $(expr "$a" + "$b")
```
**input.txt**
```
3
4
```
**执行命令**
`./test.sh < input.txt > output.txt`

### 引入外部文件
`source filename`