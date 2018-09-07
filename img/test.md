## 配置python环境


很多Python程序依赖于不同的包,服务器也被很多人同时使用,为了不同账户和不同Python环境之间的互相影响,我们需要创建Python虚拟环境
> 创建Python虚拟环境需要virtualenv的支持,现在实验室的服务器都带有这个软件,
 如果提示找不到virtualenv,请切换成管理员账户自行安装

#### 新建python虚拟环境
首先确认Xshell登陆的是自己的账号

创建虚拟环境有2个参数可选:
1.$version,代表python的版本(2.7/3.5/3.6/etc.),不过前提是机器上已经安装过了相应的python解释器
2.$dir,代表虚拟环境的目录

教程中创建python3.5的虚拟环境,并且放在用户根目录的py35env下(~/py35env)

选择好参数之后,使用命令`virtualenv -p $version $dir` 创建虚拟环境
根据本次教程的选择,输入一下命令创建虚拟环境:
`virtualenv -p $python3.5 ~/py35env`
创建完成后,在虚拟环境的目录中bin文件夹下,会生成一个脚本:activate
输入命令`source ~/py35env/bin/activate`可以激活虚拟环境
>处于激活状态时:
1.python只会安装在这个虚拟环境中
2.默认使用这个虚拟环境中的python解释器运行代码

如果`(py35env)`作为前缀出现在了命令行前说明激活成功,此时输入`deactivate`可以退出激活环境

#### 修改pip源
python通过pip管理包,下载时需要使用网络
服务器默认不连外网,另外从下载速度考虑,我们希望可以让pip通过[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/help/pypi/)下载python包
输入以下命令修改把pip源修改为清华源
```
mkdir ~/.config/pip
nano ~/.config/pip/pip.config
```
以上命令会打开文本编辑器,把下面的文字复制进去-->Ctrl+X-->y-->回车,完成保存
>[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple

之后pip都会从清华下载包,速度快,不需要登录网关联网
> 东南部的学校可以优先考虑[中科大pip源](https://lug.ustc.edu.cn/wiki/mirrors/help/pypi)