# 固件打包工具

<font color=red>**注意以下操作均在 PC 机端（x86-64 架构）上操作！**</font>

1. 安装必要的软件包：```sudo apt-get install lib32stdc++6```

2. 下载二次打包工具：[firefly-linux-repack](https://pan.baidu.com/s/1qiOqutl4WW1OFBpom8w6nA)（提取码：1234）

3. 解压二次打包工具：

    ```
    tar -xzf firefly-linux-repack.tgz
    cd firefly-linux-repack
    ```

    目录如下：
    ```
    firefly-linux-repack
        ├── bin
        │   ├── afptool
        │   └── rkImageMaker
        ├── pack.sh # 打包脚本
        ├── Readme_en.md
        ├── Readme.md
        └── unpack.sh # 解包脚本
    ```

4. 解包操作： 把官方发布的 Ubuntu 固件拷贝到 `firefly-linux-repack` 根目录，重命名为 `update.img`，执行解包脚本 `unpack.sh`。解包完成后，各分区文件在 `output` 目录下。

    ```
    mv /path/to/ROC-RK3566-PC_Ubuntu18.04-r21156_v1.2.4a_220519.img update.img
    ./unpack.sh
    ```

5. 打包操作：保持当前目录结构，文件名等不变，接入移动硬盘到 PC 机，把前面导出的 Ubuntu rootfs 替换 `output/Image/rootfs.img`，然后执行打包脚本 `pack.sh`。

    ```
    cp /media/customer/1878-4615/Firefly_Ubuntu_18.04.6_rootfs.img /path/to/firefly-linux-repack/output/Image/rootfs.img
    ./pack.sh
    ```

6. 新的完整固件为当前目录的 `new_update.img`。
