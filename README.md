# VSLAM Based Mobile Robot System Project

> @Brief：该仓库是AMASLAB 基于视觉SLAM的移动机器人系统（VSLAM Based Mobile Robot  System）项目文档。
>
> @Author：[Dong Li](https://github.com/DoongLi)
>
> @Date：2022-10-13
>
> @Github Link：[https://github.com/SUSTech-AMASLAB/VSLAM_Based_Mobile_Robot_Project](https://github.com/SUSTech-AMASLAB/VSLAM_Based_Mobile_Robot_Project)
>
> @Project Author：[喻锦城](https://github.com/SunstanYu)、[Dong Li](https://github.com/DoongLi)

## Introduction

**Project**：VSLAM Based Mobile Robot  System / 基于视觉SLAM的移动机器人系统

 **Requirements**：

- 1.基于相关硬件，用**VSLAM的方案**构建场景地图，并完成自主导航等功能。
- 2.在本仓库上，撰写相关学习、调试、方案以及相关问题文档，并将能实现上述功能的可重复 系统框架 整合到仓库中。

**Device**：松灵TRACER-MINI移动底盘、EPIC-KBS9工控机、Intel Realsense D455深度相机（或者Intel Realsense T265双鱼眼相机）

## Outline

#### 1.阅读实验室协作项目文档

**Requirements**：掌握项目完成流程和相关要求。

**Reference**：[https://github.com/SUSTech-AMASLAB/AMASLAB_Collaboration_Project_Doc](https://github.com/SUSTech-AMASLAB/AMASLAB_Collaboration_Project_Doc)

#### 2.基础内容学习

 **Requirements**：linux（Ubuntu）、Python、C++、ROS

**Reference**：[https://github.com/SUSTech-AMASLAB/Tutorial_for_Direction_Of_Robotics](https://github.com/SUSTech-AMASLAB/Tutorial_for_Direction_Of_Robotics)

#### 3.相关硬件调试

项目相关硬件如下：

- 1.EPIC-KBS9工控机：[https://github.com/SUSTech-AMASLAB/EPIC-KBS9](https://github.com/SUSTech-AMASLAB/EPIC-KBS9)
- 2.松灵TRACER-MINI移动底盘：[https://github.com/SUSTech-AMASLAB/TRACER-MINI](https://github.com/SUSTech-AMASLAB/TRACER-MINI)
- 3.Intel Realsense D455深度相机（IMU）：[https://github.com/SUSTech-AMASLAB/Intel_Realsense_Device/blob/main/Intel_Realsense_D455.md](https://github.com/SUSTech-AMASLAB/Intel_Realsense_Device/blob/main/Intel_Realsense_D455.md)
- 4.Intel Realsense T265双鱼眼相机（IMU）：[https://github.com/SUSTech-AMASLAB/Intel_Realsense_Device/blob/main/Intel_Realsense_T265.md](https://github.com/SUSTech-AMASLAB/Intel_Realsense_Device/blob/main/Intel_Realsense_T265.md)

#### 4.项目参考方案实现

Reference :

- 1.rtabmap实现：https://github.com/introlab/rtabmap   
- 2.ExplORB-SLAM实现：https://github.com/JulioPlaced/ExplORB-SLAM

#### 5.整理相关项目资料

整理项目视频、图片、文档和工程代码 , **同时项目发布者和协同项目完成者制作项目主页** . 

## File Description

- **README.md**：项目总体文档，
- **VSLAM_Relate_Paper**：该文件夹下面存放了一些VSLAM的论文；如果你对VSLAM感兴趣，或者想了解相关原理以及实现方法，你可以参考该目录下的论文或者文件。
