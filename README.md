
## 微星B460M迫击炮 MSI-B460M-MORTAR+i5-10500+iGPU-UHD630

### 硬件配置

|  配置   | 型号  |
|  ----  | ----  |
| CPU  | I5-10500 |
| 主板  | B460M 迫击炮 |
| 内存  | 威刚2666 8G*2 |
| 显卡  | I5-10500 核显 UHD630  |

### BIOS版本

当前BIOS版本：7C82v12 [BIOS下载地址](https://cn.msi.com/Motherboard/support/MAG-B460M-MORTAR)

### EFI

OpenCore: 0.6.2

macOS version: 10.15.6

EFI下载地址: [Download](https://github.com/myqqiu/Hackintosh-B460M-MORTAR-i5-10500-iGPU-UHD630/releases)


### 系统安装
* 建议使用 【黑果小兵】macOS Catalina 10.15.6 安装镜像进行安装

* 若安装镜像卡加号或其它异常无法安装，可使用本EFI替换安装镜像的EFI进行尝试
(本EFI请使用config_install.plist配置文件，即删除原config.plist后重命名config_install.plist为config.plist即可)

* 系统安装成功后，替换为本EFI默认的config.plist文件即可

### 功能测试
- [x] 睡眠/唤醒
- [x] 所有USB端口
- [x] 核显硬件加速
- [x] 板载声卡
- [x] 板载网卡

### 板载网卡设置
* 系统偏好设置 -> 网络 -> 以太网（高级） -> 硬件 -> 配置:手动, 速度:100baseTX(千兆网络环境可选择1000baseT), 双工:全双工, MTU:标准1500

### 关于睡眠的问题
* BIOS默认关闭了USB唤醒，睡眠后需按电源键唤醒
* 需鼠标键盘唤醒的，在BIOS里设置USB唤醒为允许即可（已修复开启USB唤醒时，关机后不断电操作鼠标或键盘会重新启动的问题）
> PS: 若睡眠有问题的可使用 Hackintool 工具，切换到电源选项，点击下面的螺丝刀图标修复

### 关于Mac序列号的问题
* 下载 OpenCore Configurator for Mac，打开 PlatformInfo -> Model Lookup | Check Coverage 右侧选择 iMac19,1 机型（生成你的唯一硬件UUID），然后 Save as (另存为) config.plist
* 在config.plist文件中找到如下代码，记录MLB、SystemSerialNumber和SystemUUID的值并记住它，更新EFI时，用你记录的值替换 /OC/config.plist 下对应的值即可
> PS: 还可使用 Hackintool 工具（系统 -> 序列号生成器）来获取三码

```
<key>PlatformInfo</key>
<dict>
    <key>Generic</key>
    <dict>
        <key>AdviseWindows</key>
        <false/>
        <key>MLB</key>
        <string>C02935130J9LNV9UE</string>
        <key>ROM</key>
        <data></data>
        <key>SpoofVendor</key>
        <true/>
        <key>SystemProductName</key>
        <string>iMac19,1</string>
        <key>SystemSerialNumber</key>
        <string>C02Z906MJV3Q</string>
        <key>SystemUUID</key>
        <string>FF264005-A041-4841-B17A-263B39D76BA0</string>
    </dict>
```

### Win+Mac双系统解决Win系统时间时差问题
* 在Windows下运行
```
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_DWORD /d 1
```

### 设置默认启动项
* 在启动选择界面，先选中要启动的项，然后按住键盘的 Ctrl + Enter (回车键) 进入系统，下次重启后默认就选中这个项了。
