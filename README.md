## 说明

这是一个第三方的ReMan资源管理系统的本地执行程序

## 使用方法


```sh
./task_linux_amd64_v0.1.3 -h

使用方法：
Linux: ./go-reman-task --api https://www.reman.com --token xxx
Windows: go-reman-task.exe --api https://www.reman.com --token

代理：加上--proxy参数即可，如：--proxy http://127.0.0.1:10808

若有密码认证：--proxy http://username:password@127.0.0.1:10808

Usage:
  go-reman-task [flags]

Flags:
      --api string     ReMan 网站地址，如：https://www.reman.com
  -h, --help           help for go-reman-task
      --interval int   任务执行间隔时间，单位秒 (default 5)
      --proxy string   代理地址，支持格式：http://127.0.0.1:10808 或 socks5://127.0.0.1:10809
      --token string   ReMan 网站 token 请在后台设置中生成
```


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

当然，你使用 `pm2` 更没有问题，参考：

```sh
pm2 start "./task_linux_amd64_v0.1.3 --api https://xxxx.com --token xxxyyyzzz"

pm2 save # 这条命令第一次执行即可，后面不用
```

注意上面的命令中的"",这在pm2中是必须的。

### Windows

在release页面下载"windows"版本资源，解压后执行：

```bash
task_windows_amd64_v0.1.3.exe --api https://xxxx.com --token xxxyyyzzz
```

注意：不可直接复制上面的命令，以你解压后的文件名为准。


### 其它问题

如果你是放在和reman同一台服务器上的话，可以将 `--api https://xxxx.com` 换成 `--api http://127.0.0.1:4677` 这样不用经过网络，性能极高。

注意：reman的默认监听端口是4677，如果自行修改过的话，注意替换。
