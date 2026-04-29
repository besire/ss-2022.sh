## 食用说明
### 安装脚本
*Debian / Ubuntu / CentOS 请确保已安装 curl 或 wget；Alpine Linux 最小系统请先安装 bash 和 curl/wget。*

**以下脚本根据需要选择**
+ ss 2022 | snell | shadowtls 多功能管理菜单
```bash
curl -L -s https://raw.githubusercontent.com/besire/ss-2022.sh/refs/heads/feat/alpine-support/menu.sh | bash
```
+ ss 2022 安装脚本
```bash
curl -L -s https://raw.githubusercontent.com/besire/ss-2022.sh/refs/heads/feat/alpine-support/ss-2022.sh | bash
```
+ Alpine Linux 首次运行前
```bash
apk add --no-cache bash curl wget
curl -L -s https://raw.githubusercontent.com/besire/ss-2022.sh/refs/heads/feat/alpine-support/menu.sh | bash
```
+ 下载脚本，本地执行
```bash
wget -N --no-check-certificate https://raw.githubusercontent.com/besire/ss-2022.sh/refs/heads/feat/alpine-support/ss-2022.sh && chmod +x ss-2022.sh && ./ss-2022.sh
```

# Shadowsocks Rust + ShadowTLS 安装管理脚本

这是一个用于安装和管理 Shadowsocks Rust 和 ShadowTLS 的脚本集合。

## 功能特点

- 支持 Shadowsocks Rust 的完整管理
- 支持 ShadowTLS V3 的安装和配置
- 支持 systemd 和 OpenRC 服务管理
- 自动生成配置信息和分享链接
- 支持多种加密方式
- 支持多客户端配置格式

## 系统要求

- 支持的操作系统：Debian / Ubuntu / CentOS / Alpine Linux
- 需要 root 权限
- 需要 curl、wget、jq 等基础工具，脚本会按系统自动调用 apt-get、yum 或 apk 安装缺失依赖
- Alpine Linux 使用 OpenRC 管理服务，脚本会自动创建 `/etc/init.d` 服务并使用 musl 版本的 Shadowsocks Rust 二进制

## 主要功能

### Shadowsocks Rust 功能
1. 安装 Shadowsocks Rust
2. 更新 Shadowsocks Rust
3. 卸载 Shadowsocks Rust
4. 启动/停止/重启服务
5. 修改配置信息
6. 查看配置信息
7. 查看运行状态
8. 安装 ShadowTLS

### ShadowTLS 功能
1. 安装 ShadowTLS
2. 卸载 ShadowTLS
3. 查看配置信息

## 支持的加密方式

### Shadowsocks Rust 加密方式
- aes-128-gcm (默认)
- aes-256-gcm (推荐)
- chacha20-ietf-poly1305
- 2022-blake3-aes-128-gcm (推荐)
- 2022-blake3-aes-256-gcm (推荐)
- 2022-blake3-chacha20-poly1305
- 2022-blake3-chacha8-poly1305
- 其他更多加密方式...

## 客户端配置

脚本支持生成多种客户端配置格式：

### Surge 配置
自动生成 Surge 配置格式，包含：
- 服务器地址
- 端口
- 加密方式
- 密码
- ShadowTLS 配置

### Shadowrocket 配置
提供完整的 Shadowrocket 配置说明，包括：
- Shadowsocks 节点配置
- ShadowTLS 节点配置
- 自动生成的配置二维码

### Clash Meta 配置
生成完整的 Clash Meta 配置，包含：
- 代理配置
- ShadowTLS 插件配置

## 分享功能

- 生成 SS + ShadowTLS 合并链接
- 生成配置二维码
- 支持 IPv4/IPv6 地址

## 注意事项

1. 安装 ShadowTLS 之前需要先安装 Shadowsocks Rust
2. 配置文件会自动备份
3. 更新脚本前建议先备份配置
4. 请确保安装过程中网络连接稳定
5. Alpine Linux 最小系统默认可能没有 bash，首次运行前请先执行 `apk add --no-cache bash curl wget`

## 服务管理

### Debian / Ubuntu / CentOS
```bash
systemctl status ss-rust
systemctl restart ss-rust
systemctl status shadowtls-ss
journalctl -xe --unit ss-rust
```

### Alpine Linux
```bash
rc-service ss-rust status
rc-service ss-rust restart
rc-service shadowtls-ss status
tail -n 100 /var/log/ss-rust.log
```

## 问题排查

如果遇到问题，可以：
1. 确认当前系统使用 systemd 还是 OpenRC，并使用上面的对应命令查看服务状态
2. Debian / Ubuntu / CentOS 查看服务日志：`journalctl -xe --unit ss-rust`
3. Alpine Linux 查看服务日志：`tail -n 100 /var/log/ss-rust.log`
4. 检查 Shadowsocks Rust 和 ShadowTLS 的配置文件是否存在且端口未被占用

## 更新日志

### v1.3.0
- 添加 ShadowTLS 支持
- 优化配置生成逻辑
- 改进错误处理

### v1.0.0
- 初始发布
- 支持 Shadowsocks Rust 基本功能

## 作者信息

- 作者：jinqians
- 网站：https://jinqians.com
