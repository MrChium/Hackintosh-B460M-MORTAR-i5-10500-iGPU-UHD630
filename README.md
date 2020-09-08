
## 微星B460M迫击炮 MSI-B460M-MORTAR+i5-10500+iGPU-UHD630

### 硬件配置

|  配置   | 型号  |
|  ----  | ----  |
| CPU  | I5-10500 |
| 主板  | B460M 迫击炮 |
| 内存  | 威刚2666 8G*2 |
| 显卡  | I5-10500 核显 UHD630  |

### EFI 

OpenCore: 0.6.1

macOS version: 10.15.6

支持 macOS 11 Big Sur

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
> 系统偏好设置 -> 网络 -> 以太网（高级） -> 硬件 -> 配置:手动, 速度:100baseTX, 双工:全双工, MTU:标准1500

### Win+Mac双系统解决Win系统时间时差问题
> 在Windows下运行
```
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_DWORD /d 1
```

### 设置默认启动项
> 在启动选择界面，先选中要启动的项，然后按住键盘的 Ctrl + Enter (回车键) 进入系统，下次重启后默认就选中这个项了。
