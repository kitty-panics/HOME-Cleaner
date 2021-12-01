# HOME-Cleaner

清理家目录中的垃圾文件。

## 使用

1. `git clone --depth=1 git@github.com:kitty-panics/HOME-Cleaner.git`
2. `vim HOME-Cleaner/home-cleaner`，修改其中的 **SET_RULE_PATH** 设置项
3. 将 `home-cleaner` 放进 PATH
5. 需要清理垃圾文件时，执行 `home-cleaner` 命令即可

## 分类

这里将垃圾文件分成三个大类，一类是 `文件`，一类是 `目录`，还有一类是 `记录`。

其中 `文件` 和 `目录` 这两类都能分成三种规则，分别是 `[SF]单个文件 / [SD]单个目录`、
`[RF]多个规律文件 / [RD]多个规律目录` 和 `[MF]需重建单个文件 / [MD]需重建单个目录`。

还有一类就是 `记录` 比如执行过的命令记录、打开过的文件记录，这一类下只有 `[SC]Shell 命令`
一种规则。至于为什么使用 Shell 命令，因为有些软件的历史记录是放在配置文件中 (比如 kchmviewer)，
删除后会影响软件的正常使用，而各个软件存放历史记录的方式又不同，完全没有规律可循，
所以就选择通过编写对应的 Shell 命令来删除。

## 规则

+ 文件
    + [SF] 单个文件 / Single File
    + [RF] 多个规律文件 / Rule File
    + [MF] 需重建单个文件 / Make File
+ 目录
    + [SD] 单个目录 / Single Dir
    + [RD] 多个规律目录 / Rule Dir
    + [MD] 需重建单个目录 / Make Dir
+ 记录
    + [SC] Shell 命令 / Shell Command

## F.A.Q

### 如何获取更多垃圾文件规则？

每个人对于垃圾文件的定义不同，有人需要详细的 Log 以便于后续定位 Bug，
也有人不喜欢 Log；有人需要 Cache，而又有人不喜欢 Cache。

所以就只包含了一些简单的示例规则。

### 如何判断一个文件是否为垃圾文件？

正如上一条所说，每个人对于垃圾文件的定义不同。

不过有个通用的规则来判断: 删除后不影响软件已有的数据同时又看不顺眼的文件。

### 如何编写 RF 和 RD 规则？

RF 和 RD 规则都使用 find **默认** 的正则类型，而 find 默认正则是 [Emacs 正则]，
唯一的区别是 emcas 中的 `.` 不匹配换行符，而 find 中的会匹配。

当然你也可以更改成自己喜欢的正则，编辑 `vim home-cleaner` 文件，修改其中的
**FRT** 设置项即可。

[Emacs 正则]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Regexps.html

### 为什么没有 "需重建多个文件/目录" 规则？

因为 "需重建单个文件/目录" 规则我都极少使用，更别说 "需重建多个文件/目录"，
所以就暂时不考滤加入此规则。

如果你需要此规则，可在 [Issues] 中告诉我，或者发起 [PR]。

[Issues]: https://github.com/kitty-panics/HOME-Cleaner/issues
[PR]: https://github.com/kitty-panics/HOME-Cleaner/pulls
