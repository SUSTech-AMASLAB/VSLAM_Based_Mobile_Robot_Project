# intel Realsense深度相机的配置

配置主要分两部分，一部分是realsense SDK的安装，另一部分是realsense-ros的安装

### realsense SDK2.0安装

官方参考教程：https://github.com/IntelRealSense/librealsense/blob/development/doc/distribution_linux.md

csdn参考文章：

https://blog.csdn.net/qq_44305475/article/details/123686786

```bash
#安装
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE

sudo add-apt-repository "deb https://librealsense.intel.com/Debian/apt-repo $(lsb_release -cs) main" -u

sudo apt-get install librealsense2-dkms

sudo apt-get install librealsense2-utils
#验证
realsense-viewer
#检查是否安装成功
modinfo uvcvideo | grep "version:"
#检查版本是否更新，version后应有release字段才正确
```

### realsense-ros安装

官方参考教程：https://github.com/IntelRealSense/realsense-ros

csdn参考文章：

https://blog.csdn.net/qq_44305475/article/details/123686786

安装方法：

1.通过ROS distribution简易安装

```bash
sudo apt-get install ros-$ROS_DISTRO-realsense2-camera
sudo apt-get install ros-$ROS_DISTRO-realsense2-description
```

安装的功能包位置为/opt/ros/melodic/share

连接相机验证是否安装成功：

```bash
roslaunch realsense2_camera rs_camera.launch
#能正常运行
roslaunch realsense2_camera demo_pointcloud.launch
#会自动打开rviz并显示图像
```

2.在工作空间安装功能包

重新创建工作空间参考上述文档，已有工作空间参考以下命令：

```bash
cd ~/catkin_ws/src/
git clone https://github.com/IntelRealSense/realsense-ros.git
cd realsense-ros/
git checkout `git tag | sort -V | grep -P "^2.\d+\.\d+" | tail -1`
cd ..
sudo apt-get install ros-melodic-ddynamic-reconfigure
catkin_make clean
catkin_make -DCATKIN_ENABLE_TESTING=False -DCMAKE_BUILD_TYPE=Release
catkin_make install
```

安装的功能包位置为/catkin_ws/src

连接相机验证是否安装成功：

```bash
roslaunch realsense2_camera rs_camera.launch
#能正常运行
roslaunch realsense2_camera demo_pointcloud.launch
#会自动打开rviz并显示图像
```