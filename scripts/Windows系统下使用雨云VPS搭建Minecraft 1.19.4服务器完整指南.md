# Windows系统下使用雨云VPS搭建Minecraft 1.19.4服务器完整指南

## 前言：为什么选择Mohist服务端？

本教程将指导您使用**Mohist 1.19.4**服务端在Windows系统上搭建Minecraft服务器。Mohist是一个优秀的Forge服务端实现，同时支持Bukkit/Spigot/Paper插件系统，让您能同时享受模组和插件带来的双重乐趣。

### Mohist核心优势
- 🚀 **高性能架构**：集成Paper优化，确保模组和插件同时运行的流畅性
- 🔌 **完美兼容**：同时支持Forge模组和Bukkit/Spigot插件生态系统
- 🔄 **持续更新**：活跃的开发者社区保证与最新Minecraft版本同步
- 🛠️ **简易管理**：提供直观的配置选项和友好的管理界面

## 准备工作

### 1. 服务器配置要求
- **推荐配置**：4核CPU/8GB内存及以上（Windows系统本身需要约2GB内存）
- **操作系统**：Windows Server 2019/2022
- **网络要求**：至少5Mbps带宽（10人同时在线建议10Mbps）

👉 [【点击查看】2025年最新雨云优惠码及特价云服务器方案汇总](https://bit.ly/RainYun)

## 详细搭建步骤

### 1. 连接服务器
使用Windows自带的远程桌面连接(RDP)：
1. 按Win+R输入`mstsc`打开远程桌面
2. 输入服务器IP地址和端口
3. 使用管理员账号(Administrator)登录

### 2. 系统优化设置
bash
# 关闭防火墙（仅测试环境建议）
控制面板 → Windows Defender防火墙 → 关闭所有网络类型的防火墙

### 3. Java环境配置
根据Minecraft版本选择对应JDK：
- 1.12.2及以下：Java 8
- 1.16.5：Java 11
- 1.17+：Java 17（推荐阿里Dragonwell）

**环境变量配置路径**：
`我的电脑 → 属性 → 高级系统设置 → 环境变量 → 系统变量Path`

### 4. 服务端部署
1. 创建专用文件夹（如D:\MC_Server）
2. 下载[Mohist官方服务端](https://new.mohistmc.com/downloadSoftware?project=mohist)
3. 创建启动脚本run.bat：
bat
java -Xms2G -XX:MaxRAMPercentage=95.0 -jar mohist-1.19.4-server.jar
pause

### 5. 端口映射配置
如果是NAT网络：
1. 登录雨云控制台
2. 找到"NAT端口映射"选项
3. 将内网25565端口映射到公网端口

## 服务器优化技巧

### 性能调优参数
| 参数 | 说明 | 推荐值 |
|------|------|--------|
| -Xms | 初始内存 | 总内存的1/4 |
| -Xmx | 最大内存 | 总内存的3/4 |
| -XX:MaxRAMPercentage | 内存使用率 | 85-95% |

### 安全设置建议
1. 定期备份world文件夹
2. 设置白名单（white-list=true）
3. 修改默认端口（server-port=25565）

## 常见问题解答

❓ **Q：玩家无法连接服务器怎么办？**
- 检查防火墙设置
- 确认端口映射正确
- 验证server.properties中的online-mode设置

❓ **Q：如何安装模组/插件？**
1. 模组放入mods文件夹
2. 插件放入plugins文件夹
3. 重启服务器生效

💡 **专业提示**：对于长期运行的服务器，建议选择雨云年付方案享受7折优惠，稳定性和性价比更高！

通过本教程，您已经掌握了在Windows系统上搭建Minecraft服务器的完整流程。现在就可以邀请好友加入您的专属游戏世界了！如有任何问题，欢迎在评论区留言交流。