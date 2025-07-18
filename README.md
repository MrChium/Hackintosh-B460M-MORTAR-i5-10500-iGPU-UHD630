
## 微星B460M迫击炮 MSI-B460M-MORTAR+i5-10500+iGPU-UHD630

### 硬件配置

|  配置   | 型号  |
|  ----  | ----  |
| CPU  | I5-10500 |
| 主板  | B460M 迫击炮 |
| 内存  | 威刚2666 8G*4 |
| 显卡  | I5-10500 核显 UHD630  |

### CPU支持
- [x] 支持所有10代核显为UHD630的CPU
- [x] 无核显带F的10代CPU，有以下免驱独显也可以（但无法使用核显加速）

### 显卡支持
- [x] 支持仅有CPU核显的UHD630显卡
- [x] 支持AMD独显 RX 470/480/570/570X/580/580X/590 系列显卡
- [x] 支持AMD独显 RX 5500/5600/5700 系列显卡(需使用专用config.plist)
> PS: 使用独显的需在BIOS里强制打开CPU核显（高级 -> 内建显示配置 -> 集成显卡多显示器(IGD Multi-monitor) -> 允许），否则核显硬件解码失效，只使用核显的可以忽略

### BIOS版本

当前BIOS版本：7C82v16 &nbsp;&nbsp; [BIOS下载地址](https://www.msi.cn/Motherboard/MAG-B460M-MORTAR/support)

### BIOS设置

* OC -> CPU 特征 -> Intel 虚拟化技术：允许
* OC -> CPU 特征 -> Intel VT-D 技术：禁止
* OC -> CPU 特征 -> CFG锁定：禁止
* 安全 -> 安全引导 -> 安全启动：禁止
* 设置 -> 高级 -> 集成显卡多显示器：允许（否则核显硬件解码失效，只使用核显的可以忽略）
* 设置 -> 高级 -> 唤醒事件设置 -> 唤醒事件管理：BIOS
* 设置 -> 高级 -> 唤醒事件设置 -> 即时（RTC）闹铃唤醒：禁止
* 设置 -> 高级 -> 唤醒事件设置 -> PCIE设备唤醒：禁止
* 设置 -> 高级 -> 唤醒事件设置 -> USB设备从S3/S4/S5唤醒：禁止
* 设置 -> 高级 -> 唤醒事件设置 -> PS/2鼠标从S3/S4/S5唤醒：禁止
* 设置 -> 高级 -> 唤醒事件设置 -> USB键盘从S3/S4/S5唤醒：禁止
* 设置 -> 高级 -> 电源管理设置 -> ErP Ready：禁止
* 设置 -> 高级 -> 电源管理设置 -> AC电源掉电再来电状态：关机
* 设置 -> 高级 -> 电源管理设置 -> 系统供电故障保护：禁止
* 设置 -> 高级 -> 电源管理设置 -> USB Standby Power at S4/S5：禁止

### EFI

OpenCore: 1.0.5

EFI下载地址: [Download](https://github.com/myqqiu/Hackintosh-B460M-MORTAR-i5-10500-iGPU-UHD630/releases)


### 系统安装
* 建议使用 【黑果小兵】macOS 安装镜像进行安装

* 若安装镜像卡加号或其它异常无法安装，可使用本EFI替换安装镜像的EFI进行尝试
(本EFI请使用config_install.plist配置文件，即删除原config.plist后重命名config_install.plist为config.plist即可)

* 系统安装成功后，替换为本EFI默认的config.plist文件即可
* 若使用4K显示器，请将 "UIScale" 的值修改为 "Ag==" 以获得最佳ui体验

```
<key>UIScale</key>
<data>Ag==</data>
```


### 功能测试
- [x] 睡眠/唤醒
- [x] 所有USB端口
- [x] 核显硬件加速
- [x] 板载声卡
- [x] 板载网卡

### 板载网卡设置
* 系统偏好设置 -> 网络 -> 以太网（高级） -> 硬件 -> 配置:手动, 速度:100baseTX(千兆网络环境可选择1000baseT), 双工:全双工, MTU:标准1500

### 关于睡眠的问题
* 提高系统稳定性，修复关机USB不断电的问题
* 按上文BIOS设置关闭USB唤醒，睡眠后短按电源键唤醒
* 睡眠在放弃键盘和鼠标唤醒方式后，使用短按电源键方式唤醒睡眠可实现完美睡眠
> PS: 若睡眠有问题的可使用 Hackintool 工具，切换到电源选项，点击下面的螺丝刀图标修复

### 关于Mac序列号的问题
* 下载 OpenCore Configurator for Mac，打开 PlatformInfo -> Model Lookup | Check Coverage 右侧选择 iMac20,1 机型（生成你的唯一硬件UUID），然后 Save as (另存为) config.plist
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
        <string>C02047501CDPHCDAD</string>
        <key>ProcessorType</key>
        <integer>4105</integer>
        <key>ROM</key>
        <data>ESIzRFVm</data>
        <key>SpoofVendor</key>
        <true/>
        <key>SystemMemoryStatus</key>
        <string>Auto</string>
        <key>SystemProductName</key>
        <string>iMac20,1</string>
        <key>SystemSerialNumber</key>
        <string>C02DQSZFPN5T</string>
        <key>SystemUUID</key>
        <string>C567A1A9-9233-4D4D-B021-E1F38B112F33</string>
    </dict>
```

### Win+Mac双系统解决Win系统时间时差问题
* 在Windows下运行
```
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_DWORD /d 1
```

### 设置默认启动项
* 在启动选择界面，先选中要启动的项，然后按键盘的 Ctrl + Enter (回车键) 进入系统，下次重启后默认就选中该项了

### Win+Mac双系统MacOS升级到12及以后版本卡的问题
* 出现该问题主要是“聚焦”搜索（Spotlight）在后台重建索引，占用资源极大（mds_stores的进程CPU占用极高）导致的。
> 1、选择系统菜单“系统设置”。<br>
> 2、点击菜单中的“聚焦”，选择“隐私”。<br>
> 3、将你Finder中左侧位置下的Windows分区磁盘（NTFS,FAT32等）拖移到“聚焦”隐私位置列表中，或者点按添加按钮 (+)，然后选择要添加的磁盘。<br>
> 4、如果你不需要此功能可以将除系统盘外的所有磁盘都加入隐私列表中。