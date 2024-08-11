<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">

# 在 Xiaomi Pad 5 上运行 Windows

## 安装

### 前提条件
- ```解锁的引导加载程序``` - (如果你的 bootloader 被锁定，而你不知道如何解锁，请使用 [this](unlock-bootloader.md) 指南)

- ```大脑```

- [```恢复映像```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/recovery.img)

- [```Android 平台tools```](https://developer.android.com/studio/releases/platform-tools)

### 注意：
>[!NOTE]
> 您可以使用任何 Android 进行双启动 - MIUI/Hyper OS 或任何自定义 ROM

> [!Warning]
> 您的所有数据都将被删除！如有需要，请立即备份。
>
> 如果您认为犯了错误，请不要重新启动平板电脑，请在 [Telegram 聊天](https://t.me/nabuwoa) 中寻求帮助
>
> **请不要在 YouTube 或任何其他平台上使用过时的视频指南！这些视频已经过时，使用它们可能会损坏您的设备！如果您需要视频指南，请使用 [ArtoSeVeN](https://www.youtube.com/channel/UCYjwfxlYlJ7Nnzv01oszQvA) 的 [新视频指南](https://youtu.be/BbgTbTGbXYg)**

### 对设备进行分区并备份启动
> [!NOTE]
> 不知道如何开始？解压下载的 [```Android 平台工具```](https://developer.android.com/studio/releases/platform-tools)，然后以管理员身份打开 ```命令提示符``` 或 ``powershell`` 并运行以下命令，将 `"path\to\platform-tools"` 替换为平台工具文件夹的实际路径
```cmd
cd "path\to\platform-tools"
```
> 在整个指南中使用此窗口。不要关闭它。

#### 重新启动到 **fastboot**
- 重新启动时按住 **`volume down`** 按钮，将 NABU 启动到 **fastboot**

- 使用电缆将其连接到 PC/笔记本电脑

#### 启动经过修改的恢复
> 将 **path\to\recovery.img** 替换为恢复映像的实际路径
```cmd
fastboot boot path\to\recovery.img
```

### 对设备进行分区
> 将 **$** 替换为您希望 Windows 拥有的存储量（不要添加 GB，只需输入数字）
>
> 如果它要求您再次运行它，请执行此操作
```sh
adb shell partion $
```

### 备份您现有的启动映像
```cmd
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/boot$(getprop ro.boot.slot_suffix) of=/tmp/normal_boot.img" && adb pull /tmp/normal_boot.img
```

#### 检查 Android 是否仍可启动
> 重新启动以检查 Android 是否仍可工作。如果无法启动，请清除恢复中的所有数据并重试。

```cmd
adb reboot
```

### [下一步：获取 Root](/guide/English/2-rootguide-en.md)
