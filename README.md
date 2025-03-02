
# 新版台服竞技场查询插件【pcrjjc_tw_new】

# ！！！注意：当前为测试版，未经完全测试！！！

## 各版本区别

|                                 版本                                 |     说明     |       备注        | 
|:------------------------------------------------------------------:|:----------:|:---------------:|
|          [pcrjjc](https://github.com/lulu666lulu/pcrjjc)           |    初始版本    |     梦开始的地方      | 
|            [pcrjjc2](https://github.com/cc004/pcrjjc2)             | pcrjjc重制版  |  适配了各种服（包括台服）   | 
| [pcrjjc_huannai](https://github.com/SonderXiaoming/pcrjjc_huannai) | pcrjjc2魔改版 |     各种优化和简化     | 
|         [pcrjjc3-tw](https://github.com/azmiao/pcrjjc3-tw)         |   台服专用版    |    额外支持多服查询     | 
|    [(当前)pcrjjc_tw_new](https://github.com/azmiao/pcrjjc_tw_new)    |   台服专用版    | 增加全局禁用推送功能和各种优化 | 

## 台服合服后的适配说明

#### 感谢【[2佬](https://github.com/sdyxxjj123)】适配了【新版】账号配置文件的查询

#### 感谢【[辣鱼佬](https://github.com/layvsan)】适配了【旧版】账号配置文件的查询

#### 感谢其他用爱发电的各位大佬的鼎力相助

## 本仓库的特性

> ✨增加全局禁用推送功能，不需要自动推送的直接关闭即可✨

> ✨优化查询逻辑，经测试极大地提高了多次查询的速度和稳定性✨

> ✨自动识别新版和旧版的账号配置文件，可以同时兼容查询✨

## 如何更新

一直摸兜里，直接`git pull`就完事了

## 使用方法

### 如果之前没用过pcrjjc3-tw

1. 拿个不用的号登录PCR，然后把data/data/tw.sonet.princessconnect/shared_prefs/tw.sonet.princessconnect.v2.playerprefs.xml复制到该目录

    注意：每个号至少得开启加好友功能，一服为"台服一服"，台服二三四服合服后视为一个"台服其他服"

2. 给你的`tw.sonet.princessconnect.v2.playerprefs.xml`加上前缀名，例如：
    ```
    台服一服：
    first_tw.sonet.princessconnect.v2.playerprefs.xml
    台服其他服：
    other_tw.sonet.princessconnect.v2.playerprefs.xml
    ```
    如果没有某个服的配置文件或者不需要该服就不用管，台服二三四服只需要一个即可，可以用电脑模拟器开游戏生成

3. 安装依赖：
    ```
    pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
    ```
    
4. 配置account.json设置代理：localhost就行，只要改端口，自行更换和你代理软件代理的端口一样就行，是代理端口哦，不是软件监听端口，开PAC模式不改变系统代理就行

    注意：如果你不需要代理，请打开`account.json`并将里面改成`{"proxy":{}}`

5. 开启插件，并重启Hoshino即可食用

### 如果之前用过pcrjjc3-tw

1. 将原来`pcrjjc3-tw`插件目录下的`account.json`, `binds.json`, `frame.json` 复制过来，不要复制`headers.json`，不要复制`headers.json`，不要复制`headers.json`！

2. 将原来的`xxx_tw.sonet.princessconnect.v2.playerprefs.xml`的配置文件都复制过来，一服的文件改名`first_tw.sonet.princessconnect.v2.playerprefs.xml`，其他服的改名为`other_tw.sonet.princessconnect.v2.playerprefs.xml`

3. 在hoshino中禁用插件`pcrjjc3-tw`，并启用插件`pcrjjc_tw_new`，重启bot即可

## 重点注意

1. 和pcrjjc2一样，由于使用了不验证ssl的方式，因此可能产生ssl的验证warning [issue #7](https://github.com/azmiao/pcrjjc3-tw/issues/7)，可采用在hoshino文件夹下的`aiorequests.py`文件内加上几行：
    ```
    from requests.packages.urllib3.exceptions import InsecureRequestWarning
    requests.packages.urllib3.disable_warnings(InsecureRequestWarning)
    ```
    来禁止该warning显示

2. 本插件现已支持每个群友自定义头像框，默认为彩色头像框（为[前川未来佬](https://github.com/shirakami-fubuki)从不知道什么鬼鬼地方使劲抠出来的彩框2333），其余rank框均为游戏解包抠出来的原图。

    如果你需要自己添加其他头像框也是没问题滴，直接把图片扔进本目录下的/img/frame/文件夹里即可，并且不用重启hoshino即可，大多数常见的图片格式一般都行，会自动转RGBA所以一般来说不用担心

3. 本插件现已支持自动更新版本号，妈妈再也不用担心我每次游戏版本更新时，都得手动改插件的版本号再重启hoshino了

4. 若运行过程中出现`TypeError: __init__() got an unexpected keyword argument 'strict_map_key'`报错，为依赖问题，请在终端中进行如下操作，一行一行依次复制执行，过程中提示是否卸载，选择Y：

   ```
   pip uninstall msgpack_python
   pip uninstall msgpack
   pip install msgpack~=1.0.2
   ```

5. 本插件主要适配新版hoshino，但也兼容了部分旧版hoshino，如遇问题请更新星乃本体，如果实在不方便更新可以提交issue反馈等待适配。

6. 不想要推送功能的，维护组可以直接使用命令全局禁用推送功能

## 命令

注：@BOT为@机器人

|      关键词      |               说明                |
|:-------------:|:-------------------------------:|
|   竞技场绑定 uid   |             绑定竞技场信息             |
|    竞技场订阅状态    |             查看绑定状态              |
|    删除竞技场绑定    |             删除绑定的信息             |
|   竞技场查询 uid   |      查询竞技场简要信息（绑定后无需输入uid）      |
|   详细查询 uid    |      查询账号详细信息（绑定后无需输入uid）       |
|    启用竞技场订阅    |     启用战斗竞技场排名变动推送，全局推送启用时有效     |
|    停止竞技场订阅    |          停止战斗竞技场排名变动推送          |
|   启用公主竞技场订阅   |     启用公主竞技场排名变动推送，全局推送启用时有效     |
|   停止公主竞技场订阅   |          停止公主竞技场排名变动推送          |
|     竞技场历史     | 查询战斗竞技场变化记录（战斗竞技场订阅开启有效，可保留10条） |
|    公主竞技场历史    | 查询公主竞技场变化记录（公主竞技场订阅开启有效，可保留10条） |
|     查询头像框     |       查看自己设置的详细查询里的角色头像框        |
|     更换头像框     |        更换详细查询生成的头像框，默认彩色        |
|     查询群数      |           查询bot所在群的数目           |
|   查询竞技场订阅数    |           查询绑定账号的总数量            |
| @BOT全局启用竞技场推送 |     启用所有群的竞技场排名推送功能(仅限维护组)      |
| @BOT全局禁用竞技场推送 |         禁用所有推送功能(仅限维护组)         |
|  @BOT清空竞技场订阅  |        清空所有绑定的账号(仅限维护组)         |

## 更新日志

2023-06-17  v0.0.2-beta 适配新版台服竞技场查询，感谢各位大佬

2023-05-10  v0.0.1-beta 测试版本

<details>
<summary>更以前的更新日志</summary>

（无）

</details>

## 来自电线佬的详细查询图片预览

![4@{%Z%591B` YE1%}H0E7@1](https://user-images.githubusercontent.com/71607036/154960896-1d183705-0805-4f80-9cf2-6de13d35c5c3.jpg)

![FQ~} OTM$L20L6DAEI~RN`K](https://user-images.githubusercontent.com/71607036/154960912-6fd4f1fb-df38-4ef6-997c-af01b71810f4.PNG)