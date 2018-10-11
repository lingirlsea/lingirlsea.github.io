# git文档及常用命令说明

### 配置

Git 自带一个 <code>git config</code> 的工具来帮助设置控制 Git 外观和行为的配置变量。 这些变量存储在三个不同的位置：


&emsp;1、<code>/etc/gitconfig</code> 文件: 包含系统上每一个用户及他们仓库的通用配置。 如果使用带有 <code>--system</code> 选项的 <code>git config</code> 时，它会从此文件读写配置变量。

&emsp;2、<code>\~/.gitconfig</code> 或 <code>\~/.config/git/config</code> 文件：只针对当前用户。 可以传递 <code>--global</code>选项让 Git 读写此文件。

&emsp;3、当前使用仓库的 Git 目录中的 config 文件（就是 <code>.git/config</code>）：针对该仓库。

每一个级别覆盖上一级别的配置，所以 <code>.git/config</code> 的配置变量会覆盖 <code>/etc/gitconfig</code> 中的配置变量。
