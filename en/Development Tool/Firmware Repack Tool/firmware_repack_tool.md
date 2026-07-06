# Firmware Repack Tool

<font color=red>**Note that the following operations are all performed on the PC (x86-64 architecture).**</font>

1. Install the necessary packages: ```sudo apt-get install lib32stdc++6```

2. Download the secondary packaging tool: [firefly-linux-repack](https://drive.google.com/drive/folders/1wEEnUC0S74RolTnD28FeODva0KUwrgyF?usp=sharing)

3. Unzip the secondary packaging tool:

    ```
    tar -xzf firefly-linux-repack.tgz
    cd firefly-linux-repack
    ```

    The directory is as follows:
    ```
    firefly-linux-repack
        ├── bin
        │   ├── afptool
        │   └── rkImageMaker
        ├── pack.sh # packaging script
        ├── Readme_en.md
        ├── Readme.md
        └── unpack.sh # unpack script
    ```

4. Unpacking operation: Copy the official Ubuntu firmware to the `firefly-linux-repack` root directory, rename it to `update.img`, and execute the unpacking script `unpack.sh`. After the unpacking is complete, the partition files are in the `output` directory.

    ```
    mv /path/to/ROC-RK3566-PC_Ubuntu18.04-r21156_v1.2.4a_220519.img update.img
    ./unpack.sh
    ```

5. Packaging operation: Keep the current directory structure and file name unchanged, connect the mobile hard disk to the PC, replace `output/Image/rootfs.img` with the Ubuntu rootfs exported earlier, and then execute the packaging script `pack.sh` .

    ```
    cp /media/customer/1878-4615/Firefly_Ubuntu_18.04.6_rootfs.img /path/to/firefly-linux-repack/output/Image/rootfs.img
    ./pack.sh
    ```

6. The new full firmware is `new_update.img` in the current directory.
