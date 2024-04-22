# 系统选择
- TrueNAS  
- 群晖
- 公司目前用的是[[浪潮媒资管理系统]]NAS配置
## TrueNAS
学习资料：
https://www.truenasscale.com

### TrueNAS SCALE小白级安装设置教程（物理机）
教程源地址：
URL:https://www.truenasscale.com/2021/12/09/5.html
#### 下载镜像

浏览器打开官网[truenas.com](https://www.truenas.com/)  
#### 制作启动盘


下载好镜像后，推荐使用[rufus](https://rufus.ie/zh/)制作安装盘  
[![](https://www.truenasscale.com/usr/uploads/2021/12/3050797825.png)](https://www.truenasscale.com/usr/uploads/2021/12/3050797825.png)

如果你的NAS支持UEFI的话记得分区类型要选GPT，然后点击开始。提示写入模式选择**DD模式**  
[![](https://www.truenasscale.com/usr/uploads/2021/12/500850258.png)]
后面全部点**是**就可以了

#### 设置BIOS U盘启动

NAS插入U盘开机，按F11（这里根据自己的主板查询选择启动项的按键），选择刚刚做的U盘，等待进入安装界面。

#### 安装系统

[![](https://www.truenasscale.com/usr/uploads/2021/12/243701706.png)](https://www.truenasscale.com/usr/uploads/2021/12/243701706.png)

选择**Install/Upgrade**  
然后选择你要把系统安装到的硬盘，按空格选择，回车确定  
[![](https://www.truenasscale.com/usr/uploads/2021/12/1053706883.png)](https://www.truenasscale.com/usr/uploads/2021/12/1053706883.png)

[![请输入图片描述](https://www.truenasscale.com/usr/uploads/2021/12/2534987282.png)](https://www.truenasscale.com/usr/uploads/2021/12/2534987282.png)

[请输入图片描述](https://www.truenasscale.com/usr/uploads/2021/12/2534987282.png)

选择**yes**后面也选择**yes**

[![](https://www.truenasscale.com/usr/uploads/2021/12/865270335.png)](https://www.truenasscale.com/usr/uploads/2021/12/865270335.png)

  
选择创建SWAP  **Create swap**  
[![](https://www.truenasscale.com/usr/uploads/2021/12/1859371221.png)
设置root的密码

然后根据提示继续安装，安装完成后拔掉U盘重启，进入系统继续安装





### TrueNAS SCALE基础设置
教程源地址：
URL:https://www.truenasscale.com/2021/12/09/51.html
#### 设置语言，时区

[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/247625140.png)](https://www.truenasscale.com/usr/uploads/2021/12/247625140.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/247625140.png)

  
点击**System Settings**，然后点击**General**  
[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/371954605.png)

image.png

](https://www.truenasscale.com/usr/uploads/2021/12/371954605.png)

点击**Settings**

[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/2515500455.png)](https://www.truenasscale.com/usr/uploads/2021/12/2515500455.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/2515500455.png)

点击Language输入zh选择**simplified Chinese**下面Timezone选择**Asia/Shanghai**

#### 设置网络

[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/2174425922.png)](https://www.truenasscale.com/usr/uploads/2021/12/2174425922.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/2174425922.png)

点击侧栏网络，点击**全局配置**的**设置**  
[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/1251831078.png)](https://www.truenasscale.com/usr/uploads/2021/12/1251831078.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/1251831078.png)

填上**域名服务器（DNS）** 和 **IPv4 默认网关**  
有HTTP代理的可以填上代理

#### 创建池或导入池

点击侧栏**储存**

##### 导入池

如果你以前用过zfs(freenas/truenas core/truenas scale等)，可以直接导入以前的池  
[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/3673677494.png)](https://www.truenasscale.com/usr/uploads/2021/12/3673677494.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/3673677494.png)

[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/3417553413.png)](https://www.truenasscale.com/usr/uploads/2021/12/3417553413.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/3417553413.png)

选择要导入的池下一步确认后等待导入即可。

##### 创建池

[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/1982679393.png)](https://www.truenasscale.com/usr/uploads/2021/12/1982679393.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/1982679393.png)

点击创建池

[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/632179579.png)](https://www.truenasscale.com/usr/uploads/2021/12/632179579.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/632179579.png)

输入名字，选择你要组RAID的硬盘，然后选择RAID类型，点击创建。  
如果遇到警告，可以勾上强制

###### RAID介绍

条带：与RAID0类似，不过可以不同大小的硬盘组  
镜像：与RAID1类似，磁盘镜像，至少需要两个磁盘。  
RAIDZ1：与RAID5类似，一重奇偶校验，至少需要三块磁盘；可以坏一块硬盘不丢数据。容量和速度为N-1(N为硬盘数量)  
RAIDZ2：与RAID6类似，双重奇偶校验，至少需要四个磁盘；可以坏2块硬盘不丢数据。容量和速度为N-2(N为硬盘数量)  
RAIDZ3：ZFS特有的，三重奇偶校验，至少需要5个磁盘；可以坏3块盘不丢数据。容量和速度为N-3(N为硬盘数量)

#### 创建SMB用户

由于安全问题，默认的root用户禁止使用SMB，所以要创建用户。

[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/1411159048.png)](https://www.truenasscale.com/usr/uploads/2021/12/1411159048.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/1411159048.png)

点击**证书**，点击**本地用户**

[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/836832891.png)](https://www.truenasscale.com/usr/uploads/2021/12/836832891.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/836832891.png)

点击**关闭**。然后点击右上角**添加**

[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/276973190.png)](https://www.truenasscale.com/usr/uploads/2021/12/276973190.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/276973190.png)

如图输入名字（英文），密码  
[![image.png](https://www.truenasscale.com/usr/uploads/2021/12/331334479.png)](https://www.truenasscale.com/usr/uploads/2021/12/331334479.png)

[image.png](https://www.truenasscale.com/usr/uploads/2021/12/331334479.png)

勾上**Samba认证**，最后保存即可
