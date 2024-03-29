# vscode使用技巧

## 1. vscode远端编辑
1. 下载插件Remote-SSH
2. `.ssh/config`中配置
```
host *
ControlMaster auto ## 复用之前链接，不用重复输入密码
ControlPath ~/.ssh/master-%r@%h:%p ## ssh相关记录存放

Host host1  ## 任意命名
User user1  
Port port1
Hostname ip1

Host host2
User user2
Port port2
Hostname ip2
ProxyCommand ssh host1 -W %h:%p  ## 使用host1作为跳板机

Host host3
User user3
Port port3
Hostname ip3
ProxyCommand ssh host2 -W %h:%p ## 使用host2作为跳板机
```
3. 有时候通过跳板机连接远程机器，不知道远程机器密码，可以将本地的ssh公钥放到远端机器的authorized_keys中

## 2. 在vscode终端使用命令在界面打开文件

在.zshrc中添加vscode路径
`export PATH="$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"`

使用code命令即可打开文件

# 好用的插件
1. rust_analyzer：rust实时编译分析
2. rust_syntax：rust代码高亮
3. crates：rust依赖管理
4. better toml：toml文件语法高亮
5. rust test lens：快速运行rust测试
6. Tabnine：AI自动补全