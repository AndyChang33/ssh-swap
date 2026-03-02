# ssh-swap

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
<br>[English](README.md)

快速切换多个 SSH 密钥的 CLI 工具（适用于多个 GitHub 账号）。

## 安装

```bash
git clone git@github.com:AndyChang33/ssh-swap.git
cd ssh-swap
node bin/ssh-swap init   # 创建配置、扫描密钥、添加 shell 别名
```

`init` 会：
1. 创建 `config.json`
2. 扫描 `~/.ssh/` 让你选择要添加的密钥
3. 自动将 `alias ss=...` 写入 `~/.zshrc` 或 `~/.bashrc`

## 用法

```bash
ss                       # 交互式菜单（方向键 / j,k 选择）
ss use <name>            # 切换：ssh-add -D → ssh-add <key> → ssh -T git@github.com
ss use                   # 不带参数 → 交互式菜单
ss list                  # 列出所有已配置的密钥
ss current               # 显示当前加载的密钥
ss scan                  # 扫描 ~/.ssh/ 发现新密钥
ss add <name> <path>     # 手动添加密钥
ss remove <name>         # 删除密钥
ss init                  # 首次初始化
```

## 配置

`config.json`（由 `init` / `scan` 自动生成，也可手动编辑）：

```json
{
  "keys": {
    "personal": { "path": "~/.ssh/id_ed25519", "email": "you@example.com" },
    "work": { "path": "~/.ssh/id_rsa_work", "email": "you@company.com" }
  }
}
```

## 依赖

- Node.js
- 零外部依赖

## License

[MIT](LICENSE)
