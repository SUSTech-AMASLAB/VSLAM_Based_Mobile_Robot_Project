# rtabmap安装与配置

ratbmap wiki：https://github.com/introlab/rtabmap/wiki

官方安装教程：https://github.com/introlab/rtabmap_ros#installation

opencv_contrib安装参考：https://blog.csdn.net/qq_42257666/article/details/123592033



### 1.dependencies安装：

```bash
sudo apt install ros-$ROS_DISTRO-rtabmap ros-$ROS_DISTRO-rtabmap-ros
sudo apt remove ros-$ROS_DISTRO-rtabmap ros-$ROS_DISTRO-rtabmap-ros
```



### 2.可选dependencies：

参考https://github.com/introlab/rtabmap_ros#installation，暂时可以不安装



### 3.在主目录安装rtamap的standalone libraries：

```bash
cd ~
git clone https://github.com/introlab/rtabmap.git rtabmap
cd rtabmap/build
cmake .. 
make -j6
sudo make install
```



### 4.安装rtabmap的ros-pkg

```bash
cd ~/catkin_ws
git clone https://github.com/introlab/rtabmap_ros.git src/rtabmap_ros
catkin_make -j4
```

至此安装结束，但是catkin_make时可能遇到关于opencv_config的问题，原因是cmakelist中所需的opencv_contrib库未安装

![image-20221018234919719](/home/amas-lab-0/.config/Typora/typora-user-images/image-20221018234919719.png)

所以需要安装opencv_contrib中的optflow



### 5.安装opencv_contrib

本次使用的工控机中已安装3.4.1的opencv，需单独安装对应3.4.1版本的opencv_contrib，[下载opencv_contrib](https://github.com/opencv/opencv_contrib)，在branch中可找到相应的版本

（推荐直接直接重装更高级版本的opencv或尝试装3.4主分支的contrib，因为3.4.1版本的opencv_contrib的rgbd库存在问题）

安装参考：

https://blog.csdn.net/qq_42257666/article/details/123592033



cmake时可能遇到的问题：

1. permission denied： 加sudo

2. vgg_generated和boostdesc_bgm系列文件安装超时：

   在xfeatures2d的cmake文件中的下载地址有错，需要去[opencv/opencv_3rdparty](https://github.com/opencv/opencv_3rdparty)手动下载（注：需要切换到对应文件的分支），下载后解压到opencv_contrib/xfeatures2d/src，之后就不需要cmake了，直接make就行

​	

make时可能遇到的问题：

参考文章：https://blog.csdn.net/qq_34106574/article/details/81668193

如果是3.4.1版本的opencv_contrib，大概率会出现rgbd库的问题，一般为pyopencv_linemod.hpp和linemod.hpp的问题，如果是这种情况，上述文章中的解决方案不能解决问题，原因是3.4.1版本中少了一个[patch](https://github.com/opencv/opencv_contrib/commit/92fd42e58eaa7d902f94fb653de265af4b0ee44d)，目前测试出的修改方法是把3.4主分支的pyopencv_linemod.hpp复制到本地替换3.4.1版本opencv_contrib中的pyopencv_linemod.hpp，linemod.hpp保持不变（否则编译不通过），这样可以make通过，并且工作空间中catkin_make也正常编译，但未测试过如果使用rgbd库是否正常。所以更保险的做法应该还是直接安装高于3.4.1版本的opencv









