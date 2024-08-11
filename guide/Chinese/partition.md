在小米平板 5 上运行 Windows
安装
先决条件
解锁引导程序 -（如果您的引导程序已锁定并且您不知道如何解锁，请使用本指南）

大脑

恢复映像

Android 平台工具

注意：
注意

您可以使用任何 Android 进行双启动 - MIUI/Hyper OS 或任何自定义 ROM

警告

您的所有数据都将被删除！如有需要，请立即备份。

如果您认为自己犯了错误，请不要重新启动平板电脑，请在 Telegram 聊天中寻求帮助

请不要在 YouTube 或任何其他平台上使用过时的视频指南！这些视频已经过时，您可能会使用它们损坏您的设备！如果您需要视频指南，请使用 ArtoSeVeN 的此新视频指南

对设备进行分区并备份启动
注意

不知道如何开始？解压下载的 Android 平台工具，然后以管理员身份打开命令提示符或 powershell 并运行以下命令，将“path\to\platform-tools”替换为平台工具文件夹的实际路径

cd “path\to\platform-tools”
在整个指南中使用此窗口。不要关闭它。

重启至 fastboot
重启时按住音量减小按钮，将 NABU 启动至 fastboot

使用电缆将其连接到 PC/笔记本电脑

启动经过修改的恢复
将 path\to\recovery.img 替换为恢复映像的实际路径

fastboot boot path\to\recovery.img
对设备进行分区
将 $ 替换为您希望 Windows 拥有的存储量（不要添加 GB，只需写入数字）

如果它要求您再次运行它，请这样做

adb shell 分区 $
备份您现有的启动映像
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/boot$(getprop ro.boot.slot_suffix) of=/tmp/normal_boot.img" && adb pull /tmp/normal_boot.img
检查 Android 是否仍可启动
重启以检查 Android 是否仍可运行。如果无法启动，请清除恢复中的所有数据，然后重试。

adb reboot
