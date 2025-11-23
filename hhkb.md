hhkb部分参考原作者的 wiki：  
- [键盘说明](https://github.com/z8806c/nrf52-keyboard/wiki/HHKB-BLE-Keyboard)  
- [固件更新](https://github.com/z8806c/nrf52-keyboard/wiki/HHKB-BLE-Keyboard-UpData)


# HHKB BLE Keyboard

## 键盘描述（[全部工具下载](https://github.com/z8806c/nrf52-keyboard/tree/master/tool)）

* 5 x 14 的60%键盘
* 一个Caps灯和一个RGB状态指示灯
* Type-C接口
* 蓝牙主控为nRF52832
* 拨动开关

## 配置键盘与更改按键配置

> **方式一：在线配置**
> [https://keyboard.lotlab.org/](https://keyboard.lotlab.org/)
> (先看帮助,安装对应的本地服务器)。
>
> **方式二：本地配置工具**
> [Lkb_configurator](https://raw.githubusercontent.com/z8806c/nrf52-keyboard/master/tool/lkb_configurator_setup_1.0.2.0.exe)
> (无需网络,仅支持WIN)。

**预设配列文件：**
* [HHKB原版配列](https://raw.githubusercontent.com/z8806c/nrf52-keyboard/master/tool/HHKB%E5%8E%9F%E7%89%88%E9%85%8D%E5%88%97.json)
* [HHKB右下角增加方向键（个人习惯）](https://raw.githubusercontent.com/z8806c/nrf52-keyboard/master/tool/HHKB-%E4%B8%AA%E4%BA%BA%E4%B9%A0%E6%83%AF.json)

## 系统功能按键说明

在没有USB接入时，按键空闲15秒进入慢速扫描状态，600秒自动进入休眠。
自动休眠后按任意按键即可唤醒；手动休眠后需要组合键开机，插入USB也可以唤醒设备。
如遇无法解决的问题，可以通过拨动开关断电一次来重启键盘。

| 功能 | 按键 | 功能说明 |
| :--- | :--- | :--- |
| 开机 | `Space` + `U` | 开启设备。 |
| 休眠 | `Lshift` + `Rshift` + `P` | 手动进入休眠模式。 |
| 有线/无线切换 | `Lshift` + `Rshift` + `M` | 在USB和无线同时工作时，可以切换有线/无线模式。 |
| 切换蓝牙设备 | `Lshift` + `Rshift` + `Q`/`W`/`E` | 可以在已绑定的蓝牙设备之间进行切换，`Q`/`W`/`E`代表不同蓝牙连接通道 |
| 重启蓝牙广播 | `Lshift` + `Rshift` + `R` | 重新开启蓝牙广播，用于切换设备后进行绑定。 |
| 清空当前蓝牙绑定 | `Lshift` + `Rshift` + `O` | 清空当前蓝牙设备绑定信息。仅清空当前设备，其余绑定设备不会清空。 |
| 输出电量 | `Lshift` + `Rshift` + `H` | 通过键盘输出当前键盘剩余电量。可能无法达到 100% 或者 数值有所波动，这是正常现象。 |

## RGB指示灯颜色表

| 颜色 | 状态 |
| :--- | :--- |
| 白色 | 无任何连接 |
| 青色 | 蓝牙已连接 |
| 天蓝色 | USB已连接 |
| 黄色 | 输入配对密码 |
| 紫红色 | 配对密码输入完毕 |
| 紫色 | 设备休眠 |



# HHKB BLE Keyboard UpData

## 蓝牙固件更新教程（[全部工具下载](https://github.com/z8806c/nrf52-keyboard/tree/master/tool)）

1.  打开烧录工具。
    [wch_nrf_burner.exe](https://raw.githubusercontent.com/z8806c/nrf52-keyboard/master/tool/wch_nrf_burner_setup_1.2.1.1.exe)
2.  直接通过USB连接键盘。

> * 选择配置文件，一般为`nRF54系列(CH554)`。
> * 刷新当前设备列表，并下拉选择连接的键盘。
> * 当前设备列表中`CMSIS-DAP - HTKB Rev.0` 选项。

3.  在“蓝牙固件”栏选择蓝牙核心固件，hex文件(刷入其中一个)。

> * [HHKB_V3固件](https://raw.githubusercontent.com/z8806c/nrf52-keyboard/master/tool/HHKB_V3/nrf52_kbd_sign_with_sd.hex)
> * [HHKB_V4固件(增加多设备切换)](https://raw.githubusercontent.com/z8806c/nrf52-keyboard/master/tool/HHKB_V4/nrf52_kbd_sign_with_sd.hex)

4.  点击烧录按钮，等待烧录完成即可。
5.  如传输出错导致更新失败，重新烧录即可。
6.  烧录完成后，在当前设备列表中查看固件版本号，确认是否刷入成功。

![刷入成功](https://github.com/z8806c/nrf52-keyboard/releases/download/untagged-fe3170baf1db0766387a/HHKB_V4.png)

# USB固件更新教程

> **警示:** 出厂后一般不需要更新USB固件,非必要请勿更新USB。
>
> [WCHISPTool_Setup工具](https://raw.githubusercontent.com/z8806c/nrf52-keyboard/master/tool/WCHISPTool_Setup.exe)
>
> [USB固件](https://raw.githubusercontent.com/z8806c/nrf52-keyboard/master/tool/HHKB_V4/ch554.bin)

# 故障排除

#### 键盘不明原因异常。

> 尝试关闭打开开关一次。

#### 固件异常可烧录完整固件。

> 参照蓝牙固件更新教程先刷入蓝牙引导文件
> [nrf52_bootloader](https://raw.githubusercontent.com/z8806c/nrf52-keyboard/master/tool/HHKB_V3/nrf52_bootloader.hex) (勾选擦拭蓝牙固件)。
>
> 再刷入蓝牙核心文件
> [HHKB_V3固件](https://raw.githubusercontent.com/z8806c/nrf52-keyboard/master/tool/HHKB_V3/nrf52_kbd_sign_with_sd.hex) (不勾选擦拭蓝牙固件)

#### 配置工具无法识别键盘

> 必须开启客户端：[lkb-configurator-server](https://eyun.baidu.com/s/3c3X2Zmw)

#### 更新按键配置后所有按键失效

> 尝试将按键配置还原为默认按键配置。

#### 指示灯忽然亮起变为白色，然后迅速变成蓝色

> 这是蓝牙信号不好的原因

#### 按下CapsLock后，指示灯也会亮起

> 这是正常现象。按下CapsLock后，灯的状态改变了，所有的灯都会亮起5秒，这也就包括了指示灯。

#### Windows 下出现“驱动程序错误”

* 在Windows的设备管理器中删除这个设备，或取消这个设备的绑定
* 重启你的电脑
* 清空键盘绑定信息
* 在电脑上尝试重新连接

#### 如何改善蓝牙连接稳定性

* 蓝牙的信号可能受到多方面因素的影响。你可以尝试以下方法来改善蓝牙信号：
* 将键盘和主机尽可能的靠近
* 降低2.4GHZ的WiFi的发射功率
* 减少空间内其他WiFi和蓝牙设备的存在
* 不要触摸蓝牙模块的天线位置
* 将蓝牙接收器的天线从桌子下方移动到桌子上方
* 更换蓝牙接收器
