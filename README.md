# HOME-Cleaner

清理家目录中的垃圾文件。

## 使用

1. `git clone --depth=1 git@github.com:kitty-panics/HOME-Cleaner.git`
2. `vim HOME-Cleaner/home-cleaner`，修改其中的 **SET_RULE_PATH** 设置项
3. 将 `home-cleaner` 放进 PATH
5. 需要清理垃圾文件时，执行 `home-cleaner` 命令即可

## F.A.Q

### 如何获取更多垃圾文件规则？

每个人对于垃圾文件的定义不同，有人需要详细的 Log 以便于后续定位 Bug，
也有人不喜欢 Log；有人需要 Cache，而又有人不喜欢 Cache。

所以就只包含了一些简单的示例规则。

### 如何判断一个文件是否为垃圾文件？

正如上一条所说，每个人对于垃圾文件的定义不同。

不过有个通用的规则来判断: 删除后不影响软件已有的数据同时又看不顺眼的文件。

### 如何编写 RF 和 RD 规则？

RF 和 RD 规则都使用 find **默认** 的正则类型，当然你也可以更改成自己喜欢的，
编辑 `vim home-cleaner` 文件，修改其中的 **FRT** 设置项即可。
