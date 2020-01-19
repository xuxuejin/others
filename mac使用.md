# Mac 使用问题记录
## mac Rootless 关闭与开启
全新的 mac OS 使用了 Rootless，/system/sbin/usr被锁定，部分命令不能使用，即使加了 sudo 也不好使，会提示 “Operation not permitted”。
解决办法：
* 先查看电脑 rootless 状态：csrutil status 
* 重启电脑，按住 command+r 进入回复，然后在菜单栏：实用工具 -> 终端，输入：csrutil disable，然后再输入：reboot 重启即可
* 建议改完之后还改回来，防止造成不必要损失，输入：csrutil enable

## 安装 brew 
 Homebrew 简称 brew，是 macOS 上的包管理工具。类似 RHEL/CentOS 上的 yum 或者 Ubuntu 上的 apt-get 一样。brew 是 ruby 开发的，需要确认 ruby 是否已安装。
 
 * 查看 ruby 是否安装
 ```
which ruby
或
ruby -v
```
使用官方的安装方法：/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" 并不一定能正常安装，需要科学上网才行。

解决办法：
1 更换国内的镜像(第一次使用的更换镜像，也出现过问题，并不能保证一次安装成功)
2 本地安装法
 * 在浏览器输入https://raw.githubusercontent.com/Homebrew/install/master/install（第一次可能打不开，多刷几次）
 * 保存网页的内容于任意路径，并命名为 brew_install.rb，记住保存的路径
 * 进入 brew_install.rb 保存的路径，在终端输入指令：ruby brew_install.rb
 
 按照上面的方法2安装，就可以成功安装，但是在安装过程中可能还会遇到一个问题：Git error: RPC failed; curl 56 LibreSSL SSL_read: SSL_ERROR_SYSCALL, errno 54，这是由于 git 在 pull 或者 push 大文件造成的提交或者拉取失败。
 
 解决方法：git config --global http.postBuffer 1048576000 （推荐1048576000 设置过小，还需要重新设置）
 
 至此，brew 就能彻底安装成功，检验是否已经正确安装：brew -v （查看版本号）
 
 ## node的安装与卸载
 直接去 node 官网下载安装包也可能正常安装 node，但是既然已经安装 brew 了，不妨试试 brew 如何安装 node
 
 * 卸载 node （pkg卸载）
 sudo rm -rf /usr/local/{bin/{node,npm},lib/node_modules/npm,lib/node,share/man/*/node.*}
 
 * 查看包文件
brew search node

* 安装 node
```
brew install node
```
这种安装方法还是比较麻烦的，安装完成之后还要设置环境变量，还要设置软连接，比较麻烦，最好的做法，直接去 node 官网下载安装包手动安装。

## 设置 git Tab 键提示功能
git 安装后直接使用 tab 功能不能提示，需要进行简单的设置才行，有两种方法，这里只写一种最简单高效的方式：
1. 首先下载自动补齐脚本，在终端输入使用 curl 命令如下：
curl https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -o ~/.git-completion.bash
2. 编辑 ~/.bash_profile 文件，在最后增加如下代码。如果没有该文件，就新建一个
```
if [ -f ~/.git-completion.bash ]; then
    source ~/.git-completion.bash
fi
```
3. 重启终端，愉快地使用补全功能吧

 
 
 
 
 
 


 
