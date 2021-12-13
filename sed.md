sed,stream editor,sed is an non-interactived editor
it's based on line.

### sed 命令的语法格式

sed [option] [sed-command] [input-file]

总的来说 sed 命令主要由四部分构成

    sed 关键字
    [option] 命令行选项，用于改变 sed 的工作流程。
    [sed-command] 是具体的 sed 命令
    [input-file] 输入数据，如果不指定，则默认从标准输入中读取。

sed 工作流程

如果你想成为一个 sed 专家，你必须知道 sed 的内部是如何工作的。

sed 的工作流程，说起来真的很简单：

读取行 -> 执行 -> 显示 -> 读取行 -> 执行 -> 显示 -> .... -> 读取行 -> 执行 -> 显示

```
cat sed-script
```

1d
2d

```
sed -i -f sed-script file.txt
```
