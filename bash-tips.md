#### echo

echo a;echo b
a
b
echo -n a;echo b
ab
echo "hello\nworld"
hello\nworld

echo -e "hello\nworld"
hello
world
-e 参数 解释特殊字符

#### bash 扩展

bash 扩展有以下几种形式:
?扩展 \*扩展 []扩展,{}扩展
echo {2,4,6,8,10}
2,4,6,8,10
echo {a,e,i,o,u}.txt
a.txt b.txt c.txt d.txt e.txt

#### pacman 备份和恢复已安装软件包

定期备份软件包是个好习惯。万一系统出了大问题，需要重装，就可以利用备份的软件包恢复到原先的系统。

1. 生成系统上安装的非本地（即从官方仓库获取的）软件包列表：

```
$ comm -23 <(pacman -Qeq|sort) <(pacman -Qmq|sort) > pkglist
```

2. 把生成的 pkglist 存储在一个安全的地方，比如 U 盘，或者 gist.github.com、evernote、dropbox 之类的文本储存网站。

今后重装系统时，把 pkglist 复制到新系统。

3. 使用如下命令安装所有软件包：

```
pacman -S $(< pkglist)
```

#### shell 脚本中 echo 显示内容带颜色

shell 脚本中 echo 显示内容带颜色显示,echo 显示带颜色，需要使用参数-e  
格式如下：

`echo -e "\033[字背景颜色；文字颜色m字符串\033[0m" `

例如：

> echo -e "\033[41;36m something here \033[0m"

#### 显示当前正在运行的 shell 类型

```
echo $0
```

#### sed tips

```
sed -i 's/111/aaa' example.txt
sed -n '/111/,+6 p' example.txt
```

删除空白行

```
sed '/^$/d' example.txt
```

用制表符代替空格

```
$ sed -r 's/ +/\t/g' file.txt
```

#### bash 批量重命名

假如我们现在有一堆 .txt 文件，我们想将它们的后缀改成 .cpp。先来看完整的代码：

```bash
#!/bin/bash
for name in $(ls *.txt)
do
    mv $name ${name%.txt}.cpp
done
```

#### echo ssid connected

```
iwctl station wlan0 show | grep -i network | sed 's/Connected network/SSID:/'
```

#### 逐行读取的区别(shell)

说明：
假定有个名为 file 的文本文件.

```
$ cat file
aaaa
bbbb
cccc dddd
```

```
$ cat file | while read line; do echo $line; done
aaaa
bbbb
cccc dddd
```

```
for line in $(<file); do echo $line; done
aaaa
bbbb
cccc
dddd
```

for 以空格作为分割符，while 以换行作为分割符.

#### xargs usage

在 linux 中许多命令只能支持直接在命令后输入参数，只有少部分命令支持从 stdin 作为参数，而这时候 xargs 命令就派上用场了.  
_xargs 命令最重要的作用就是将标准输入作为 linux 命令的输入_

_interactive find:_

```
xargs -L 1 find -name
```

上面命令指定了每一行（-L 1）作为命令行参数，分别运行一次命令（find -name）。
xargs -n 2 find -name
上面命令指定了每一项（-n 2）作为命令行参数(默认以空格分割)，分别运行一次命令（find -name）。

```
cat test.txt | xargs -I line sh -c 'echo line;mkdir line'
```

解释:从文件读取每一行，xargs 转换为 sh 命令的参数，执行一次 echo 和一次 mkdir.

```
echo "banana:apple:orange" | xargs -d: -n1
banana
apple
orange
```

#### Install packages from a text file

```
pacman -S $(cat /tmp/pack1.txt)
```

```
cat /tmp/pack1.txt | xargs pacman -S
```

#### 给 file 的所有行添加引号

```
sed "s/.\*/'&'" file.txt
```

#### wget from file

```
cat url-list.txt | xargs wget -c
```

#### bash 条件判断

**文件判断:** </br>
-e file: file 存在 </br>
-d file: file 是一个目录 </br>
-f file: file 是一个普通文件（regular file） </br>
-s file: file 非空（大小不为零） </br>
-w file: file 是否有可写标志 </br>
-x file: file 是否有可执行标志 </br>

**字符串判断**

主要包括字符串长度判断，和字符串判等两类：

> -n string: 字符串长度非零 </br>
> -z string: 字符串长度为零 </br>
> string1 = string2: 字符串相等 </br>
> string1 != string2: 字符串不相等 </br>
> string: 字符串不是 null 时为真，否则为 假 </br>

