# Vultr VPS 建站常见问题解决方案指南（持续更新）

作为一名设计师转型的建站新手，我在使用 WordPress 和 Typecho 搭建个人作品集网站和博客的过程中，积累了一些 Vultr VPS 的实用经验。本文将分享这些常见问题的解决方案，希望能帮助遇到类似问题的朋友。

## 一、VPS 基础配置问题

### 1. SSH 22 端口被关闭的解决方法

近期许多 Vultr 用户都遇到了 22 端口被关闭的问题，这会导致无法通过 SSH 连接服务器。以下是详细的解决方案：

#### 方法一：使用 Vultr 控制台登录

1. 登录 Vultr 控制面板
2. 找到对应服务器实例
3. 点击"View Console"按钮
4. 使用 root 用户名和初始密码登录（如未修改过）

👉 [【点击查看】2025年最新 Vultr 优惠码及特价云服务器方案汇总](https://bit.ly/VuLtr)

#### 方法二：通过防火墙配置开启端口

1. 检查防火墙状态：
   bash
   systemctl status firewalld
   
   - 显示"Active: inactive (dead)"表示防火墙关闭
   - 显示"Active: active (running)"表示防火墙已开启

2. 如防火墙关闭，先启动：
   bash
   systemctl start firewalld
   

3. 开启22端口：
   bash
   firewall-cmd --zone=public --add-port=22/tcp --permanent
   

4. 重载防火墙配置：
   bash
   firewall-cmd --reload
   

5. 建议重启服务器：
   bash
   reboot
   

### 常用防火墙命令速查表

| 命令 | 功能 |
|------|------|
| `systemctl start firewalld` | 启动防火墙 |
| `systemctl status firewalld` | 查看防火墙状态 |
| `systemctl disable firewalld` | 停止防火墙 |
| `systemctl stop firewalld` | 禁用防火墙 |
| `firewall-cmd --zone=public --list-ports` | 查看所有开放端口 |
| `firewall-cmd --zone=public --add-port=80/tcp --permanent` | 开放指定端口 |
| `firewall-cmd --zone=public --query-port=80/tcp` | 检查端口状态 |
| `firewall-cmd --zone=public --remove-port=80/tcp --permanent` | 关闭指定端口 |

## 二、其他常见问题（待更新）

后续将陆续补充更多 Vultr VPS 建站过程中可能遇到的问题和解决方案，包括：
- 网站部署优化技巧
- 数据库配置问题
- 域名解析设置
- 网站备份策略

建议收藏本文，持续关注更新内容！