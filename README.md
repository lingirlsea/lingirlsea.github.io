## Git便捷文档及常用命令说明

#### 1、配置

###### 初次运行前的配置
Git 自带一个 <code>git config</code> 的工具来帮助设置控制 Git 外观和行为的配置变量。 这些变量存储在三个不同的位置：

&emsp;1、<code>/etc/gitconfig</code> 文件: 包含系统上每一个用户及他们仓库的通用配置。 如果使用带有 <code>--system</code> 选项的 <code>git config</code> 时，它会从此文件读写配置变量。

&emsp;2、<code>\~/.gitconfig</code> 或 <code>\~/.config/git/config</code> 文件：只针对当前用户。 可以传递 <code>--global</code>选项让 Git 读写此文件。

&emsp;3、当前使用仓库的 Git 目录中的 config 文件（就是 <code>.git/config</code>）：针对该仓库。

每一个级别覆盖上一级别的配置，所以 <code>.git/config</code> 的配置变量会覆盖 <code>/etc/gitconfig</code> 中的配置变量。



###### 用户信息
<pre>
$ git config --global user.name "lingirlsea"
$ git config --global user.email lingirlsea@email.com
</pre>
如果使用了 <code>--global</code> 选项，那么该命令只需要运行一次，因为之后无论你在该系统上做任何事情， Git 都会使用那些信息。 当你想针对特定项目使用不同的用户名称与邮件地址时，可以在那个项目目录下运行没有 <code>--global</code> 选项的命令来配置。



###### 检查配置信息
<pre>
$ git config --list
</pre>

你可能会看到重复的变量名，因为 Git 会从不同的文件中读取同一个配置（例如：<code>/etc/gitconfig</code> 与 <code>\~/.gitconfig</code>）。 这种情况下，Git 会使用它找到的每一个变量的最后一个配置。

你可以通过输入 <code>git config <key></code>： 来检查 Git 的某一项配置
<pre>
$ git config user.name
</pre>
