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
## Header 2
### Header 3

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
