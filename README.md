# uwe5622_driver_neo

uwe5622的内核驱动源码，从 fork 的仓库中，修改了：
1. 过时的内核 API 调用，以适配新的内核（条件编译保证旧内核兼容）
2. 被移除的优先级设置策略
3. 不适配新版本设备树的一些逻辑

注意：
本驱动需搭配本人其他有关仓库对内核源码树的修改（因为有些东西是官方零零散散添加到源码树里面的，缺少一些文件会导致编译失败或模块工作异常），具体涉及到的有：  
1. /drivers/misc/sunxi-addr/sunxi-addr.c(添加整个sunxi-addr文件夹)
2. /drivers/nvmem/sunxi_sid.c(修改)
3. /net/bluetooth/hci_event.c(修改)  

关于驱动固件：  
如果固件是放在/lib/firmware目录下，可能需要在此目录下新建uwe5622文件夹并把固件迁移进去才能正常加载固件  
  
将会在近期(202606190000UTC+8前)上传完毕所有改动(202606171336UTC+8已上传所有改动,请参阅仓库：https://github.com/LinuxMint-User/orangepi-zero-3-uwe5622-driver-neo-patches)  
本仓库将专注于驱动而不专注于设备，设备树文件的编写请参阅仓库：https://github.com/LinuxMint-User/orangepi-zero-3-dtb-neo  

当前仅测试了 6.18 LTS 版本，从 fork 的 6.11（不包含） 至 6.18（不包含）版本未测试，新版本添加的条件编译均已 6.18 版本为阈值，如有问题请提交 issue 或自行修改阈值。
当前仅测试了 WiFi 功能，蓝牙功能暂未测试(蓝牙功能已测试正常202606162251UTC+8)
目前驱动仅仅为能跑阶段，一些内存越界行为将在未来修复
对于香橙派 Zero 3 来说，设备树文件需要从新内核源码编译产物中获得并根据旧设备树做适当修改，详见另一个仓库。

Fork 仓库的 README 内容：

# uwe5622_driver

uwe5622的内核驱动

从[linux-orangepi](https://github.com/orangepi-xunlong/linux-orangepi/tree/orange-pi-6.6-rk35xx)中复制了6.6版本，升级到了6.11

~~买开发板之前一定要确认关键驱动有没有进内核主线~~
