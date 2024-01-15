# Touchx-Driver
USB version

### 状态指示灯：

参考链接：

https://zhuanlan.zhihu.com/p/481123867

| 颜色 | 持续绿色 | 闪烁绿色 | 闪烁黄色       | 持续黄色       |
| ---- | -------- | -------- | -------------- | -------------- |
| 意义 | 正确校准 | 等待校准 | 等待重启和开机 | 待机或等待状态 |



### 安装驱动：

安装参考链接：

https://blog.csdn.net/zp1127zp/article/details/108532045

https://github.com/bharatm11/Geomagic_Touch_ROS_Drivers

https://fsuarez6.github.io/projects/geomagic-touch-in-ros/

官方驱动链接：

https://support.3dsystems.com/s/article/OpenHaptics-for-Linux-Developer-Edition-v34?language=en_US



官方链接里包含两个压缩包

分别为OpenHaptic的环境配置文件与Touch的驱动文件。



名为(openhaptics+版本号)的压缩包为环境配置文件，解压后进去执行

```bash
sudo ./install
```



另外一个压缩包是名为(TouchDriver+日期)的驱动

根据文件`installation+Instructions_2022.pdf`文件内容进行安装

#### step1-2 

注意sudo权限问题。

#### step3 

一般高版本ubuntu自带qt。

#### step4-6 

是创建文件夹config用于保存Touch连接后的配置。

环境变量GTDD_HOME我们可以直接写入/etc/enviroment文件并保存，添加一行

```bash
GTDD_HOME="/usr/share/3DSystems"
```

环境变量的生效需要先注销再重新登入ubuntu系统。

#### step7 

是每次连接Touch需要进行的操作，一个是检测haptics设备的端口号（只有连上设备才会有形如/dev/ttyACM*的输出），需要在解压后的TouchDriver目录下运行bash ListUSBHapticDevices；一个是给端口赋权限sudo chmod 777 [端口名]。

#### Step8 

在TouchDriver的bin目录下运行

```bash
sudo ./Touch_Setup
```

注意要sudo权限，不然会没法把结果保存到step4-6的config中。

这个程序运行后会出现一个界面，确认设备号和驱动版本有显示后，点击"apply"与"ok"。

接着运行

```bash
sudo ./Touch_Diagnostic
```

对Touch进行标定。前述步骤都没问题的话，这个程序可以正常运行并实时显示Touch的状态。如果出现找不到设备的状态，请确认端口权限给了，然后是否是sudo运行的Touch_Setup。
