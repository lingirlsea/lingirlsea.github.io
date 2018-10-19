## Git便捷文档及常用命令说明

#### 配置

###### 初次运行前的配置
Git 自带一个 <code>git config</code> 的工具来帮助设置控制 Git 外观和行为的配置变量。 这些变量存储在三个不同的位置：

&emsp;1、<code>/etc/gitconfig</code> 文件: 包含系统上每一个用户及他们仓库的通用配置。 如果使用带有 <code>--system</code> 选项的 <code>git config</code> 时，它会从此文件读写配置变量。

&emsp;2、<code>\~/.gitconfig</code> 或 <code>\~/.config/git/config</code> 文件：只针对当前用户。 可以传递 <code>--global</code> 选项让 Git 读写此文件。

&emsp;3、当前使用仓库的 Git 目录中的 config 文件（就是 <code>.git/config</code> ）：针对该仓库。

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

你可能会看到重复的变量名，因为 Git 会从不同的文件中读取同一个配置（例如：<code>/etc/gitconfig</code> 与 <code>\~/.gitconfig</code> ）。 这种情况下，Git 会使用它找到的每一个变量的最后一个配置。

你可以通过输入 <code>git config <key></code> ： 来检查 Git 的某一项配置
<pre>
$ git config user.name
</pre>


#### 获取帮助
若你使用 Git 时需要获取帮助，有三种方法可以找到 Git 命令的使用手册：
<pre>
$ git help &lt;verb&gt;
$ git &lt;verb&gt --help
$ man git-&lt;verb&gt
</pre>
例如，要想获得 config 命令的手册，执行
<pre>
$ git help config
</pre>

#### 常用命令


- 在现有项目中初始化仓库
> $ git init


- 克隆
> $ git clone
> - <code>url</code> 克隆仓库
> - <code>url</code> <code>rename</code> 克隆仓库并重命名


- 添加
> $ git add 
> - <code>filename</code> 将指定文件添加到跟踪或提交到暂存区


- 提交
> $ git commit
> - 不加参数，默认启用文本编辑器以便输入提交信息
> - <code>-m, --message</code> &lt;message&gt; 将暂存区的文件提交至本地Git仓库
> - <code>-a -m</code> 跳过 git add，自动把所有已经跟踪过的文件暂存起来一并提交


- 状态
> $ git status
>
> <code> -s, --short </code> 状态简览
> - 新添加的未跟踪文件前面有 <code>??</code> 标记
> - 新添加到暂存区中的文件前面有 <code>A</code> 标记
> - 修改过的文件前面有 <code>M</code> 标记，右边的 <code>M</code> 表示该文件被修改了但是还没放入暂存区，左边的 <code>M</code> 表示该文件被修改了并放入了暂存区


- 差异
> $ git diff
>
> - 不加参数，比较的是工作目录中当前文件和暂存区域快照之间的差异， 也就是修改之后还没有暂存起来的变化内容
> - <code>--cached, --staged(1.6.1以上)</code> 查看已暂存的将要添加到下次提交的内容


- 移除
> $ git rm
>
> - <code>filename</code> 从跟踪文件清单中移除名为filename的文件，并连带从工作目录删除
> - <code>blob</code> 模式，例如，删除以 ~ 结尾的所有文件
>   <br><br><pre>git rm \*~</pre>
> - <code>--cached</code> 把文件从 Git 仓库中删除（亦即从暂存区域移除），但仍然保留在当前工作目录中


- 移动
> $ git mv <code>filename</code> <code>newfilename</code> 
> 


- 查看提交历史
> $ git log
> 
> - 不加参数，按提交时间列出所有的更新，最近的更新排在最上面

> - <code>-n</code>                  显示最近的 <code>n</code> 条记录

> - <code>-p</code>                  按补丁格式显示每个更新之间的差异

> - <code>--stat</code>              显示每次更新的文件修改统计信息

> - <code>--shortstat</code>         只显示 <code>--stat</code> 中最后的行数修改添加移除统计

> - <code>--name-only</code>         仅在提交信息后显示已修改的文件清单

> - <code>--name-status</code>       显示新增、修改、删除的文件清单

> - <code>--abbrev-commit</code>     仅显示 SHA-1 的前几个字符，而非所有的 40 个字符

> - <code>--relative-date</code>     使用较短的相对时间显示（比如，“2 weeks ago”）

> - <code>--graph</code>             显示 ASCII 图形表示的分支合并历史

> - <code>--since, --after</code>    仅显示指定时间之后的提交
>   <br><br><pre>--since=2.weeks | 2008-01-15 | 2 years 1 day 3 minutes ago ...</pre>

> - <code>--until, --before</code>   仅显示指定时间之前的提交

> - <code>--author</code>            仅显示指定作者相关的提交

> - <code>--committer</code>         仅显示指定提交者相关的提交

> - <code>--grep</code>              仅显示含指定关键字的提交

> - <code>-S</code>                  仅显示添加或移除了某个关键字的提交

> - <code>--pretty=oneline|short|full|fuller|format</code> 指定使用不同于默认格式的方式展示提交历史
>   <br><br><pre>--pretty=format:"%h - %an, %ar : %s" 定制要显示的记录格式，这样的输出对后期提取分析格外有用
    <br><code>%H</code>     提交对象（commit）的完整哈希字串
    <br><code>%h</code>     提交对象的简短哈希字串
    <br><code>%T</code>     树对象（tree）的完整哈希字串
    <br><code>%t</code>     树对象的简短哈希字串
    <br><code>%P</code>     父对象（parent）的完整哈希字串
    <br><code>%p</code>     父对象的简短哈希字串
    <br><code>%an</code>    作者（author）的名字
    <br><code>%ae</code>    作者的电子邮件地址
    <br><code>%ad</code>    作者修订日期（可以用 --date= 选项定制格式）
    <br><code>%ar</code>    作者修订日期，按多久以前的方式显示
    <br><code>%cn</code>    提交者（committer）的名字
    <br><code>%ce</code>    提交者的电子邮件地址
    <br><code>%cd</code>    提交日期
    <br><code>%cr</code>    提交日期，按多久以前的方式显示
    <br><code>%s</code>     提交说明   
  </pre>












































































