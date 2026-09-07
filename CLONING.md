# CLONING

要贡献资源的话，首先 fork 本仓库，然后 clone 到本地。

特别注意这个仓库包含大量二进制文件，全量 clone 不合适，建议使用 sparse clone 结合过滤和浅 clone：

```bash
git clone --sparse --filter=blob:none --depth=1 <你fork的仓库地址>
```

这时候只有一个基本结构，因此如果你要修改某个特定目录的内容，使用 sparse-checkout 先检出这个目录。checkout 的时候粒度越细，拉取的不必要的东西越少：

```bash
git sparse-checkout <目录>
```

即使远端尚无你需要修改的目录，也可以先这么设置。

比如如果你要改 `B计算机操作系统/测试`

```bash
git sparse-checkout 'B计算机操作系统/测试'
```

然后添加或者修改。

要管理检出目录，使用

```bash
git sparse-checkout list
```

列出选择了的目录。

使用

```bash
git sparse-checkout add <目录>
```

追加目录。注意 set 会替换掉之前检出的目录。

最后

```bash
git add <更改了的文件>
# 或者直接 git add -A
git commit -m
git push origin <分支>
```

一条龙，开 PR 就行了。
