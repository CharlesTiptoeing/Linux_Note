## Linux Learning

这是我记录总结linux学习, C refer to command mode, E refer to the editor mode.

#### Vim

| | shortcode | Description | shortcode | Description | |
| - | :-: | - | :-: | - | - |
| C | a | 在光标后插入 | o | 在光标下插入新行 | C |
| E | set nu | 加行号 | gg | 光标移至第一行 | E |
| E | n | 输入n跳到第n行 | nx | 删除光标所在处后n个字符 | C |
| C | ndd | 删除光标所在行下面的n行 | :n1,n2d | 删除指定范围行 | E |


#### when writing an code
| | shortcode | Description | shortcode | Description | |
| - | :-: | - | :-: | - | - |
| C | ctrl + a | 光标移到命令行开头 | ctrl + e | 光标移到命令行尾 | C |
| E | ctrl + u | 剪切命令行 | ctrl + c | 强制停止命令 | E |
| E | n | 输入n跳到第n行 | nx | 删除光标所在处后n个字符 | C |
| C | ndd | 删除光标所在行下面的n行 | :n1,n2d | 删除指定范围行 | E |

#### cat
| | shortcode | Description | 
| - | :-: | - | 
| C | 命令 > 文件 | 把命令的输出保存到指定文件夹 | 
| E | 命令 >> 文件 | 以追加的方式把命令的输出保存到指定文件夹 | 
| E | 命令 &> 文件 | 以覆盖的方式把正确输出和错误输出到一个文件中去 |
| C | 命令 &>> 文件 | 以追加的方式把正确输出和错误输出到一个文件中去 | 

#### 多命令顺序执行
| shortcode | Description | 
| :-: | - | 
| order1 ; order2 | 多个命令循序执行 | 
| order1 && order2 | 当命令1顺利执行后，命令2才会执行 | 
| order1 “｜｜” order2 | 当命令1无法执行时，命令2才会执行，vice versa |
| \order | 将特殊符号的作用取消，直接输出字符 |


#### 位置参数变量
| shortcode | Description | 
| :-: | - | 
| $n | n为数字，$0代表命令本身，十以上为${10} ，和站位符有点像| 
| $(()) | 进行整数运算| 
| $* | 变量代表命令行的所有参数，将参数看为一个整体 |
| $@ | 变量代表命令行的所有参数，将参数分别对待 |

```markdown
#!/bin/bash
for i in "$*"
#$*中所有参数看作为一个整体，所以这个for循环只循环一次
   do
       echo "The parameter is:$i"
   done
x=1

for y in "$@"
   do
       echo "The parameter$x is $y"
       x=$(($x+1))
   done


```


#### 预定义变量
| shortcode | Description | 
| :-: | - | 
| $？ | 最后一次执行命令的返回状态，如果这个变量的值为0，证明上一条命令正常执行，vice versa | 
| $$ | 当前进行的进程号 | 
| $！ | 后台运行的最后一个进程的进程号 |
| $@ | 变量代表命令行的所有参数，将参数分别对待 |


#### read [选项][变量名]
| shortcode | Description | 
| :-: | - | 
| -p"提示信息" | 输入提醒信息 | 
| -t 秒数 | 指定等待时间 | 
| -n字符数 | read命令只接受指定的字符数 |
| -s | 变量代表命令行的所有参数，将参数分别对待 |

### Bash的运算符
$((运算式))    $(命令式)
#### declare声明变量符 declare [+/-][选项]变量名
| shortcode | Description | 
| :-: | - | 
| -： | 给变量设定类型属性 | 
| +： | 取消变量的类型属性 |
| -i: | 将变量声明为整数形 | 
| -x | 将变量声明为环境变量 |
| -p | 显示变量被声明的类型 |

#### source 配置文件 = .配置文件

#### printf '输出类型输出格式' 输出内容
输出类型 %m.nf 输出浮点数。m和n为数字，指输出的整数位和小数数位。

输出格式
| shortcode | Description | 
| :-: | - | 
| \n | 换行 | 
| \r | 回车键，Enter键 |
| \t | 退格键，Tab键 | 

#### sed将数据进行选取，替换，删除，新增
sed [选项]'[动作]' 文件名
选项
| shortcode | Description | 
| :-: | - | 
| -n | 只把sed处理过的命令输出到屏膜 | 
| -e | 应用多条sed命令编辑 |
| -i | 直接修改文件 | 

动作
| shortcode | Description | 
| :-: | - | 
| a\: | 追加 | 
| c\: | 行替换 |
| i\: | 插入 | 
| d: | 删除 | 
| p: | 打印 |
| s: | 字符替换，格式为“行范围s/旧字符/新字符/g” | 
example: sed -i '3s/74/99/g' test.file 第三行的74替换为99

#### sort [选项] 文件名
| shortcode | Description | 
| :-: | - | 
| -f: | 忽略大小写 | 
| -n: | 以数值型进行排序，默认为字符串型 |
| -r: | 反向排序 | 
| -t: | 指定分隔符，默认为制表符 | 
| -k n[,m] | 按照指定字符范围排序，从n字段开始到m字段结束 |

#### 按照文件类型进行判断
| shortcode | Description | 
| :-: | - | 
| -d 文件 | 判断文件是否存在，并且是否为目录文件 | 
| -e 文件 | 判断文件是否存在（存在为真） |
| -f 文件 | 判断文件是否存在，并且是否为普通文件 | 
两种判断格式：
1. test -e /root/install.log[文件目录]
2. [ -e /root/install.log ]

#### 多重条件判断
| shortcode | Description | 
| :-: | - | 
| 判断1 -a 判断2 | 逻辑与 | 
| 判断1 -o 判断2 | 逻辑或 |
| -v 判断 | 逻辑非，判断取反 |

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/CharlesTiptoeing/Linux_Note/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
