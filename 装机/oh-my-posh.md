在重新装机后，对整个终端、vscode等的美化都消失了。在这次的重新设置中，打算记录下来，方便下次或者其他人查阅。

## Windows Terminal
windows自带的命令提示符`cmd`并不好用，美化后的效果也并不太好，使用比较多的就是Windows Terminal，也可以使用PowerShell。
直接去[Microsoft Store](https://apps.microsoft.com/store/apps)搜索就可以。如果挂了梯子，需要把梯子先关闭，不然进不去微软的商店。(我以前经常进不去，有一次梯子刚好失效了，发现竟然点的进去，没研究过，感觉有点坑)

oh-my-posh需要在上面的控制台作为载体使用。


> [!命令行] 
> winget install JanDeDobbeleer.OhMyPosh -s winget


## oh-my-posh安装以及配置

可以搜索出来很多的教程，在我查阅的时候让我有点分不清楚到底该怎么做，每一篇都是几行命令，或者出现把Windows Terminal和oh-my-posh放在一起安装的。在我一次失败的配置后，我发现我的环境变量里面竟然有两个PowerShell路径。这种现象实在不可恭维。并且我遇到了很多的bug不知道怎么解决。于是我转身投入[官方文档](https://ohmyposh.dev/)的怀抱，并且正确安装了oh-my-posh。

整个安装，文档里描述的比较详细，并且提供了如果出现异常情况的解决办法，也不太需要身后的英语基础。一直顺利的进行到**Fonts**时，可能会出现一些分歧。

### choice Fonts
一个好的终端或者说编辑器，除了比较舒服的配色意外，更需要一个看着顺眼的字体。
在文档中，也特别将字体这一步设置成一小节。对于没有下载过字体的人来说可能有些接受不了。所以我想简单的介绍一下：
首先需要找一个[字体仓库]( https://www.nerdfonts.com/)，这里不太推荐使用例如**Fira Code**的字体，oh-my-posh的一个特点就是有丰富的图案，但是FiraCode并不支持，会出现乱码。我推荐的仓库里面的字体是Nerd Fonts，它与Fira Code的关系可以理解成一个是猫一个是狗，都是动物所属不同。对于Windows用户，下载完压缩包以后，打开会是一些蓝色盒子样式的文件，打开后左上角就有安装两个字。
在下载安装完喜欢的字体以后，打开Windows Terminal，如果是中午的就是**终端**(后面统一称之为终端)。
快捷键`shitf + ctrl + ，`打开终端的配置文件，就可以设置字体了。(这部分内容官方文档里面也有)

### 无法选择字体
在成功打开setting.json后，将下载好的字体写进去保存，终端可能会跳出差不多是“找不到下载的字体”的错误。此时可以终端窗口的上方，有一个小箭头(加号的旁边)，然后依次是：先选择Windows Powershell -> 其他设置下外观 -> 字体。可以在这里仔细的查看字体并选择。

### 选择主题
设置完字体后就到了最后的主题了。同样，官方提供了一个设置主题的办法，但是我在运行时同样也遇到了bug，并没有找到跟我的bug相同的解答，所以我就放弃了。
选择了直接在脚本中进行编辑:

> [!脚本] 
> notepad $PROFILE


如果是按照官方文档之前的安装方法的话，指到Customize这步之前。其实是可以找到脚本的所在位置的：
C:\\Users\\\<UserName>\\Documents\\WindowsPowerShell。里面的一个很长一串名字的文件就是运行时所启动的脚本。

> [!NOTE] 名字由来
> 在notepad $PROFILE出现错误时，文档中会提示你先运行以下命令：
> New-Item -Path $PROFILE -Type File -Force

> [!NOTE] $PROFILE的文件头
> oh-my-posh init pwsh | Invoke-Expression
> 这条命令是不能动的，如果没有这条命令，会出现oh-my-posh下的一些命令如：Get-PoshThemes

关于$PROFILE是一个脚本，就不多解释了，所以想加的操作都在文件里面加就好了。
oh-my-posh已经内置了很多好看的主题，就可以用`Get-PoshThemes`来查看。

### Get-PSReadLineKeyHandler : 找不到与参数名称“Key”匹配的参数
并没有找到跟我一模一样问题的，倒是找到了几篇差不多的。

我猜是版本问题
---------------------------
2022.11.12 10:45
好吧，并不是版本的问题，我去查找了一下关于Get-PSReadLineKeyHandler的官方文档，发现如下结果：
![Pasted image 20221121104805](https://raw.githubusercontent.com/CDUbyuN/images/master/Pasted%20image%2020221121104805.png)

查看Powshell版本的命令行是

> [!NOTE] 指令
>  (Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\3\PowerShellEngine -Name 'PowerShellVersion').PowerShellVersion

![Pasted image 20221121104947](https://raw.githubusercontent.com/CDUbyuN/images/master/Pasted%20image%2020221121104947.png)
所以我就卡在这个地方没有进度了。

## 2022-11-30 16:23
今天突然又尝试一下，发现突然就成功了。我并不知道到底是哪里出现了问题，并不认为是我哪里设置出了问题，因为电脑是刷机了一下。如果有人能帮助我解决这个问题请务必联系我！
