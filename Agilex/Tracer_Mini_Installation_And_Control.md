# Agilex松灵机器人初始配置与键盘控制

官方文档https://github.com/agilexrobotics

官方产品介绍https://github.com/agilexrobotics/AgileX-Robotics-all-products-user-manuals

知乎参考资料https://zhuanlan.zhihu.com/p/550920775

官方csdn：https://blog.csdn.net/AgileX/article/details/106730024?spm=1001.2014.3001.5501

## 硬件配置

将usb接口接入工控机，**启动底盘电源**，开始配置系统

运行以下指令完成硬件配置

使能gs_usb kernel模块：

```bash
sudo modprobe gs_usb
#开机运行一次即可
```

使能can_to_sub并设置波特率：

```bash
# 安装依赖包
sudo apt install can-utils
# 连接
sudo ip link set can0 up type can bitrate 500000
#每次拔出重新连接CAN_TO_USB线都要设置
```

检测：

```bash
ifconfig -a
#出现can0则成功识别CAN_TO_USB线
candump can0
#监听到数据则成功连接底盘
```



## 功能包配置

安装编译工具和TUI监控工具

```bash
sudo apt install build-essential cmake
sudo apt install libncurses5-dev
```

安装依赖ros包

```bash
sudo apt install ros-melodic-controller-manager
sudo apt install ros-melodic-joint-state-publisher-gui 
sudo apt install -y libasio-dev
```

下载功能包

实验室的是tracer底盘所以需要tracer_ros包

```bash
# 下载代码
cd catkin_ws/src/
# 这个都一样，底盘驱动的sdk
git clone https://github.com/agilexrobotics/ugv_sdk.git  --recursive
# 下载自己需要的功能包
git clone https://github.com/agilexrobotics/tracer_ros.git
```

注：

tracer_ros包中有一处问题会编译不通过，注释掉才可以通过

问题在/catkin_ws/src/tracer_ros/tracer_gazebo_sim/CMakeLists.txt

![image-20220929111952100](/home/amas-lab-0/.config/Typora/typora-user-images/image-20220929111952100.png)

编译

```bash
cd ..
catkin_make
```



## 键盘控制机器人

首先需要安装功能包否则运行不了launch文件

```bash
sudo apt-get install ros-melodic-teleop-twist-keyboard
```

运行launch文件

```bash
roslaunch tracer_bringup tracer_robot_base.launch
#开启机器人base节点
roslaunch tracer_bringup tracer_teleop_keyboard.launch
#开启键盘控制节点
```

- q/z：增大/减小最大速度
- ｉ／，：控制小车直行 or 后退
- ｋ：停止运动（使用ctrl + z，效果相同）
- ｊ／ｌ：控制小车逆时针 or 顺时针旋转
- ｕ／ｏ：控制小车左转 or 右转
- m／. ：控制小车左后 or 右后倒车

## SDK 测试demo

首先编译文件

```bash
cd ugv_sdk/build
cmake ..
make
```

然后运行测试样例

```bash
cd ~/scout_ws/src/ugv_sdk/bulid
./bin/demo_tracer_robot can0
```

如果不加can0会运行失败并提示：

Usage: app_tracer_demo <interface>
Example 1: ./app_tracer_demo can0

正常运行会进行灯光测试和运动测试