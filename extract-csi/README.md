# 解析 `.dat` 类型的数据包

## Matlab 配置

给系统（不是用户）环境变量中增加一个 `MW_MINGW64_LOC`， 其数值为 `mingw64` 的安装路径。 例如安装的路径是 `E:\mingw64`。

设置完成后打开 Matlab, 在 Matlab 的命令行中输入 `setenv('MW_MINGW64_LOC', 'E:\mingw64')`.

## 读取 csi 数据

进入 `Atheros-CSI-Tool-UserSpace-APP-master\matlab`， 将数据包 `data_20230420` 文件夹放进去。

编译 `read_csi.c` 文件得到后缀为 `mexw64` 的文件后就可以调用 `read_csi` 函数， 该函数会在 `read_log_file.m` 文件中被用到。

- 编译

```matlab
mex read_csi.c
```

- 读取

```matlab
read_log_file('data_20230420/1_noPerson/01_np.dat')
```

> 这个 `read_log_file` 读取 csi 部分作者进行了一个长度的判断， 不清楚什么意思， 需要自己去调整一下才能返回 csi 部分的数据。
>
> 官网连接：[Atheros CSI Tool](https://wands.sg/research/wifi/AtherosCSI/)
