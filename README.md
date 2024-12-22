## 说明

这是一个第三方的ReMan资源管理系统的本地执行程序

## 使用方法

### Linux

在release页面下载"linux"版本资源，解压后执行：

```bash
./task_linux_amd64_v0.1.3 --api https://xxxx.com --token xxxyyyzzz
```

注意：不可直接复制上面的命令，以你解压后的文件名为准。

后台运行：

```bash
nohup ./task_linux_amd64_v0.1.3 --api https://xxxx.com --token xxxyyyzzz &
```

这里使用了`nohup`命令，可以在关闭终端后继续运行。注意最后的`&`符号，表示后台运行。

### Windows

在release页面下载"windows"版本资源，解压后执行：

```bash
task_windows_amd64_v0.1.3.exe --api https://xxxx.com --token xxxyyyzzz
```

注意：不可直接复制上面的命令，以你解压后的文件名为准。
