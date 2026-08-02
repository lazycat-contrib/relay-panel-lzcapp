# RelayPanel for LazyCat

这是 [RelayPanel](https://github.com/MoeShinX/relay-panel) 的懒猫微服 LPK v2 移植。

## 功能

- 使用上游预构建 Panel 镜像，数据通过 SQLite 持久化到 `/lzcapp/var/data`
- 默认使用懒猫应用域名；如已在懒猫侧完成自定义域名绑定，也可在安装时填写该域名，使 Panel 生成正确的公网地址
- 首次使用上游默认账号 `admin / admin123` 自动登录，并在改密成功后自动保存新密码
- GitHub Actions 自动跟踪 Panel 的稳定 SemVer 镜像标签，生成版本化 Release LPK，并发布到懒猫官方商店和喵喵商店

## Node 部署

本 LPK 仅包含 Panel。Relay Node 通常应部署在独立中继服务器上；请先在 Panel 中创建入站组，再按上游文档使用生成的 `NODE_TOKEN` 部署 Node。

## GitHub Actions Secrets

发布工作流需要为本仓库授权以下 GitHub Secrets：

- `LAZYCAT_TOKEN`
- `APPSTORE_URL`
- `APPSTORE_TOKEN`
- `APP_ID`（可选）
- `PRIVATE_STORE_GROUP_CODES`（可选）

同名 Repository Secret 会覆盖 Organization Secret。组织级 Secret 必须显式授权本仓库。

## 本地构建

```bash
lzc-cli project release -o dist/relay-panel.lpk
lzc-cli lpk info dist/relay-panel.lpk
```

## License

上游 RelayPanel 使用 [AGPL-3.0](https://github.com/MoeShinX/relay-panel/blob/main/LICENSE) 许可证。
