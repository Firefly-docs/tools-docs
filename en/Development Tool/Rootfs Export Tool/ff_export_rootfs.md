# Export device rootfs

<font color=red>**Note that the following operations are all performed on the device side.**</font>

1. In the Ubuntu environment of the device, install `fireflydev`:

	```
	sudo apt update
	sudo apt install fireflydev
	```

2. After installing `fireflydev`, you can use the `ff_export_rootfs` script to export the root file system
<font color=red>**Exporting to external storage devices or the /userdata/ root directory is allowed only; exporting to other directories on the device is prohibited.！**</font>

	* It is recommended to use a mobile hard disk with a larger capacity

    * The exporter does things like `apt clean` to reduce the filesystem size

    * Export the root file system, for example, to the `/media/firefly/AC91-C4AE/` directory (it takes a while):
	```
    ff_export_rootfs /media/firefly/AC91-C4AE/
	```

    * Compress the file system, delete unnecessary blank space to reduce memory resource usage:
    ```
    # Some customers said that the size of the exported rootfs is 3.3G, but actually only 3G is used, because the rootfs is not compressed
    e2fsck -p -f Firefly_Ubuntu_18.04.6_rootfs.img
    resize2fs -M Firefly_Ubuntu_18.04.6_rootfs.img
    ```

## Next step: firmware repack

After exporting rootfs, only the rootfs image file is generated. To create a complete flashable firmware image, use the firmware repack tool on the PC for secondary packaging. See: [Firmware Repack Tool](../Firmware%20Repack%20Tool/firmware_repack_tool.md).
