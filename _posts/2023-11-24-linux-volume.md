---
title: "Extending Logical Volume in Ubuntu"

categories:
  - Notes
tags:
  - [lv, pv, vg]

permalink: /categories/notes/3

toc: true
toc_sticky: true

date: 2023-11-24
last_modified_at: 2023-11-24
---

I found the machine for model serving in my office has insufficient volumn avaiable. I started my day by extending logical volume.
Here's what I did:

### 1. Check current volume status

```shell
# fdisk -l
```

![img](/assets/images/posts_img/notes/3/image.png)

I found that I have 2 hard drives(/dev/sda, /dev/sdb) but those are not fully utilized as logical volumes.

```shell
# pvdisplay
# vgdisplay
# lvdisplay
```

![img](/assets/images/posts_img/notes/3/image-1.png)

### Adding physical volume to volume group

Next, I created PV for the /dev/sdb1 partition

```shell
sudo pvcreate /dev/sdb1
```

![img](/assets/images/posts_img/notes/3/image-2.png)

After successfully creating PV, I added it to the existing VG

```shell
# vgextend [vg-name] [pv-name]
```

![img](/assets/images/posts_img/notes/3/image-3.png)

I can see VG size is extended about 1.06TB

### Extending LV and resizing the file system

To fully utilize the newly added space, I extended the LV
```shell
# lvextend -l +100%FREE [lv-path]
```
![img](/assets/images/posts_img/notes/3/image-4.png)

Lastly, I resized the filesystem mounted on '/'

```shell
# sudo resize2fs [device]
```
![img](/assets/images/posts_img/notes/3/image-5.png)
