<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="在小米平板 5 上运行 Windows 11">

# 在小米平板 5 上运行 Windows

## 为平板电脑获取 root 权限
> [!NOTE]
> **如果您已经获取 root 权限，请跳过此步骤并转到下一页**

### 先决条件
- ```Brain```

- [```Android 启动备份```](/guide/English/1-partition-en.md#Make-a-backup-of-your-existing-boot-image)（您在指南第一页备份的）

### 修补启动映像
- 将 ```normal_boot.img``` 文件从 ```platform tools``` 文件夹复制到平板电脑上

- 下载并安装平板电脑上的 [Magisk 应用程序](https://github.com/topjohnwu/Magisk/releases/latest)

- 打开 Magisk 应用程序并点击“安装”按钮。选择“选择并修补文件”选项，找到您复制到平板电脑的“normal_boot.img”文件。点击“开始”按钮并等待修补过程完成。

- 将“magisk_patched....img”文件从平板电脑上的“下载”文件夹复制到计算机上的“平台工具”文件夹。

### 重启至 fastboot
- 重启时按住 **`降低音量`** 按钮，将 NABU 启动至 **fastboot**

- 使用电缆将其连接到 PC/笔记本电脑

- 返回之前打开的命令提示符窗口

### 刷新修补的启动映像
> 将 `magisk_patched.img` 替换为实际的 ```magisk_patched.img``` 名称/路径。
```cmd
fastboot flash boot magisk_patched.img
```

### 重启至 Android
```cmd
fastboot reboot
```

#### 完成设置
- 再次打开 **Magisk** 应用。
- 按照屏幕上的说明操作，您的设备应在几秒钟后重启。

### 复制 root 启动映像
> 设备启动后

- 手机屏幕上可能会出现 Shell 的超级用户请求。如果出现，请授予其访问权限。
```cmd
adb shell "su -c cp dev/block/by-name/boot /sdcard/root.img" & adb pull /sdcard/root.img
```

### [下一步：安装 Windows](/guide/English/3-install-en.md)
