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
