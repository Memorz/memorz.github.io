
# Grasscutter 电脑端安装教程


**友情提醒：游玩 Grasscutter 请记得屏蔽 `log-upload-os.mihoyo.com` ，或者全程不要关闭代理，否则会上传 `device_id` 给官方，存在未知风险。**

**上述问题解决办法：修改hosts文件进行屏蔽**

```
#hosts文件位置：
#Windows: C:\Windows\System32\drivers\etc\hosts
#Linux: /etc/hosts

#将下列五行复制粘贴到hosts文件保存即可，不会更改并保存hosts文件的自行百度
0.0.0.0 log-upload-os.mihoyo.com
0.0.0.0 overseauspider.yuanshen.com
0.0.0.0 log-upload.mihoyo.com
0.0.0.0 log-upload-os.hoyoverse.com
0.0.0.0 uspider.yuanshen.com﻿
```

![此图片的alt属性为空；文件名为image-2.png](https://memorz.top/wp-content/uploads/2022/05/image-2.png)

如果还要玩官服的话，玩官服之前删除掉hosts文件中的这几行，玩Grasscutter的时候重新加上。

## 阅前须知
本教程不欢迎不会动手的人、不善于利用搜索引擎和不懂[提问的艺术](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way/blob/main/README-zh_CN.md)的人使用，如果您是以上所罗列出的类型，那么请现在放弃搭建的想法并关闭此教程。

**文章链接中的文件更新不及时，故建议前往[✈️群聊](https://t.me/genkitCN_chat)获取。**

本地搭建支持使用官服客户端，不必将官服转换为国际服。

安卓部署Grasscutter简易教程（需root）：[**点此跳转**](https://www.chitang.tech/posts/grasscutter-android/)。

本教程基于[**中文简易版教程**](https://telegra.ph/Grasscutter-CN-04-21)制作，部分参考[**Overview - GrassCutter Docs zh_CN (Unofficial)**](https://www.grasscutter.cf/) 和 [**Hello from GenKit Wiki | GenKit Wiki (mhysb.xyz)**](https://genkit.mhysb.xyz/)。

如果只是想电脑本地部署并游玩，或者在服务器上部署并且只在电脑上游玩，本教程完全适合你，但要是还想在手机上游玩的话，推荐使用隔壁大佬们的教程：

**[原神 2.6 私服启动教程2.2——虚之亚洛克OTOOBLOG](https://blog.otoo.top/Blog/Genshin2-6-Grasscutters/)**

**[GenshinTJ——荼蘼博客](https://blog.tomys.top/2022-04/genshintj/?_gl=1*90xya1*_ga*ODEzMjQ1MDQuMTY1MTIxMzU2Mg..*_ga_N194P9LRRJ*MTY1MTM2ODk4My4xMi4xLjE2NTEzNzAxNDEuMA..)**

[**📥 获取服务端 | GenKit Wiki (mhysb.xyz)**](https://genkit.mhysb.xyz/docs/quick-start/get-server)

## 安装 JDK-17.0.3

[admonition title="注意" color="red"]最新开发版必须使用 jdk 17，不要装17以下的，也不要装18。[/admonition]

**[点此下载](https://download.oracle.com/java/17/latest/jdk-17_windows-x64_bin.exe)** Java SE Development Kit 17.0.3.1 x64 Installer 并安装，安装完以后打开 cmd，输入 `java -version`，如果输出为 `java version "17.0.3.1"` 则可以进行下一步，如果并没有输出 Java 版本号，则需要自行将 `xxx\Oracle\Java\javapath` 加入系统环境变量 Path 中（如何加入 Path 自行百度）。

## 安装 Mongodb

从 [**MongoDB官网**](https://www.mongodb.com/try/download/community) 下载 `Mongodb 5.0.`8 **压缩包**格式文件，或者 **[点击这里](https://fastdl.mongodb.org/windows/mongodb-windows-x86_64-5.0.8.zip)** 直接开始下载，下载后将文件解压到 `D:\Grasscutter\mongodb` ，此时在 `D:\Grasscutter\mongodb\bin` 中应该有 `mongod.exe` 文件。

在 `D:\Grasscutter\mongodb` 中新建一个 `db` 文件夹用于保存数据库文件（以上所罗列出的文件夹没有的话就创建，本来你就该创建，别到群里又问为什么我没有这个文件夹，动一动脑子😅）。

![此图片的alt属性为空；文件名为%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D2png](https://memorz.top/wp-content/uploads/2022/04/%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D2.png)

## 配置环境

### 下载Grasscutter的Development分支构建版本

前往✈️频道下载[**最新的Grasscutter的Dev分支**](https://t.me/GrasscutterArchives)，下载完成后将其解压至 `D:\Grasscutter` 下，并重命名为 `grasscutter.jar` ，然后双击该文件，或者在该目录下打开 cmd，输入 `java -jar grasscutter.jar` 来运行该文件，运行一次后服务器会自动关闭并生成**配置文件**与**不完整的目录结构**。

![此图片的alt属性为空；文件名为image3png](https://memorz.top/wp-content/uploads/2022/05/image-3.png)

### 配置所需环境

下载 [**Grasscutter_Resources 仓库**](https://github.com/Koko-boya/Grasscutter_Resources) 和  [**gi-bin-output 仓库**](https://github.com/spencerbonilla/gi-bin-output)，将 `Resources （来自于Grasscutter_Resources仓库）` 中除 `BinOutput` 的所有部分放入 `` `D:\Grasscutter` `` 文件夹中的 `resources` 中,将 `2.5.52/Data （来自于gi-bin-output仓库）`文件夹下的 `_BinOutput` 文件夹重命名为 `BinOutput` 并放入 `` `D:\Grasscutter` `` 文件夹中的 `resources` 中。

![此图片的alt属性为空；文件名为image5png](https://memorz.top/wp-content/uploads/2022/05/image-5.png)

下载 [**Grasscutter 仓库development分支**](https://github.com/Grasscutters/Grasscutter/tree/development)，将其中的 `data`, `keys` 文件夹和 `keystore.p12` 文件放入 `` `D:\Grasscutter` `` 文件夹中。

![此图片的alt属性为空；文件名为image6png](https://memorz.top/wp-content/uploads/2022/05/image-6.png)

## 运行数据库

打开 `cmd` 依次输入以下命令（**每个都得输，注意，是每个！！！！**）：

```
D:
cd D:\Grasscutter\mongodb\bin
mongod --dbpath "D:\Grasscutter\mongodb\db"
```

如果有数据输出，且没有结束运行，则此步已配置正确，**不要关闭此 `cmd` 窗口，保持后台运行**。

![此图片的alt属性为空；文件名为%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D3png](https://memorz.top/wp-content/uploads/2022/04/%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D3.png)

## 运行服务端

运行 `cmd` 并依次输入以下命令：

```
D:
cd D:\Grasscutter
java -jar grasscutter.jar
```

此时如果没有端口冲突并且 `mongodb` 也在后台同时运行，那么服务器端将正常运行。

![此图片的alt属性为空；文件名为%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D4png](https://memorz.top/wp-content/uploads/2022/04/%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D4.png)

运行成功后你需要输入 `account create 用户名 用户id（即 uid）` 来创建你的游戏账号。

## 客户端连接

请下载 [**此 Releases**](https://github.com/Grasscutters/GrassClipper/releases) 下的 `GrassClipper.zip` 文件，解压到任意目录（非 Grasscutter 文件夹）后，打开 `GrassClipper.exe` ，在弹出的窗口点击 `Install` （必须），待部署完以后关闭**部署时弹出的 `cmd`** ，然后点击下方 `Set game executable` 选择游戏的exe文件，例如：`D:\Program Files\Genshin Impact\Genshin Impact Game\Yuanshen.exe` ，之后在上方右侧输入 `127.0.0.1` ，端口填 `443`（必须），然后点击运行，即可打开游戏，在登录时你需要输入**创建的用户名（username）**和**任意密码**即可加入测试服务器。

PS：启动器支持中文，想设置成中文的可以点右上角设置，language 框选 simplified Chinese 就行。

![此图片的alt属性为空；文件名为image1024x576png](https://memorz.top/wp-content/uploads/2022/05/image-1024x576.png)

下载并配置代理

![此图片的alt属性为空；文件名为image11024x576png](https://memorz.top/wp-content/uploads/2022/05/image-1-1024x576.png)

[alert]如果启动游戏后在登录界面发现还是跟国服登录界面一样的话，那么恭喜你，失败了🤡。成功的话启动游戏后登录界面是国际服登录界面（哪怕你客户端是国服）。[/alert]

[collapse title="GrassClipper打开不了或者打开后白屏的话点此查看解决办法" color="indigo"]

下载**[GrassClipper-X-1.0.0-win-x64.7z](https://cup163.lanzouf.com/iSi4k03vvrsb)**，解压到任意目录（非 Grasscutter 文件夹），打开里面的 `GrassClipper.exe` 按照下图进行配置。**注意：**第二步选择游戏路径一定要选择到 Genshin Impact Game 文件夹下的GenshinImpact.exe（国际服）或yuanshen.exe（国服），第四步一定要锁上，不要解锁，第七步记得勾选 Custom Server。

![此图片的alt属性为空；文件名为image31024x597png](https://memorz.top/wp-content/uploads/2022/04/image-3-1024x597.png)

[/collapse]

## 游戏内指令

游戏内切换场景、获取角色命之座、材料、物品等需要在对话框使用指令，具体看下图：

![此图片的alt属性为空；文件名为%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D8png](https://memorz.top/wp-content/uploads/2022/04/%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D8.png)

![此图片的alt属性为空；文件名为%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D9png](https://memorz.top/wp-content/uploads/2022/04/%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D9.png)

如果显示暂无会话外的好友就在好友列表选择 Server 打开聊天框即可

部分常用指令：

生成怪物：spawn+空格+怪物ID+空格+等级+空格+数量

给予物品：g/give+空格+uid+空格+物品ID+空格+数量

给予角色：givec/givechar+空格+uid+空格+角色ID

现在以获取万叶为例，在对话框输入`/givec 1660(自己的uid) 10000047`

![此图片的alt属性为空；文件名为%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D10png](https://memorz.top/wp-content/uploads/2022/04/%E5%8E%9F%E7%A5%9E%E7%A7%81%E6%9C%8D10.png)

**注意：**在对话框输入指令时必须加上斜杠“/”或感叹号 “!”，否则无法识别。

完整指令列表**[点此获取](https://cup163.lanzouf.com/iM0Bt0433ddc)**

[admonition color="indigo"]不想狼狈地在指令列表里找对应命令？看这里就对了，前往下载**[GrasscutterTools-命令生成工具](https://github.com/jie65535/GrasscutterCommandGenerator)**，想省时间的你值得拥有（doge）。该工具如若报毒属正常现象，担心的可以不用。或者使用网页端[**GrasscutterTools**](https://wmn1525.github.io/grasscutterTools/dist/index.html#/)也可以。[/admonition]

## 全卡池

前往文章开头✈️群聊下载 `Banners.json` ，替换 `data` 目录下的同名文件即可（没有复刻池）。

## 常见问题

### 进入游戏时显示网络错误 4026

很多问题都能导致4206错误，比如网络代理问题、数据库出错、jdk版本问题等等，一个个排查吧。再或者修改 `config.json` 中 `DispatchServer.PublicIp` 为 `dispatchcnglobal.yuanshen.com` ，如果修改后能正常进入游戏，可以回退该配置为原来的。

### 端口占用

如果出现下图情况则证明端口被占用

![此图片的alt属性为空；文件名为image21024x462png](https://memorz.top/wp-content/uploads/2022/04/image-2-1024x462.png)

解决办法：**[点此跳转](https://jingyan.baidu.com/article/90808022bdd680bc91c80f99.html)**

或者使用该工具：[**点此下载**](https://cup163.lanzouf.com/iOFB303r92re)

检查一下自己电脑的443和22102端口是否被占用（装有 VMware 的话 443 端口可能会被占用）

### 进游戏以后运行命令出现“不允许权限运行命令”

在启动 jar 文件的那个 cmd 窗口输入 `permission add <username> *` <username>即你创建的游戏账户

### 文件名、目录或卷标语法不正确

路径必须全英文，如果你系统账户是中文的话会报错

### 游戏登录窗口转圈后提示网络错误

修改 `config.json` 中 `DispatchServer.PublicIp` 为 `dispatchcnglobal.yuanshen.com`，保存并重新启动 `grasscutter.jar` 和游戏，如果修改过后可以正常进入游戏，可以回退这个配置为原来的。

### 关闭私服后打开官服进不去

打开控制面板——Internet选项——连接——局域网设置——取消代理服务器，然后重启

### 系统找不到指定的路径

解压出来再打开。

### 找不到文件“D:/Grassclipper/ext/mitmdump.exe”

Grassclipper下的ext文件夹是在你install proxy的时候自动创建的，如果说你在运行的时候提示说`找不到文件“D:/Grassclipper/ext/mitmdump.exe”` 那证明你proxy根本没有部署完整，去设置里重新部署proxy或者换启动器。

### jdk版本问题

出现下图一模一样的错误即为jdk版本不对，更换jdk版本。

![此图片的alt属性为空；文件名为image11024x538png](https://memorz.top/wp-content/uploads/2022/04/image-1-1024x538.png)

### 打开GrassClipper启动器出现白屏

最简单粗暴的办法：换启动器。

### 开启代理后还是登录了官服，或者跳验证码等

电脑中有奇怪的东西把端口占用了导致代理失败

### 502 / 4301 / 无法连接服务器

绝对是你没正确配置，仔细检查一遍

### 其余问题

其余问题进群反馈：**[点此进入](https://t.me/genkitCN_chat)**

## 更新

由于框架已经基本部署完整，所以更新时只用替换 grasscutter.jar 文件并删除掉 config.json 即可，如果你在 config.json 文件中更改了端口和IP的话，需要重新进入 config.json 文件进行配置。

~~文末链接会不定时更新最新的grasscutter.jar的Dev开发版，放在云盘中的**Dev开发版**文件夹中，需要可自取。~~（已弃用）

## 下载

不再提供下载链接，有需求请自行前往✈️群聊下载

## 写在最后

如果部署过程中出现问题，欢迎评论区留言或者**[加群](https://t.me/+nMAE7aGJlmczZGM9)**反馈（个人建议前往群聊，留言不一定能看见）。

如果此教程有帮到你的话，可以打赏一只鸡腿嘛QAQ
