---
id: Swap-Partition
title: Swap Partition
---

# Create/Edit Swap Partition

![Tested Platform](https://img.shields.io/badge/RockyLinux\_9.1-Tested-green?style=flat\&logo=RockyLinux)

---

## Set-up Steps

### 1.  Check the free space

    ```bash
    free -m
    ```
### 2.  Create a partition

    ```bash
    dd if=/dev/zero of=SWAPFILE_DIRECTORY bs=COUNT count=SPACE
    ```

:::tip
`COUNT` could be `1K` \ `1M` \ `1G` etc.

`SPACE` depends on your need, e.g. `1024`
:::

### 3.  Formation

    ```bash
    mkswap $SWAPFILE_DIRECTORY
    chmod -R 600 $SWAPFILE_DIRECTORY
    ```


### 4.  Turn it on

    ```bash
    swapon $SWAPFILE_DIRECTORY
    ```


### 5. Enable it permanently
   1.  Open /etc/fstab in the editor.

       ```bash
       vim /etc/fstab
       ```
   2.  Add the line to it

       ```bash
       $SWAPFILE_DIRECTORY swap swap defaults 0 0
       ```

