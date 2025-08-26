# ReMan资源管理系统 - 本地执行程序

## 📋 程序简介

这是 ReMan 资源管理系统的第三方本地执行程序，用于在本地环境中自动执行资源管理任务。

**请在右侧 Releases 中下载最新版本**

## 🚀 快速开始

### 1. 获取所需信息
- **API 地址**：你的 ReMan 网站地址（如：`https://your-site.reman.com`）
- **Token**：在 ReMan 后台设置中生成的访问令牌，路径：站点配置->其它配置->须隐藏配置

### 2. 查看帮助信息
```bash
./task_linux_amd64_v0.1.3 -h
```

## ⚙️ 参数说明

| 参数 | 说明 | 示例 |
|------|------|------|
| `--api` | ReMan 网站地址 | `https://www.reman.com` |
| `--token` | 访问令牌（必需） | 从后台设置中获取 |
| `--interval` | 任务执行间隔（秒） | 默认5秒 |
| `--proxy` | 代理设置（可选） | `http://127.0.0.1:10808` |

### 代理配置示例
```bash
# HTTP 代理
--proxy http://127.0.0.1:10808

# 带认证的代理
--proxy http://username:password@127.0.0.1:10808

# SOCKS5 代理
--proxy socks5://127.0.0.1:10809
```

## 💻 安装与运行

### Linux 系统

#### 前台运行
```bash
./task_linux_amd64_v0.1.3 --api https://your-site.com --token your_token_here
```

#### 后台运行
```bash
# 使用 nohup 后台运行
nohup ./task_linux_amd64_v0.1.3 --api https://your-site.com --token your_token_here &

# 使用 PM2 管理（推荐）
pm2 start "./task_linux_amd64_v0.1.3 --api https://your-site.com --token your_token_here" --name "reman-task"
pm2 save  # 保存配置（首次运行时执行）
pm2 startup  # 设置开机自启
```

### Windows 系统

```cmd
task_windows_amd64_v0.1.3.exe --api https://your-site.com --token your_token_here
```

## ⚡ 性能优化

如果程序与 ReMan 服务部署在同一台服务器上，可以使用本地地址提高性能：

```bash
--api http://127.0.0.1:4677
```

> **注意**：4677 是 ReMan 的默认端口，如果你修改过端口，请相应调整。

## 📝 常见问题

### Q: 如何获取 Token？
A: 登录 ReMan 后台，在设置页面中生成访问令牌。路径：站点配置->其它配置->须隐藏配置

### Q: 程序异常退出怎么办？
A: 检查网络连接、API 地址和 Token 是否正确。建议使用 PM2 管理进程，可自动重启。

### Q: 如何查看运行日志？
A: 
- nohup 方式：查看 `nohup.out` 文件
- PM2 方式：使用 `pm2 logs reman-task`

### Q: 如何停止程序？
A:
- 前台运行：按 `Ctrl+C`
- nohup 方式：`ps aux | grep task` 找到进程ID，然后 `kill PID`
- PM2 方式：`pm2 stop reman-task`

## ⚠️ 注意事项

1. **文件名**：请以实际下载的文件名为准，不要直接复制示例命令
2. **权限**：Linux 下可能需要添加执行权限：`chmod +x task_linux_amd64_v0.1.3`
3. **防火墙**：确保能正常访问 ReMan API 地址
4. **Token 安全**：请妥善保管你的访问令牌，不要泄露给他人

## 📊 PM2 常用命令

```bash
pm2 list              # 查看所有进程
pm2 logs reman-task   # 查看日志
pm2 restart reman-task # 重启进程
pm2 stop reman-task   # 停止进程
pm2 delete reman-task # 删除进程
```

---

如有问题，请检查网络连接和配置参数是否正确。
