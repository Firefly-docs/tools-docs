# 导出 rootfs

<font color=red>**注意以下操作均在设备端上操作！**</font>

1. 在设备的 Ubuntu/Debian 环境下，安装 `fireflydev`：

	```
	sudo apt update
	sudo apt install fireflydev
	```

2. 安装 `fireflydev` 后，就能使用 `ff_export_rootfs` 脚本导出根文件系统
<font color=red>**仅允许导出到外部存储设备或 /userdata/根目录，禁止导出至设备的其他目录！**</font>

	* 建议使用容量较大的移动硬盘

	* 导出工具会执行 `apt clean` 等操作以减小文件系统大小

	* 将根文件系统导出，例如导出到 `/media/firefly/AC91-C4AE/` 目录（需要等待一定时间）：
	```
    ff_export_rootfs /media/firefly/AC91-C4AE/
	```

    * 压缩文件系统，删除不必要的空白空间以减少存储器资源的占用：
    ```
    # 有部分客户说导出的 rootfs 大小为 3.3G，可实际只用了 3G，原因是没有对 rootfs 进行压缩
    e2fsck -p -f Firefly_Ubuntu_18.04.6_rootfs.img
    resize2fs -M Firefly_Ubuntu_18.04.6_rootfs.img
    ```