**number:**

> num1 -eq num2: equal </br>
> num1 -ne num2: not equal </br>
> num1 -le num2: <= </br>
> num1 -lt num2: < </br>
> num1 -ge num2: >= </br>
> num1 -gt num2: > </br>

**[[ 条件表达式**

> 可以把 [[expression]] 看做是 [ 的现代版本，它与 test 命令有几乎一样的参数。 **但它是一个新的语法结构，不再是一个普通的 test 命令**,因此不受制与 Shell 的 参数展开，比如 不需要用引号包裹所有变量，也支持类似 &&，|| 这样的逻辑操作而不需要用类似 -a，-o 这样的参数。 例如：

```
if [[ $string1 == 'harttle' ]]; then
    echo The author for this article is harttle
fi
```

#### bash 大小写转换

```
echo "Hello There" | tr [:lower:] [:upper:]
echo "Hello There" | awk '{print tolower($0)}'
echo "Hello There" | sed 's/[a-z]/\U&/g'
```

这三条命令的输出是一样的:  
output:  
HELLO THERE

使用 python 改变首字母的大小写:

echo -n "design & engineering" | python3 -c

"import sys; print(sys.stdin.read().title())"
Design & Engineering

#### 引用

关于引用的黄金规则其实很简单：

"如果你的参数中有空格或符号，那么你 必须 引用它。  
如果没有，引用则是可选的，但是安全起见，还是最好引用它。"

** 要求 无引用的参数 极其罕见，主要是在 [[ 测试中以及 ${..+..} 扩展周围。  
其他任何情况下，都不要试图通过移除或省略参数中的引用来使代码工作；如果这样做，你更可能引发严重且难以发现的 bug **

#### 条件测试

[[ 是个 shell 命令
type -a [
type -a [[
也就是说,[[不能直接接命令或是参数,[[和参数之间需要以空格分割.

```
$ [[ Jack = Jane ]] && echo "Jack is Jane" || echo "Jack is not Jane"
Jack is not Jane
$ [[Jack = Jane ]] && echo "Jack is Jane" || echo "Jack is not Jane"
-bash: [[Jack: command not found
$ [[ Jack=Jane ]] && echo "Jack is Jane" || echo "Jack is not Jane"
Jack is Jane
```

上面的三个命令中只有第一个出现了我们预期的结果.所以第一种写法是正确的.
第三条命令的错误可能更隐蔽。当我们有 bug 的代码导致的不是 bash 解析器错误，而只是表现怪异时，这种情况总是惊人的。这类 bug 既难以发现，也难以理解。在我们的例子中，[[命令的第一个参数是一个单独的字符串 Jack=Jane。不幸的是，使用 [[ 命令执行相等测试的语法是 [[ arg = arg]]，由此 bash 才会比较两个独立的字符串参数是否相等。第三个例子中，在 [[命令之后，我们并没有三个参数：有的只是一个长参数。错误结果的产生是因为 [[ 命令有一个测试某一字符串是否为空的简易语法：[[ string]]。

#### 关于子进程

直接指令下达 或者是利用 bash（sh）来运行脚本时，都会使用一个新的 bash 环境来执行脚本的指令。
也就是说这种方式执行是在子程序的 bash 内执行的。
当子程序完成后，子程序内的各项变量或动作将会结束儿不会传回到父程序中。

#### awk tips

A versatile programming language for working on files.
More information: https://github.com/onetrueawk/awk.

- Print the fifth column (a.k.a. field) in a space-separated file:
  awk '{print $5}' filename

- Print the second column of the lines containing "foo" in a space-separated file:
  awk '/foo/ {print $2}' filename

- Print the last column of each line in a file, using a comma (instead of space) as a field separator:
  awk -F ',' '{print $NF}' filename

- Sum the values in the first column of a file and print the total:
  awk '{s+=$1} END {print s}' filename

- Print every third line starting from the first line:(line 1,4,7,10.....)
  awk 'NR%3==1' filename

- Print different values based on conditions:
  awk '{if ($1 == "foo") print "Exact match foo"; else if ($1 ~ "bar") print "Partial match bar"; else print "Baz"}' filename

- Print all lines where the 10th column value equals the specified value :
  awk '($10 == value)'

- Print all the lines which the 10th column value is between a min and a max :
  awk '($10 >= min_value && $10 <= max_value)'
