# K3s 学习手册

> 单机 K3s 从安装到实战的完整记录，以 **Docker Compose 迁移**为主线。

---

## 目标读者

从 Docker / Docker Compose 迁移到 K3s 的使用者。

所有示例都来自真实运行的服务，不是演示用的样例。环境是**单机 K3s**。

## 文档

| # | 文档 | 内容 |
| --- | --- | --- |
| 00 | [安装配置](k3s-00-安装配置.md) | K3s 安装、镜像加速、免 sudo 使用 kubectl |
| 01 | [基础命令](k3s-01-基础命令.md) | kubectl 速查，16 章 |
| 02 | [创建应用](k3s-02-创建应用.md) | 一个服务从 Compose 迁移到 K3s 的完整过程 |
| 03 | [路由配置](k3s-03-路由配置.md) | Traefik / Ingress / 自动 HTTPS / 中间件 |
| 04 | [存储挂载](k3s-04-存储挂载.md) | PVC、local-path、StatefulSet、备份 |
| 05 | [静态站点](k3s-05-静态站点.md) | nginx 静态站的完整部署过程 |
| 06 | [其他示例](k3s-06-其他示例.md) | OpenList：权限模型、subPath、多存储、并发写 |
| 07 | [备份恢复](k3s-07-备份恢复.md) | 集群状态 + 应用数据：备份对象、存放位置、恢复流程 |

## 阅读路径

**初次接触 K3s**，建议按顺序阅读：

```text
00 安装配置 → 01 基础命令 → 02 创建应用
           → 03 路由配置（域名和 HTTPS）
           → 04 存储挂载（数据持久化）
```

**已有 K3s 环境，按需查阅**：

- kubectl 命令 → [01 基础命令](k3s-01-基础命令.md)
- 域名或证书异常 → [03 路由配置](k3s-03-路由配置.md)
- 数据无法持久化 / Pod 启动失败 → [04 存储挂载](k3s-04-存储挂载.md)
- 集群备份与恢复 → [备份恢复](k3s-07-备份恢复.md)

## 几个贯穿全篇的约定

- 文档目录统一放在 **`/opt/k3s/`**
- 一个服务一个子目录，修改某个服务只涉及它自己的文件
- 示例围绕 **frps**、**vaultwarden**、**pairdrop**、**nginx**、**openlist** 这几个真实服务
- 每份文档的第一章都是「动手」，概念和进阶内容放在后面

---

## 本地预览

本文档用 [docsify](https://docsify.js.org/#/zh-cn/quickstart) 渲染。

```bash
cd k3s-learn

# 方式一：使用 Python 自带的 HTTP 服务
python3 -m http.server 3000
# 打开 http://localhost:3000

# 方式二：带热重载，修改后自动刷新
npm i -g docsify-cli
docsify serve
# 端口由工具自行分配，打开输出中打印的地址
```
