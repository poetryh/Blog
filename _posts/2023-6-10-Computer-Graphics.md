---
title: "computer graphics - 1Day"
header:
categories:
  - Book
tags:
  - fundamentals-of-computer-graphics-4th
---

### 1 Introduction  介绍

* #### 1.1 GraphicsAreas  图形学的研究领域
  建模（Modeling）：用数学的方式，利用一些插值规则 (interpolation rule) 把顶点（vertex）连接，同时反射（reflection）它 ，“描述”这个东西。
  
  渲染（Rendering）：从模型创建阴影图像（shaded images）。
  
  动画（Animation）：通过图像序列（sequences image）创建视错觉运动（illusion of motion）。

  Other：用户交互（UI），虚拟现实（VR），可视化（Visualization），图像处理（Image processing），3D扫描（3D scan），计算机摄影{利用计算机图形，视觉，图像处理实现的新式摄影}（photography）
-- --
* #### 1.2 Major Applications 主要应用领域
  游戏（Game）：越来越复杂的3D场景模型，以及光照渲染算法。
  
  卡通（CarToon）：包括利用三渲二场景，降低艺术家重复无意义的操作。
  
  视效（Visual effects）：利用3D建模与合成创建环境，足够真实让观众不会怀疑。
  
  动画片（Animated films）:许多技术与视效层面基本相同，不过不会过于真实。
  
  计算机辅助设计/建造（CAM/CAD）：利用计算机软件和硬件来帮助设计师创建、修改和分析产品的几种模型。
  
  模拟类（Simulation）：例：飞行，汽车，安全培训模拟。
  
  医学影像（Medical imaging）：例，CT。
  
  信息/数据可视化（Information visualization）：用图像给复杂的数据总结。
-- --
* ### 1.3 Graphics APIs 图形API[（应用程序接口-API）](https://www.redhat.com/zh/topics/api/what-are-application-programming-interfaces)
  API：预先定义好的函数集合，通过API可以让两个程序之间数据互通；而图形API就是更好的让GPU与其他硬件互通，最典型的例子有：
    
    * 图形与用户界面集合：例Java，其中UI和图形API完全集成，并标准化，直接在Java中被支持。
    * 仅图形：例Direct3D，OpenGL，UI完全独立，需要重新设计。
-- --
* ### 1.4 Graphics Pipeline 图形管线
  本质既是优化“渲染流水线”的过程，优化其过程，以及可读性。
    
      过程：读取顶点信息-处理信息-三角化顶点-光栅化-像素绘制
  
  图形管线中每一步都有值得分析的操作，其中最重要的一步即在坐标系中采取4x4的矩阵，前三列代表xyz位置，而最后一列使用齐次坐标（homogenous coordinate) 的技巧，主要服务于 3D空间内的坐标变换，这样坐标变换就可以轻松的用连续的矩阵相乘来表示（而不是一些加一些乘）。 又例如在光栅化的时候我们要决定哪一个物体更靠近摄像机并被绘制，在此会运用到一个z-buffer的技巧，即将物体到摄像机的距离算作z向量，记录每一个像素点内最近的z向量与对应的图形，加以绘制，过程比较像图论单元最短路问题中更新距离矩阵。
  -------
  就绘制效率而言，图形管线的速度基本与需绘制的三角形数量成正比。因此，减少需绘制的三角形就成为了一个优化速度的好方法。当绘制较远距离的场景时，经常会通过降低三角形的数量来优化速度，引申出了多层次细节（level of detail）这个概念。另一个例子是只绘画在摄像机前且未被遮挡的物体，这个技巧叫做面剔除(face-culling)。
  -- --
  &nbsp;

    [齐次坐标（homogenous coordinate) - 知乎 Ikuku](https://zhuanlan.zhihu.com/p/258437902)
    
    [多层次细节LOD - 知乎 菜鸡的图形学笔记](https://zhuanlan.zhihu.com/p/32700416)
    
    [面剔除（face-culling） - OpenGl Learn](https://learnopengl-cn.readthedocs.io/zh/latest/04%20Advanced%20OpenGL/04%20Face%20culling/#:~:text=%E5%A6%82%E6%9E%9C%E6%88%91%E4%BB%AC%E5%8E%BB%E6%83%B3%E8%B1%A1%E4%BB%BB%E4%BD%95,Face%20culling)
    
    [z缓冲（z-buffer） -  知乎 启思](https://zhuanlan.zhihu.com/p/344018798)
